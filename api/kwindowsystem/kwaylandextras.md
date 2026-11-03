---
title: "KWaylandExtras Class"
description: "A collection of functions to do Wayland things. This class was introduced in Qt 6.0."
---

# KWaylandExtras Class

A collection of functions to do Wayland things. This class was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <KWaylandExtras>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KWindowSystem)`  
  `target_link_libraries(mytarget PRIVATE KF6::KWindowSystem)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kwaylandextras-members.md)  
[Deprecated members](kwaylandextras-obsolete.md)

## Static Public Members

- [QFuture\<QString\> exportToplevel(QWindow \*window)](#exportToplevel) (since 6.28)
- [quint32 lastInputSerial(QWindow \*window)](#lastInputSerial)
- [KWaylandExtras \*self()](#self)
- [void setXdgToplevelDescription(QWindow \*window, const QString &description)](#setXdgToplevelDescription) (since 6.22)
- [void setXdgToplevelTag(QWindow \*window, const QString &tag)](#setXdgToplevelTag) (since 6.22)
- [void unexportToplevel(QWindow \*window)](#unexportToplevel) (since 6.28)
- [QFuture\<QString\> xdgActivationToken(QWindow \*window, const QString &appId)](#xdgActivationToken) (since 6.19)
- [QFuture\<QString\> xdgActivationToken(QWindow \*window, uint32\_t serial, const QString &appId)](#xdgActivationToken-1) (since 6.19)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[static, since 6.28\] QFuture\<QString\> KWaylandExtras::exportToplevel(QWindow \**window*) {#exportToplevel}

Requests to export the given `window` using xdg\_foreign\_v2. The window must be a toplevel window and not a popup.

If the export fails, an empty string will be the result of the operation.

This function was introduced in Qt 6.28.

### \[static invokable\] quint32 KWaylandExtras::lastInputSerial(QWindow \**window*) {#lastInputSerial}

Offers the seat's current serial for the given `window`.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[static\] KWaylandExtras \*KWaylandExtras::self() {#self}

### \[static, since 6.22\] void KWaylandExtras::setXdgToplevelDescription(QWindow \**window*, const QString &*description*) {#setXdgToplevelDescription}

Assigns the specified `description` to the given `window`.

This function was introduced in Qt 6.22.

### \[static, since 6.22\] void KWaylandExtras::setXdgToplevelTag(QWindow \**window*, const QString &*tag*) {#setXdgToplevelTag}

Assigns the specified `tag` to the given `window`.

This function was introduced in Qt 6.22.

### \[static invokable, since 6.28\] void KWaylandExtras::unexportToplevel(QWindow \**window*) {#unexportToplevel}

Unexports the `window` previously exported [exportToplevel](kwaylandextras.md#exportToplevel)()

Asks the compositor to revoke a previously exported handle for `window`.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

This function was introduced in Qt 6.28.

### \[static, since 6.19\] QFuture\<QString\> KWaylandExtras::xdgActivationToken(QWindow \**window*, const QString &*appId*) {#xdgActivationToken}

Requests an xdg\_activation\_v1 token for a specific window `window` with the given `appId`. The last received input serial will be used to request the token.

The appId may be empty, in which case any application can use the token. This should usually be avoided!

> **Note:** No xdgActivationTokenArrived() signal will be emitted for this token. Use the [QFuture](https://doc.qt.io/qt-6/qfuture.html) instead.

This function was introduced in Qt 6.19.

### \[static, since 6.19\] QFuture\<QString\> KWaylandExtras::xdgActivationToken(QWindow \**window*, uint32\_t *serial*, const QString &*appId*) {#xdgActivationToken-1}

Requests an xdg\_activation\_v1 token for a specific window `window` with the given `appId`. The `serial` indicates an event that triggered the request.

The appId may be empty, in which case any application can use the token. This should usually be avoided!

> **Note:** No xdgActivationTokenArrived() signal will be emitted for this token. Use the [QFuture](https://doc.qt.io/qt-6/qfuture.html) instead.

This function was introduced in Qt 6.19.
