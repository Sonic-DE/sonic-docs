---
title: "KWindowInfo Class"
description: "This class provides information about a given X11 window."
---

# KWindowInfo Class

This class provides information about a given X11 window. [More...](#details)

- **Header:** `#include <KWindowInfo>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KWindowSystem)`  
  `target_link_libraries(mytarget PRIVATE KF6::KWindowSystem)`

[List of all members, including inherited members](kwindowinfo-members.md)

## Public Functions

- [KWindowInfo(WId window, NET::Properties properties, NET::Properties2 properties2 = Properties2())](#KWindowInfo)
- [bool actionSupported(NET::Action action) const](#actionSupported)
- [QStringList activities() const](#activities)
- [QByteArray applicationMenuObjectPath() const](#applicationMenuObjectPath)
- [QByteArray applicationMenuServiceName() const](#applicationMenuServiceName)
- [QByteArray clientMachine() const](#clientMachine)
- [int desktop() const](#desktop)
- [QByteArray desktopFileName() const](#desktopFileName)
- [NETExtendedStrut extendedStrut() const](#extendedStrut)
- [QRect frameGeometry() const](#frameGeometry)
- [QRect geometry() const](#geometry)
- [WId groupLeader() const](#groupLeader)
- [QByteArray gtkApplicationId() const](#gtkApplicationId)
- [bool hasState(NET::States s) const](#hasState)
- [QString iconName() const](#iconName)
- [bool isMinimized() const](#isMinimized)
- [bool isOnCurrentDesktop() const](#isOnCurrentDesktop)
- [bool isOnDesktop(int desktop) const](#isOnDesktop)
- [NET::MappingState mappingState() const](#mappingState)
- [QString name() const](#name)
- [bool onAllDesktops() const](#onAllDesktops)
- [int pid() const](#pid)
- [NET::States state() const](#state)
- [WId transientFor() const](#transientFor)
- [bool valid(bool withdrawn\_is\_valid = false) const](#valid)
- [QString visibleIconName() const](#visibleIconName)
- [QString visibleIconNameWithState() const](#visibleIconNameWithState)
- [QString visibleName() const](#visibleName)
- [QString visibleNameWithState() const](#visibleNameWithState)
- [WId win() const](#win)
- [QByteArray windowClassClass() const](#windowClassClass)
- [QByteArray windowClassName() const](#windowClassName)
- [QByteArray windowRole() const](#windowRole)
- [NET::WindowType windowType(NET::WindowTypes supported\_types) const](#windowType)

## Detailed Description {#details}

It provides the information for the current state when a [KWindowInfo](kwindowinfo.md) instance gets created. The instance does not get updated when the window changes. To get update about window changes connect to [KX11Extras::windowChanged](kx11extras.md#windowChanged) and create a new [KWindowInfo](kwindowinfo.md) instance to reflect the current state.

[KWindowInfo](kwindowinfo.md) does not encapsulate all information about the window. One needs to request which information is required by passing the appropriate [NET::Property](net.md#Property-enum) and [NET::Property2](net.md#Property2-enum) flags to the constructor. Please refer to the documentation of the methods to see which flags are required. This is done to limit the interaction with the xserver and avoid excess roundtrips.

[KWindowInfo](kwindowinfo.md) does nothing when running outside of X11.

Example usage of this class illustrated by monitoring a QWidget for change of the demands attention window state:

```cpp
QWidget *widget = new QWidget(nullptr);
widget->show(); // ensures native window gets created
connect(KX11Extras::self(), &KX11Extras::KWindowSystem::windowChanged,
       [window](WId id, NET::Properties properties, NET::Properties2 properties2) {
    if (widget->winId() != winId) {
        return; // not our window
    }
    if (properties & NET::WMState) {
        // let's check whether our window is demanding attention
        KWindowInfo info(widget->winId(), NET::WMState);
        qDebug() << "Has demands attention: " << info.hasState(NET::DemandsAttention);
    }
});
```

## Member Function Documentation {#member-function-documentation}

### KWindowInfo::KWindowInfo(WId *window*, NET::Properties *properties*, NET::Properties2 *properties2* = NET::Properties2()) {#KWindowInfo}

Reads all the info about the given `window`.

Only the information requested through the `properties` and `properties2` parameters are fetched. Refer to the methods you are interested in to see which flags to pass.

`properties` Bitmask of [NET::Property](net.md#Property-enum)

`properties2` Bitmask of [NET::Property2](net.md#Property2-enum)

### bool KWindowInfo::actionSupported(NET::Action *action*) const {#actionSupported}

Returns true if the given `action` is currently supported for the window.

The supported actions are set by the window manager and can differ depending on the window manager. Requires [NET::WM2AllowedActions](net.md#Property2-enum) passed as properties2 parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), 0, NET::WM2AllowedActions);
if (info.valid())
    info.actionSupported(NET::ActionClose);
```

### QStringList KWindowInfo::activities() const {#activities}

Returns the list of activity UUIDs this window belongs to.

The Plasma workspace allows the user to separate its work into different activities, by assigning windows, documents etc. to the specific ones. An activity is an abstract concept whose meaning can differ from one user to another. Typical examples of activities are "developing a KDE project", "studying the 19th century art", "composing music", "lazing on a Sunday afternoon" etc.

If the list is empty, or contains a null UUID, the window is on all activities.

Requires [NET::WM2Activities](net.md#Property2-enum) passed as properties parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), 0, NET::WM2Activities);
if (info.valid())
    info.desktop();
```

### QByteArray KWindowInfo::applicationMenuObjectPath() const {#applicationMenuObjectPath}

Returns object path of a window's application menu if present.

Requires [NET::WMPid](net.md#Property-enum) passed as properties parameter to the constructor.

### QByteArray KWindowInfo::applicationMenuServiceName() const {#applicationMenuServiceName}

Returns service name of a window's application menu if present.

Requires [NET::WMPid](net.md#Property-enum) passed as properties parameter to the constructor.

### QByteArray KWindowInfo::clientMachine() const {#clientMachine}

Returns the WM\_CLIENT\_MACHINE property for the window.

Requires [NET::WM2ClientMachine](net.md#Property2-enum) passed as properties2 parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), 0, NET::WM2ClientMachine);
if (info.valid())
    info.clientMachine();
```

### int KWindowInfo::desktop() const {#desktop}

Returns the virtual desktop this window is on.

If the window is on all desktops NET::OnAllDesktops is returned. You should prefer using [isOnDesktop](kwindowinfo.md#isOnDesktop)(). Requires [NET::WMDesktop](net.md#Property-enum) passed as properties parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), NET::WMDesktop);
if (info.valid())
    info.desktop();
```

*See also* [isOnDesktop](kwindowinfo.md#isOnDesktop)()

### QByteArray KWindowInfo::desktopFileName() const {#desktopFileName}

Returns the desktop file name of the window's application if present.

This is either the base name without full path and without file extension of the desktop file for the window's application (e.g. "org.kde.foo").

If the application's desktop file name is not at a standard location it should be the full path to the desktop file name (e.g. "/opt/kde/share/org.kde.foo.desktop").

Requires [NET::WM2DesktopFileName](net.md#Property2-enum) passed as properties2 parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), 0, NET::WM2DesktopFileName);
if (info.valid())
    info.desktopFileName();
```

### NETExtendedStrut KWindowInfo::extendedStrut() const {#extendedStrut}

Returns the window extended (partial) strut.

Requires [NET::WM2ExtendedStrut](net.md#Property2-enum) passed as properties2 parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), 0, NET::WM2ExtendedStrut);
if (info.valid())
    info.extendedStrut();
```

### QRect KWindowInfo::frameGeometry() const {#frameGeometry}

Returns the frame geometry of the window, i.e. including the window decoration.

Requires [NET::WMFrameExtents](net.md#Property-enum) passed as properties parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), NET::WMFrameExtents);
if (info.valid())
    info.frameGeometry();
```

### QRect KWindowInfo::geometry() const {#geometry}

Returns the position and size of the window contents.

Requires [NET::WMGeometry](net.md#Property-enum) passed as properties parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), NET::WMGeometry);
if (info.valid())
    info.geometry();
```

### WId KWindowInfo::groupLeader() const {#groupLeader}

Returns the leader window for the group the window is in, if any.

Requires [NET::WM2GroupLeader](net.md#Property2-enum) passed as properties2 parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), 0, NET::WM2GroupLeader);
if (info.valid())
    info.groupLeader();
```

### QByteArray KWindowInfo::gtkApplicationId() const {#gtkApplicationId}

Returns the GTK application id of the window if present.

This is comparable to [desktopFileName](kwindowinfo.md#desktopFileName).

Requires [NET::WM2GTKApplicationId](net.md#Property2-enum) passed as properties2 parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), 0, NET::WM2GTKApplicationId);
if (info.valid())
    info.gtkApplicationId();
```

### bool KWindowInfo::hasState(NET::States *s*) const {#hasState}

Returns `true` if the window has the given state flag `s` set.

Requires [NET::WMState](net.md#Property-enum) passed as properties parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), NET::WMState);
if (info.valid())
    info.hasState(NET::DemandsAttention);
```

*See also* [NET::State](net.md#State-enum)

### QString KWindowInfo::iconName() const {#iconName}

Returns the name of the window that should be shown in taskbar.

Note that this has nothing to do with normal icons but with an "iconic" representation of the window. Requires [NET::WMIconName](net.md#Property-enum) passed as properties parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), NET::WMIconName);
if (info.valid())
    info.iconName();
```

### bool KWindowInfo::isMinimized() const {#isMinimized}

Returns true if the window is minimized.

Note that it is true only if the window is truly minimized, not shaded or on another virtual desktops, which makes it different from [mappingState](kwindowinfo.md#mappingState)() == [NET::Iconic](net.md#MappingState-enum) or QWidget::isMinimized(). Requires [NET::WMState](net.md#Property-enum) and [NET::XAWMState](net.md#Property-enum) passed as properties parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), NET::WMState | NET::XAWMState);
if (info.valid())
    info.isMinimized();
```

### bool KWindowInfo::isOnCurrentDesktop() const {#isOnCurrentDesktop}

Returns true if the window is on the currently active virtual desktop.

Requires [NET::WMDesktop](net.md#Property-enum) passed as properties parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), NET::WMDesktop);
if (info.valid())
    info.isOnCurrentDesktop();
```

### bool KWindowInfo::isOnDesktop(int *desktop*) const {#isOnDesktop}

Returns true if the window is on the given virtual `desktop`.

Requires [NET::WMDesktop](net.md#Property-enum) passed as properties parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), NET::WMDesktop);
if (info.valid())
    info.isOnDesktop(KWindowSystem::currentDesktop());
```

### NET::MappingState KWindowInfo::mappingState() const {#mappingState}

Returns the mapping state of the window.

Note that it's very likely that you don't want to use this function, and use [isOnDesktop](kwindowinfo.md#isOnDesktop)(), [isMinimized](kwindowinfo.md#isMinimized)() etc. instead. Requires [NET::XAWMState](net.md#Property-enum) passed as properties parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), NET::XAWMState);
if (info.valid())
    info.mappingState();
```

*See also* [NET::MappingState](net.md#MappingState-enum), [isOnDesktop](kwindowinfo.md#isOnDesktop)(), isMinimzed()

### QString KWindowInfo::name() const {#name}

Returns the name of the window, as specified by the application.

The difference to [visibleName](kwindowinfo.md#visibleName)() is that this is the name provided by the application without any modifications by the window manager. You should often use [visibleName](kwindowinfo.md#visibleName)() instead. Requires [NET::WMName](net.md#Property-enum) passed as properties parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), NET::WMName);
if (info.valid())
    info.name();
```

*See also* [visibleName](kwindowinfo.md#visibleName)()

### bool KWindowInfo::onAllDesktops() const {#onAllDesktops}

Returns true if the window is on all desktops.

A window is on all desktops if [desktop](kwindowinfo.md#desktop)() returns NET::OnAllDesktops. Requires [NET::WMDesktop](net.md#Property-enum) passed as properties parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), NET::WMDesktop);
if (info.valid())
    info.onAllDesktops();
```

*See also* [desktop](kwindowinfo.md#desktop)()

### int KWindowInfo::pid() const {#pid}

Returns the process ID of the window's application if present.

Requires [NET::WMPid](net.md#Property-enum) passed as properties parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), NET::WMPid);
if (info.valid())
    info.pid();
```

### NET::States KWindowInfo::state() const {#state}

Returns the window's state flags.

Requires [NET::WMState](net.md#Property-enum) passed as properties parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), NET::WMState);
if (info.valid())
    info.state();
```

*See also* [NET::State](net.md#State-enum)

### WId KWindowInfo::transientFor() const {#transientFor}

Returns the window identifier of the main window this window belongs to.

This is the value of the WM\_TRANSIENT\_FOR X11 property.

Requires [NET::WM2TransientFor](net.md#Property2-enum) passed as properties2 parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), 0, NET::WM2TransientFor);
if (info.valid())
    info.transientFor();
```

### bool KWindowInfo::valid(bool *withdrawn\_is\_valid* = false) const {#valid}

Returns false if this window info is not valid.

In case the window does not exist `false` is returned.

`withdrawn_is_valid` If true, windows in the withdrawn state (i.e. not managed) are also considered. This is usually not the case.

### QString KWindowInfo::visibleIconName() const {#visibleIconName}

Returns the visible name of the window that should be shown in a taskbar.

Note that this has nothing to do with normal icons but with an "iconic" representation of the window. Requires [NET::WMVisibleIconName](net.md#Property-enum) passed as properties parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), NET::WMVisibleIconName);
if (info.valid())
    info.visibleIconName();
```

### QString KWindowInfo::visibleIconNameWithState() const {#visibleIconNameWithState}

Returns a visible icon name with state.

This is a simple convenience function that returns the visible iconic name but with parentheses around minimized windows. Note that this has nothing to do with normal icons. Requires [NET::WMVisibleIconName](net.md#Property-enum), [NET::WMState](net.md#Property-enum) and [NET::XAWMState](net.md#Property-enum) passed as properties parameter to the constructor. Returns the window iconic name with state

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), NET::WMVisibleIconName | NET::WMState | NET::XAWMState);
if (info.valid())
    info.visibleIconNameWithState();
```

*See also* [visibleIconName](kwindowinfo.md#visibleIconName)()

### QString KWindowInfo::visibleName() const {#visibleName}

Returns the visible name of the window.

The visible name differs from the name by including possible \<2\> appended when there are two or more windows with the same name. Requires [NET::WMVisibleName](net.md#Property-enum) passed as properties parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), NET::WMVisibleName);
if (info.valid())
    info.visibleName();
```

*See also* [name](kwindowinfo.md#name)()

### QString KWindowInfo::visibleNameWithState() const {#visibleNameWithState}

Returns a visible name with state.

This is a simple convenience function that returns the visible name but with parentheses around minimized windows. Requires [NET::WMVisibleName](net.md#Property-enum), [NET::WMState](net.md#Property-enum) and [NET::XAWMState](net.md#Property-enum) passed as properties parameter to the constructor. Returns the window name with state

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), NET::WMVisibleName | NET::WMState | NET::XAWMState);
if (info.valid())
    info.visibleNameWithState();
```

*See also* [visibleName](kwindowinfo.md#visibleName)()

### WId KWindowInfo::win() const {#win}

Returns the window identifier.

### QByteArray KWindowInfo::windowClassClass() const {#windowClassClass}

Returns the class component of the WM\_CLASS X11 property for the window.

Requires [NET::WM2WindowClass](net.md#Property2-enum) passed as properties2 parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), 0, NET::WM2WindowClass);
if (info.valid())
    info.windowClassClass();
```

### QByteArray KWindowInfo::windowClassName() const {#windowClassName}

Returns the name component of the WM\_CLASS X11 property for the window.

Requires [NET::WM2WindowClass](net.md#Property2-enum) passed as properties2 parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), 0, NET::WM2WindowClass);
if (info.valid())
    info.windowClassName();
```

### QByteArray KWindowInfo::windowRole() const {#windowRole}

Returns the WM\_WINDOW\_ROLE X11 property for the window.

Requires [NET::WM2WindowRole](net.md#Property2-enum) passed as properties2 parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), 0, NET::WM2WindowRole);
if (info.valid())
    info.windowRole();
```

### NET::WindowType KWindowInfo::windowType(NET::WindowTypes *supported\_types*) const {#windowType}

Returns the window type of this window.

The argument should be all window `supported_types` your application supports. Requires [NET::WMWindowType](net.md#Property-enum) passed as properties parameter to the constructor.

```cpp
QWidget *window = new QWidget(nullptr);
window->show();
KWindowInfo info(window->winId(), NET::WMWindowType);
if (info.valid())
    info.windowType(NET::NormalMask | NET::DialogMask);
```

*See also* [NET::WindowType](net.md#WindowType-enum), [NET::WindowTypeMask](net.md#WindowTypeMask-enum)
