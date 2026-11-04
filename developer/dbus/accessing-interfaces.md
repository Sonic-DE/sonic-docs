---
title: Accessing D-Bus interfaces
description: Calling D-Bus methods and connecting to D-Bus signals with Qt D-Bus.
source_url: https://develop.kde.org/docs/features/d-bus/accessing_dbus_interfaces/
source_authors: [Alicia Boya García, Carl Schwan, Marius P, Mikhail Zolotukhin, Thiago Sueto, Tobias Fella]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: Qt 6.11 documentation, sonic-frameworks-cmake-modules, sonic-screenlocker 0ed103d7, sonic-workspace d0b84fd142, sonic-frameworks-widgets-addons
---

# Accessing D-Bus interfaces

D-Bus lets applications offer their internal API to other processes. Those APIs can be used at run time from command-line tools or from D-Bus libraries and bindings. This page shows the second way, with examples you can use in your applications.

## Using QDBusMessage

[QDBusMessage](https://doc.qt.io/qt-6/qdbusmessage.html) is a D-Bus message that can be sent, or has been received, on a bus. Each message has one of four types, depending on its purpose:

- method call
- signal
- reply
- error

[QDBusMessage::MessageType](https://doc.qt.io/qt-6/qdbusmessage.html#MessageType-enum) lists them, and [QDBusMessage::type()](https://doc.qt.io/qt-6/qdbusmessage.html#type) returns a message's type.

### Calling a D-Bus method

You can call a method of a D-Bus service with a message made by the static function

```cpp
QDBusMessage::createMethodCall(const QString &service, const QString &path, const QString &interface, const QString &method)
```

It returns a [QDBusMessage](https://doc.qt.io/qt-6/qdbusmessage.html) that you then send.

The `interface` may be left empty when the method name is unique on the object at `path`. When two interfaces of the object have a method of the same name, the result is undefined: either may be called, or an error returned. So pass the interface whenever the object has more than one.

For example, to call the (fictional) `ping` method of the `/network` object of the `org.foo.bar` service:

```cpp
QDBusMessage m = QDBusMessage::createMethodCall("org.foo.bar",
                                                "/network",
                                                "",
                                                "ping");
bool queued = QDBusConnection::sessionBus().send(m);
```

The last line queues the message for sending on the session bus; the returned `bool` says whether queueing worked.

That leaves two questions:

- How do you pass parameters with a method call?
- How do you get the return value of a method that has one?

### Passing parameters

To send arguments with the call, put them in a `QList<QVariant>` and set it on the message. If `ping` took a host name:

```cpp
QDBusMessage m = QDBusMessage::createMethodCall("org.foo.bar",
                                                "/network",
                                                "",
                                                "ping");
QList<QVariant> args;
args.append("sonicde.org");
m.setArguments(args);
bool queued = QDBusConnection::sessionBus().send(m);
```

[QDBusMessage](https://doc.qt.io/qt-6/qdbusmessage.html) also has `operator<<` for appending arguments, which makes this shorter:

```cpp
QDBusMessage m = QDBusMessage::createMethodCall("org.foo.bar",
                                                "/network",
                                                "",
                                                "ping");
m << "sonicde.org";
bool queued = QDBusConnection::sessionBus().send(m);
```

> **Note:** The arguments must be in the order the D-Bus method expects them.

### Getting replies

To receive what the method returns, use [QDBusConnection::call()](https://doc.qt.io/qt-6/qdbusconnection.html#call) instead of `send()`. It blocks until the reply arrives or the call times out. If `ping` returned information about the host:

```cpp
QDBusMessage m = QDBusMessage::createMethodCall("org.foo.bar",
                                                "/network",
                                                "",
                                                "ping");
m << "sonicde.org";
QDBusMessage response = QDBusConnection::sessionBus().call(m);
```

The response is of type `QDBusMessage::ReplyMessage` when the call succeeded and `QDBusMessage::ErrorMessage` when it failed. [QDBusMessage::arguments()](https://doc.qt.io/qt-6/qdbusmessage.html#arguments) returns the returned values as a `QList<QVariant>`.

### Is this the best way?

Calling remote methods with [QDBusMessage](https://doc.qt.io/qt-6/qdbusmessage.html) directly is neither the easiest nor the recommended way. The next sections show the more convenient [QDBusInterface](https://doc.qt.io/qt-6/qdbusinterface.html) class, and then classes generated from XML, which let you call remote interfaces like local functions.

## Using QDBusInterface

> **Warning:** This section is for learning only. **Avoid QDBusInterface, especially in graphical applications.** Its constructor makes a blocking call to introspect the remote object ("obtain the description of the remote interface", in Qt's words; [QTBUG-14485](https://bugreports.qt.io/browse/QTBUG-14485), still open). **Classes generated from D-Bus XML, explained later, don't have this problem**, because they know the interface at compile time.
>
> These blocking calls are worst when they set up interfaces to services that aren't essential: each one is a round trip to the process providing the service. At best your application loads a little slower; at worst a hung service blocks it until the D-Bus timeout, usually 25 seconds, runs out.

[QDBusInterface](https://doc.qt.io/qt-6/qdbusinterface.html) is a simple, direct way to make D-Bus calls and connect to D-Bus signals.

A [QDBusInterface](https://doc.qt.io/qt-6/qdbusinterface.html) object represents one D-Bus interface. Its constructor takes a service name, an object path, optionally an interface name, optionally the connection (the session bus by default) and optionally a parent. With an empty interface name, the object merges all the interfaces found by introspecting the remote object.

Pass the interface name explicitly. With an empty name, every QDBusInterface you create introspects the remote object again; with a name, Qt D-Bus caches the description and reuses it for later objects of the same interface.

[QDBusInterface](https://doc.qt.io/qt-6/qdbusinterface.html) is a [QObject](https://doc.qt.io/qt-6/qobject.html), so you can give it a parent and let Qt delete it with the parent.

Here is an example, explained part by part below:

```cpp
const QString hostname = QStringLiteral("sonicde.org");
QDBusConnection bus = QDBusConnection::sessionBus();
auto *interface = new QDBusInterface("org.foo.bar",
                                     "/network",
                                     "org.foo.bar.network",
                                     bus,
                                     this);

interface->call("ping");
interface->call("ping", hostname);

QList<QVariant> args;
args.append(hostname);
interface->callWithArgumentList(QDBus::Block, "ping", args);

QDBusReply<int> reply = interface->call("ping", hostname);

if (reply.isValid()) {
    KMessageBox::information(this,
                             i18n("Ping to %1 took %2 s", hostname, reply.value()),
                             i18n("Pinging %1", hostname));
}

args.clear();
interface->callWithCallback("listInterfaces", args,
                            this,
                            SLOT(interfaceList(QStringList)),
                            SLOT(interfaceListError(QDBusError)));

connect(interface, SIGNAL(interfaceUp(QString)),
        this, SLOT(interfaceUp(QString)));
```

### Synchronous calls

First the example creates a [QDBusInterface](https://doc.qt.io/qt-6/qdbusinterface.html) for the same object as the QDBusMessage examples above.

It then calls methods of that object in several ways. The first `call("ping")` has no arguments; the second passes one. [call()](https://doc.qt.io/qt-6/qdbusabstractinterface.html#call) takes any number of arguments, as long as each converts to [QVariant](https://doc.qt.io/qt-6/qvariant.html) (before Qt 5.14 it took at most eight).

When the arguments are already in a `QList<QVariant>`, use [callWithArgumentList()](https://doc.qt.io/qt-6/qdbusabstractinterface.html#callWithArgumentList) instead, as the example does next.

### Handling replies

The next `call("ping", hostname)` keeps the reply in a [QDBusReply](https://doc.qt.io/qt-6/qdbusreply.html). The example checks that the reply is valid (no error was returned and the value really is an `int`) and shows the result in a message box.

### Asynchronous calls and signals

All the calls so far were synchronous: the application waits until the reply arrives. The last two uses of [QDBusInterface](https://doc.qt.io/qt-6/qdbusinterface.html) in the example are asynchronous, and both use Qt's signals and slots.

[callWithCallback()](https://doc.qt.io/qt-6/qdbusabstractinterface.html#callWithCallback) returns as soon as the call is queued, so the application doesn't block. When the reply arrives, Qt calls the `interfaceList` slot with the returned values; if the call fails, it calls `interfaceListError` with the [QDBusError](https://doc.qt.io/qt-6/qdbuserror.html). This function needs a `QList<QVariant>` for the arguments. (An older overload without the error slot is deprecated.)

Finally the example connects to a D-Bus signal, just like connecting to a local signal, with [QObject::connect()](https://doc.qt.io/qt-6/qobject.html#connect). QDBusInterface adds the signals the D-Bus interface advertises to its meta-object at run time, which is why this connection uses the `SIGNAL()` and `SLOT()` macros: there is no C++ function to point to.

### Something more convenient?

This is much easier than [QDBusMessage](https://doc.qt.io/qt-6/qdbusmessage.html), but some annoyances remain: you need to know the interface name, choose the right [QDBusReply](https://doc.qt.io/qt-6/qdbusreply.html) type (`int` above), and find typos in method names at run time instead of letting the compiler find them.

The [Qt D-Bus XML compiler](https://doc.qt.io/qt-6/qdbusxml2cpp.html), `qdbusxml2cpp`, solves this.

## Using classes generated from D-Bus XML

Ideally you would create a local object that represents the remote interface and just use it:

```cpp
auto *interface = new org::foo::bar::network("org.foo.bar", "/network",
                                             QDBusConnection::sessionBus(),
                                             this);
interface->ping("sonicde.org");
```

Qt lets you do exactly that. All it needs is an XML file describing the interface. Packages install these files in D-Bus's interfaces directory.

> **Tip:** The system's D-Bus interfaces directory is given by
>
> ```bash
> pkg-config dbus-1 --variable=interfaces_dir
> ```
>
> usually `/usr/share/dbus-1/interfaces`. A project using SonicDE's CMake modules (`KDEInstallDirs`) installs its own interface files to `KDE_INSTALL_DBUSINTERFACEDIR`.

You can also write the XML from your own C++ headers; [Creating D-Bus interfaces](creating-interfaces.md) explains how.

Many SonicDE packages export the path of the interface files they install as a CMake variable. The screen locker, for example, provides `SCREENSAVER_DBUS_INTERFACE`, and SonicDE's desktop uses it like this in its `CMakeLists.txt`:

```cmake
find_package(ScreenSaverDBusInterface CONFIG REQUIRED)

qt_add_dbus_interface(myapp_SRCS ${SCREENSAVER_DBUS_INTERFACE} screensaver_interface)
```

[qt_add_dbus_interface()](https://doc.qt.io/qt-6/qtdbus-cmake-qt-add-dbus-interface.html) generates `screensaver_interface.h` and `screensaver_interface.cpp` at build time and adds them to the sources. You then

```cpp
#include "screensaver_interface.h"
```

and use the generated class as in the example above.

The generated header shows exactly which methods and signals the service provides, with their signatures and return types. Calling the class directly lets the compiler check your calls, so fewer mistakes show up at run time.

The generated class derives from [QDBusAbstractInterface](https://doc.qt.io/qt-6/qdbusabstractinterface.html), like [QDBusInterface](https://doc.qt.io/qt-6/qdbusinterface.html), so everything QDBusInterface can do, it can do too.

Because it is easy to use and checked at compile time, this is the preferred way to use *complicated* D-Bus interfaces.

It has a drawback: the XML file must exist at build time. If it comes from another package, that package must be installed (or built) first, which adds a build dependency. Copying the XML file into your sources avoids that, but only works if you can keep your copy in step with the real interface.

Each way has its trade-offs. Some suggestions:

- Use `QDBusInterface` only where blocking doesn't matter (for example small command-line tools) and the remote interface is simple.
- Use a generated class with the installed XML file when the XML comes from software that is very likely built first, such as SonicWin, power management or other core SonicDE packages.
- Use a generated class when the XML is installed by the same project, for example a daemon and its client: within one project the generated class always matches.
- Copying the XML into your project isn't ideal, but suits stable APIs, and is a good option when the alternative pulls in many unnecessary dependencies or no XML file is installed (you can create one by introspection).
- For complex cases the others don't cover, you can still use `QDBusMessage` with `QDBusConnection` directly.

## A little introspection

Sometimes you need to know whether a service is available, or which application provides it. [QDBusConnectionInterface](https://doc.qt.io/qt-6/qdbusconnectioninterface.html), another [QDBusAbstractInterface](https://doc.qt.io/qt-6/qdbusabstractinterface.html) subclass, tells you which services are registered and who owns them.

With a service name you can call `Introspect` on the `org.freedesktop.DBus.Introspectable` interface of any of its objects. It returns XML describing the object, its interfaces and its child objects, which can be introspected in turn. [QDomDocument](https://doc.qt.io/qt-6/qdomdocument.html) reads the XML.

Qt's `qdbus` tool does exactly this; its source is `src/qdbus/qdbus/qdbus.cpp` in the [qttools](https://code.qt.io/cgit/qt/qttools.git/) repository.
