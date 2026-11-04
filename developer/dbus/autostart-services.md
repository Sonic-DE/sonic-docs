---
title: D-Bus autostart services
description: Let the D-Bus daemon start your application when a call is made to its service (D-Bus service activation), and install the service file with CMake.
source_url: https://develop.kde.org/docs/features/d-bus/dbus_autostart_services/
source_authors: [Carl Schwan, Mikhail Zolotukhin, Thiago Sueto, Tobias Fella]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-frameworks-cmake-modules (ECMGenerateDBusServiceFile, KDEInstallDirsCommon), sonic-workspace d0b84fd142 (krunner, ksecretprompter)
---

# D-Bus autostart services

The D-Bus daemon can start an application when a call is made to a service it provides and it isn't running yet. This is called D-Bus service activation. This page shows how to make your application such an autostart service and install it with CMake.

## How it works

When a message arrives for delivery, the D-Bus daemon looks for the service it is addressed to on the bus it was sent on.

If no such service is registered, the daemon looks through the `.service` files in the services directory of its data path, such as `/usr/share/dbus-1/services`, for one with the matching service name. That file says which program to start. The daemon starts it, waits until it has registered the service, and then (if all goes well) delivers the message.

The application that sent the message doesn't notice any of this.

## Writing a service file

Service files are simple `.ini`-style files, much like `.desktop` files.

A valid service file:

- ends with `.service`
- has a `[D-BUS Service]` group
- has a `Name` and an `Exec` key

For an application called MyApp, the file could look like this:

```ini
[D-BUS Service]
Name=org.foo.myapp
Exec=/usr/bin/myapp
```

`Name` and `Exec` look like the keys of a `.desktop` file, but unlike there, `Exec` must give the full path of the program to start.

With this file, a message to the `org.foo.myapp` service while that service isn't registered starts `/usr/bin/myapp`. It is then up to MyApp to register the service on the bus.

## Installing the service file

The full path in `Exec` depends on the install prefix, which is only known when the project is configured, so let CMake write the file.

### With ecm_generate_dbus_service_file (preferred)

SonicDE's CMake modules have a function that writes and installs the file in one step. SonicDE's own packages use it; KRunner's `CMakeLists.txt` (in `sonic-workspace/krunner`), for example, installs `org.kde.krunner.service` with it. For MyApp:

```cmake
include(ECMGenerateDBusServiceFile)

ecm_generate_dbus_service_file(
    NAME org.foo.myapp
    EXECUTABLE ${KDE_INSTALL_FULL_BINDIR}/myapp
    DESTINATION ${KDE_INSTALL_DBUSSERVICEDIR}
)
```

This generates `org.foo.myapp.service` and installs it to the D-Bus services directory. `EXECUTABLE` must be an absolute path, so use the `_FULL_` variant of the `KDEInstallDirs` variable. A program installed elsewhere works the same way; SonicDE's secret prompter uses `${KDE_INSTALL_FULL_LIBEXECDIR}/ksecretprompter`.

### With configure_file

You can also write the file yourself. Keep it in the source tree with an extra suffix such as `.in`, so the build can fill in the path without overwriting your source file. For MyApp, create `org.foo.myapp.service.in`:

```ini
[D-BUS Service]
Name=org.foo.myapp
Exec=@KDE_INSTALL_FULL_BINDIR@/myapp
```

and add to `CMakeLists.txt`:

```cmake
configure_file(org.foo.myapp.service.in
               ${CMAKE_CURRENT_BINARY_DIR}/org.foo.myapp.service)
install(FILES ${CMAKE_CURRENT_BINARY_DIR}/org.foo.myapp.service
        DESTINATION ${KDE_INSTALL_DBUSSERVICEDIR})
```

Either way, installing the project (`cmake --install`) puts a complete service file in the right place, and D-Bus starts your application whenever it is needed.
