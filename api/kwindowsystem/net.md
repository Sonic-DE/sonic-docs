---
title: "NET Class"
description: "Base namespace class."
---

# NET Class

Base namespace class. [More...](#details)

- **Header:** `#include <NET>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KWindowSystem)`  
  `target_link_libraries(mytarget PRIVATE KF6::KWindowSystem)`
- **Inherited By:** [NETRootInfo](netrootinfo.md) and [NETWinInfo](netwininfo.md)

[List of all members, including inherited members](net-members.md)

## Public Types

- [enum NET::Action](#Action-enum)
- [enum NET::DesktopLayoutCorner](#DesktopLayoutCorner-enum)
- [enum NET::Direction](#Direction-enum)
- [enum NET::MappingState](#MappingState-enum)
- [enum NET::Orientation](#Orientation-enum)
- [enum NET::Property2](#Property2-enum)
- [enum NET::Property](#Property-enum)
- [enum NET::Protocol](#Protocol-enum)
- [enum NET::RequestSource](#RequestSource-enum)
- [enum NET::Role](#Role-enum)
- [enum NET::State](#State-enum)
- [enum NET::WindowType](#WindowType-enum)
- [enum NET::WindowTypeMask](#WindowTypeMask-enum)

## Static Public Members

- [int timestampCompare(unsigned long time1, unsigned long time2)](#timestampCompare)
- [int timestampDiff(unsigned long time1, unsigned long time2)](#timestampDiff)
- [bool typeMatchesMask(NET::WindowType type, NET::WindowTypes mask)](#typeMatchesMask)

## Detailed Description {#details}

The NET API is an implementation of the NET Window Manager Specification.

This class is the base class for the [NETRootInfo](netrootinfo.md) and [NETWinInfo](netwininfo.md) classes, which are used to retrieve and modify the properties of windows. To keep the namespace relatively clean, all enums are defined here.

*See also* [https://specifications.freedesktop.org/wm-spec/wm-spec-latest.html](https://specifications.freedesktop.org/wm-spec/wm-spec-latest.html)

## Member Type Documentation {#member-type-documentation}

### enum NET::Action {#Action-enum}

**flags NET::Actions**

Actions that can be done with a window (\_NET\_WM\_ALLOWED\_ACTIONS).

| Constant |   |
| --- | --- |
| `NET::ActionMove` | `1u << 0` |
| `NET::ActionResize` | `1u << 1` |
| `NET::ActionMinimize` | `1u << 2` |
| `NET::ActionShade` | `1u << 3` |
| `NET::ActionStick` | `1u << 4` |
| `NET::ActionMaxVert` | `1u << 5` |
| `NET::ActionMaxHoriz` | `1u << 6` |
| `NET::ActionMax` | `ActionMaxVert | ActionMaxHoriz` |
| `NET::ActionFullScreen` | `1u << 7` |
| `NET::ActionChangeDesktop` | `1u << 8` |
| `NET::ActionClose` | `1u << 9` |

The `Actions` type is a typedef for `QFlags<Action>. `It stores an OR combination of `Action` values.

### enum NET::DesktopLayoutCorner {#DesktopLayoutCorner-enum}

Starting corner for desktop layout.

| Constant |   |
| --- | --- |
| `NET::DesktopLayoutCornerTopLeft` | `0` |
| `NET::DesktopLayoutCornerTopRight` | `1` |
| `NET::DesktopLayoutCornerBottomLeft` | `2` |
| `NET::DesktopLayoutCornerBottomRight` | `3` |

### enum NET::Direction {#Direction-enum}

Direction for [WMMoveResize](net.md#Property-enum).

When a client wants the Window Manager to start a [WMMoveResize](net.md#Property-enum), it should specify one of:

| Constant | Value |   |
| --- | --- | --- |
| `NET::TopLeft` | `0` |   |
| `NET::Top` | `1` |   |
| `NET::TopRight` | `2` |   |
| `NET::Right` | `3` |   |
| `NET::BottomRight` | `4` |   |
| `NET::Bottom` | `5` |   |
| `NET::BottomLeft` | `6` |   |
| `NET::Left` | `7` |   |
| `NET::Move` | `8` | For movement only. |
| `NET::KeyboardSize` | `9` | Resizing via keyboard. |
| `NET::KeyboardMove` | `10` | Movement via keyboard. |
| `NET::MoveResizeCancel` | `11` | To ask the WM to stop moving a window. |

### enum NET::MappingState {#MappingState-enum}

Client window mapping state. The class automatically watches the mapping state of the client windows, and uses the mapping state to determine how to set/change different properties. Note that this is very lowlevel and you most probably don't want to use this state.

| Constant | Value | Description |
| --- | --- | --- |
| `NET::Visible` | `1` | Indicates the client window is visible to the user. |
| `NET::Withdrawn` | `0` | Indicates that neither the client window nor its icon is visible. |
| `NET::Iconic` | `3` | Indicates that the client window is not visible, but its icon is. This can be when the window is minimized or when it's on a different virtual desktop. See also [NET::Hidden](net.md#State-enum). |

### enum NET::Orientation {#Orientation-enum}

Orientation.

| Constant |   |
| --- | --- |
| `NET::OrientationHorizontal` | `0` |
| `NET::OrientationVertical` | `1` |

### enum NET::Property2 {#Property2-enum}

**flags NET::Properties2**

Supported properties. This enum is an extension to [NET::Property](net.md#Property-enum), because them enum is limited only to 32 bits.

Client window properties and protocols:

| Constant | Value |   |
| --- | --- | --- |
| `NET::WM2UserTime` | `1u << 0` |   |
| `NET::WM2StartupId` | `1u << 1` |   |
| `NET::WM2TransientFor` | `1u << 2` | Main window for the window (WM\_TRANSIENT\_FOR). |
| `NET::WM2GroupLeader` | `1u << 3` | Group leader (window\_group in WM\_HINTS). |
| `NET::WM2AllowedActions` | `1u << 4` |   |
| `NET::WM2RestackWindow` | `1u << 5` |   |
| `NET::WM2MoveResizeWindow` | `1u << 6` |   |
| `NET::WM2ExtendedStrut` | `1u << 7` |   |
| `NET::WM2KDETemporaryRules` | `1u << 8` | Non-standard. |
| `NET::WM2WindowClass` | `1u << 9` | WM\_CLASS |
| `NET::WM2WindowRole` | `1u << 10` | WM\_WINDOW\_ROLE |
| `NET::WM2ClientMachine` | `1u << 11` | WM\_CLIENT\_MACHINE |
| `NET::WM2ShowingDesktop` | `1u << 12` |   |
| `NET::WM2Opacity` | `1u << 13` | \_NET\_WM\_WINDOW\_OPACITY |
| `NET::WM2DesktopLayout` | `1u << 14` | \_NET\_DESKTOP\_LAYOUT |
| `NET::WM2FullPlacement` | `1u << 15` | \_NET\_WM\_FULL\_PLACEMENT |
| `NET::WM2FullscreenMonitors` | `1u << 16` | \_NET\_WM\_FULLSCREEN\_MONITORS |
| `NET::WM2FrameOverlap` | `1u << 17` | Non-standard. |
| `NET::WM2Activities (since Qt 4.6)` | `1u << 18` | Non-standard. |
| `NET::WM2BlockCompositing (since Qt 4.7)` | `1u << 19` | Standard since 5.17. |
| `NET::WM2KDEShadow (since Qt 4.7)` | `1u << 20` | Non-standard. |
| `NET::WM2Urgency (since Qt 5.3)` | `1u << 21` | Urgency hint in WM\_HINTS (see ICCCM 4.1.2.4). |
| `NET::WM2Input (since Qt 5.3)` | `1u << 22` | Input hint (input in WM\_HINTS, see ICCCM 4.1.2.4). |
| `NET::WM2Protocols (since Qt 5.3)` | `1u << 23` | See [NET::Protocol](net.md#Protocol-enum). |
| `NET::WM2InitialMappingState (since Qt 5.5)` | `1u << 24` | Initial state hint of WM\_HINTS (see ICCCM 4.1.2.4). |
| `NET::WM2IconPixmap (since Qt 5.7)` | `1u << 25` | Icon pixmap and mask in WM\_HINTS (see ICCCM 4.1.2.4). |
| `NET::WM2OpaqueRegion (since Qt 5.7)` | `1u << 25` |   |
| `NET::WM2DesktopFileName (since Qt 5.28)` | `1u << 26` | Non-standard. The base name of the desktop file name or the full path to the desktop file. |
| `NET::WM2GTKFrameExtents (since Qt 5.65)` | `1u << 27` | Non-standard. Extents of the shadow drawn by the client. |
| `NET::WM2AppMenuServiceName (since Qt 5.69)` | `1u << 28` | . Non-standard. |
| `NET::WM2AppMenuObjectPath (since Qt 5.69)` | `1u << 29` | . Non-standard. |
| `NET::WM2GTKApplicationId (since Qt 5.91)` | `1u << 30` | Non-standard. \_GTK\_APPLICATION\_ID |
| `NET::WM2GTKShowWindowMenu (since Qt 5.96)` | `1u << 31` | Non-standard. \_GTK\_SHOW\_WINDOW\_MENU |
| `NET::WM2AllProperties` | `~0u` |   |

The `Properties2` type is a typedef for `QFlags<Property2>. `It stores an OR combination of `Property2` values.

### enum NET::Property {#Property-enum}

**flags NET::Properties**

Supported properties. Clients and Window Managers must define which properties/protocols it wants to support.

| Constant | Value | Description |
| --- | --- | --- |
| `NET::WMAllProperties` | `~0u` | Root/Desktop window properties and protocols: |
| `NET::Supported` | `1u << 0` |   |
| `NET::ClientList` | `1u << 1` |   |
| `NET::ClientListStacking` | `1u << 2` |   |
| `NET::NumberOfDesktops` | `1u << 3` |   |
| `NET::DesktopGeometry` | `1u << 4` |   |
| `NET::DesktopViewport` | `1u << 5` |   |
| `NET::CurrentDesktop` | `1u << 6` |   |
| `NET::DesktopNames` | `1u << 7` |   |
| `NET::ActiveWindow` | `1u << 8` |   |
| `NET::WorkArea` | `1u << 9` |   |
| `NET::SupportingWMCheck` | `1u << 10` |   |
| `NET::VirtualRoots` | `1u << 11` |   |
| `NET::CloseWindow` | `1u << 13` |   |
| `NET::WMMoveResize` | `1u << 14` |   |

Client window properties and protocols:

| Constant | Value |   |
| --- | --- | --- |
| `NET::WMName` | `1u << 15` |   |
| `NET::WMVisibleName` | `1u << 16` |   |
| `NET::WMDesktop` | `1u << 17` |   |
| `NET::WMWindowType` | `1u << 18` |   |
| `NET::WMState` | `1u << 19` |   |
| `NET::WMStrut` | `1u << 20` | Obsoleted by [WM2ExtendedStrut](net.md#Property2-enum). |
| `NET::WMGeometry` | `1u << 31` |   |
| `NET::WMFrameExtents` | `1u << 28` |   |
| `NET::WMIconGeometry` | `1u << 21` |   |
| `NET::WMIcon` | `1u << 22` |   |
| `NET::WMIconName` | `1u << 29` |   |
| `NET::WMVisibleIconName` | `1u << 30` |   |
| `NET::WMHandledIcons` | `1u << 24` |   |
| `NET::WMPid` | `1u << 23` |   |
| `NET::WMPing` | `1u << 25` |   |

ICCCM properties (provided for convenience):

| Constant |   |
| --- | --- |
| `NET::XAWMState` | `1u << 27` |

The `Properties` type is a typedef for `QFlags<Property>. `It stores an OR combination of `Property` values.

### enum NET::Protocol {#Protocol-enum}

**flags NET::Protocols**

Protocols supported by the client. See ICCCM 4.1.2.7.

| Constant | Value |   |
| --- | --- | --- |
| `NET::NoProtocol` | `0` |   |
| `NET::TakeFocusProtocol` | `1 << 0` | WM\_TAKE\_FOCUS |
| `NET::DeleteWindowProtocol` | `1 << 1` | WM\_DELETE\_WINDOW |
| `NET::PingProtocol` | `1 << 2` | \_NET\_WM\_PING from EWMH |
| `NET::SyncRequestProtocol` | `1 << 3` | \_NET\_WM\_SYNC\_REQUEST from EWMH |
| `NET::ContextHelpProtocol` | `1 << 4` | Non-standard. \_NET\_WM\_CONTEXT\_HELP |

The `Protocols` type is a typedef for `QFlags<Protocol>. `It stores an OR combination of `Protocol` values.

### enum NET::RequestSource {#RequestSource-enum}

Source of the request.

| Constant | Value | Description |
| --- | --- | --- |
| `NET::FromUnknown` | `0` | Indicates that the source of the request is unknown. |
| `NET::FromApplication` | `1` | Indicates that the request comes from a normal application. |
| `NET::FromTool` | `2` | Indicated that the request comes from pager or similar tool. |

### enum NET::Role {#Role-enum}

Application role. This is used internally to determine how several action should be performed (if at all).

| Constant | Value | Description |
| --- | --- | --- |
| `NET::Client` | `0` | Indicates that the application is a client application. |
| `NET::WindowManager` | `1` | Indicates that the application is a window manager application. |

### enum NET::State {#State-enum}

**flags NET::States**

Window state.

To set the state of a window, you'll typically do something like:

```cpp
KX11Extras::setState( winId(), NET::SkipTaskbar | NET::SkipPager | NET::SkipSwitcher );
```

for example to not show the window on the taskbar, desktop pager, or window switcher. winId() is a function of QWidget()

Note that KeepAbove (StaysOnTop) and KeepBelow are meant as user preference and applications should avoid setting these states themselves.

| Constant | Value | Description |
| --- | --- | --- |
| `NET::Modal` | `1u << 0` | Indicates that this is a modal dialog box. The WM\_TRANSIENT\_FOR hint MUST be set to indicate which window the dialog is a modal for, or set to the root window if the dialog is a modal for its window group. |
| `NET::Sticky` | `1u << 1` | Indicates that the Window Manager SHOULD keep the window's position fixed on the screen, even when the virtual desktop scrolls. Note that this is different from being kept on all desktops. |
| `NET::MaxVert` | `1u << 2` | Indicates that the window is vertically maximized. |
| `NET::MaxHoriz` | `1u << 3` | Indicates that the window is horizontally maximized. |
| `NET::Max` | `MaxVert | MaxHoriz` | convenience value. Equal to MaxVert \| MaxHoriz. |
| `NET::Shaded` | `1u << 4` | Indicates that the window is shaded (rolled-up). |
| `NET::SkipTaskbar` | `1u << 5` | Indicates that a window should not be included on a taskbar. |
| `NET::KeepAbove` | `1u << 6` | Indicates that a window should on top of most windows (but below fullscreen windows). |
| `NET::SkipPager` | `1u << 7` | Indicates that a window should not be included on a pager. |
| `NET::Hidden` | `1u << 8` | Indicates that a window should not be visible on the screen (e.g. when minimised). Only the window manager is allowed to change it. |
| `NET::FullScreen` | `1u << 9` | Indicates that a window should fill the entire screen and have no window decorations. |
| `NET::KeepBelow` | `1u << 10` | Indicates that a window should be below most windows (but above any desktop windows). |
| `NET::DemandsAttention` | `1u << 11` | there was an attempt to activate this window, but the window manager prevented this. E.g. taskbar should mark such window specially to bring user's attention to this window. Only the window manager is allowed to change it. |
| `NET::SkipSwitcher (since Qt 5.45)` | `1u << 12` | Indicates that a window should not be included on a switcher. |
| `NET::Focused (since Qt 5.58)` | `1u << 13` | Indicates that a client should render as though it has focus Only the window manager is allowed to change it. |

The `States` type is a typedef for `QFlags<State>. `It stores an OR combination of `State` values.

### enum NET::WindowType {#WindowType-enum}

Window type.

| Constant | Value | Description |
| --- | --- | --- |
| `NET::Unknown` | `-1` | Indicates that the window did not define a window type. |
| `NET::Normal` | `0` | Indicates that this is a normal, top-level window. |
| `NET::Desktop` | `1` | Indicates a desktop feature. This can include a single window containing desktop icons with the sam\*e dimensions as the screen, allowing the desktop environment to have full control of the desktop, without the need for proxying root window clicks. |
| `NET::Dock` | `2` | Indicates a dock or panel feature. |
| `NET::Toolbar` | `3` | Indicates a toolbar window. |
| `NET::Menu` | `4` | Indicates a pinnable (torn-off) menu window. |
| `NET::Dialog` | `5` | Indicates that this is a dialog window. |
| `NET::Override` | `6` | Non-standard. Deprecated: has unclear meaning and is KDE-only. |
| `NET::TopMenu` | `7` | Non-standard. Indicates a toplevel menu (AKA macmenu). This is a KDE extension to the \_NET\_WM\_WINDOW\_TYPE mechanism. |
| `NET::Utility` | `8` | Indicates a utility window. |
| `NET::Splash` | `9` | Indicates that this window is a splash screen window. |
| `NET::DropdownMenu` | `10` | Indicates a dropdown menu (from a menubar typically). |
| `NET::PopupMenu` | `11` | Indicates a popup menu (a context menu typically). |
| `NET::Tooltip` | `12` | Indicates a tooltip window. |
| `NET::Notification` | `13` | Indicates a notification window. |
| `NET::ComboBox` | `14` | Indicates that the window is a list for a combobox. |
| `NET::DNDIcon` | `15` | Indicates a window that represents the dragged object during DND operation. |
| `NET::OnScreenDisplay (since Qt 5.6)` | `16` | Non-standard. Indicates an On Screen Display window (such as volume feedback). |
| `NET::CriticalNotification (since Qt 5.58)` | `17` | Non-standard. Indicates a critical notification (such as battery is running out). |
| `NET::AppletPopup` | `18` | Non-standard. Indicates that this window is an applet. |

*See also* [NET::WindowTypeMask](net.md#WindowTypeMask-enum)

### enum NET::WindowTypeMask {#WindowTypeMask-enum}

**flags NET::WindowTypes**

Values for [WindowType](net.md#WindowType-enum) when they should be OR'ed together, e.g. for the properties argument of the [NETRootInfo](netrootinfo.md) constructor.

| Constant | Value |   |
| --- | --- | --- |
| `NET::NormalMask` | `1u << 0` |   |
| `NET::DesktopMask` | `1u << 1` |   |
| `NET::DockMask` | `1u << 2` |   |
| `NET::ToolbarMask` | `1u << 3` |   |
| `NET::MenuMask` | `1u << 4` |   |
| `NET::DialogMask` | `1u << 5` |   |
| `NET::OverrideMask` | `1u << 6` |   |
| `NET::TopMenuMask` | `1u << 7` |   |
| `NET::UtilityMask` | `1u << 8` |   |
| `NET::SplashMask` | `1u << 9` |   |
| `NET::DropdownMenuMask` | `1u << 10` |   |
| `NET::PopupMenuMask` | `1u << 11` |   |
| `NET::TooltipMask` | `1u << 12` |   |
| `NET::NotificationMask` | `1u << 13` |   |
| `NET::ComboBoxMask` | `1u << 14` |   |
| `NET::DNDIconMask` | `1u << 15` |   |
| `NET::OnScreenDisplayMask (since Qt 5.6)` | `1u << 16` | Non-standard. |
| `NET::CriticalNotificationMask (since Qt 5.58)` | `1u << 17` | Non-standard. |
| `NET::AppletPopupMask` | `1u << 18` | Non-standard. |
| `NET::AllTypesMask` | `0U - 1` | All window types. |

The `WindowTypes` type is a typedef for `QFlags<WindowTypeMask>. `It stores an OR combination of `WindowTypeMask` values.

*See also* [NET::WindowType](net.md#WindowType-enum)

## Member Function Documentation {#member-function-documentation}

### \[static\] int NET::timestampCompare(unsigned long *time1*, unsigned long *time2*) {#timestampCompare}

Compares two X timestamps, taking into account wrapping and 64bit architectures. Return value is like with strcmp(), 0 for equal, -1 for `time1` \< `time2`, 1 for `time1` \> `time2`.

### \[static\] int NET::timestampDiff(unsigned long *time1*, unsigned long *time2*) {#timestampDiff}

Returns a difference of two X timestamps, `time2` - `time1`, where `time2` must be later than `time1`, as returned by [timestampCompare](net.md#timestampCompare)().

### \[static\] bool NET::typeMatchesMask(NET::WindowType *type*, NET::WindowTypes *mask*) {#typeMatchesMask}

Returns `true` if the given window `type` matches the `mask` given using [WindowTypeMask](net.md#WindowTypeMask-enum) flags.
