---
title: "KX11Extras Class"
description: "A collection of functions to obtain information from and manipulate X11 windows."
---

# KX11Extras Class

A collection of functions to obtain information from and manipulate X11 windows. [More...](#details)

- **Header:** `#include <KX11Extras>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KWindowSystem)`  
  `target_link_libraries(mytarget PRIVATE KF6::KWindowSystem)`
- **In QML:** [KX11Extras](qml-org-kde-kwindowsystem-kx11extras.md)
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kx11extras-members.md)

## Public Types

- [enum KX11Extras::IconSource](#IconSource-enum)

## Properties

- [\[read-only\] compositingActive : bool](#compositingActive-prop)

## Signals

- [void activeWindowChanged(WId id)](#activeWindowChanged)
- [void compositingChanged(bool enabled)](#compositingChanged)
- [void currentDesktopChanged(int desktop)](#currentDesktopChanged)
- [void desktopNamesChanged()](#desktopNamesChanged)
- [void numberOfDesktopsChanged(int num)](#numberOfDesktopsChanged)
- [void stackingOrderChanged()](#stackingOrderChanged)
- [void strutChanged()](#strutChanged)
- [void windowAdded(WId id)](#windowAdded)
- [void windowChanged(WId id, NET::Properties properties, NET::Properties2 properties2)](#windowChanged)
- [void windowRemoved(WId id)](#windowRemoved)
- [void workAreaChanged()](#workAreaChanged)

## Static Public Members

- [void activateWindow(WId win, long time = 0)](#activateWindow)
- [WId activeWindow()](#activeWindow)
- [void clearState(WId win, NET::States state)](#clearState) (since 6.0)
- [bool compositingActive()](#compositingActive)
- [int currentDesktop()](#currentDesktop)
- [QString desktopName(int desktop)](#desktopName)
- [void forceActiveWindow(WId win, long time = 0)](#forceActiveWindow)
- [bool hasWId(WId id)](#hasWId)
- [QPixmap icon(WId win, int width = -1, int height = -1, bool scale = false)](#icon)
- [QPixmap icon(WId win, int width, int height, bool scale, int flags)](#icon-1)
- [QPixmap icon(WId win, int width, int height, bool scale, int flags, NETWinInfo \*info)](#icon-2)
- [bool mapViewport()](#mapViewport)
- [void minimizeWindow(WId win)](#minimizeWindow)
- [int numberOfDesktops()](#numberOfDesktops)
- [QString readNameProperty(WId window, unsigned long atom)](#readNameProperty)
- [KX11Extras \*self()](#self)
- [void setCurrentDesktop(int desktop)](#setCurrentDesktop)
- [void setDesktopName(int desktop, const QString &name)](#setDesktopName)
- [void setExtendedStrut(WId win, qreal left\_width, qreal left\_start, qreal left\_end, qreal right\_width, qreal right\_start, qreal right\_end, qreal top\_width, qreal top\_start, qreal top\_end, qreal bottom\_width, qreal bottom\_start, qreal bottom\_end)](#setExtendedStrut)
- [void setOnActivities(WId win, const QStringList &activities)](#setOnActivities)
- [void setOnAllDesktops(WId win, bool b)](#setOnAllDesktops)
- [void setOnDesktop(WId win, int desktop)](#setOnDesktop)
- [void setState(WId win, NET::States state)](#setState) (since 6.0)
- [void setStrut(WId win, qreal left, qreal right, qreal top, qreal bottom)](#setStrut)
- [void setType(WId win, NET::WindowType windowType)](#setType) (since 6.0)
- [QList\<WId\> stackingOrder()](#stackingOrder)
- [void unminimizeWindow(WId win)](#unminimizeWindow)
- [QList\<WId\> windows()](#windows)
- [QRect workArea(int desktop = -1)](#workArea)
- [QRect workArea(const QList\<WId\> &excludes, int desktop = -1)](#workArea-1)

## Detailed Description {#details}

These are generally not applicable to other window systems.

## Member Type Documentation {#member-type-documentation}

### enum KX11Extras::IconSource {#IconSource-enum}

Masks specifying from which sources to read an icon.

They are tried from the best until an icon is found.

| Constant | Value | Description |
| --- | --- | --- |
| `KX11Extras::NETWM` | `1` | Property from the window manager specification. |
| `KX11Extras::WMHints` | `2` | From WMHints property. |
| `KX11Extras::ClassHint` | `4` | Load icon after getting name from the classhint. |
| `KX11Extras::XApp` | `8` | Load the standard X icon (last fallback). |

## Property Documentation {#property-documentation}

### \[read-only\] compositingActive : bool {#compositingActive-prop}

This property holds whether desktop compositing is active.

**Access functions:**

- `bool` **[compositingActive](kx11extras.md#compositingActive)**()

**Notifier signal:**

- `void` **[compositingChanged](kx11extras.md#compositingChanged)**(`bool` *enabled*)

## Member Function Documentation {#member-function-documentation}

### \[static\] void KX11Extras::activateWindow(WId *win*, long *time* = 0) {#activateWindow}

Requests that window `win` is activated, with the optional X server timestamp `time` of the user activity that caused this request.

There are two ways how to activate a window, by calling activateWindow() and [forceActiveWindow](kx11extras.md#forceActiveWindow)(). Generally, applications shouldn't make attempts to explicitly activate their windows, and instead let the user to activate them. In the special cases where this may be needed, applications should use activateWindow(). Window manager may consider whether this request wouldn't result in focus stealing, which would be obtrusive, and may refuse the request.

The usage of [forceActiveWindow](kx11extras.md#forceActiveWindow)() is meant only for pagers and similar tools, which represent direct user actions related to window manipulation. Except for rare cases, this request will be always honored, and normal applications are forbidden to use it.

### \[static\] WId KX11Extras::activeWindow() {#activeWindow}

Returns the currently active window id, or 0 if no window is active.

### \[signal\] void KX11Extras::activeWindowChanged(WId *id*) {#activeWindowChanged}

Hint that \<Window\> with the given `id` is active (= has focus) now.

### \[static, since 6.0\] void KX11Extras::clearState(WId *win*, NET::States *state*) {#clearState}

Clears the state of window `win` from `state`.

Possible values are OR'ed combinations of:

- [NET::Modal](net.md#State-enum)
- [NET::Sticky](net.md#State-enum)
- [NET::MaxVert](net.md#State-enum)
- [NET::MaxHoriz](net.md#State-enum)
- [NET::Shaded](net.md#State-enum)
- [NET::SkipTaskbar](net.md#State-enum)
- [NET::SkipPager](net.md#State-enum)
- [NET::Hidden](net.md#State-enum)
- [NET::FullScreen](net.md#State-enum)
- [NET::KeepAbove](net.md#State-enum)
- [NET::KeepBelow](net.md#State-enum)
- [NET::SkipSwitcher](net.md#State-enum)

This function was introduced in Qt 6.0.

### \[static\] bool KX11Extras::compositingActive() {#compositingActive}

Returns true if a compositing manager is running (i.e. ARGB windows are supported, effects will be provided, etc.).

> **Note:** Getter function for property [compositingActive](kx11extras.md#compositingActive-prop).

### \[signal\] void KX11Extras::compositingChanged(bool *enabled*) {#compositingChanged}

Compositing was `enabled` or disabled.

Note that this signal may be emitted before any compositing plugins have been initialized in the window manager.

If you need to check if a specific compositing plugin such as the blur effect is enabled, you should track that separately rather than test for it in a slot connected to this signal.

> **Note:** Notifier signal for property [compositingActive](kx11extras.md#compositingActive-prop).

### \[static\] int KX11Extras::currentDesktop() {#currentDesktop}

Returns the current virtual desktop.

*See also* [setCurrentDesktop](kx11extras.md#setCurrentDesktop)()

### \[signal\] void KX11Extras::currentDesktopChanged(int *desktop*) {#currentDesktopChanged}

Switched to another virtual `desktop`.

### \[static\] QString KX11Extras::desktopName(int *desktop*) {#desktopName}

Returns the name of the specified `desktop` number.

*See also* [setDesktopName](kx11extras.md#setDesktopName)()

### \[signal\] void KX11Extras::desktopNamesChanged() {#desktopNamesChanged}

Desktops have been renamed.

### \[static\] void KX11Extras::forceActiveWindow(WId *win*, long *time* = 0) {#forceActiveWindow}

Sets window `win` to be the active window, with the optional X server timestamp `time` of the user activity that caused this request.

Note that this should be called only in special cases, applications shouldn't force themselves or other windows to be the active window. Generally, this call should used only by pagers and similar tools. See the explanation in description of [activateWindow](kx11extras.md#activateWindow)().

### \[static\] bool KX11Extras::hasWId(WId *id*) {#hasWId}

Returns whether `id` is still managed at present.

### \[static\] QPixmap KX11Extras::icon(WId *win*, int *width* = -1, int *height* = -1, bool *scale* = false) {#icon}

Returns an icon for window `win`.

If `width` and `height` are specified, the best icon for the requested size is returned.

If `scale` is true, the icon is smooth-scaled to have exactly the requested size.

### \[static\] QPixmap KX11Extras::icon(WId *win*, int *width*, int *height*, bool *scale*, int *flags*) {#icon-1}

Overloaded variant that allows specifying from which sources the icon should be read. You should usually prefer the simpler variant which tries all possibilities to get an icon.

`win` The id of the window. `width` The desired width, or -1. `height` The desired height, or -1. `scale` If true the icon will be scaled to the desired size. Otherwise the icon will not be modified. `flags` OR-ed flags from the [IconSource](kx11extras.md#IconSource-enum) enum.

This is an overloaded function.

### \[static\] QPixmap KX11Extras::icon(WId *win*, int *width*, int *height*, bool *scale*, int *flags*, NETWinInfo \**info*) {#icon-2}

Overloaded variant that allows passing in the [NETWinInfo](netwininfo.md) `info` to use for reading the information. This variant is only useful on the X11 platform, other platforms do not use [NETWinInfo](netwininfo.md) and delegate to the variant without [NETWinInfo](netwininfo.md). Though if compiled with X11 support the X11 variant is used on other platforms if `info` is not `nullptr`. This can be used by applications connecting to an XServer.

The [NETWinInfo](netwininfo.md) must be constructed with properties:

- [NET::WMIcon](net.md#Property-enum) to use the [IconSource](kx11extras.md#IconSource-enum) flag NETWM
- [NET::WM2IconPixmap](net.md#Property2-enum) to use the [IconSource](kx11extras.md#IconSource-enum) flag [WMHints](kx11extras.md#IconSource-enum)
- [NET::WM2WindowClass](net.md#Property2-enum) to use the [IconSource](kx11extras.md#IconSource-enum) flag [ClassHint](kx11extras.md#IconSource-enum)

`win` The id of the window.

`width` The desired width, or -1.

`height` The desired height, or -1.

`scale` If true the icon will be scaled to the desired size. Otherwise the icon will not be modified.

`flags` OR-ed flags from the [IconSource](kx11extras.md#IconSource-enum) enum.

This is an overloaded function.

### \[static\] bool KX11Extras::mapViewport() {#mapViewport}

Returns true if viewports are mapped to virtual desktops.

### \[static\] void KX11Extras::minimizeWindow(WId *win*) {#minimizeWindow}

Minimizes the window with id `win`.

On X11 this follows the protocol described in ICCCM section 4.1.4.

*See also* [unminimizeWindow](kx11extras.md#unminimizeWindow)()

### \[static\] int KX11Extras::numberOfDesktops() {#numberOfDesktops}

Returns the number of virtual desktops.

### \[signal\] void KX11Extras::numberOfDesktopsChanged(int *num*) {#numberOfDesktopsChanged}

The number `num` of desktops changed.

### \[static\] QString KX11Extras::readNameProperty(WId *window*, unsigned long *atom*) {#readNameProperty}

Reads and returns the contents of the given text property (WM\_NAME, WM\_ICON\_NAME,...).

### \[static\] KX11Extras \*KX11Extras::self() {#self}

### \[static\] void KX11Extras::setCurrentDesktop(int *desktop*) {#setCurrentDesktop}

Convenience function to set the current desktop to `desktop` number.

See [NETRootInfo](netrootinfo.md).

*See also* [currentDesktop](kx11extras.md#currentDesktop)()

### \[static\] void KX11Extras::setDesktopName(int *desktop*, const QString &*name*) {#setDesktopName}

Sets the `name` of the specified `desktop` number.

*See also* [desktopName](kx11extras.md#desktopName)()

### \[static\] void KX11Extras::setExtendedStrut(WId *win*, qreal *left\_width*, qreal *left\_start*, qreal *left\_end*, qreal *right\_width*, qreal *right\_start*, qreal *right\_end*, qreal *top\_width*, qreal *top\_start*, qreal *top\_end*, qreal *bottom\_width*, qreal *bottom\_start*, qreal *bottom\_end*) {#setExtendedStrut}

Sets the strut of window `win` to `left_width` ranging from `left_start` to `left_end` on the left edge, and simiarly for the other edges. For not reserving a strut, pass 0 as the width. E.g. to reserve 10x10 square in the topleft corner, use e.g. setExtendedStrut( w, 10, 0, 10, 0, 0, 0, 0, 0, 0, 0, 0, 0 ).

`win` The id of the window.

`left_width` Width of the strut at the left edge.

`left_start` Starting y coordinate of the strut at the left edge.

`left_end` Ending y coordinate of the strut at the left edge.

`right_width` Width of the strut at the right edge.

`right_start` Starting y coordinate of the strut at the right edge.

`right_end` Ending y coordinate of the strut at the right edge.

`top_width` Width of the strut at the top edge.

`top_start` Starting x coordinate of the strut at the top edge.

`top_end` Ending x coordinate of the strut at the top edge.

`bottom_width` Width of the strut at the bottom edge.

`bottom_start` Starting x coordinate of the strut at the bottom edge.

`bottom_end` Ending x coordinate of the strut at the bottom edge.

### \[static\] void KX11Extras::setOnActivities(WId *win*, const QStringList &*activities*) {#setOnActivities}

Moves window id `win` to the list of `activities` UUIDs.

*See also* [KWindowInfo::activities](kwindowinfo.md#activities)

### \[static\] void KX11Extras::setOnAllDesktops(WId *win*, bool *b*) {#setOnAllDesktops}

Sets window id `win` to be present on all virtual desktops if `b` is true. Otherwise the window lives only on one single desktop.

### \[static\] void KX11Extras::setOnDesktop(WId *win*, int *desktop*) {#setOnDesktop}

Moves window id `win` to `desktop`.

### \[static, since 6.0\] void KX11Extras::setState(WId *win*, NET::States *state*) {#setState}

Sets the state of window `win` to `state`.

Possible values are OR'ed combinations of:

- [NET::Modal](net.md#State-enum)
- [NET::Sticky](net.md#State-enum)
- [NET::MaxVert](net.md#State-enum)
- [NET::MaxHoriz](net.md#State-enum)
- [NET::Shaded](net.md#State-enum)
- [NET::SkipTaskbar](net.md#State-enum)
- [NET::SkipPager](net.md#State-enum)
- [NET::Hidden](net.md#State-enum)
- [NET::FullScreen](net.md#State-enum)
- [NET::KeepAbove](net.md#State-enum)
- [NET::KeepBelow](net.md#State-enum)
- [NET::SkipSwitcher](net.md#State-enum)

This function was introduced in Qt 6.0.

### \[static\] void KX11Extras::setStrut(WId *win*, qreal *left*, qreal *right*, qreal *top*, qreal *bottom*) {#setStrut}

Convenience function for [setExtendedStrut](kx11extras.md#setExtendedStrut)() that automatically makes struts as wide/high as the screen width/height. Sets the strut of window `win` to `left`, `right`, `top`, `bottom`.

*See also* [setExtendedStrut](kx11extras.md#setExtendedStrut)

### \[static, since 6.0\] void KX11Extras::setType(WId *win*, NET::WindowType *windowType*) {#setType}

Sets the type of window `win` to `windowType`.

This function was introduced in Qt 6.0.

*See also* [NET::WindowType](net.md#WindowType-enum)

### \[static\] QList\<WId\> KX11Extras::stackingOrder() {#stackingOrder}

Returns the list of all toplevel windows currently managed by the window manager in the current stacking order (from lower to higher).

May be useful for pagers.

### \[signal\] void KX11Extras::stackingOrderChanged() {#stackingOrderChanged}

Emitted when the stacking order of the window changed.

The new order can be obtained with [stackingOrder](kx11extras.md#stackingOrder)().

### \[signal\] void KX11Extras::strutChanged() {#strutChanged}

Something changed with the struts, may or may not have changed the work area.

Usually just using the [workAreaChanged](kx11extras.md#workAreaChanged)() signal is sufficient.

### \[static\] void KX11Extras::unminimizeWindow(WId *win*) {#unminimizeWindow}

Unminimizes the window with id `win`.

On X11 this follows the protocol described in ICCCM section 4.1.4.

*See also* [minimizeWindow](kx11extras.md#minimizeWindow)()

### \[signal\] void KX11Extras::windowAdded(WId *id*) {#windowAdded}

A window with the given `id` has been added.

### \[signal\] void KX11Extras::windowChanged(WId *id*, NET::Properties *properties*, NET::Properties2 *properties2*) {#windowChanged}

The window with the given `id` changed.

Carries the [NET::Properties](net.md#Property-enum) `properties` and [NET::Properties2](net.md#Property2-enum) `properties2` that were changed.

### \[signal\] void KX11Extras::windowRemoved(WId *id*) {#windowRemoved}

A window with the given `id` has been removed.

### \[static\] QList\<WId\> KX11Extras::windows() {#windows}

Returns the list of all toplevel windows currently managed by the window manager in the order of creation.

Please do not rely on indexes of this list: Whenever you enter Qt's event loop in your application, it may happen that entries are removed or added. Your module should perhaps work on a copy of this list and verify a window with [hasWId](kx11extras.md#hasWId)() before any operations.

Iteration over this list can be done easily with:

```cpp
QList<WId> windows = KWindowSystem::windows();
for (auto it = windows.cbegin(), end = windows.cend(); it != end; ++it) {
   ... do something here,  (*it) is the current WId.
}
```

### \[static\] QRect KX11Extras::workArea(int *desktop* = -1) {#workArea}

Returns the workarea for the specified `desktop`, or the current work area if no desktop has been specified.

The current desktop corresponds to -1.

### \[static\] QRect KX11Extras::workArea(const QList\<WId\> &*excludes*, int *desktop* = -1) {#workArea-1}

Returns the workarea for the specified `desktop`, or the current work area if no desktop has been specified.

A list of struts belonging to clients can be specified with `excludes`.

### \[signal\] void KX11Extras::workAreaChanged() {#workAreaChanged}

The workarea has changed.
