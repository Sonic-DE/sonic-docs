---
title: Sonic Logging
description: Log from SonicDE code with one handler per program, per-program log files, journald and rotation, on any init system.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-logging (README.md, src/logging.h, src/log.h, src/logging.cpp), sonic-desktop-interface (sonic_logging_autoinstall.cpp), sonic-screenlocker (greeter/worker/main.cpp), sonic-frameworks-doctools (src/docbook2markdown/main.cpp, src/meinproc.cpp); written from the code, not run"
---

# Sonic Logging

[Sonic Logging](/docs/api/soniclogging/soniclogging-index), in `sonic-frameworks-logging`
(`find_package(SonicLogging)`, `Sonic::Logging`), is how SonicDE code logs. It installs one Qt message
handler per program, which writes the program's own log file, also sends to journald where it runs,
and needs neither systemd nor libsystemd. It replaces Qt logging categories, `qCDebug()` and custom
message handlers in SonicDE code.

Where the logs end up, from a user's point of view, is described in [Logs](../../user/administration/logs.md).

## Logging from your code

Declare the binary's component once, in exactly one `.cpp` of each library, plugin or executable, and
log with the `sonic*()` macros anywhere in that binary:

```cpp
#include <Sonic/Logging/Log>

SONIC_LOGGING_COMPONENT("org.sonicde.myplugin")

void Thing::load()
{
    sonicDebug() << "loading" << m_path;
    if (!ok) {
        sonicWarning() << "can't read" << m_path;
    }
}
```

- `sonicDebug()`, `sonicInfo()`, `sonicWarning()` and `sonicCritical()` log under the component.
  `sonicFatal()` logs a critical line and then aborts; logging rules can't turn it off.
- The component is a `QLoggingCategory`, private to the binary that declares it, so each shared object
  logs under its own name. A second declaration in the same binary, or none, is a link error.
- Debug messages are on by default only in debug builds of the declaring code. Turn them on otherwise
  with `QT_LOGGING_RULES="org.sonicde.myplugin.debug=true"`. `sonicLoggingComponent().isDebugEnabled()`
  tells you whether they're on, for example to skip expensive work.
- `<Sonic/Logging/Log>` is all the macros need. Keep `<QDebug>` only when the file uses the type itself,
  for example to declare a `QDebug operator<<`.

In CMake, link `Sonic::Logging`, and add `sonicde/sonic-frameworks-logging` to the package manifest's
`depends` in sonicde-builder:

```cmake
find_package(SonicLogging REQUIRED)
target_link_libraries(myplugin PRIVATE Sonic::Logging)
```

## Installing the handler

### In an executable

Call `install()` early in `main()`. It works before the `Q*Application` exists, and returns the
handler that was in place before, for callers that restore it:

```cpp
#include <Sonic/Logging/Logging>

SONIC_LOGGING_COMPONENT("org.sonicde.myapp")

int main(int argc, char **argv)
{
    Sonic::Logging::install();
    QApplication app(argc, argv);
    sonicInfo() << "started";
    return app.exec();
}
```

A second `install()` returns `nullptr` and changes nothing. `logFilePath()` returns the chosen file, or
an empty string when a service manager collects the output.

### In a plugin

A plugin loaded into a host that doesn't install a handler itself, such as `sonicshell` loading
widgets, uses `SONIC_LOGGING_AUTO_INSTALL()` next to its component:

```cpp
#include <Sonic/Logging/Logging>

SONIC_LOGGING_COMPONENT("org.sonicde.myplugin")
SONIC_LOGGING_AUTO_INSTALL()
```

Messages then go to the host's log file, named after the host program. An automatic install never
replaces a handler the host installed, and an explicit `install()` always wins over it. The macro takes
an optional `void()` function, which runs once at the same point, even in plugins loaded after the
application started. sonic-desktop-interface shares one such file, `sonic_logging_autoinstall.cpp`,
between its plugins, each passing its own component ID.

### In tests

Test binaries that compile logging sources declare their own component and don't call `install()`.

## Options

`install()` takes `Sonic::Logging::Options`. Set only the members you change:

| Option | Default | What it does |
| --- | --- | --- |
| `binaryName` | the program's name | Names the log file. The screen locker's worker uses `kscreenlocker_worker-<service>`, so that workers for different sign-in methods keep separate logs. |
| `journald` | `true` | Also send to journald when its socket exists. |
| `rotationSizeBytes` | `2097152` (2 MiB) | Rename the file to `<file>.last` once it passes this size. Zero or less turns this off. |
| `rotateOnStartup` | `false` | Also rotate to `.last` on every start. A program running as root then rotates only on startup, not by size. |
| `writeLogFile` | `true` | Write the program's own file. Tools that run inside package builds set it to `false`, so they never create `/var/log/sonic` or a file in the build user's home. Lines then go to stderr and journald. |
| `mirrorToStderrWhenTty` | `true` | Mirror lines to stderr when it's a terminal. |
| `mirrorToStderr` | `false` | Mirror lines to stderr even when it isn't a terminal, for command-line tools whose stderr a build or script reads. Ignored when a service manager collects the output, or stderr is the journal. |
| `dropDebugCategoryPrefixes`, `dropDebugCategoryExact`, `dropDebugMessageSubstrings` | Qt, KF and window manager noise | Debug messages that are dropped. SonicDE's own `org.sonicde.*` debug messages are never dropped, and warnings and errors never are. |

For example:

```cpp
Sonic::Logging::install({.rotateOnStartup = true});      // the login manager's programs
Sonic::Logging::install({.mirrorToStderr = true});       // docbook2markdown6, run by CI
Sonic::Logging::install({.writeLogFile = false});        // meinproc6, run inside package builds
```

## Where lines go

- **Files:** `~/.local/state/sonic/<binary>.log` (`$XDG_STATE_HOME/sonic/`, mode 0600) for ordinary
  programs; `/var/log/sonic/<binary>.log` for programs running as root. Packagers can move the root
  directory with `-DSONIC_LOGGING_ROOT_DIR=…`, and `rootLogDirectory()` returns it. The root directory is
  created root-owned with mode 0755. An untrusted one (another owner, a symlink, writable by group or
  others) is moved aside to `/var/log/sonic.untrusted-<timestamp>` and never reused.
- **journald**, in addition, through its native protocol. Entries carry `SYSLOG_IDENTIFIER` (the binary
  name), `PRIORITY`, `SONIC_COMPONENT`, `QT_CATEGORY` and, where available, `CODE_*`.
- **Service managers:** when systemd, runit, s6, OpenRC's supervise-daemon or dinit collects the program's
  output, or it goes to `~/.xsession-errors`, lines go there and no own file is written. A shell pipe or
  redirect never counts. A stalled reader costs log lines, never a hung program.
- **stderr** mirrors the lines when it's a terminal, and is the fallback when no file can be written.
- No syslog.

Each line reads `<timestamp> (DD|II|WW|EE) [<source>] <message>`. The source is the category for the
program's own messages, the library's ID for a library's messages, and the binary name for messages
without a category.

Root services call `Sonic::Logging::prepareRootLogDirectory()` before their service manager opens a
log inside `/var/log/sonic`. The login manager does this with `soniclogin --prepare-log-directory` in
its OpenRC, runit, s6 and dinit service files.
