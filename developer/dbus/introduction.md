---
title: Introduction to D-Bus
description: The core concepts of D-Bus from an application developer's point of view.
source_url: https://develop.kde.org/docs/features/d-bus/introduction_to_dbus/
source_authors: [Benson Muite, Carl Schwan, Friso Smit, Kunda Ki, Mikhail Zolotukhin, Thiago Sueto, Tobias Fella, Vyacheslav Gurin]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-workspace d0b84fd142, sonic-screenlocker 0ed103d7, sonic-win 71cc168eef
---

# Introduction to D-Bus

[D-Bus](https://www.freedesktop.org/wiki/Software/dbus/) is a free and open source inter-process communication (IPC) mechanism from the [freedesktop.org](https://freedesktop.org) project. Many applications use it, and many freedesktop.org standards are built on it, such as [Desktop Notifications](https://specifications.freedesktop.org/notification-spec), [media player control](https://specifications.freedesktop.org/mpris-spec) and [XDG desktop portals](https://github.com/flatpak/xdg-desktop-portal).

> **Note:** D-Bus isn't the only IPC mechanism in SonicDE. SonicDE is gradually replacing it in its own components with [Sonic IPC](/docs/api/sonicipc/sonicipc-index) (`sonic-frameworks-ipc`), a small library built on Unix domain sockets. D-Bus remains the way to talk to freedesktop services and other applications.

IPC means getting information from one process to another: exchanging data, calling methods and listening to events.

On the desktop, IPC is used for scripting (a script controls running applications), for access to central services, and for coordination between several instances of cooperating applications.

Desktop notifications are a good example. Applications send their notifications to a central server, in SonicDE the desktop shell, which shows them and sends back events such as the notification being closed or one of its actions being chosen.

Another example is a unique application: when it starts, it checks whether another instance is already running, and if one is, it asks that instance over IPC to show itself and exits.

D-Bus doesn't depend on a language or toolkit, so applications and services from any provider can talk to each other. Qt provides classes and tools for D-Bus. These pages introduce the concepts of D-Bus and how Qt and SonicDE use them.

## Buses

D-Bus provides several message *buses* for applications to communicate on. Each bus has its own connections: messages sent on one bus can't be seen on another, but all applications connected to the same bus can talk to each other. Any number of applications can be connected to a bus, and an application can be connected to several buses at once. This lets different buses have different security policies.

D-Bus has two predefined buses, which cover most uses:

- The **system bus** is for system-wide services such as hardware management. It is shared between users and usually has strict security policies.
- Each desktop session (each logged-in user) has its own **session bus**, the one desktop applications use most.

An application can also create buses of its own.

## Messages

**Messages** are the unit of communication on a bus. All information passes over the bus as messages, much as TCP/IP sends packets. Unlike a network packet, a D-Bus message always contains all of the data being sent or received. Besides the data, a message records its sender and receiver, so it can be routed.

A message is a method call, a signal, a method's return value or an error.

## Namespaces and addresses

A bus carries many applications, and one application can offer many objects to send messages to, so every object on a bus needs a unique address, as a street address identifies one house. Three pieces of information together make that address: the interface, the service and the object path.

### Interfaces

An **interface** is a set of methods and signals advertised on the bus. It is a contract between applications: it defines the name, parameters and return values of each method. The methods don't have to match the application's own functions one to one, though they often do. Several applications can provide the same interface with different implementations, and callers use it without knowing how it is implemented.

Interfaces can be described in XML, for documentation and reuse. Developers can generate classes from the XML, which makes D-Bus easier to use and less error-prone: the compiler checks the calls.

### Services

A **service** is an application's connection to a bus.

In the D-Bus specification a service is a "well-known" [bus name](https://dbus.freedesktop.org/doc/dbus-specification.html#message-protocol-names). Despite the term, bus names are names of connections on a bus, not names of buses. These pages say *service*, as Qt's documentation does.

Service names are kept unique by using reverse domain names. SonicDE's own names use `org.sonicde`, such as the desktop shell, `org.sonicde.sonicshell`. Services inherited from KDE keep their `org.kde` names for now, so that applications written for KDE keep working: the screen locker, for example, registers `org.kde.screensaver` on the session bus (as well as the standard `org.freedesktop.ScreenSaver`).

Name your services after your organization's or application's domain. If your domain is `awesomeapps.org` and your application is `wickedwidget`, a good service name is `org.awesomeapps.wickedwidget`.

If an application has more than one connection to a bus, or several instances can run at once, each connection needs its own service name. Often the process ID is appended to the name.

### Objects

An application usually offers more than one object on the bus. The **path** part of the address tells them apart: each path of a service is a different object, such as `/MainInterface` or `/Documents/Doc1`. The path structure is up to the application; paths only identify and group its objects.

Some libraries put their reverse domain name in front of their object paths. This is common for libraries and plugins that share a service with an application and must not clash with the objects that application exports. SonicDE prefixes its object paths this way, for example `/org/sonicde/osdService`. Give your own objects prefixed paths too. Paths inherited from KDE stay as they are for now, for compatibility, whether prefixed like SonicWin's `/org/kde/KWin` or short like its `/Scripting`. SonicDE's own objects that still have short paths, such as the desktop shell's `/SonicShell`, are being moved to prefixed paths.

An object provides interfaces, and one object can provide several.

### Putting it together

A D-Bus message carries an address made of all of these parts, so it reaches the right application, object and method. KRunner, SonicDE's search and run window, can be called like this:

```text
org.kde.krunner /App org.kde.krunner.App.display
```

`org.kde.krunner` is the service, `/App` the object path, `org.kde.krunner.App` the interface and `display` a method of it. SonicWin calls exactly this method when a screen edge is set to open KRunner. When `display` is unique among the object's interfaces, this short form works too:

```text
org.kde.krunner /App display
```

This way every destination has a unique, reliable address.

## Calling and being called

With a way to address any object on a bus, applications can send and receive messages.

### Methods

A method call is a message that runs code in the receiving application. If the method isn't available, for example because the address is wrong or the application isn't running, the caller gets an error. If the call succeeds, the caller gets the return value, or just a success reply when there is none. This round trip costs time; keep it in mind in performance-critical code.

The calling application always starts a method call, and its messages have exactly one sender and one receiver.

### Signals

Signals go the other way and have no single receiver. The application that exports an interface emits a signal, and any application on the same bus can receive it. Applications use signals to announce changes of state and other events to whoever is interested.

This works much like Qt's signals and slots: a D-Bus signal is their counterpart between processes.

## Useful tools

Several tools help with exploring the buses and developing D-Bus applications. This page introduces the interactive ones; the following pages cover the development tools.

### qdbus

`qdbus` is Qt's command-line tool for listing the services, objects and interfaces on a bus and for sending messages to an address. It uses the session bus, or the system bus with `--system`. Qt 6 installs it in Qt's tool directory (`qtpaths6 --query QT_HOST_BINS`); some distributions also put it in the `PATH` as `qdbus6`.

The arguments after the options are an address and, if given, parameters to pass. With an incomplete address `qdbus` lists what is below it: with no address, the services on the bus; with a service, its object paths; with a path too, the methods of all of the object's interfaces. This makes `qdbus` useful for exploring, testing and scripting.

### qdbusviewer

`qdbusviewer` is a Qt application with a graphical interface to much the same features as `qdbus`. It ships with Qt, in the same directory as `qdbus`; some distributions name it `qdbusviewer6`.
