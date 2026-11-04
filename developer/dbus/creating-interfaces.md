---
title: Creating D-Bus interfaces
description: "Offer your application's functions on D-Bus: describe the interface, generate the XML and adaptor with CMake, and register the object."
source_url: https://develop.kde.org/docs/features/d-bus/creating_dbus_interfaces/
source_authors: [Carl Schwan, Chris Holland, Han Young, Mikhail Zolotukhin, Thiago Sueto, Tobias Fella]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: Qt 6.11 documentation and qdbuscpp2xml 6.11, sonic-frameworks-dbus, sonic-frameworks-core-addons, sonic-frameworks-io (kioexec), sonic-frameworks-cmake-modules
---

# Creating D-Bus interfaces

D-Bus lets an application offer its internal API to other processes as interfaces they can call. This page shows how to create and implement such interfaces.

## Defining the interface

A D-Bus interface usually mirrors the API of one or more classes of the application that provides it. The bridge to D-Bus is a [QDBusAbstractAdaptor](https://doc.qt.io/qt-6/qdbusabstractadaptor.html) subclass that receives D-Bus messages and acts on them. Mostly that means one-line functions that call functions of the same name in another object. You can almost always avoid writing them by hand by generating a D-Bus XML description of the interface.

An interface as seen on the bus is described in a standard XML format, defined in the [D-Bus specification](https://dbus.freedesktop.org/doc/dbus-specification.html#introspection-format). For example:

```xml
<!DOCTYPE node PUBLIC "-//freedesktop//DTD D-BUS Object Introspection 1.0//EN" "http://www.freedesktop.org/standards/dbus/1.0/introspect.dtd">
<node>
  <interface name="org.foo.Background">
    <signal name="backgroundChanged">
    </signal>
    <method name="refreshBackground">
    </method>
    <method name="currentBackground">
      <arg type="s" direction="out"/>
    </method>
    <method name="setBackground">
      <arg type="b" direction="out"/>
      <arg name="name" type="s" direction="in"/>
    </method>
  </interface>
</node>
```

If you have called `Introspect` of the `org.freedesktop.DBus.Introspectable` interface in `qdbus` or `qdbusviewer`, this will look familiar.

You could write this XML by hand and map it to a class yourself, but that is slow and error-prone. If other applications didn't need the XML to use your interface, you might as well write the QDBusAbstractAdaptor by hand.

Instead, write a class with the functions you want to offer, and let Qt's tools do the rest.

### Defining methods

The example is an interface for setting the desktop background and asking which one is set. It offers three methods, shown in this class:

```cpp
#include <QObject>

class Background : public QObject
{
    Q_OBJECT

public:
    explicit Background(QObject *parent);

    void doNotExportToDBus();

    void refreshBackground();
    QString currentBackground();

Q_SIGNALS:
    void doNotExportThisSignal();
    void backgroundChanged();

public Q_SLOTS:
    bool setBackground(QString name);

protected Q_SLOTS:
    void dbusCanNotSeeMe();
};
```

Next, mark what D-Bus should see. The options are:

- export all signals
- export all public slots
- export all properties
- export only scriptable signals
- export only scriptable public slots
- export only scriptable properties

They can be combined. For this example the class becomes:

```cpp
#include <QObject>

class Background : public QObject
{
    Q_OBJECT

public:
    explicit Background(QObject *parent);

    void doNotExportToDBus();

Q_SIGNALS:
    void doNotExportThisSignal();
    Q_SCRIPTABLE void backgroundChanged();

public Q_SLOTS:
    void refreshBackground();
    QString currentBackground();
    bool setBackground(QString name);

protected Q_SLOTS:
    void dbusCanNotSeeMe();
};
```

The functions to export are now public slots, and the signal to export is marked `Q_SCRIPTABLE`. The interface will export all public slots and the scriptable signals.

Then implement the class as usual.

> **Tip:** Once an API is on D-Bus, other applications and users' scripts may rely on it, and changing it breaks them. Keep public D-Bus APIs compatible for the whole life of a major release of your application.

### Naming the interface

Next, choose the name the interface has on the bus. By convention it is a reverse domain name, which prevents clashes: if your project's website is `foo.org`, start your interface names with `org.foo`. (SonicDE's own new interfaces start with `org.sonicde`.)

So the example interface could be `org.foo.Background`. The easiest way to set the name is a `Q_CLASSINFO` entry in the class:

```cpp
class Background : public QObject
{
    Q_OBJECT
    Q_CLASSINFO("D-Bus Interface", "org.foo.Background")
```

The interface is now called `org.foo.Background`.

## Generating the interface

### The simple way

The simplest way is to use the class itself as the interface. Make sure it has `Q_CLASSINFO("D-Bus Interface", "org.foo.Background")` below `Q_OBJECT`, skip the next sections, and go on to [registering the class directly](#registering-the-class-directly).

### The portable way

This needs a few more build steps, but is better when other applications will use your interface. It installs the XML file, from which other applications generate their own classes; anyone with your project installed can use the file without your source.

With the interface set up in the class, generate an *adaptor* class that connects D-Bus to your objects. The first step is the XML shown at the top of this page.

You can generate the XML once with `qdbuscpp2xml` and keep it in your sources, or let CMake generate it at build time. CMake keeps the source tree clean, and you can't forget to regenerate the XML after changing the class.

### Option one: run qdbuscpp2xml yourself

`qdbuscpp2xml`, one of Qt's tools, reads a C++ header or source file and writes the D-Bus XML for its class. Its options choose what to export:

| Option | Exports |
| --- | --- |
| `-S` | all signals |
| `-M` | all public slots |
| `-P` | all properties |
| `-A` | all of them (`-PSM`) |
| `-s` | scriptable signals |
| `-m` | scriptable public slots |
| `-p` | scriptable properties |
| `-a` | all scriptable items (`-psm`) |

The example exports all public slots and only the scriptable signals:

```bash
qdbuscpp2xml -M -s background.h -o org.foo.Background.xml
```

This writes `org.foo.Background.xml` with the XML shown at the top of this page. Keep the file in your project's sources.

`qdbuscpp2xml` is in Qt's tool directory (`qtpaths6 --query QT_HOST_BINS`).

### Option two: let CMake run qdbuscpp2xml (preferred)

Add this to your project's `CMakeLists.txt`:

```cmake
qt_generate_dbus_interface(background.h org.foo.Background.xml OPTIONS -M -s)
install(FILES ${CMAKE_CURRENT_BINARY_DIR}/org.foo.Background.xml
        DESTINATION ${KDE_INSTALL_DBUSINTERFACEDIR})
```

[qt_generate_dbus_interface()](https://doc.qt.io/qt-6/qtdbus-cmake-qt-generate-dbus-interface.html) generates `org.foo.Background.xml` from `background.h` in the build directory. With SonicDE's CMake modules (`include(KDEInstallDirs)`), `KDE_INSTALL_DBUSINTERFACEDIR` is the D-Bus interfaces directory, usually `/usr/share/dbus-1/interfaces`. (The older name `DBUS_INTERFACES_INSTALL_DIR` isn't defined with `KDEInstallDirs6`.)

### Building the adaptor with CMake

Now build the adaptor from the XML file:

```cmake
qt_add_dbus_adaptor(my_nice_project_SRCS ${CMAKE_CURRENT_BINARY_DIR}/org.foo.Background.xml
                    background.h Background)
```

[qt_add_dbus_adaptor()](https://doc.qt.io/qt-6/qtdbus-cmake-qt-add-dbus-adaptor.html) generates `backgroundadaptor.h` and `backgroundadaptor.cpp` in the build directory and adds them to the sources; the class is `BackgroundAdaptor`. Don't keep these files in your sources.

SonicDE's `kioexecd` (in `sonic-frameworks-io/src/kioexec`) is built exactly this way:

```cmake
qt_generate_dbus_interface(${CMAKE_CURRENT_SOURCE_DIR}/kioexecd.h org.kde.KIOExecd.xml)
qt_add_dbus_adaptor(kioexecd_dbus_SRCS ${CMAKE_CURRENT_BINARY_DIR}/org.kde.KIOExecd.xml kioexecd.h KIOExecd)
```

The installed XML file is a reference for users, and other applications generate interface classes from it with `qdbusxml2cpp`, as described in [Accessing D-Bus interfaces](accessing-interfaces.md).

Next, [create the adaptor at run time](#creating-the-adaptor).

## Registering the interface at run time

### Registering the class directly

With the simple way, register the class with [QDBusConnection::registerObject()](https://doc.qt.io/qt-6/qdbusconnection.html#registerObject), usually in its constructor. If there can be more than one instance of the class, give each its own path. For a class with only one instance, the constructor might contain:

```cpp
#include <QDBusConnection>

Background::Background(QObject *parent)
    : QObject(parent)
{
    QDBusConnection::sessionBus().registerService(QStringLiteral("org.foo.myapp"));
    QDBusConnection::sessionBus().registerObject(QStringLiteral("/org/foo/Background"), this,
                                                 QDBusConnection::ExportScriptableContents);

    // ... the rest of the constructor
}
```

The first call registers the service name, which no other project may use. If your `main()` uses [KDBusService](/docs/api/kdbusaddons/kdbusservice), you can leave that line out: KDBusService registers a name made from the application's organization domain, reversed, and its name. The domain comes from your [KAboutData](/docs/api/kcoreaddons/kaboutdata): the host of its homepage address, or `kde.org` when you use the short constructor. For example:

```cpp
KAboutData aboutData(QStringLiteral("myapp"), i18n("My App"), QStringLiteral("1.0"),
                     i18n("Does nice things"), KAboutLicense::GPL_V2, QString(), QString(),
                     QStringLiteral("https://foo.org"));
KAboutData::setApplicationData(aboutData);
KDBusService service(KDBusService::Unique);
// registers org.foo.myapp
```

The second call registers this object at the path `/org/foo/Background` of that service. Prefix your object paths with your reverse domain as SonicDE does (see [Introduction to D-Bus](introduction.md#objects)). Apart from the root path `/`, a path never ends with `/`. The object must be a `QObject` with `Q_CLASSINFO("D-Bus Interface", "org.foo.Background")`. The third argument says what D-Bus may see; see [QDBusConnection::RegisterOption](https://doc.qt.io/qt-6/qdbusconnection.html#RegisterOption-enum).

If the class can have several instances, give each a path of its own, for example:

```cpp
QDBusConnection::sessionBus().registerObject(QStringLiteral("/org/foo/Background/") + uniqueInstanceId, this,
                                             QDBusConnection::ExportScriptableContents);
```

### Creating the adaptor

With the portable way, include the generated header and create the adaptor:

```cpp
#include "background.h"
#include "backgroundadaptor.h"

Background::Background(QObject *parent)
    : QObject(parent)
{
    new BackgroundAdaptor(this);
    QDBusConnection dbus = QDBusConnection::sessionBus();
    dbus.registerObject(QStringLiteral("/org/foo/Background"), this);
    dbus.registerService(QStringLiteral("org.foo.Background"));
}
```

The adaptor is a `QObject` with `this` as its parent, so it is deleted with the Background object, and it forwards the D-Bus calls it receives to `this`.

Then register the object on the bus with [QDBusConnection::registerObject()](https://doc.qt.io/qt-6/qdbusconnection.html#registerObject) and offer it to others with [QDBusConnection::registerService()](https://doc.qt.io/qt-6/qdbusconnection.html#registerService).

> **Tip:** If your application creates several objects of the same class, register each with a unique path. If they have no natural unique names, the `this` pointer can serve.
