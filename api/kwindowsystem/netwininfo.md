---
title: "NETWinInfo Class"
description: "Common API for application window properties/protocols."
---

# NETWinInfo Class

Common API for application window properties/protocols. [More...](#details)

- **Header:** `#include <NETWM>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KWindowSystem)`  
  `target_link_libraries(mytarget PRIVATE KF6::KWindowSystem)`
- **Inherits:** [NET](net.md)

[List of all members, including inherited members](netwininfo-members.md)  
[Deprecated members](netwininfo-obsolete.md)

## Public Types

- [\[anonymous\] enum](#anonymous-netwm-h-1009-enum)

## Public Functions

- [NETWinInfo(xcb\_connection\_t \*connection, xcb\_window\_t window, xcb\_window\_t rootWindow, NET::Properties properties, NET::Properties2 properties2, NET::Role role = Client)](#NETWinInfo-1)
- [NETWinInfo(const NETWinInfo &wininfo)](#NETWinInfo)
- [const char \*activities() const](#activities)
- [NET::Actions allowedActions() const](#allowedActions)
- [const char \*appMenuObjectPath() const](#appMenuObjectPath)
- [const char \*appMenuServiceName() const](#appMenuServiceName)
- [const char \*clientMachine() const](#clientMachine)
- [int desktop(bool ignore\_viewport = false) const](#desktop)
- [const char \*desktopFileName() const](#desktopFileName)
- [NET::Properties event(xcb\_generic\_event\_t \*event)](#event)
- [void event(xcb\_generic\_event\_t \*event, NET::Properties \*properties, NET::Properties2 \*properties2 = nullptr)](#event-1)
- [NETExtendedStrut extendedStrut() const](#extendedStrut)
- [NETStrut frameExtents() const](#frameExtents)
- [NETStrut frameOverlap() const](#frameOverlap)
- [NETFullscreenMonitors fullscreenMonitors() const](#fullscreenMonitors)
- [xcb\_window\_t groupLeader() const](#groupLeader)
- [const char \*gtkApplicationId() const](#gtkApplicationId)
- [NETStrut gtkFrameExtents() const](#gtkFrameExtents)
- [bool handledIcons() const](#handledIcons)
- [bool hasNETSupport() const](#hasNETSupport)
- [bool hasWindowType() const](#hasWindowType)
- [xcb\_pixmap\_t icccmIconPixmap() const](#icccmIconPixmap)
- [xcb\_pixmap\_t icccmIconPixmapMask() const](#icccmIconPixmapMask)
- [NETIcon icon(int width = -1, int height = -1) const](#icon)
- [NETRect iconGeometry() const](#iconGeometry)
- [const char \*iconName() const](#iconName)
- [const int \*iconSizes() const](#iconSizes)
- [NET::MappingState initialMappingState() const](#initialMappingState)
- [bool input() const](#input)
- [bool isBlockingCompositing() const](#isBlockingCompositing)
- [void kdeGeometry(NETRect &frame, NETRect &window)](#kdeGeometry)
- [NET::MappingState mappingState() const](#mappingState)
- [const char \*name() const](#name)
- [unsigned long opacity() const](#opacity)
- [qreal opacityF() const](#opacityF)
- [std::vector\<NETRect\> opaqueRegion() const](#opaqueRegion)
- [NET::Properties2 passedProperties2() const](#passedProperties2)
- [NET::Properties passedProperties() const](#passedProperties)
- [int pid() const](#pid)
- [NET::Protocols protocols() const](#protocols)
- [void setActivities(const char \*activities)](#setActivities)
- [void setAllowedActions(NET::Actions actions)](#setAllowedActions)
- [void setAppMenuObjectPath(const char \*path)](#setAppMenuObjectPath)
- [void setAppMenuServiceName(const char \*name)](#setAppMenuServiceName)
- [void setBlockingCompositing(bool active)](#setBlockingCompositing)
- [void setDesktop(int desktop, bool ignore\_viewport = false)](#setDesktop)
- [void setDesktopFileName(const char \*name)](#setDesktopFileName)
- [void setExtendedStrut(const NETExtendedStrut &extended\_strut)](#setExtendedStrut)
- [void setFrameExtents(NETStrut strut)](#setFrameExtents)
- [void setFrameOverlap(NETStrut strut)](#setFrameOverlap)
- [void setFullscreenMonitors(NETFullscreenMonitors topology)](#setFullscreenMonitors)
- [void setGtkFrameExtents(NETStrut strut)](#setGtkFrameExtents)
- [void setHandledIcons(bool handled)](#setHandledIcons)
- [void setIcon(NETIcon icon, bool replace = true)](#setIcon)
- [void setIconGeometry(NETRect geometry)](#setIconGeometry)
- [void setIconName(const char \*name)](#setIconName)
- [void setName(const char \*name)](#setName)
- [void setOpacity(unsigned long opacity)](#setOpacity)
- [void setOpacityF(qreal opacity)](#setOpacityF)
- [void setPid(int pid)](#setPid)
- [void setStartupId(const char \*startup\_id)](#setStartupId)
- [void setState(NET::States state, NET::States mask)](#setState)
- [void setUserTime(xcb\_timestamp\_t time)](#setUserTime)
- [void setVisibleIconName(const char \*name)](#setVisibleIconName)
- [void setVisibleName(const char \*visibleName)](#setVisibleName)
- [void setWindowType(NET::WindowType type)](#setWindowType)
- [const char \*startupId() const](#startupId)
- [NET::States state() const](#state)
- [bool supportsProtocol(NET::Protocol protocol) const](#supportsProtocol)
- [xcb\_window\_t transientFor() const](#transientFor)
- [bool urgency() const](#urgency)
- [xcb\_timestamp\_t userTime() const](#userTime)
- [const char \*visibleIconName() const](#visibleIconName)
- [const char \*visibleName() const](#visibleName)
- [const char \*windowClassClass() const](#windowClassClass)
- [const char \*windowClassName() const](#windowClassName)
- [const char \*windowRole() const](#windowRole)
- [NET::WindowType windowType(NET::WindowTypes supported\_types) const](#windowType)
- [xcb\_connection\_t \*xcbConnection() const](#xcbConnection)

## Protected Functions

- [void changeDesktop(int desktop)](#changeDesktop)
- [void changeFullscreenMonitors(NETFullscreenMonitors topology)](#changeFullscreenMonitors)
- [void changeState(NET::States state, NET::States mask)](#changeState)

## Detailed Description {#details}

The [NETWinInfo](netwininfo.md) class provides a common API for clients and window managers to set/read/change properties on an application window as defined by the NET Window Manager Specification.

\*

*See also* [NET](net.md), [NETRootInfo](netrootinfo.md), [http://www.freedesktop.org/standards/wm-spec/](http://www.freedesktop.org/standards/wm-spec/)

## Member Type Documentation {#member-type-documentation}

### \[anonymous\] enum {#anonymous-netwm-h-1009-enum}

Indexes for the properties array.

| Constant | Value |   |
| --- | --- | --- |
| `NETWinInfo::PROTOCOLS` | `0` |   |
| `NETWinInfo::PROTOCOLS2` | `1` |   |
| `NETWinInfo::PROPERTIES_SIZE` | `2` | \* |

## Member Function Documentation {#member-function-documentation}

### NETWinInfo::NETWinInfo(xcb\_connection\_t \**connection*, xcb\_window\_t *window*, xcb\_window\_t *rootWindow*, NET::Properties *properties*, NET::Properties2 *properties2*, NET::Role *role* = Client) {#NETWinInfo-1}

Create a [NETWinInfo](netwininfo.md) object, which will be used to set/read/change information stored on an application window.

`connection` XCB connection

`window` The Window id of the application window.

`rootWindow` The Window id of the root window.

`properties` The [NET::Properties](net.md#Property-enum) flags

`properties2` The [NET::Properties2](net.md#Property2-enum) flags

`role` Select the application role. If this argument is omitted, the role will default to Client. \*

### NETWinInfo::NETWinInfo(const NETWinInfo &*wininfo*) {#NETWinInfo}

Creates a shared copy of the specified [NETWinInfo](netwininfo.md) object.

`wininfo` the [NETWinInfo](netwininfo.md) to copy \*

### const char \*NETWinInfo::activities() const {#activities}

returns a comma-separated list of the activities the window is associated with. FIXME this might be better as a NETRArray ?

*See also* [setActivities](netwininfo.md#setActivities)()

### NET::Actions NETWinInfo::allowedActions() const {#allowedActions}

Returns actions that the window manager allows for the window.

*See also* [setAllowedActions](netwininfo.md#setAllowedActions)()

### const char \*NETWinInfo::appMenuObjectPath() const {#appMenuObjectPath}

Returns The menu object path of the window's application if present.

*See also* [setAppMenuObjectPath](netwininfo.md#setAppMenuObjectPath)()

### const char \*NETWinInfo::appMenuServiceName() const {#appMenuServiceName}

Returns The menu service name of the window's application if present.

*See also* [setAppMenuServiceName](netwininfo.md#setAppMenuServiceName)()

### \[virtual protected\] void NETWinInfo::changeDesktop(int *desktop*) {#changeDesktop}

A Window Manager should subclass [NETWinInfo](netwininfo.md) and reimplement this function when it wants to know when a Client made a request to change desktops (ie. move to another desktop).

`desktop` the number of the desktop \*

### \[virtual protected\] void NETWinInfo::changeFullscreenMonitors(NETFullscreenMonitors *topology*) {#changeFullscreenMonitors}

A Window Manager should subclass NETWinInfo2 and reimplement this function when it wants to know when a Client made a request to change the fullscreen monitor topology for its fullscreen state.

`topology` A structure (top, bottom, left, right) representing the fullscreen monitor topology. \*

### \[virtual protected\] void NETWinInfo::changeState(NET::States *state*, NET::States *mask*) {#changeState}

A Window Manager should subclass [NETWinInfo](netwininfo.md) and reimplement this function when it wants to know when a Client made a request to change state (ie. to Shade / Unshade).

`state` the new state

`mask` the mask for the state \*

### const char \*NETWinInfo::clientMachine() const {#clientMachine}

Returns the client machine for the window (i.e. WM\_CLIENT\_MACHINE property).

### int NETWinInfo::desktop(bool *ignore\_viewport* = false) const {#desktop}

Returns the desktop where the window is residing.

> **Note:** KDE uses virtual desktops and does not directly support viewport in any way. It is however mapped to virtual desktops if needed.

`ignore_viewport` if false, viewport is mapped to virtual desktops

\*

*See also* [setDesktop](netwininfo.md#setDesktop)(), OnAllDesktops()

### const char \*NETWinInfo::desktopFileName() const {#desktopFileName}

Returns The desktop file name of the window's application if present.

*See also* [setDesktopFileName](netwininfo.md#setDesktopFileName)

### NET::Properties NETWinInfo::event(xcb\_generic\_event\_t \**event*) {#event}

This function takes the pass XEvent and returns an OR'ed list of [NETWinInfo](netwininfo.md) properties that have changed. The new information will be read immediately by the class. This overloaded version returns only a single mask, and therefore cannot check state of all properties like the other variant.

`event` the event

Returns the properties \*

### void NETWinInfo::event(xcb\_generic\_event\_t \**event*, NET::Properties \**properties*, NET::Properties2 \**properties2* = nullptr) {#event-1}

This function takes the passed in xcb\_generic\_event\_t and returns the updated properties in the passed in arguments.

The new information will be read immediately by the class. It is possible to pass in a null pointer in the arguments. In that case the passed in argument will obviously not be updated, but the class will process the information nevertheless.

`event` the event

`properties` The [NET::Properties](net.md#Property-enum) that changed

`properties2` The [NET::Properties2](net.md#Property2-enum) that changed

### NETExtendedStrut NETWinInfo::extendedStrut() const {#extendedStrut}

Returns the extended (partial) strut specified by this client. See \_NET\_WM\_STRUT\_PARTIAL in the spec. \*

*See also* [setExtendedStrut](netwininfo.md#setExtendedStrut)()

### NETStrut NETWinInfo::frameExtents() const {#frameExtents}

Returns the frame decoration strut, i.e. the width of the decoration borders.

\*

*See also* [setFrameExtents](netwininfo.md#setFrameExtents)()

### NETStrut NETWinInfo::frameOverlap() const {#frameOverlap}

Returns the frame overlap strut, i.e. how far the window frame extends behind the client area on each side.

\*

*See also* [setFrameOverlap](netwininfo.md#setFrameOverlap)()

### NETFullscreenMonitors NETWinInfo::fullscreenMonitors() const {#fullscreenMonitors}

Returns the desired fullscreen monitor topology for this client, should it be in fullscreen state. See \_NET\_WM\_FULLSCREEN\_MONITORS in the spec. \*

*See also* [setFullscreenMonitors](netwininfo.md#setFullscreenMonitors)()

### xcb\_window\_t NETWinInfo::groupLeader() const {#groupLeader}

Returns the leader window for the group the window is in, if any.

### const char \*NETWinInfo::gtkApplicationId() const {#gtkApplicationId}

Returns The GTK application id of the window if present.

### NETStrut NETWinInfo::gtkFrameExtents() const {#gtkFrameExtents}

Returns the extents of the drop-shadow drawn by a GTK client.

\*

*See also* [setGtkFrameExtents](netwininfo.md#setGtkFrameExtents)()

### bool NETWinInfo::handledIcons() const {#handledIcons}

Returns whether or not this client handles icons. \*

*See also* [setHandledIcons](netwininfo.md#setHandledIcons)()

### bool NETWinInfo::hasNETSupport() const {#hasNETSupport}

Returns true if the window has any window type set, even if the type itself is not known to this implementation. Presence of a window type as specified by the NETWM spec is considered as the window supporting this specification. Returns true if the window has support for the NETWM spec \*

### bool NETWinInfo::hasWindowType() const {#hasWindowType}

This function returns false if the window has not window type specified at all. Used by [KWindowInfo::windowType](kwindowinfo.md#windowType)() to return either [NET::Normal](net.md#WindowType-enum) or [NET::Dialog](net.md#WindowType-enum) as appropriate as a fallback. \*

### xcb\_pixmap\_t NETWinInfo::icccmIconPixmap() const {#icccmIconPixmap}

Returns the icon pixmap as set in WM\_HINTS. See ICCCM 4.1.2.4.

The default value is XCB\_PIXMAP\_NONE.

Using the ICCCM variant for the icon is deprecated and only offers a limited functionality compared to icon. Only use this variant as a fallback.

*See also* [icccmIconPixmapMask](netwininfo.md#icccmIconPixmapMask), [icon](netwininfo.md#icon)

### xcb\_pixmap\_t NETWinInfo::icccmIconPixmapMask() const {#icccmIconPixmapMask}

Returns the mask for the icon pixmap as set in WM\_HINTS. See ICCCM 4.1.2.4.

The default value is XCB\_PIXMAP\_NONE.

*See also* [icccmIconPixmap](netwininfo.md#icccmIconPixmap)

### NETIcon NETWinInfo::icon(int *width* = -1, int *height* = -1) const {#icon}

Returns an icon. If width and height are passed, the icon returned will be the closest it can find (the next biggest). If width and height are omitted, then the largest icon in the list is returned.

`width` the preferred width for the icon, -1 to ignore

`height` the preferred height for the icon, -1 to ignore

Returns the icon \*

*See also* [setIcon](netwininfo.md#setIcon)()

### NETRect NETWinInfo::iconGeometry() const {#iconGeometry}

Returns the icon geometry. \*

*See also* [setIconGeometry](netwininfo.md#setIconGeometry)()

### const char \*NETWinInfo::iconName() const {#iconName}

Returns the iconic name of the window in UTF-8 format. Note that this has nothing to do with icons, but it's for "iconic" representations of the window (taskbars etc.), that should be shown when the window is in iconic state. See description of \_NET\_WM\_ICON\_NAME for details. \*

*See also* [setIconName](netwininfo.md#setIconName)()

### const int \*NETWinInfo::iconSizes() const {#iconSizes}

Returns a list of provided icon sizes. Each size is pair width,height, terminated with pair 0,0. \*

### NET::MappingState NETWinInfo::initialMappingState() const {#initialMappingState}

Returns the initial mapping state as set in WM\_HINTS. See ICCCM 4.1.2.4 and 4.1.4.

The default value if Withdrawn in case the Client is mapped without a WM\_HINTS property or without the initial state hint set.

### bool NETWinInfo::input() const {#input}

Returns whether the Input flag is set in WM\_HINTS. See ICCCM 4.1.2.4 and 4.1.7.

The default value is true in case the Client is mapped without a WM\_HINTS property.

### bool NETWinInfo::isBlockingCompositing() const {#isBlockingCompositing}

Returns whether the client wishes to block compositing (for better performance)

### void NETWinInfo::kdeGeometry(NETRect &*frame*, NETRect &*window*) {#kdeGeometry}

Places the window frame geometry in frame, and the application window geometry in window. Both geometries are relative to the root window.

`frame` the geometry for the frame

`window` the geometry for the window \*

### NET::MappingState NETWinInfo::mappingState() const {#mappingState}

Returns the mapping state for the window (see the NET base class documentation for a description of mapping state). \*

### const char \*NETWinInfo::name() const {#name}

Returns the name of the window in UTF-8 format. \*

*See also* [setName](netwininfo.md#setName)()

### unsigned long NETWinInfo::opacity() const {#opacity}

Returns the opacity of the window.

*See also* [setOpacity](netwininfo.md#setOpacity)()

### qreal NETWinInfo::opacityF() const {#opacityF}

Returns the opacity of the window.

*See also* [setOpacityF](netwininfo.md#setOpacityF)()

### std::vector\<NETRect\> NETWinInfo::opaqueRegion() const {#opaqueRegion}

Returns The opaque region as specified by the Client.

### NET::Properties2 NETWinInfo::passedProperties2() const {#passedProperties2}

Returns the properties2 argument passed to the constructor.

*See also* [passedProperties](netwininfo.md#passedProperties)()

### NET::Properties NETWinInfo::passedProperties() const {#passedProperties}

Returns the properties argument passed to the constructor.

\*

*See also* [passedProperties2](netwininfo.md#passedProperties2)()

### int NETWinInfo::pid() const {#pid}

Returns the process id for the client window. \*

*See also* [setPid](netwininfo.md#setPid)()

### NET::Protocols NETWinInfo::protocols() const {#protocols}

Returns The window manager protocols this Client supports.

### void NETWinInfo::setActivities(const char \**activities*) {#setActivities}

Sets the comma-separated list of activities the window is associated with.

*See also* [activities](netwininfo.md#activities)()

### void NETWinInfo::setAllowedActions(NET::Actions *actions*) {#setAllowedActions}

Sets actions that the window manager allows for the window.

*See also* [allowedActions](netwininfo.md#allowedActions)()

### void NETWinInfo::setAppMenuObjectPath(const char \**path*) {#setAppMenuObjectPath}

Sets the `name` as the D-BUS object path for the application menu.

*See also* [appMenuObjectPath](netwininfo.md#appMenuObjectPath)()

### void NETWinInfo::setAppMenuServiceName(const char \**name*) {#setAppMenuServiceName}

Sets the `name` as the D-BUS service name for the application menu.

*See also* [appMenuServiceName](netwininfo.md#appMenuServiceName)()

### void NETWinInfo::setBlockingCompositing(bool *active*) {#setBlockingCompositing}

Sets whether the client wishes to block compositing (for better performance)

*See also* [isBlockingCompositing](netwininfo.md#isBlockingCompositing)()

### void NETWinInfo::setDesktop(int *desktop*, bool *ignore\_viewport* = false) {#setDesktop}

Set which window the desktop is (should be) on.

> **Note:** KDE uses virtual desktops and does not directly support viewport in any way. It is however mapped to virtual desktops if needed.

`desktop` the number of the new desktop

`ignore_viewport` if false, viewport is mapped to virtual desktops

\*

*See also* [desktop](netwininfo.md#desktop)(), OnAllDesktops()

### void NETWinInfo::setDesktopFileName(const char \**name*) {#setDesktopFileName}

Sets the `name` as the desktop file name.

This is either the base name without full path and without file extension of the desktop file for the window's application (e.g. "org.kde.foo").

If the application's desktop file name is not at a standard location it should be the full path to the desktop file name (e.g. "/opt/kde/share/org.kde.foo.desktop").

If the window does not know the desktop file name, it should not set the name at all.

*See also* [desktopFileName](netwininfo.md#desktopFileName)()

### void NETWinInfo::setExtendedStrut(const NETExtendedStrut &*extended\_strut*) {#setExtendedStrut}

Set the extended (partial) strut for the application window.

`extended_strut` the new strut \*

*See also* [extendedStrut](netwininfo.md#extendedStrut)()

### void NETWinInfo::setFrameExtents(NETStrut *strut*) {#setFrameExtents}

Set the frame decoration strut, i.e. the width of the decoration borders.

`strut` the new strut \*

*See also* [frameExtents](netwininfo.md#frameExtents)()

### void NETWinInfo::setFrameOverlap(NETStrut *strut*) {#setFrameOverlap}

Sets the window frame overlap strut, i.e. how far the window frame extends behind the client area on each side.

Set the strut values to -1 if you want the window frame to cover the whole client area.

The default values are 0.

\*

*See also* [frameOverlap](netwininfo.md#frameOverlap)()

### void NETWinInfo::setFullscreenMonitors(NETFullscreenMonitors *topology*) {#setFullscreenMonitors}

Sets the desired multiple-monitor topology (4 monitor indices indicating the top, bottom, left, and right edges of the window) when the fullscreen state is enabled. The indices are from the set returned by the Xinerama extension. See \_NET\_WM\_FULLSCREEN\_MONITORS for details.

`topology` A struct that models the desired monitor topology, namely: top is the monitor whose top edge defines the top edge of the fullscreen window, bottom is the monitor whose bottom edge defines the bottom edge of the fullscreen window, left is the monitor whose left edge defines the left edge of the fullscreen window, and right is the monitor whose right edge defines the right edge of the fullscreen window.

\*

*See also* [fullscreenMonitors](netwininfo.md#fullscreenMonitors)()

### void NETWinInfo::setGtkFrameExtents(NETStrut *strut*) {#setGtkFrameExtents}

Sets the extents of the drop-shadow drawn by the client.

\*

*See also* [gtkFrameExtents](netwininfo.md#gtkFrameExtents)()

### void NETWinInfo::setHandledIcons(bool *handled*) {#setHandledIcons}

Set whether this application window handles icons.

`handled` true if the window handles icons, false otherwise \*

*See also* [handledIcons](netwininfo.md#handledIcons)()

### void NETWinInfo::setIcon(NETIcon *icon*, bool *replace* = true) {#setIcon}

Set icons for the application window. If replace is True, then the specified icon is defined to be the only icon. If replace is False, then the specified icon is added to a list of icons.

`icon` the new icon

`replace` true to replace, false to append to the list of icons \*

*See also* [icon](netwininfo.md#icon)()

### void NETWinInfo::setIconGeometry(NETRect *geometry*) {#setIconGeometry}

Set the icon geometry for the application window.

`geometry` the new icon geometry \*

*See also* [iconGeometry](netwininfo.md#iconGeometry)()

### void NETWinInfo::setIconName(const char \**name*) {#setIconName}

Sets the iconic name for the application window.

`name` the new iconic name \*

*See also* [iconName](netwininfo.md#iconName)()

### void NETWinInfo::setName(const char \**name*) {#setName}

Sets the name for the application window.

`name` the new name of the window \*

*See also* [name](netwininfo.md#name)()

### void NETWinInfo::setOpacity(unsigned long *opacity*) {#setOpacity}

Sets opacity (0 = transparent, 0xffffffff = opaque ) on the window.

*See also* [opacity](netwininfo.md#opacity)()

### void NETWinInfo::setOpacityF(qreal *opacity*) {#setOpacityF}

Sets opacity (0 = transparent, 1 = opaque) on the window.

*See also* [opacityF](netwininfo.md#opacityF)()

### void NETWinInfo::setPid(int *pid*) {#setPid}

Set the application window's process id.

`pid` the window's process id \*

*See also* [pid](netwininfo.md#pid)()

### void NETWinInfo::setStartupId(const char \**startup\_id*) {#setStartupId}

Sets the startup notification id `id` on the window.

*See also* [startupId](netwininfo.md#startupId)()

### void NETWinInfo::setState(NET::States *state*, NET::States *mask*) {#setState}

Set the state for the application window (see the NET base class documentation for a description of window state).

`state` the name state

`mask` the mask for the state \*

*See also* [state](netwininfo.md#state)()

### void NETWinInfo::setUserTime(xcb\_timestamp\_t *time*) {#setUserTime}

Sets user timestamp `time` on the window (property \_NET\_WM\_USER\_TIME). The timestamp is expressed as XServer time. If a window is shown with user timestamp older than the time of the last user action, it won't be activated after being shown, with the special value 0 meaning not to activate the window after being shown.

*See also* [userTime](netwininfo.md#userTime)()

### void NETWinInfo::setVisibleIconName(const char \**name*) {#setVisibleIconName}

For Window Managers only: set the visible iconic name ( i.e. xterm, xterm \<2\>, xterm \<3\>, ... )

`name` the new visible iconic name \*

*See also* [visibleIconName](netwininfo.md#visibleIconName)()

### void NETWinInfo::setVisibleName(const char \**visibleName*) {#setVisibleName}

For Window Managers only: set the visible name ( i.e. xterm, xterm \<2\>, xterm \<3\>, ... )

`visibleName` the new visible name \*

*See also* [visibleName](netwininfo.md#visibleName)()

### void NETWinInfo::setWindowType(NET::WindowType *type*) {#setWindowType}

Sets the window type for this client (see the NET base class documentation for a description of the various window types).

`type` the window type \*

*See also* [windowType](netwininfo.md#windowType)()

### const char \*NETWinInfo::startupId() const {#startupId}

Returns the startup notification id of the window.

*See also* [setStartupId](netwininfo.md#setStartupId)()

### NET::States NETWinInfo::state() const {#state}

Returns the state of the window (see the NET base class documentation for a description of the various states). \*

*See also* [setState](netwininfo.md#setState)()

### bool NETWinInfo::supportsProtocol(NET::Protocol *protocol*) const {#supportsProtocol}

Returns true if the Client supports the `protocol`. `protocol` The window manager protocol to test for

### xcb\_window\_t NETWinInfo::transientFor() const {#transientFor}

Returns the WM\_TRANSIENT\_FOR property for the window, i.e. the mainwindow for this window.

### bool NETWinInfo::urgency() const {#urgency}

Returns whether the UrgencyHint is set in the WM\_HINTS.flags. See ICCCM 4.1.2.4.

### xcb\_timestamp\_t NETWinInfo::userTime() const {#userTime}

Returns the time of last user action on the window, or -1 if not set.

*See also* [setUserTime](netwininfo.md#setUserTime)()

### const char \*NETWinInfo::visibleIconName() const {#visibleIconName}

Returns the visible iconic name as set by the window manager in UTF-8 format. Note that this has nothing to do with icons, but it's for "iconic" representations of the window (taskbars etc.), that should be shown when the window is in iconic state. See description of \_NET\_WM\_VISIBLE\_ICON\_NAME for details. \*

*See also* [setVisibleIconName](netwininfo.md#setVisibleIconName)()

### const char \*NETWinInfo::visibleName() const {#visibleName}

Returns the visible name as set by the window manager in UTF-8 format. \*

*See also* [setVisibleName](netwininfo.md#setVisibleName)()

### const char \*NETWinInfo::windowClassClass() const {#windowClassClass}

Returns the class component of the window class for the window (i.e. WM\_CLASS property).

### const char \*NETWinInfo::windowClassName() const {#windowClassName}

Returns the name component of the window class for the window (i.e. WM\_CLASS property).

### const char \*NETWinInfo::windowRole() const {#windowRole}

Returns the window role for the window (i.e. WM\_WINDOW\_ROLE property).

### NET::WindowType NETWinInfo::windowType(NET::WindowTypes *supported\_types*) const {#windowType}

Returns the window type for this client (see the NET base class documentation for a description of the various window types). Since clients may specify several windows types for a window in order to support backwards compatibility and extensions not available in the NETWM spec, you should specify all window types you application supports (see the [NET::WindowTypeMask](net.md#WindowTypeMask-enum) mask values for various window types). This method will return the first window type that is listed in the supported types, or [NET::Unknown](net.md#WindowType-enum) if none of the window types is supported. \*

*See also* [setWindowType](netwininfo.md#setWindowType)()

### xcb\_connection\_t \*NETWinInfo::xcbConnection() const {#xcbConnection}

Returns the xcb connection used.

Returns the XCB connection \*

## Member Variable Documentation {#member-variable-documentation}

### const int NETWinInfo::OnAllDesktops {#OnAllDesktops-var}

Sentinel value to indicate that the client wishes to be visible on all desktops.

Returns the value to be on all desktops \*
