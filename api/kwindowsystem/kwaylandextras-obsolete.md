---
title: "Obsolete Members for KWaylandExtras"
description: "Deprecated members of KWaylandExtras."
parent: "kwindowsystem/kwaylandextras"
---

# Obsolete Members for KWaylandExtras

**The following members of class [KWaylandExtras](kwaylandextras.md) are deprecated.** We strongly advise against using them in new code.

## Signals

- [void windowExported(QWindow \*window, const QString &handle)](#windowExported) (since 6.0) (deprecated in 6.28)
- [void xdgActivationTokenArrived(int serial, const QString &token)](#xdgActivationTokenArrived) (deprecated in 6.19)

## Static Public Members

- [void exportWindow(QWindow \*window)](#exportWindow) (since 6.0) (deprecated in 6.28)
- [void requestXdgActivationToken(QWindow \*win, uint32\_t serial, const QString &app\_id)](#requestXdgActivationToken) (deprecated in 6.19)
- [void unexportWindow(QWindow \*window)](#unexportWindow) (since 6.0) (deprecated in 6.28)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[static invokable, since 6.0, deprecated in 6.28\] void KWaylandExtras::exportWindow(QWindow \**window*) {#exportWindow}

This function is deprecated since 6.28. We strongly advise against using it in new code.

Requests to export the given `window` using xdg\_foreign\_v2.

Use [exportToplevel](kwaylandextras.md#exportToplevel)() instead.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

This function was introduced in Qt 6.0.

*See also* [windowExported](kwaylandextras-obsolete.md#windowExported)

### \[static invokable, deprecated in 6.19\] void KWaylandExtras::requestXdgActivationToken(QWindow \**win*, uint32\_t *serial*, const QString &*app\_id*) {#requestXdgActivationToken}

This function is deprecated since 6.19. We strongly advise against using it in new code.

Requests an xdg\_activation\_v1 token for a specific window `win` with the given `app_id`.

`serial` Serial of the event that triggered the request.

Use [xdgActivationToken](kwaylandextras.md#xdgActivationToken)() instead.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [lastInputSerial](kwaylandextras.md#lastInputSerial)

### \[static invokable, since 6.0, deprecated in 6.28\] void KWaylandExtras::unexportWindow(QWindow \**window*) {#unexportWindow}

This function is deprecated since 6.28. We strongly advise against using it in new code.

Unexports the `window` previously exported using xdg\_foreign\_v2.

Asks the compositor to revoke the handle.

Use [unexportToplevel](kwaylandextras.md#unexportToplevel)() instead.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

This function was introduced in Qt 6.0.

### \[signal, since 6.0, deprecated in 6.28\] void KWaylandExtras::windowExported(QWindow \**window*, const QString &*handle*) {#windowExported}

This function is deprecated since 6.28. We strongly advise against using it in new code.

The `handle` of the given `window` to pass to the client.

Use [exportToplevel](kwaylandextras.md#exportToplevel)() instead.

This function was introduced in Qt 6.0.

*See also* [exportWindow](kwaylandextras-obsolete.md#exportWindow)

### \[signal, deprecated in 6.19\] void KWaylandExtras::xdgActivationTokenArrived(int *serial*, const QString &*token*) {#xdgActivationTokenArrived}

This function is deprecated since 6.19. We strongly advise against using it in new code.

Activation `token` to pass to the client.

`serial` Serial of the event that triggered the request

Use [xdgActivationToken](kwaylandextras.md#xdgActivationToken)() instead.

*See also* [requestXdgActivationToken](kwaylandextras-obsolete.md#requestXdgActivationToken)
