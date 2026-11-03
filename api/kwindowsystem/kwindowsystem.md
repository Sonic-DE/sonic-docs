---
title: "KWindowSystem Class"
description: "Convenience access to certain properties and features of window systems."
---

# KWindowSystem Class

Convenience access to certain properties and features of window systems. [More...](#details)

- **Header:** `#include <KWindowSystem>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KWindowSystem)`  
  `target_link_libraries(mytarget PRIVATE KF6::KWindowSystem)`
- **In QML:** [KWindowSystem](qml-org-kde-kwindowsystem-kwindowsystem.md)
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kwindowsystem-members.md)

## Public Types

- [enum KWindowSystem::Platform](#Platform-enum)

## Properties

- [\[read-only\] isPlatformX11 : const bool](#isPlatformX11-prop)
- [\[read-only\] isPlatformWayland : const bool](#isPlatformWayland-prop)
- [showingDesktop : bool](#showingDesktop-prop)

## Signals

- [void showingDesktopChanged(bool showing)](#showingDesktopChanged)

## Static Public Members

- [void activateWindow(QWindow \*window, long time = 0)](#activateWindow)
- [bool isPlatformX11()](#isPlatformX11)
- [bool isPlatformWayland()](#isPlatformWayland)
- [KWindowSystem::Platform platform()](#platform)
- [void setCurrentXdgActivationToken(const QString &token)](#setCurrentXdgActivationToken)
- [void setMainWindow(QWindow \*subwindow, WId mainwindow)](#setMainWindow)
- [void setMainWindow(QWindow \*subwindow, const QString &mainwindow)](#setMainWindow-1) (since 6.0)
- [void setShowingDesktop(bool showing)](#setShowingDesktop)
- [bool showingDesktop()](#showingDesktop)
- [void updateStartupId(QWindow \*window)](#updateStartupId)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum KWindowSystem::Platform {#Platform-enum}

Enum describing the windowing system platform used by the [QGuiApplication](https://doc.qt.io/qt-6/qguiapplication.html).

| Constant | Value | Description |
| --- | --- | --- |
| `KWindowSystem::Platform::Unknown` | `0` | A platform unknown to the application is used |
| `KWindowSystem::Platform::X11` | `1` | The X11 window system. |
| `KWindowSystem::Platform::Wayland` | ? | The Wayland window system. |

*See also* [platform](kwindowsystem.md#platform)()

## Property Documentation {#property-documentation}

### \[read-only\] isPlatformX11 : const bool {#isPlatformX11-prop}

**Access functions:**

- `bool` **[isPlatformX11](kwindowsystem.md#isPlatformX11)**()

### \[read-only\] isPlatformWayland : const bool {#isPlatformWayland-prop}

**Access functions:**

- `bool` **[isPlatformWayland](kwindowsystem.md#isPlatformWayland)**()

### showingDesktop : bool {#showingDesktop-prop}

This property holds whether "show desktop" is currently active.

**Access functions:**

- `bool` **[showingDesktop](kwindowsystem.md#showingDesktop)**()
- `void` **[setShowingDesktop](kwindowsystem.md#setShowingDesktop)**(`bool` *showing*)

**Notifier signal:**

- `void` **[showingDesktopChanged](kwindowsystem.md#showingDesktopChanged)**(`bool` *showing*)

## Member Function Documentation {#member-function-documentation}

### \[static invokable\] void KWindowSystem::activateWindow(QWindow \**window*, long *time* = 0) {#activateWindow}

Requests that window `window` is activated.

Applications shouldn't make attempts to explicitly activate their windows, and instead let the user activate them. In the special cases where this may be needed, applications can use activateWindow(). The window manager may consider whether this request wouldn't result in focus stealing, which would be obtrusive, and may refuse the request.

In case of problems, consult KWin's README.md file, or ask on the kwin@kde.org mailing list.

`window` the window to make active `time` X server timestamp of the user activity that caused this request

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[static\] bool KWindowSystem::isPlatformX11() {#isPlatformX11}

Returns whether the Platform is X11.

> **Note:** Getter function for property [isPlatformX11](kwindowsystem.md#isPlatformX11-prop).

*See also* [platform](kwindowsystem.md#platform), [isPlatformWayland](kwindowsystem.md#isPlatformWayland)

### \[static\] bool KWindowSystem::isPlatformWayland() {#isPlatformWayland}

Returns whether the Platform is Wayland.

> **Note:** Getter function for property [isPlatformWayland](kwindowsystem.md#isPlatformWayland-prop).

*See also* [platform](kwindowsystem.md#platform), [isPlatformX11](kwindowsystem.md#isPlatformX11)

### \[static\] KWindowSystem::Platform KWindowSystem::platform() {#platform}

Returns the Platform used by the [QGuiApplication](https://doc.qt.io/qt-6/qguiapplication.html). The Platform gets resolved the first time the method is invoked and cached for further usages. Returns The Platform used by the [QGuiApplication](https://doc.qt.io/qt-6/qguiapplication.html).

### \[static invokable\] void KWindowSystem::setCurrentXdgActivationToken(const QString &*token*) {#setCurrentXdgActivationToken}

Sets the `token` that will be used when [activateWindow](kwindowsystem.md#activateWindow) is called next

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[static\] void KWindowSystem::setMainWindow(QWindow \**subwindow*, WId *mainwindow*) {#setMainWindow}

Sets the parent window of `subwindow` to be `mainwindow`. This overrides the parent set the usual way as the QWidget or [QWindow](https://doc.qt.io/qt-6/qwindow.html) parent, but only for the window manager - e.g. stacking order and window grouping will be affected, but features like automatic deletion of children when the parent is deleted are unaffected and normally use the [QObject](https://doc.qt.io/qt-6/qobject.html) parent.

This function should be used before a dialog is shown for a window that belongs to another application.

### \[static, since 6.0\] void KWindowSystem::setMainWindow(QWindow \**subwindow*, const QString &*mainwindow*) {#setMainWindow-1}

Sets the parent window of `subwindow` to be `mainwindow`.

This function should be used before a dialog is shown for a window that belongs to another application.

`subwindow` the sub window `mainwindow` The main window ID or XDG Foreign token

This function was introduced in Qt 6.0.

### \[static\] void KWindowSystem::setShowingDesktop(bool *showing*) {#setShowingDesktop}

Sets the state of the "showing desktop" mode of the window manager. If on, windows are hidden and desktop background is shown and focused.

`showing` if true, the window manager is put in "showing desktop" mode. If false, the window manager is put out of that mode.

> **Note:** Setter function for property [showingDesktop](kwindowsystem.md#showingDesktop-prop).

*See also* [showingDesktop](kwindowsystem.md#showingDesktop)()

### \[static\] bool KWindowSystem::showingDesktop() {#showingDesktop}

Returns the state of showing the desktop.

> **Note:** Getter function for property [showingDesktop](kwindowsystem.md#showingDesktop-prop).

*See also* [setShowingDesktop](kwindowsystem.md#setShowingDesktop)()

### \[signal\] void KWindowSystem::showingDesktopChanged(bool *showing*) {#showingDesktopChanged}

The state of `showing` the desktop has changed.

> **Note:** Notifier signal for property [showingDesktop](kwindowsystem.md#showingDesktop-prop).

### \[static\] void KWindowSystem::updateStartupId(QWindow \**window*) {#updateStartupId}

Updates the platform-specific startup id, if any.

This method is to be called when a running application instance is reused for handling the request to start this application. A typical use would be in the handler of the KDBusService activation signal.

For X11, this updates the id for the Startup Notification protocol, taking the id from QX11Info::nextStartupId(), if not empty.

`window` the main window (needed by X11 platform)
