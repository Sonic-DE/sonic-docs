---
title: Intermediate D-Bus
description: "Using Qt D-Bus with harder real-world interfaces: complex return types, several return values, and objects that can't be introspected."
source_url: https://develop.kde.org/docs/features/d-bus/intermediate_dbus/
source_authors: [Carl Schwan, Mikhail Zolotukhin, Tobias Fella]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: Qt 6.11 documentation (Qt D-Bus type system, QDBusReply, QDBusConnection::connect)
---

# Intermediate D-Bus

The techniques in [Accessing D-Bus interfaces](accessing-interfaces.md) work for methods with fairly simple signatures. The more complex interfaces found in practice need the techniques on this page.

## Complex return types

Qt D-Bus needs some setup for methods that return more than single primitive values: the type must be known to Qt's type system so it can be read from the message.

### Lists

D-Bus arrays map to [QList](https://doc.qt.io/qt-6/qlist.html). Declare the list type to Qt's type system, for example:

```cpp
Q_DECLARE_METATYPE(QList<QDBusObjectPath>)
```

Use `Q_DECLARE_METATYPE` outside any function or block; the top of the file is the best place.

Register the type with Qt D-Bus as well, before it is used:

```cpp
qDBusRegisterMetaType<QList<QDBusObjectPath>>();
```

Qt D-Bus already knows how to read and write `QList` and `QMap` of supported types, so you don't need to write streaming operators for them. See [The Qt D-Bus Type System](https://doc.qt.io/qt-6/qdbustypesystem.html).

### Dictionaries

D-Bus dictionaries map to [QMap](https://doc.qt.io/qt-6/qmap.html). Declare and register them the same way as lists.

### Several return values

Some D-Bus methods return several values. [QDBusReply](https://doc.qt.io/qt-6/qdbusreply.html) holds only the first one, so for the others use the [QDBusMessage](https://doc.qt.io/qt-6/qdbusmessage.html) itself. `QDBusAbstractInterface::call()` and its relatives return a QDBusMessage; a QDBusReply is only built from it.

[QDBusMessage::arguments()](https://doc.qt.io/qt-6/qdbusmessage.html#arguments) returns all the values as a `QList<QVariant>`.

For example, for a method `org.foo.DBusTute.Favourites.Get(out INT32 number, out STRING colour, out STRING flavour)`:

```cpp
QDBusInterface iface("org.foo.DBusTute",
                     "/org/foo/DBusTute/Favourites",
                     "org.foo.DBusTute.Favourites",
                     QDBusConnection::sessionBus());
QDBusMessage reply = iface.call("Get");
QList<QVariant> values = reply.arguments();
int favouriteNumber = values.takeFirst().toInt();
QString favouriteColour = values.takeFirst().toString();
QString favouriteFlavour = values.takeFirst().toString();
```

## Interfaces that don't support Introspect

[QDBusInterface](https://doc.qt.io/qt-6/qdbusinterface.html) uses introspection to give you D-Bus signals and properties like a local object's. That needs the remote object to implement `org.freedesktop.DBus.Introspectable`, which isn't required.

### Properties

Properties read with `QObject::property()` are found by `Introspect`. Without it, if you know the names and types of the properties (from the remote interface's source), use the D-Bus properties interface directly:

```text
org.freedesktop.DBus.Properties.Get (in STRING interface_name,
                                     in STRING property_name,
                                     out VARIANT value);
org.freedesktop.DBus.Properties.Set (in STRING interface_name,
                                     in STRING property_name,
                                     in VARIANT value);
```

### Signals

Without `Introspect`, `QObject::connect()` fails at run time with a "no such signal" error.

You can still connect to these signals one level lower, with [QDBusConnection::connect()](https://doc.qt.io/qt-6/qdbusconnection.html#connect). If you use [QDBusInterface](https://doc.qt.io/qt-6/qdbusinterface.html) for its `call()` functions, take its connection and connect on that:

```cpp
QDBusInterface iface("org.foo.DBusTute",
                     "/org/foo/DBusTute/Favourites",
                     "org.foo.DBusTute.Favourites",
                     QDBusConnection::sessionBus());

iface.connection().connect("org.foo.DBusTute",
                           "/org/foo/DBusTute/Favourites",
                           "org.foo.DBusTute.Favourites",
                           "FavouritesChanged", this,
                           SLOT(favouritesChanged()));
```

This works like the string-based `QObject::connect()`. `QDBusConnection::connect()` takes the slot only as a `SLOT()` string, so function pointers and lambdas can't be used.
