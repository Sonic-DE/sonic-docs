---
title: "KDBusService Class"
description: "KDBusService takes care of registering the current process with D-Bus."
---

# KDBusService Class

[KDBusService](kdbusservice.md) takes care of registering the current process with D-Bus. [More...](#details)

- **Header:** `#include <KDBusService>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS DBusAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::DBusAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kdbusservice-members.md)

## Public Types

- [enum KDBusService::StartupOption](#StartupOption-enum)

## Public Functions

- [KDBusService(KDBusService::StartupOptions options = Multiple, QObject \*parent = nullptr)](#KDBusService)
- [~KDBusService()](#dtor.KDBusService)
- [QString errorMessage() const](#errorMessage)
- [bool isRegistered() const](#isRegistered)
- [QString serviceName() const](#serviceName)
- [void setExitValue(int value)](#setExitValue)

## Public Slots

- [void unregister()](#unregister)

## Signals

- [void activateActionRequested(const QString &actionName, const QVariant &parameter)](#activateActionRequested)
- [void activateRequested(const QStringList &arguments, const QString &workingDirectory)](#activateRequested)
- [void openRequested(const QList\<QUrl\> &uris)](#openRequested)

## Detailed Description {#details}

This registers the application at a predictable location on D-Bus, registers the [QCoreApplication](https://doc.qt.io/qt-6/qcoreapplication.html) (or subclass) object at /MainApplication, and assists in implementing the application side of D-Bus activation from the [Desktop Entry Specification](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html).

An application can either work in Multiple mode or Unique mode.

In Multiple mode, the application can be launched many times. The service name in the D-Bus registration will contain the PID to distinguish the various instances; for example: *org.kde.konqueror-12345*.

In Unique mode, only one instance of this application can ever run. The first instance of the application registers with D-Bus without the PID, and any attempt to run the application again will cause the [activateRequested](kdbusservice.md#activateRequested)() signal to be emitted in the already-running instance; the duplicate instance will then quit. The exit value can be set by the already running instance with [setExitValue](kdbusservice.md#setExitValue)(), the default value is `0`.

Unique-mode applications should usually delay parsing command-line arguments until after creating a [KDBusService](kdbusservice.md) object; that way they know they are the original instance of the application.

Applications that set the D-Bus activation entry (`DBusActivatable=true`) in their desktop files will use Unique mode and connect to the signals emitted by this class. Note that the D-Bus interface is exported for Multiple-mode applications as well, so it also makes sense for such applications to connect to the signals emitted by this class.

> **Note:** In order to avoid a race, the application should export its objects to D-Bus before allowing the event loop to run (for example, by calling [QCoreApplication::exec](https://doc.qt.io/qt-6/qcoreapplication.html#exec)()). Otherwise, the application will appear on the bus before its objects are accessible via D-Bus, which could be a problem for other applications or scripts which start the application in order to talk D-Bus to it immediately.

Example usage:

```cpp
QApplication app(argc, argv);
app.setApplicationName("kuiserver");
app.setOrganizationDomain("kde.org");
// Create your D-Bus objects here
// ...
KDBusService service(KDBusService::Unique);
// If this point is reached, this is the only running instance
// i.e. org.kde.kuiserver has been registered
return app.exec();
```

## Member Type Documentation {#member-type-documentation}

### enum KDBusService::StartupOption {#StartupOption-enum}

**flags KDBusService::StartupOptions**

Options to control the behaviour of [KDBusService](kdbusservice.md)

| Constant | Value | Description |
| --- | --- | --- |
| `KDBusService::Unique` | `1` | Indicates that only one instance of this application should ever exist. Cannot be combined with `Multiple`. |
| `KDBusService::Multiple` | `2` | Indicates that multiple instances of the application may exist. Cannot be combined with `Unique`. This is the default. |
| `KDBusService::NoExitOnFailure` | `4` | Indicates that the application should not exit if it failed to register with D-Bus. If not set, [KDBusService](kdbusservice.md) will quit the application if it failed to register the service with D-Bus or a `Unique` instance can not be activated. A `Multiple` instance will exit with error code `1`. The exit value of a `Unique` instance can be set from the running instance with [setExitValue](kdbusservice.md#setExitValue)(), the default value is `0`. |
| `KDBusService::Replace (since Qt 5.65)` | `8` | Indicates that if there's already a unique service running, to be quit and replaced with our own. If exported, it will try first quitting the service calling `org.qtproject.Qt.QCoreApplication.quit`, which is exported by [KDBusService](kdbusservice.md) by default. |

The `StartupOptions` type is a typedef for `QFlags<StartupOption>. `It stores an OR combination of `StartupOption` values.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KDBusService::KDBusService(KDBusService::StartupOptions *options* = Multiple, QObject \**parent* = nullptr) {#KDBusService}

Tries to register the current process to D-Bus at an address based on the application name and organization domain under the given `parent`.

The D-Bus service name is the reversed organization domain, followed by the application name. If `options` includes the `Multiple` flag, the application PID will be appended. For example:

```cpp
app.setApplicationName("kuiserver");
app.setOrganizationDomain("kde.org");
```

The above will make [KDBusService](kdbusservice.md) register as `org.kde.kuiserver` in `Unique` mode, and `org.kde.kuiserver-1234` (if the process has PID `1234`) in `Multiple` mode.

### \[override virtual noexcept\] KDBusService::~KDBusService() {#dtor.KDBusService}

Destroys this object (but does not unregister the application).

Deleting this object before [unregister](kdbusservice.md#unregister)() could confuse clients, who will see the service on the bus but will be unable to use the activation methods.

### \[signal\] void KDBusService::activateActionRequested(const QString &*actionName*, const QVariant &*parameter*) {#activateActionRequested}

Signals that an application action `actionName` should be triggered with the given `parameter`.

This signal is emitted to request handling of the respective method of the D-Bus activation. For GUI applications, the signal handler also needs to deal with any platform-specific startup ids and make sure the mainwindow is shown as well as request its activation from the window manager. See documentation of [activateRequested](kdbusservice.md#activateRequested)(const [QStringList](https://doc.qt.io/qt-6/qstringlist.html) &arguments, const [QString](https://doc.qt.io/qt-6/qstring.html) &) for details.

See the desktop entry specification for more information about action activation.

### \[signal\] void KDBusService::activateRequested(const QStringList &*arguments*, const QString &*workingDirectory*) {#activateRequested}

Signals that the application is to be activated.

If this is a `Unique` application, when [KDBusService](kdbusservice.md) is constructed in subsequent instances of the application (ie: when the executable is run when an instance is already running), it will cause this signal to be emitted in the already-running instance (with the arguments passed to the duplicate instance), and the duplicate instance will then exit.

If this application's desktop file indicates that it supports D-Bus activation (DBusActivatable=true), a command launcher may also call the Activate() D-Bus method to trigger this signal. In this case, `arguments` will be empty.

In single-window applications, the connected signal should typically raise the window.

`arguments` The arguments the executable was called with, starting with the executable file name. See [QCoreApplication::arguments](https://doc.qt.io/qt-6/qcoreapplication.html#arguments)(). This can be empty.

`workingDirectory` The directory from which the executable is called. This can be empty.

A typical implementation of the signal handler would be:

```cpp
if (!arguments.isEmpty()) {
    commandLineParser->parse(arguments); // same QCommandLineParser instance as the one used in main()
    handleCmdLine(workingDirectory); // shared method with main(), which uses commandLineParser to handle options and positional arguments
}
```

For GUI applications, the handler also needs to deal with any platform-specific startup ids and make sure the mainwindow is shown as well as request its activation from the window manager. For X11, [KDBusService](kdbusservice.md) makes the id for the Startup Notification protocol available from QX11Info::nextStartupId(), if there is one. For Wayland, [KDBusService](kdbusservice.md) provides the token for the XDG Activation protocol in the "XDG\_ACTIVATION\_TOKEN" environment variable and unsets it again after the signal, if there is one. The util method `KWindowSystem::updateStartupId(QWindow *window)` (since KF 5.91) takes care of that. A typical implementation in the signal handler would be:

```cpp
mainWindow->show();
KWindowSystem::updateStartupId(mainWindow->windowHandle());
mainWindow->raise();
KWindowSystem::activateWindow(mainWindow->windowHandle());
```

If you're using the builtin handling of `--help` and `--version` in [QCommandLineParser](https://doc.qt.io/qt-6/qcommandlineparser.html), you should call parser.process(arguments) before creating the [KDBusService](kdbusservice.md) instance, since parse() doesn't handle those (and exiting the already-running instance would be wrong anyway).

*See also* [setExitValue](kdbusservice.md#setExitValue)()

### QString KDBusService::errorMessage() const {#errorMessage}

Returns the error message from the D-Bus registration if it failed.

Note that this is only useful when specifying the option [NoExitOnFailure](kdbusservice.md#StartupOption-enum). Otherwise the process has quit by the time you can get a chance to call this.

### bool KDBusService::isRegistered() const {#isRegistered}

Returns true if the D-Bus registration succeeded.

Note that this is only useful when specifying the option [NoExitOnFailure](kdbusservice.md#StartupOption-enum). Otherwise, the simple fact that this process is still running indicates that the registration succeeded.

### \[signal\] void KDBusService::openRequested(const QList\<QUrl\> &*uris*) {#openRequested}

Signals that one or more files should be opened in the application.

This signal is emitted to request handling of the respective method of the D-Bus activation. For GUI applications, the signal handler also needs to deal with any platform-specific startup ids and make sure the mainwindow is shown as well as request its activation from the window manager. See documentation of [activateRequested](kdbusservice.md#activateRequested)(const [QStringList](https://doc.qt.io/qt-6/qstringlist.html) &arguments, const [QString](https://doc.qt.io/qt-6/qstring.html) &) for details.

`uris` The URLs of the files to open.

### QString KDBusService::serviceName() const {#serviceName}

Returns the name of the D-Bus service registered by this class. Mostly useful when using the option Multiple.

### void KDBusService::setExitValue(int *value*) {#setExitValue}

Sets the exit value to be used for a duplicate instance.

If this is a `Unique` application, a slot connected to [activateRequested](kdbusservice.md#activateRequested)() can use this to specify a non-zero exit value for the duplicate instance. This would typically be done if invalid command-line arguments are passed.

Note that this will only work if the signal-slot connection type is [Qt::DirectConnection](https://doc.qt.io/qt-6/qt.html#ConnectionType-enum).

`value` The exit value for the duplicate instance.

### \[slot\] void KDBusService::unregister() {#unregister}

Manually unregister the given [serviceName](kdbusservice.md#serviceName) from D-Bus.
