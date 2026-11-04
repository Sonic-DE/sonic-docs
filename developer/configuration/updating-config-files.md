---
title: Updating KConfig files
description: Migrate your application's configuration files to a new layout with kconf_update.
source_url: https://invent.kde.org/documentation/develop-kde-org/-/blob/master/content/docs/features/configuration/updating_kconfig_files.md
source_authors: [Carl Schwan, Chris Holland, Mikhail Zolotukhin, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-frameworks-settings (src/kconf_update/kconf_update.cpp, KConfig::checkUpdate), sonic-daemon (kded6 KUpdateD), sonic-workspace d0b84fd142 (shell/kconf_update); the update file and compiled script below were built against SonicDE's KConfig and run with kconf_update --testmode
---

# Updating KConfig files

Sometimes you want to change how your application stores its settings: you split the application into several components, join several into one, or the old layout just didn't make sense.

Then the settings must move from the old layout to the new one. You could make the application read both and decide which to use, but if you changed the layout to simplify the code, that makes it more complicated instead.

If you store settings with KConfig, `kconf_update` updates the configuration files for you, without adding code to your application.

## How it works

Applications install *update files* (ending in `.upd`) in `${KDE_INSTALL_KCONFUPDATEDIR}`, usually `/usr/share/kconf_update`. An update file is divided into sections, each with a unique ID, and each section names a script that does the update.

SonicDE's kded (`kded6`, from `sonic-daemon`) runs `kconf_update` once when it starts and again whenever a file in the `kconf_update` directories changes. `kconf_update` keeps track in its own configuration file, `kconf_updaterc` (in `~/.config/`): for each update file, the IDs of the sections already done. Sections already done are skipped.

So if you replace an update file with a new version that adds a section, only the new section runs.

An application that doesn't rely on kded can start the update itself with [KConfig::checkUpdate()](/docs/api/kconfigcore/kconfig#checkUpdate), which runs `kconf_update --check` on the update file if the configuration doesn't record the update yet.

> **Note:** KDE Frameworks 5's `kconf_update` also had commands that moved and renamed groups and keys itself (`File=`, `Group=`, `Key=` and others), and could pipe configuration entries through a script. SonicDE's `kconf_update` (KDE Frameworks 6) only runs scripts: every change is made by your script, which opens and edits the configuration files itself. An update file that doesn't start with `Version=6` is rejected.

## The update file

An update file looks like this:

```ini
# Configuration update for MyApp
Version=6

Id=toolbuttonpopupmode-2026
Script=myapp-toolbuttonpopupmode-2026
```

Empty lines and lines starting with `#` are comments. The commands are:

- `Version=6` — required, before the first section: the file is written for this version of `kconf_update`.
- `Id=` — starts a section. Give it a name that says why the update is needed; including the year, as in `toolbuttonpopupmode-2026`, helps.
- `Script=<file>` or `Script=<file>,<interpreter>` — the script that does the update. With an interpreter (for example `Script=myapp-update.py,python3`), `kconf_update` finds the interpreter in the `PATH` and runs the script with it.
- `ScriptArguments=` — arguments to pass to the script; put it after `Script=`.

`kconf_update` looks for the script in the `kconf_update` data directories first (`${KDE_INSTALL_KCONFUPDATEDIR}`, where interpreted scripts go), then, for a script without interpreter, in `${KDE_INSTALL_LIBDIR}/kconf_update_bin/` (where compiled scripts go) and in the `PATH`. A script must finish within 60 seconds and exit with 0 on success.

SonicDE's own updates follow this pattern; the desktop shell's are in `sonic-workspace/shell/kconf_update`:

```ini
Version=6

Id=plasmashell-6.0-keep-custom-position-of-panels
Script=sonicshell-6.0-keep-custom-position-of-panels
```

## A compiled update script

A compiled script can use KConfig and any other C++ API, and doesn't need an interpreter at run time.

Say your application made the behavior of a KActionMenu configurable with the entries `delayed` and `stickyMenu`, and you switch to the newer `QToolButton::ToolButtonPopupMode`, stored as `popupMode`. This script migrates the old entries:

```cpp
#include <KConfigGroup>
#include <KSharedConfig>

#include <cstdlib>

// Replaces the delayed and stickyMenu entries of myapprc's [ActionMenuState] with popupMode.
int main()
{
    const KSharedConfigPtr config = KSharedConfig::openConfig(QStringLiteral("myapprc"), KConfig::SimpleConfig);
    KConfigGroup group(config, QStringLiteral("ActionMenuState"));
    if (!group.hasKey("delayed") && !group.hasKey("stickyMenu")) {
        return EXIT_SUCCESS;
    }

    // delayed => 0 (DelayedPopup)
    // !delayed && stickyMenu => 2 (InstantPopup)
    // !delayed && !stickyMenu => 1 (MenuButtonPopup, the default)
    const bool delayed = group.readEntry("delayed", true);
    const bool stickyMenu = group.readEntry("stickyMenu", true);
    const int popupMode = delayed ? 0 : (stickyMenu ? 2 : 1);
    if (popupMode != 1) {
        group.writeEntry("popupMode", popupMode);
    }
    group.deleteEntry("delayed");
    group.deleteEntry("stickyMenu");

    return config->sync() ? EXIT_SUCCESS : EXIT_FAILURE;
}
```

The update file is the one shown above. Your `CMakeLists.txt` installs both:

```cmake
find_package(ECM 6.0 REQUIRED NO_MODULE)
set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH})
include(KDEInstallDirs)
find_package(KF6 6.0 REQUIRED COMPONENTS Config)

install(FILES myapp.upd DESTINATION ${KDE_INSTALL_KCONFUPDATEDIR})

add_executable(myapp-toolbuttonpopupmode-2026 popupmode.cpp)
target_link_libraries(myapp-toolbuttonpopupmode-2026 KF6::ConfigCore)
install(TARGETS myapp-toolbuttonpopupmode-2026 DESTINATION ${KDE_INSTALL_LIBDIR}/kconf_update_bin/)
```

SonicDE's update scripts are built the same way (see `sonic-workspace/shell/kconf_update/CMakeLists.txt`).

## An interpreted update script

A script in a language such as Python works the same way: it opens the configuration file and changes it. Choose a language whose interpreter is available wherever your application runs, and remember that your application now depends on it. Install the script next to the update file, in `${KDE_INSTALL_KCONFUPDATEDIR}`, and name the interpreter in the update file:

```ini
Version=6

Id=no-more-double-negation-2026
Script=myapp-no-double-negation.py,python3
```

## Testing update files

Test an update file before you ship it: once users have run a broken update, it won't run again.

`kconf_update` is in `${KDE_INSTALL_LIBEXECDIR_KF}`, on most systems `/usr/lib64/libexec/kf6/kconf_update` or `/usr/lib/libexec/kf6/kconf_update`. It has these options:

- `--debug` prints what it does, including the content of each script it runs (for a compiled script that is binary noise).
- `--testmode` doesn't record sections as done, so every run runs them again, and switches Qt's standard paths to test mode: `kconf_update` then looks for its own files under `~/.qttest/` (configuration in `~/.qttest/config/`, scripts in `~/.qttest/share/kconf_update/`).

> **Warning:** Test mode only applies to `kconf_update` itself. The script it starts runs normally and edits your real configuration files. To test safely, run `kconf_update` with `HOME` (or `XDG_CONFIG_HOME`) pointing to a scratch directory that holds copies of the files.

For example, with the compiled script above:

```bash
mkdir -p ~/scratch/home/.config ~/scratch/home/.qttest/share/kconf_update
cp myapprc ~/scratch/home/.config/
cp build/myapp-toolbuttonpopupmode-2026 ~/scratch/home/.qttest/share/kconf_update/
HOME=~/scratch/home /usr/lib64/libexec/kf6/kconf_update --debug --testmode ./myapp.upd
```

The output ends with:

```text
kf.config.kconf_update: "myapp.upd" : Found new update "toolbuttonpopupmode-2026"
kf.config.kconf_update: "myapp.upd" : Running script "myapp-toolbuttonpopupmode-2026"
...
kf.config.kconf_update: Successfully ran "…/kconf_update/myapp-toolbuttonpopupmode-2026"
```

and `~/scratch/home/.config/myapprc` changes from

```ini
[ActionMenuState]
delayed=false
stickyMenu=true
```

to

```ini
[ActionMenuState]
popupMode=2
```

Test with a configuration file that holds only the entries you care about first, then with a real one from an installation of your application.

### Testing installed update files

Once the update works, build and install your application. kded notices the new update file and runs `kconf_update`; check the configuration file afterwards.

To run an installed update again, restore the old configuration file and remove the update file's group (named after the `.upd` file) from `~/.config/kconf_updaterc`. `kconf_update` then runs it again the next time it is started, for example by running it by hand without arguments.

### Debug output

`kconf_update` logs to the category `kf.config.kconf_update`. When kded runs it in the background, enable that category to see its output, for example with a `[Rules]` group in `~/.config/QtProject/qtlogging.ini`:

```ini
[Rules]
kf.config.kconf_update=true
```

## Doing other things than updating configuration

A script doesn't have to change configuration files: it can, for example, rebuild another service's database when the user updates your application. Be careful with that, since the script may run in the background at any time kded starts.

## More examples

Other applications' update files and scripts are good examples. The installed update files are in `/usr/share/kconf_update`; SonicDE's own are in the repositories, for example `sonic-workspace/shell/kconf_update`.
