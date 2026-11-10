---
title: Sonic Init Info
description: Find out at runtime which init system, service manager and seat manager a machine runs, instead of assuming systemd.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-init-info (README.md, src/initinfo.h); written from the code, not run"
---

# Sonic Init Info

SonicDE runs on systemd, OpenRC, runit, s6, dinit, sysvinit and the BSDs.
[Sonic Init Info](/docs/api/sonicinitinfo/sonicinitinfo-index), in `sonic-frameworks-init-info`
(`find_package(SonicInitInfo)`, `Sonic::InitInfo`), tells a component at runtime which of them the
machine is running, so it can do the right thing instead of assuming systemd. It needs Qt Core and
[Sonic Logging](sonic-logging.md); Qt D-Bus is optional.

```cmake
find_package(SonicInitInfo REQUIRED)
target_link_libraries(myapp PRIVATE Sonic::InitInfo)
```

```cpp
#include <Sonic/InitInfo/InitInfo>

using namespace Sonic::InitInfo;

if (serviceManager() == ServiceManager::OpenRC) {
    // use rc-service and rc-update
}
if (seatManager() == SeatManager::Elogind) {
    // elogind-specific session handling
}
```

## What it reports

All functions are in the `Sonic::InitInfo` namespace.

| Function | Returns |
| --- | --- |
| `pid1()` | The init process itself, a `Pid1`: `Systemd`, `SysVinit`, `OpenRCInit`, `RunitInit`, `S6LinuxInit`, `Dinit`, `Busybox`, `BsdInit` or `Unknown`. |
| `serviceManager()` | What actually manages services, a `ServiceManager`: `Systemd`, `OpenRC`, `Runit`, `S6`, `Dinit`, `SysVinit`, `BsdRc`, `OpenBsdRc` or `Unknown`. It can differ from PID 1: OpenRC commonly runs under sysvinit. |
| `seatManager()` | A `SeatManager`: `SystemdLogind`, `Elogind`, `ConsoleKit2`, `Seatd` or `None`. |
| `hasJournald()` | Whether journald's native socket exists. |
| `defaultInitialVt(manager)` | The virtual terminal a display manager starts on: 2 where getty usually owns VT 1 (OpenRC, runit, s6), else 1. |
| `name(value)` | A name for any of the values above, for logging and display. |

## How it decides

- PID 1 comes from `/proc/1/comm`, or from where the `/sbin/init` symlink points when `/proc` hides it.
- The service manager comes from PID 1 and that init's own configuration, such as `/etc/inittab`.
- The seat manager is found by looking for its running daemon. When the library is built with Qt
  D-Bus, who owns the name on the system bus is an extra signal.

It only reads stable sources, not transient runtime files, and needs no root. Nothing is cached, so keep
the result if you need it more than once.

In containers and sandboxes PID 1 is the sandbox's helper, so `Unknown` and `None` are normal results:
always handle them.

`pid1()`, `serviceManager()`, `seatManager()` and `hasJournald()` take an optional `Environment`, whose `procRoot` and `fsRoot` point the detection at
another tree and whose `useDBus` turns the D-Bus check off. Tests use it with a fake tree.

The library logs its decisions under the component `org.sonicde.frameworks.initinfo`. Turn the debug
messages on with `QT_LOGGING_RULES="org.sonicde.frameworks.initinfo.debug=true"`.
