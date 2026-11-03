---
title: "NETRootInfo Class"
description: "Common API for root window properties/protocols."
---

# NETRootInfo Class

Common API for root window properties/protocols. [More...](#details)

- **Header:** `#include <NETWM>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KWindowSystem)`  
  `target_link_libraries(mytarget PRIVATE KF6::KWindowSystem)`
- **Inherits:** [NET](net.md)

[List of all members, including inherited members](netrootinfo-members.md)

## Public Types

- [\[anonymous\] enum](#anonymous-netwm-h-53-enum)

## Public Functions

- [NETRootInfo(xcb\_connection\_t \*connection, NET::Properties properties, NET::Properties2 properties2 = Properties2(), int screen = -1, bool doActivate = true)](#NETRootInfo-1)
- [NETRootInfo(xcb\_connection\_t \*connection, xcb\_window\_t supportWindow, const char \*wmName, NET::Properties properties, NET::WindowTypes windowTypes, NET::States states, NET::Properties2 properties2, NET::Actions actions, int screen = -1, bool doActivate = true)](#NETRootInfo-2)
- [NETRootInfo(const NETRootInfo &rootinfo)](#NETRootInfo)
- [void activate()](#activate)
- [xcb\_window\_t activeWindow() const](#activeWindow)
- [const xcb\_window\_t \*clientList() const](#clientList)
- [int clientListCount() const](#clientListCount)
- [const xcb\_window\_t \*clientListStacking() const](#clientListStacking)
- [int clientListStackingCount() const](#clientListStackingCount)
- [void closeWindowRequest(xcb\_window\_t window)](#closeWindowRequest)
- [int currentDesktop(bool ignore\_viewport = false) const](#currentDesktop)
- [NETSize desktopGeometry() const](#desktopGeometry)
- [QSize desktopLayoutColumnsRows() const](#desktopLayoutColumnsRows)
- [NET::DesktopLayoutCorner desktopLayoutCorner() const](#desktopLayoutCorner)
- [NET::Orientation desktopLayoutOrientation() const](#desktopLayoutOrientation)
- [const char \*desktopName(int desktop) const](#desktopName)
- [NETPoint desktopViewport(int desktop) const](#desktopViewport)
- [NET::Properties event(xcb\_generic\_event\_t \*event)](#event)
- [void event(xcb\_generic\_event\_t \*event, NET::Properties \*properties, NET::Properties2 \*properties2 = nullptr)](#event-1)
- [bool isSupported(NET::Property property) const](#isSupported)
- [bool isSupported(NET::Action action) const](#isSupported-1)
- [bool isSupported(NET::Property2 property) const](#isSupported-2)
- [bool isSupported(NET::State state) const](#isSupported-3)
- [bool isSupported(NET::WindowTypeMask type) const](#isSupported-4)
- [void moveResizeRequest(xcb\_window\_t window, int x\_root, int y\_root, NET::Direction direction, xcb\_button\_t button = XCB\_BUTTON\_INDEX\_ANY, NET::RequestSource source = RequestSource::FromUnknown)](#moveResizeRequest)
- [void moveResizeWindowRequest(xcb\_window\_t window, int flags, int x, int y, int width, int height)](#moveResizeWindowRequest)
- [int numberOfDesktops(bool ignore\_viewport = false) const](#numberOfDesktops)
- [NET::Actions passedActions() const](#passedActions)
- [NET::Properties2 passedProperties2() const](#passedProperties2)
- [NET::Properties passedProperties() const](#passedProperties)
- [NET::States passedStates() const](#passedStates)
- [NET::WindowTypes passedWindowTypes() const](#passedWindowTypes)
- [void restackRequest(xcb\_window\_t window, NET::RequestSource source, xcb\_window\_t above, int detail, xcb\_timestamp\_t timestamp)](#restackRequest)
- [xcb\_window\_t rootWindow() const](#rootWindow)
- [void sendPing(xcb\_window\_t window, xcb\_timestamp\_t timestamp)](#sendPing)
- [void setActiveWindow(xcb\_window\_t window)](#setActiveWindow)
- [void setActiveWindow(xcb\_window\_t window, NET::RequestSource src, xcb\_timestamp\_t timestamp, xcb\_window\_t active\_window)](#setActiveWindow-1)
- [void setClientList(const xcb\_window\_t \*windows, unsigned int count)](#setClientList)
- [void setClientListStacking(const xcb\_window\_t \*windows, unsigned int count)](#setClientListStacking)
- [void setCurrentDesktop(int desktop, bool ignore\_viewport = false)](#setCurrentDesktop)
- [void setDesktopGeometry(const NETSize &geometry)](#setDesktopGeometry)
- [void setDesktopLayout(NET::Orientation orientation, int columns, int rows, NET::DesktopLayoutCorner corner)](#setDesktopLayout)
- [void setDesktopName(int desktop, const char \*desktopName)](#setDesktopName)
- [void setDesktopViewport(int desktop, const NETPoint &viewport)](#setDesktopViewport)
- [void setNumberOfDesktops(int numberOfDesktops)](#setNumberOfDesktops)
- [void setShowingDesktop(bool showing)](#setShowingDesktop)
- [void setSupported(NET::Property property, bool on = true)](#setSupported)
- [void setSupported(NET::Action property, bool on = true)](#setSupported-1)
- [void setSupported(NET::Property2 property, bool on = true)](#setSupported-2)
- [void setSupported(NET::State property, bool on = true)](#setSupported-3)
- [void setSupported(NET::WindowTypeMask property, bool on = true)](#setSupported-4)
- [void setVirtualRoots(const xcb\_window\_t \*windows, unsigned int count)](#setVirtualRoots)
- [void setWorkArea(int desktop, const NETRect &workArea)](#setWorkArea)
- [void showWindowMenuRequest(xcb\_window\_t window, int device\_id, int x\_root, int y\_root)](#showWindowMenuRequest)
- [bool showingDesktop() const](#showingDesktop)
- [xcb\_window\_t supportWindow() const](#supportWindow)
- [NET::Actions supportedActions() const](#supportedActions)
- [NET::Properties2 supportedProperties2() const](#supportedProperties2)
- [NET::Properties supportedProperties() const](#supportedProperties)
- [NET::States supportedStates() const](#supportedStates)
- [NET::WindowTypes supportedWindowTypes() const](#supportedWindowTypes)
- [const xcb\_window\_t \*virtualRoots() const](#virtualRoots)
- [int virtualRootsCount() const](#virtualRootsCount)
- [const char \*wmName() const](#wmName)
- [NETRect workArea(int desktop) const](#workArea)
- [xcb\_connection\_t \*xcbConnection() const](#xcbConnection)
- [const NETRootInfo &NETRootInfo::operator=(const NETRootInfo &rootinfo)](#operator-eq)

## Protected Functions

- [void addClient(xcb\_window\_t window)](#addClient)
- [void changeActiveWindow(xcb\_window\_t window, NET::RequestSource src, xcb\_timestamp\_t timestamp, xcb\_window\_t active\_window)](#changeActiveWindow)
- [void changeCurrentDesktop(int desktop)](#changeCurrentDesktop)
- [void changeDesktopGeometry(int desktop, const NETSize &geom)](#changeDesktopGeometry)
- [void changeDesktopViewport(int desktop, const NETPoint &viewport)](#changeDesktopViewport)
- [void changeNumberOfDesktops(int numberOfDesktops)](#changeNumberOfDesktops)
- [void changeShowingDesktop(bool showing)](#changeShowingDesktop)
- [void closeWindow(xcb\_window\_t window)](#closeWindow)
- [void gotPing(xcb\_window\_t window, xcb\_timestamp\_t timestamp)](#gotPing)
- [void moveResize(xcb\_window\_t window, int x\_root, int y\_root, unsigned long direction, xcb\_button\_t button, NET::RequestSource source)](#moveResize)
- [void moveResizeWindow(xcb\_window\_t window, int flags, int x, int y, int width, int height)](#moveResizeWindow)
- [void removeClient(xcb\_window\_t window)](#removeClient)
- [void restackWindow(xcb\_window\_t window, NET::RequestSource source, xcb\_window\_t above, int detail, xcb\_timestamp\_t timestamp)](#restackWindow)
- [void showWindowMenu(xcb\_window\_t window, int device\_id, int x\_root, int y\_root)](#showWindowMenu)
- [void virtual\_hook(int id, void \*data)](#virtual_hook)

## Detailed Description {#details}

The [NETRootInfo](netrootinfo.md) class provides a common API for clients and window managers to set/read/change properties on the root window as defined by the NET Window Manager Specification..

\*

*See also* [NET](net.md), [NETWinInfo](netwininfo.md)

## Member Type Documentation {#member-type-documentation}

### \[anonymous\] enum {#anonymous-netwm-h-53-enum}

Indexes for the properties array.

| Constant | Value |   |
| --- | --- | --- |
| `NETRootInfo::PROTOCOLS` | `0` |   |
| `NETRootInfo::WINDOW_TYPES` | `1` |   |
| `NETRootInfo::STATES` | `2` |   |
| `NETRootInfo::PROTOCOLS2` | `3` |   |
| `NETRootInfo::ACTIONS` | `4` |   |
| `NETRootInfo::PROPERTIES_SIZE` | `5` | \* |

## Member Function Documentation {#member-function-documentation}

### NETRootInfo::NETRootInfo(xcb\_connection\_t \**connection*, NET::Properties *properties*, NET::Properties2 *properties2* = NET::Properties2(), int *screen* = -1, bool *doActivate* = true) {#NETRootInfo-1}

Clients should use this constructor to create a [NETRootInfo](netrootinfo.md) object, which will be used to query information set on the root window. The application role is automatically set to Client when using this constructor.

`connection` XCB connection

`properties` The properties the client is interested in.

`properties2` The properties2 the client is interested in.

`properties_size` The number of elements in the properties array.

`screen` For Clients that support multiple screen (ie. "multiheaded") displays, the screen number may be explicitly defined. If this argument is omitted, the default screen will be used.

`doActivate` true to call [activate](netrootinfo.md#activate)() to do an initial data read/update of the query information. \*

### NETRootInfo::NETRootInfo(xcb\_connection\_t \**connection*, xcb\_window\_t *supportWindow*, const char \**wmName*, NET::Properties *properties*, NET::WindowTypes *windowTypes*, NET::States *states*, NET::Properties2 *properties2*, NET::Actions *actions*, int *screen* = -1, bool *doActivate* = true) {#NETRootInfo-2}

Window Managers should use this constructor to create a [NETRootInfo](netrootinfo.md) object, which will be used to set/update information stored on the [rootWindow](netrootinfo.md#rootWindow). The application role is automatically set to WindowManager when using this constructor.

`connection` XCB connection

`supportWindow` The Window id of the [supportWindow](netrootinfo.md#supportWindow). The [supportWindow](netrootinfo.md#supportWindow) must be created by the window manager as a child of the [rootWindow](netrootinfo.md#rootWindow). The [supportWindow](netrootinfo.md#supportWindow) must not be destroyed until the Window Manager exits.

`wmName` A string which should be the window manager's name (ie. "KWin" or "Blackbox").

`properties` The properties the window manager supports

`windowTypes` The window types the window manager supports

`states` The states the window manager supports

`properties2` The properties2 the window manager supports

`actions` The actions the window manager supports

`screen` For Window Managers that support multiple screen (ie. "multiheaded") displays, the screen number may be explicitly defined. If this argument is omitted, the default screen will be used.

`doActivate` true to activate the window \*

### NETRootInfo::NETRootInfo(const NETRootInfo &*rootinfo*) {#NETRootInfo}

Creates a shared copy of the specified [NETRootInfo](netrootinfo.md) object.

`rootinfo` the [NETRootInfo](netrootinfo.md) object to copy \*

### void NETRootInfo::activate() {#activate}

Window Managers must call this after creating the [NETRootInfo](netrootinfo.md) object, and before using any other method in the class. This method sets initial data on the root window and does other post-construction duties.

Clients must also call this after creating the object to do an initial data read/update. \*

### xcb\_window\_t NETRootInfo::activeWindow() const {#activeWindow}

Returns the active (focused) window.

Returns the id of the active window \*

*See also* [setActiveWindow](netrootinfo.md#setActiveWindow)()

### \[virtual protected\] void NETRootInfo::addClient(xcb\_window\_t *window*) {#addClient}

A Client should subclass [NETRootInfo](netrootinfo.md) and reimplement this function when it wants to know when a window has been added.

`window` the id of the window to add \*

### \[virtual protected\] void NETRootInfo::changeActiveWindow(xcb\_window\_t *window*, NET::RequestSource *src*, xcb\_timestamp\_t *timestamp*, xcb\_window\_t *active\_window*) {#changeActiveWindow}

A Window Manager should subclass [NETRootInfo](netrootinfo.md) and reimplement this function when it wants to know when a Client made a request to change the active (focused) window.

`window` the id of the window to activate

`src` the source from which the request came

`timestamp` the timestamp of the user action causing this request

`active_window` active window of the requesting application, if any \*

### \[virtual protected\] void NETRootInfo::changeCurrentDesktop(int *desktop*) {#changeCurrentDesktop}

A Window Manager should subclass [NETRootInfo](netrootinfo.md) and reimplement this function when it wants to know when a Client made a request to change the current desktop.

`desktop` the number of the desktop \*

### \[virtual protected\] void NETRootInfo::changeDesktopGeometry(int *desktop*, const NETSize &*geom*) {#changeDesktopGeometry}

A Window Manager should subclass [NETRootInfo](netrootinfo.md) and reimplement this function when it wants to know when a Client made a request to change the specified desktop geometry.

`desktop` the number of the desktop

`geom` the new size \*

### \[virtual protected\] void NETRootInfo::changeDesktopViewport(int *desktop*, const NETPoint &*viewport*) {#changeDesktopViewport}

A Window Manager should subclass [NETRootInfo](netrootinfo.md) and reimplement this function when it wants to know when a Client made a request to change the specified desktop viewport.

`desktop` the number of the desktop

`viewport` the new position of the viewport \*

### \[virtual protected\] void NETRootInfo::changeNumberOfDesktops(int *numberOfDesktops*) {#changeNumberOfDesktops}

A Window Manager should subclass [NETRootInfo](netrootinfo.md) and reimplement this function when it wants to know when a Client made a request to change the number of desktops.

`numberOfDesktops` the new number of desktops \*

### \[virtual protected\] void NETRootInfo::changeShowingDesktop(bool *showing*) {#changeShowingDesktop}

A Window Manager should subclass [NETRootInfo](netrootinfo.md) and reimplement this function when it wants to know when a pager made a request to change showing the desktop. See \_NET\_SHOWING\_DESKTOP for details.

`showing` whether to activate the showing desktop mode \*

### const xcb\_window\_t \*NETRootInfo::clientList() const {#clientList}

Returns an array of Window id's, which contain all managed windows.

Returns the array of Window id's

\*

*See also* [setClientList](netrootinfo.md#setClientList)(), [clientListCount](netrootinfo.md#clientListCount)()

### int NETRootInfo::clientListCount() const {#clientListCount}

Returns the number of managed windows in [clientList](netrootinfo.md#clientList) array.

Returns the number of managed windows in the [clientList](netrootinfo.md#clientList) array

\*

*See also* [clientList](netrootinfo.md#clientList)()

### const xcb\_window\_t \*NETRootInfo::clientListStacking() const {#clientListStacking}

Returns an array of Window id's, which contain all managed windows in stacking order.

Returns the array of Window id's in stacking order

\*

*See also* [setClientListStacking](netrootinfo.md#setClientListStacking)(), [clientListStackingCount](netrootinfo.md#clientListStackingCount)()

### int NETRootInfo::clientListStackingCount() const {#clientListStackingCount}

Returns the number of managed windows in the [clientListStacking](netrootinfo.md#clientListStacking) array.

Returns the number of Window id's in the client list

\*

*See also* [clientListStacking](netrootinfo.md#clientListStacking)()

### \[virtual protected\] void NETRootInfo::closeWindow(xcb\_window\_t *window*) {#closeWindow}

A Window Manager should subclass [NETRootInfo](netrootinfo.md) and reimplement this function when it wants to know when a Client made a request to close a window.

`window` the id of the window to close \*

### void NETRootInfo::closeWindowRequest(xcb\_window\_t *window*) {#closeWindowRequest}

Clients (such as pagers/taskbars) that wish to close a window should call this function. This will send a request to the Window Manager, which usually can usually decide how to react to such requests.

`window` the id of the window to close \*

### int NETRootInfo::currentDesktop(bool *ignore\_viewport* = false) const {#currentDesktop}

Returns the current desktop.

> **Note:** KDE uses virtual desktops and does not directly support viewport in any way. They are however mapped to virtual desktops if needed.

`ignore_viewport` if false, viewport is mapped to virtual desktops

Returns the number of the current desktop \*

*See also* [setCurrentDesktop](netrootinfo.md#setCurrentDesktop)()

### NETSize NETRootInfo::desktopGeometry() const {#desktopGeometry}

Returns the desktop geometry size.

> **Note:** KDE uses virtual desktops and does not directly support viewport in any way. You should use calls for virtual desktops, viewport is mapped to them if needed.

Returns the size of the desktop \*

*See also* [setDesktopGeometry](netrootinfo.md#setDesktopGeometry)()

### QSize NETRootInfo::desktopLayoutColumnsRows() const {#desktopLayoutColumnsRows}

Returns the desktop layout number of columns and rows. Note that either may be 0 (see \_NET\_DESKTOP\_LAYOUT). \*

### NET::DesktopLayoutCorner NETRootInfo::desktopLayoutCorner() const {#desktopLayoutCorner}

Returns the desktop layout starting corner. \*

### NET::Orientation NETRootInfo::desktopLayoutOrientation() const {#desktopLayoutOrientation}

Returns the desktop layout orientation. \*

### const char \*NETRootInfo::desktopName(int *desktop*) const {#desktopName}

Returns the name for the specified desktop.

`desktop` the number of the desktop

Returns the name of the desktop \*

*See also* [setDesktopName](netrootinfo.md#setDesktopName)()

### NETPoint NETRootInfo::desktopViewport(int *desktop*) const {#desktopViewport}

Returns the viewport of the specified desktop.

> **Note:** KDE uses virtual desktops and does not directly support viewport in any way. You should use calls for virtual desktops, viewport is mapped to them if needed.

`desktop` the number of the desktop

Returns the position of the desktop's viewport \*

*See also* [setDesktopViewport](netrootinfo.md#setDesktopViewport)()

### NET::Properties NETRootInfo::event(xcb\_generic\_event\_t \**event*) {#event}

This function takes the passed XEvent and returns an OR'ed list of [NETRootInfo](netrootinfo.md) properties that have changed. The new information will be read immediately by the class. This overloaded version returns only a single mask, and therefore cannot check state of all properties like the other variant.

`event` the event

Returns the properties \*

### void NETRootInfo::event(xcb\_generic\_event\_t \**event*, NET::Properties \**properties*, NET::Properties2 \**properties2* = nullptr) {#event-1}

This function takes the passed xcb\_generic\_event\_t and returns the updated properties in the passed in arguments.

The new information will be read immediately by the class. It is possible to pass in a null pointer in the arguments. In that case the passed in argument will obviously not be updated, but the class will process the information nevertheless.

`event` the event

`properties` The [NET::Properties](net.md#Property-enum) that changed

`properties2` The [NET::Properties2](net.md#Property2-enum) that changed

### \[virtual protected\] void NETRootInfo::gotPing(xcb\_window\_t *window*, xcb\_timestamp\_t *timestamp*) {#gotPing}

A Window Manager should subclass [NETRootInfo](netrootinfo.md) and reimplement this function when it wants to receive replies to the \_NET\_WM\_PING protocol.

`window` the window from which the reply came

`timestamp` timestamp of the ping

### bool NETRootInfo::isSupported(NET::Property *property*) const {#isSupported}

Returns true if the given property is supported by the window manager. Note that for Client mode, [NET::Supported](net.md#Property-enum) needs to be passed in the properties argument for this to work. \*

### bool NETRootInfo::isSupported(NET::Action *action*) const {#isSupported-1}

\*

This is an overloaded function.

### bool NETRootInfo::isSupported(NET::Property2 *property*) const {#isSupported-2}

\*

This is an overloaded function.

### bool NETRootInfo::isSupported(NET::State *state*) const {#isSupported-3}

\*

This is an overloaded function.

### bool NETRootInfo::isSupported(NET::WindowTypeMask *type*) const {#isSupported-4}

\*

This is an overloaded function.

### \[virtual protected\] void NETRootInfo::moveResize(xcb\_window\_t *window*, int *x\_root*, int *y\_root*, unsigned long *direction*, xcb\_button\_t *button*, NET::RequestSource *source*) {#moveResize}

A Window Manager should subclass [NETRootInfo](netrootinfo.md) and reimplement this function when it wants to know when a Client made a request to start a move/resize.

`window` The window that wants to move/resize

`x_root` X position of the cursor relative to the root window.

`y_root` Y position of the cursor relative to the root window.

`direction` One of [NET::Direction](net.md#Direction-enum) (see base class documentation for a description of the different directions).

`button` the button which should be pressed.

`source` who initiated the move resize operation. \*

### void NETRootInfo::moveResizeRequest(xcb\_window\_t *window*, int *x\_root*, int *y\_root*, NET::Direction *direction*, xcb\_button\_t *button* = XCB\_BUTTON\_INDEX\_ANY, NET::RequestSource *source* = RequestSource::FromUnknown) {#moveResizeRequest}

Clients (such as pagers/taskbars) that wish to start a WMMoveResize (where the window manager controls the resize/movement, i.e. \_NET\_WM\_MOVERESIZE) should call this function. This will send a request to the Window Manager.

`window` The client window that would be resized/moved.

`x_root` X position of the cursor relative to the root window.

`y_root` Y position of the cursor relative to the root window.

`direction` One of [NET::Direction](net.md#Direction-enum) (see base class documentation for a description of the different directions).

`button` the button which should be pressed.

`source` who initiated the move resize operation. \*

### \[virtual protected\] void NETRootInfo::moveResizeWindow(xcb\_window\_t *window*, int *flags*, int *x*, int *y*, int *width*, int *height*) {#moveResizeWindow}

A Window Manager should subclass [NETRootInfo](netrootinfo.md) and reimplement this function when it wants to know when a pager made a request to move/resize a window. See \_NET\_MOVERESIZE\_WINDOW for details.

`window` the id of the window to more/resize

`flags` Flags specifying the operation (see \_NET\_MOVERESIZE\_WINDOW description)

`x` Requested X position for the window

`y` Requested Y position for the window

`width` Requested width for the window

`height` Requested height for the window \*

### void NETRootInfo::moveResizeWindowRequest(xcb\_window\_t *window*, int *flags*, int *x*, int *y*, int *width*, int *height*) {#moveResizeWindowRequest}

Clients (such as pagers/taskbars) that wish to move/resize a window using WM2MoveResizeWindow (\_NET\_MOVERESIZE\_WINDOW) should call this function. This will send a request to the Window Manager. See \_NET\_MOVERESIZE\_WINDOW description for details.

`window` The client window that would be resized/moved.

`flags` Flags specifying the operation (see \_NET\_MOVERESIZE\_WINDOW description)

`x` Requested X position for the window

`y` Requested Y position for the window

`width` Requested width for the window

`height` Requested height for the window \*

### int NETRootInfo::numberOfDesktops(bool *ignore\_viewport* = false) const {#numberOfDesktops}

Returns the number of desktops.

> **Note:** KDE uses virtual desktops and does not directly support viewport in any way. They are however mapped to virtual desktops if needed.

`ignore_viewport` if false, viewport is mapped to virtual desktops

Returns the number of desktops \*

*See also* [setNumberOfDesktops](netrootinfo.md#setNumberOfDesktops)()

### NET::Actions NETRootInfo::passedActions() const {#passedActions}

Returns the actions argument passed to the constructor.

*See also* [passedProperties](netrootinfo.md#passedProperties)(), [passedProperties2](netrootinfo.md#passedProperties2)(), [passedStates](netrootinfo.md#passedStates)(), [passedWindowTypes](netrootinfo.md#passedWindowTypes)()

### NET::Properties2 NETRootInfo::passedProperties2() const {#passedProperties2}

Returns the properties2 argument passed to the constructor.

*See also* [passedProperties](netrootinfo.md#passedProperties)(), [passedStates](netrootinfo.md#passedStates)(), [passedWindowTypes](netrootinfo.md#passedWindowTypes)(), [passedActions](netrootinfo.md#passedActions)()

### NET::Properties NETRootInfo::passedProperties() const {#passedProperties}

Returns the properties argument passed to the constructor.

*See also* [passedProperties2](netrootinfo.md#passedProperties2)(), [passedStates](netrootinfo.md#passedStates)(), [passedWindowTypes](netrootinfo.md#passedWindowTypes)(), [passedActions](netrootinfo.md#passedActions)()

### NET::States NETRootInfo::passedStates() const {#passedStates}

Returns the states argument passed to the constructor.

*See also* [passedProperties](netrootinfo.md#passedProperties)(), [passedProperties2](netrootinfo.md#passedProperties2)(), [passedWindowTypes](netrootinfo.md#passedWindowTypes)(), [passedActions](netrootinfo.md#passedActions)()

### NET::WindowTypes NETRootInfo::passedWindowTypes() const {#passedWindowTypes}

Returns the windowTypes argument passed to the constructor.

*See also* [passedProperties](netrootinfo.md#passedProperties)(), [passedProperties2](netrootinfo.md#passedProperties2)(), [passedStates](netrootinfo.md#passedStates)(), [passedActions](netrootinfo.md#passedActions)()

### \[virtual protected\] void NETRootInfo::removeClient(xcb\_window\_t *window*) {#removeClient}

A Client should subclass [NETRootInfo](netrootinfo.md) and reimplement this function when it wants to know when a window has been removed.

`window` the id of the window to remove \*

### void NETRootInfo::restackRequest(xcb\_window\_t *window*, NET::RequestSource *source*, xcb\_window\_t *above*, int *detail*, xcb\_timestamp\_t *timestamp*) {#restackRequest}

Sends the \_NET\_RESTACK\_WINDOW request. \*

### \[virtual protected\] void NETRootInfo::restackWindow(xcb\_window\_t *window*, NET::RequestSource *source*, xcb\_window\_t *above*, int *detail*, xcb\_timestamp\_t *timestamp*) {#restackWindow}

A Window Manager should subclass [NETRootInfo](netrootinfo.md) and reimplement this function when it wants to know when a Client made a request to restack a window. See \_NET\_RESTACK\_WINDOW for details.

`window` the id of the window to restack

`source` the source of the request

`above` other window in the restack request

`detail` restack detail

`timestamp` the timestamp of the request \*

### xcb\_window\_t NETRootInfo::rootWindow() const {#rootWindow}

Returns the Window id of the rootWindow. \*

### void NETRootInfo::sendPing(xcb\_window\_t *window*, xcb\_timestamp\_t *timestamp*) {#sendPing}

Sends a ping with the given timestamp to the window, using the \_NET\_WM\_PING protocol.

### void NETRootInfo::setActiveWindow(xcb\_window\_t *window*) {#setActiveWindow}

Sets the active (focused) window the specified window. This should be used only in the window manager mode.

`window` the if of the new active window \*

*See also* [activeWindow](netrootinfo.md#activeWindow)()

### void NETRootInfo::setActiveWindow(xcb\_window\_t *window*, NET::RequestSource *src*, xcb\_timestamp\_t *timestamp*, xcb\_window\_t *active\_window*) {#setActiveWindow-1}

Requests that the specified window becomes the active (focused) one.

`window` the id of the new active window

`src` whether the request comes from normal application or from a pager or similar tool

`timestamp` X server timestamp of the user action that caused the request

`active_window` active window of the requesting application, if any \*

### void NETRootInfo::setClientList(const xcb\_window\_t \**windows*, unsigned int *count*) {#setClientList}

Sets the list of managed windows on the Root/Desktop window.

`windows` The array of Window id's

`count` The number of windows in the array \*

*See also* [clientList](netrootinfo.md#clientList)()

### void NETRootInfo::setClientListStacking(const xcb\_window\_t \**windows*, unsigned int *count*) {#setClientListStacking}

Sets the list of managed windows in stacking order on the Root/Desktop window.

`windows` The array of Window id's

`count` The number of windows in the array. \*

*See also* [clientListStacking](netrootinfo.md#clientListStacking)()

### void NETRootInfo::setCurrentDesktop(int *desktop*, bool *ignore\_viewport* = false) {#setCurrentDesktop}

Sets the current desktop to the specified desktop.

> **Note:** KDE uses virtual desktops and does not directly support viewport in any way. It is however mapped to virtual desktops if needed.

`desktop` the number of the desktop

`ignore_viewport` if false, viewport is mapped to virtual desktops \*

*See also* [currentDesktop](netrootinfo.md#currentDesktop)()

### void NETRootInfo::setDesktopGeometry(const NETSize &*geometry*) {#setDesktopGeometry}

Sets the desktop geometry to the specified geometry.

> **Note:** KDE uses virtual desktops and does not directly support viewport in any way. You should use calls for virtual desktops, viewport is mapped to them if needed.

`geometry` the new size of the desktop \*

*See also* [desktopGeometry](netrootinfo.md#desktopGeometry)()

### void NETRootInfo::setDesktopLayout(NET::Orientation *orientation*, int *columns*, int *rows*, NET::DesktopLayoutCorner *corner*) {#setDesktopLayout}

Sets the desktop layout. This is set by the pager. When setting, the pager must own the \_NET\_DESKTOP\_LAYOUT\_Sn manager selection. See \_NET\_DESKTOP\_LAYOUT for details. \*

### void NETRootInfo::setDesktopName(int *desktop*, const char \**desktopName*) {#setDesktopName}

Sets the name of the specified desktop.

> **Note:** KDE uses virtual desktops and does not directly support viewport in any way. Viewport is mapped to virtual desktops if needed, but not for this call.

`desktop` the number of the desktop

`desktopName` the new name of the desktop \*

*See also* [desktopName](netrootinfo.md#desktopName)()

### void NETRootInfo::setDesktopViewport(int *desktop*, const NETPoint &*viewport*) {#setDesktopViewport}

Sets the viewport for the current desktop to the specified point.

> **Note:** KDE uses virtual desktops and does not directly support viewport in any way. You should use calls for virtual desktops, viewport is mapped to them if needed.

`desktop` the number of the desktop

`viewport` the new position of the desktop's viewport \*

*See also* [desktopViewport](netrootinfo.md#desktopViewport)()

### void NETRootInfo::setNumberOfDesktops(int *numberOfDesktops*) {#setNumberOfDesktops}

Sets the number of desktops to the specified number.

> **Note:** KDE uses virtual desktops and does not directly support viewport in any way. Viewport is mapped to virtual desktops if needed, but not for this call.

`numberOfDesktops` the number of desktops \*

*See also* [numberOfDesktops](netrootinfo.md#numberOfDesktops)()

### void NETRootInfo::setShowingDesktop(bool *showing*) {#setShowingDesktop}

Sets the \_NET\_SHOWING\_DESKTOP status (whether desktop is being shown).

*See also* [showingDesktop](netrootinfo.md#showingDesktop)()

### void NETRootInfo::setSupported(NET::Property *property*, bool *on* = true) {#setSupported}

Sets the given property if on is true, and clears the property otherwise. In WindowManager mode this function updates \_NET\_SUPPORTED. In Client mode this function does nothing.

\*

*See also* [isSupported](netrootinfo.md#isSupported)()

### void NETRootInfo::setSupported(NET::Action *property*, bool *on* = true) {#setSupported-1}

\*

This is an overloaded function.

### void NETRootInfo::setSupported(NET::Property2 *property*, bool *on* = true) {#setSupported-2}

\*

This is an overloaded function.

### void NETRootInfo::setSupported(NET::State *property*, bool *on* = true) {#setSupported-3}

\*

This is an overloaded function.

### void NETRootInfo::setSupported(NET::WindowTypeMask *property*, bool *on* = true) {#setSupported-4}

\*

This is an overloaded function.

### void NETRootInfo::setVirtualRoots(const xcb\_window\_t \**windows*, unsigned int *count*) {#setVirtualRoots}

Sets the list of virtual root windows on the root window.

`windows` The array of Window id's

`count` The number of windows in the array. \*

*See also* [virtualRoots](netrootinfo.md#virtualRoots)()

### void NETRootInfo::setWorkArea(int *desktop*, const NETRect &*workArea*) {#setWorkArea}

Sets the workarea for the specified desktop

`desktop` the number of the desktop

`workArea` the new work area of the desktop \*

*See also* [workArea](netrootinfo.md#workArea)()

### \[virtual protected\] void NETRootInfo::showWindowMenu(xcb\_window\_t *window*, int *device\_id*, int *x\_root*, int *y\_root*) {#showWindowMenu}

A Window Manager should subclass [NETRootInfo](netrootinfo.md) and reimplement this function when it wants to know when a Client made a request to show a window menu.

`window` The window that wants to move/resize

`device_id` GTK device id.

`x_root` X position of the cursor relative to the root window.

`y_root` Y position of the cursor relative to the root window. \*

### void NETRootInfo::showWindowMenuRequest(xcb\_window\_t *window*, int *device\_id*, int *x\_root*, int *y\_root*) {#showWindowMenuRequest}

Clients that wish to show the window menu using WM2GTKShowWindowMenu (\_GTK\_SHOW\_WINDOW\_MENU) should call this function. This will send a request to the Window Manager. See \_GTK\_SHOW\_WINDOW\_MENU description for details.

`window` The client window that would be resized/moved.

`device_id` GTK device id

`x` Requested X position for the menu relative to the root window

`y` Requested Y position for the menu relative to the root window \*

### bool NETRootInfo::showingDesktop() const {#showingDesktop}

Returns the status of \_NET\_SHOWING\_DESKTOP.

*See also* [setShowingDesktop](netrootinfo.md#setShowingDesktop)()

### xcb\_window\_t NETRootInfo::supportWindow() const {#supportWindow}

Returns the Window id of the supportWindow. \*

### NET::Actions NETRootInfo::supportedActions() const {#supportedActions}

\* In the Window Manager mode, this is equivalent to the actions \* argument passed to the constructor. In the Client mode, if \* [NET::Supported](net.md#Property-enum) was passed in the properties argument, the returned \* value are all actions supported by the Window Manager. Other supported \* protocols and properties are returned by the specific methods. \*

\*

\*

\* \*

*See also* [supportedProperties](netrootinfo.md#supportedProperties)(), [supportedProperties2](netrootinfo.md#supportedProperties2)(), [supportedStates](netrootinfo.md#supportedStates)(), [supportedWindowTypes](netrootinfo.md#supportedWindowTypes)()

### NET::Properties2 NETRootInfo::supportedProperties2() const {#supportedProperties2}

In the Window Manager mode, this is equivalent to the properties2 argument passed to the constructor. In the Client mode, if [NET::Supported](net.md#Property-enum) was passed in the properties argument, the returned value are all properties2 supported by the Window Manager. Other supported protocols and properties are returned by the specific methods.

*See also* [supportedProperties](netrootinfo.md#supportedProperties)(), [supportedStates](netrootinfo.md#supportedStates)(), [supportedWindowTypes](netrootinfo.md#supportedWindowTypes)(), [supportedActions](netrootinfo.md#supportedActions)()

### NET::Properties NETRootInfo::supportedProperties() const {#supportedProperties}

In the Window Manager mode, this is equivalent to the properties argument passed to the constructor. In the Client mode, if [NET::Supported](net.md#Property-enum) was passed in the properties argument, the returned value are all properties supported by the Window Manager. Other supported protocols and properties are returned by the specific methods.

\*

*See also* [supportedProperties2](netrootinfo.md#supportedProperties2)(), [supportedStates](netrootinfo.md#supportedStates)(), [supportedWindowTypes](netrootinfo.md#supportedWindowTypes)(), [supportedActions](netrootinfo.md#supportedActions)()

### NET::States NETRootInfo::supportedStates() const {#supportedStates}

\* In the Window Manager mode, this is equivalent to the states \* argument passed to the constructor. In the Client mode, if \* [NET::Supported](net.md#Property-enum) was passed in the properties argument, the returned \* value are all states supported by the Window Manager. Other supported \* protocols and properties are returned by the specific methods. \*

\*

\*

\* \*

*See also* [supportedProperties](netrootinfo.md#supportedProperties)(), [supportedProperties2](netrootinfo.md#supportedProperties2)(), [supportedWindowTypes](netrootinfo.md#supportedWindowTypes)(), [supportedActions](netrootinfo.md#supportedActions)()

### NET::WindowTypes NETRootInfo::supportedWindowTypes() const {#supportedWindowTypes}

\* In the Window Manager mode, this is equivalent to the windowTypes \* argument passed to the constructor. In the Client mode, if \* [NET::Supported](net.md#Property-enum) was passed in the properties argument, the returned \* value are all window types supported by the Window Manager. Other supported \* protocols and properties are returned by the specific methods. \*

\*

\*

\* \*

*See also* [supportedProperties](netrootinfo.md#supportedProperties)(), [supportedProperties2](netrootinfo.md#supportedProperties2)(), [supportedStates](netrootinfo.md#supportedStates)(), [supportedActions](netrootinfo.md#supportedActions)()

### const xcb\_window\_t \*NETRootInfo::virtualRoots() const {#virtualRoots}

Returns an array of Window id's, which contain the virtual root windows.

Returns the array of Window id's

\*

*See also* [setVirtualRoots](netrootinfo.md#setVirtualRoots)(), [virtualRootsCount](netrootinfo.md#virtualRootsCount)()

### int NETRootInfo::virtualRootsCount() const {#virtualRootsCount}

Returns the number of window in the [virtualRoots](netrootinfo.md#virtualRoots) array.

Returns the number of Window id's in the virtual root array

\*

*See also* [virtualRoots](netrootinfo.md#virtualRoots)()

### \[virtual protected\] void NETRootInfo::virtual\_hook(int *id*, void \**data*) {#virtual_hook}

Virtual hook, used to add new "virtual" functions while maintaining binary compatibility. Unused in this class.

### const char \*NETRootInfo::wmName() const {#wmName}

Returns the name of the Window Manager. \*

### NETRect NETRootInfo::workArea(int *desktop*) const {#workArea}

Returns the workArea for the specified desktop.

`desktop` the number of the desktop

Returns the size of the work area \*

*See also* [setWorkArea](netrootinfo.md#setWorkArea)()

### xcb\_connection\_t \*NETRootInfo::xcbConnection() const {#xcbConnection}

Returns the xcb connection used. \*

### const NETRootInfo &NETRootInfo::operator=(const NETRootInfo &*rootinfo*) {#operator-eq}

Assignment operator. Ensures that the shared data reference counts are correct. \*
