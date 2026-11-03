---
title: "OverlayDrawer QML Type"
description: "A Drawer used to expose additional UI elements needed for small secondary tasks for which the main UI elements are not needed."
---

# OverlayDrawer QML Type

A Drawer used to expose additional UI elements needed for small secondary tasks for which the main UI elements are not needed. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [Drawer](https://doc.qt.io/qt-6/qml-qtquick-controls-drawer.html)
- Inherited By: [ContextDrawer](qml-org-kde-kirigami-contextdrawer.md) and [GlobalDrawer](qml-org-kde-kirigami-globaldrawer.md)

## Detailed Description {#details}

For example in Okular Mobile, an Overlay Drawer is used to display thumbnails of all pages within a document along with a search field. This is used for the distinct task of navigating to another page.

## Property Documentation {#property-documentation}

### \[read-only\] animating : bool {#animating-prop}

This property tells whether the drawer is currently opening or closing itself.

### collapsed : bool {#collapsed-prop}

This property tells whether the drawer is collapsed to a very thin sidebar, usually icon only.

When true, the drawer will be collapsed to a very thin sidebar, usually icon only.

Only collapsible drawers can be collapsed.

When collapsed, drawers can't be manually resized even when [interactiveResizeEnabled](qml-org-kde-kirigami-overlaydrawer.md#interactiveResizeEnabled-prop) is true

default: `false`

*See also* [collapsible](qml-org-kde-kirigami-overlaydrawer.md#collapsible-prop)

### collapsedSize : int {#collapsedSize-prop}

This property holds the size of the collapsed drawer.

For vertical drawers this will be the width of the drawer and for horizontal drawers this will be the height of the drawer.

default: Units.iconSizes.medium, just enough to accommodate medium sized icons

### collapsible : bool {#collapsible-prop}

This property holds whether the drawer can be collapsed to a very thin, usually icon only sidebar.

Only modal drawers are collapsible. Collapsible is not supported in the mobile mode.

### drawerOpen : bool {#drawerOpen-prop}

This property tells whether the drawer is open and visible.

default: `false`

### \[read-only\] handle : Item {#handle-prop}

Readonly property that points to the item that will act as a physical handle for the Drawer.

### handleClosedIcon group {#handleClosedIcon-prop}

**handleClosedIcon.color : color**

**handleClosedIcon.fromControlsIcon : function**

**handleClosedIcon.height : real**

**handleClosedIcon.name : string**

**handleClosedIcon.source : var**

**handleClosedIcon.width : real**

This grouped property holds the description of an optional icon.

If no custom icon is set, an X icon is shown, which will morph into the Menu or overflow icons.

For [OverlayDrawer](qml-org-kde-kirigami-overlaydrawer.md) the default is view-right-new or view-left-new depending on the drawer location.

### handleClosedToolTip : string {#handleClosedToolTip-prop}

This property holds the tooltip displayed when the drawer is closed.

### \[read-only\] handleOpenIcon : Primitives.IconPropertiesGroup {#handleOpenIcon-prop}

This property holds the options for handle's open icon.

If no custom icon is set, a menu icon is shown for the application globalDrawer and an overflow menu icon is shown for the contextDrawer. That's the default for the [GlobalDrawer](qml-org-kde-kirigami-globaldrawer.md) and [ContextDrawer](qml-org-kde-kirigami-contextdrawer.md) components respectively.

For [OverlayDrawer](qml-org-kde-kirigami-overlaydrawer.md) the default is view-right-close or view-left-close depending on the drawer location

| Name | Description |
| --- | --- |
| name | This property holds icon name. The icon will be loaded from the platform theme. If the icon is found in the theme, it will always be used; even if icon.source is also set. If the icon is not found, icon.source will be used instead. |
| source | This property holds the icon source. The icon will be loaded as a regular image. |
| width | This property holds the width of the icon. |
| height | This property holds the height of the icon. |
| color | This property holds the icon tint color. The icon is tinted with the specified color, unless the color is set to "transparent". |
| fromControlsIcon | Bind this icon to all matching properties of a Controls icon group. This function automatically binds all properties to matching properties of a controls icon group, since we cannot just reuse the Controls icon group. To use it, you can assign the result to an [IconPropertiesGroup](qml-org-kde-kirigami-primitives-iconpropertiesgroup.md), like so: ```qml icon: icon.fromControlsIcon(control.icon). ``` |

### handleOpenToolTip : string {#handleOpenToolTip-prop}

This property holds the tooltip displayed when the drawer is open.

### handleVisible : bool {#handleVisible-prop}

This property holds whether the handle is visible, to make opening the drawer easier.

Currently supported only on left and right drawers.

### \[read-only\] icon.color : color {#icon.color-prop}

This property holds the options for handle's open icon.

If no custom icon is set, a menu icon is shown for the application globalDrawer and an overflow menu icon is shown for the contextDrawer. That's the default for the [GlobalDrawer](qml-org-kde-kirigami-globaldrawer.md) and [ContextDrawer](qml-org-kde-kirigami-contextdrawer.md) components respectively.

For [OverlayDrawer](qml-org-kde-kirigami-overlaydrawer.md) the default is view-right-close or view-left-close depending on the drawer location

| Name | Description |
| --- | --- |
| name | This property holds icon name. The icon will be loaded from the platform theme. If the icon is found in the theme, it will always be used; even if icon.source is also set. If the icon is not found, icon.source will be used instead. |
| source | This property holds the icon source. The icon will be loaded as a regular image. |
| width | This property holds the width of the icon. |
| height | This property holds the height of the icon. |
| color | This property holds the icon tint color. The icon is tinted with the specified color, unless the color is set to "transparent". |
| fromControlsIcon | Bind this icon to all matching properties of a Controls icon group. This function automatically binds all properties to matching properties of a controls icon group, since we cannot just reuse the Controls icon group. To use it, you can assign the result to an [IconPropertiesGroup](qml-org-kde-kirigami-primitives-iconpropertiesgroup.md), like so: ```qml icon: icon.fromControlsIcon(control.icon). ``` |

### \[read-only\] icon.fromControlsIcon : function {#icon.fromControlsIcon-prop}

This property holds the options for handle's open icon.

If no custom icon is set, a menu icon is shown for the application globalDrawer and an overflow menu icon is shown for the contextDrawer. That's the default for the [GlobalDrawer](qml-org-kde-kirigami-globaldrawer.md) and [ContextDrawer](qml-org-kde-kirigami-contextdrawer.md) components respectively.

For [OverlayDrawer](qml-org-kde-kirigami-overlaydrawer.md) the default is view-right-close or view-left-close depending on the drawer location

| Name | Description |
| --- | --- |
| name | This property holds icon name. The icon will be loaded from the platform theme. If the icon is found in the theme, it will always be used; even if icon.source is also set. If the icon is not found, icon.source will be used instead. |
| source | This property holds the icon source. The icon will be loaded as a regular image. |
| width | This property holds the width of the icon. |
| height | This property holds the height of the icon. |
| color | This property holds the icon tint color. The icon is tinted with the specified color, unless the color is set to "transparent". |
| fromControlsIcon | Bind this icon to all matching properties of a Controls icon group. This function automatically binds all properties to matching properties of a controls icon group, since we cannot just reuse the Controls icon group. To use it, you can assign the result to an [IconPropertiesGroup](qml-org-kde-kirigami-primitives-iconpropertiesgroup.md), like so: ```qml icon: icon.fromControlsIcon(control.icon). ``` |

### \[read-only\] icon.height : real {#icon.height-prop}

This property holds the options for handle's open icon.

If no custom icon is set, a menu icon is shown for the application globalDrawer and an overflow menu icon is shown for the contextDrawer. That's the default for the [GlobalDrawer](qml-org-kde-kirigami-globaldrawer.md) and [ContextDrawer](qml-org-kde-kirigami-contextdrawer.md) components respectively.

For [OverlayDrawer](qml-org-kde-kirigami-overlaydrawer.md) the default is view-right-close or view-left-close depending on the drawer location

| Name | Description |
| --- | --- |
| name | This property holds icon name. The icon will be loaded from the platform theme. If the icon is found in the theme, it will always be used; even if icon.source is also set. If the icon is not found, icon.source will be used instead. |
| source | This property holds the icon source. The icon will be loaded as a regular image. |
| width | This property holds the width of the icon. |
| height | This property holds the height of the icon. |
| color | This property holds the icon tint color. The icon is tinted with the specified color, unless the color is set to "transparent". |
| fromControlsIcon | Bind this icon to all matching properties of a Controls icon group. This function automatically binds all properties to matching properties of a controls icon group, since we cannot just reuse the Controls icon group. To use it, you can assign the result to an [IconPropertiesGroup](qml-org-kde-kirigami-primitives-iconpropertiesgroup.md), like so: ```qml icon: icon.fromControlsIcon(control.icon). ``` |

### \[read-only\] icon.name : string {#icon.name-prop}

This property holds the options for handle's open icon.

If no custom icon is set, a menu icon is shown for the application globalDrawer and an overflow menu icon is shown for the contextDrawer. That's the default for the [GlobalDrawer](qml-org-kde-kirigami-globaldrawer.md) and [ContextDrawer](qml-org-kde-kirigami-contextdrawer.md) components respectively.

For [OverlayDrawer](qml-org-kde-kirigami-overlaydrawer.md) the default is view-right-close or view-left-close depending on the drawer location

| Name | Description |
| --- | --- |
| name | This property holds icon name. The icon will be loaded from the platform theme. If the icon is found in the theme, it will always be used; even if icon.source is also set. If the icon is not found, icon.source will be used instead. |
| source | This property holds the icon source. The icon will be loaded as a regular image. |
| width | This property holds the width of the icon. |
| height | This property holds the height of the icon. |
| color | This property holds the icon tint color. The icon is tinted with the specified color, unless the color is set to "transparent". |
| fromControlsIcon | Bind this icon to all matching properties of a Controls icon group. This function automatically binds all properties to matching properties of a controls icon group, since we cannot just reuse the Controls icon group. To use it, you can assign the result to an [IconPropertiesGroup](qml-org-kde-kirigami-primitives-iconpropertiesgroup.md), like so: ```qml icon: icon.fromControlsIcon(control.icon). ``` |

### \[read-only\] icon.source : var {#icon.source-prop}

This property holds the options for handle's open icon.

If no custom icon is set, a menu icon is shown for the application globalDrawer and an overflow menu icon is shown for the contextDrawer. That's the default for the [GlobalDrawer](qml-org-kde-kirigami-globaldrawer.md) and [ContextDrawer](qml-org-kde-kirigami-contextdrawer.md) components respectively.

For [OverlayDrawer](qml-org-kde-kirigami-overlaydrawer.md) the default is view-right-close or view-left-close depending on the drawer location

| Name | Description |
| --- | --- |
| name | This property holds icon name. The icon will be loaded from the platform theme. If the icon is found in the theme, it will always be used; even if icon.source is also set. If the icon is not found, icon.source will be used instead. |
| source | This property holds the icon source. The icon will be loaded as a regular image. |
| width | This property holds the width of the icon. |
| height | This property holds the height of the icon. |
| color | This property holds the icon tint color. The icon is tinted with the specified color, unless the color is set to "transparent". |
| fromControlsIcon | Bind this icon to all matching properties of a Controls icon group. This function automatically binds all properties to matching properties of a controls icon group, since we cannot just reuse the Controls icon group. To use it, you can assign the result to an [IconPropertiesGroup](qml-org-kde-kirigami-primitives-iconpropertiesgroup.md), like so: ```qml icon: icon.fromControlsIcon(control.icon). ``` |

### \[read-only\] icon.width : real {#icon.width-prop}

This property holds the options for handle's open icon.

If no custom icon is set, a menu icon is shown for the application globalDrawer and an overflow menu icon is shown for the contextDrawer. That's the default for the [GlobalDrawer](qml-org-kde-kirigami-globaldrawer.md) and [ContextDrawer](qml-org-kde-kirigami-contextdrawer.md) components respectively.

For [OverlayDrawer](qml-org-kde-kirigami-overlaydrawer.md) the default is view-right-close or view-left-close depending on the drawer location

| Name | Description |
| --- | --- |
| name | This property holds icon name. The icon will be loaded from the platform theme. If the icon is found in the theme, it will always be used; even if icon.source is also set. If the icon is not found, icon.source will be used instead. |
| source | This property holds the icon source. The icon will be loaded as a regular image. |
| width | This property holds the width of the icon. |
| height | This property holds the height of the icon. |
| color | This property holds the icon tint color. The icon is tinted with the specified color, unless the color is set to "transparent". |
| fromControlsIcon | Bind this icon to all matching properties of a Controls icon group. This function automatically binds all properties to matching properties of a controls icon group, since we cannot just reuse the Controls icon group. To use it, you can assign the result to an [IconPropertiesGroup](qml-org-kde-kirigami-primitives-iconpropertiesgroup.md), like so: ```qml icon: icon.fromControlsIcon(control.icon). ``` |

### interactiveResizeEnabled : bool {#interactiveResizeEnabled-prop}

When true it will be possible to resize the drawer by dragging its edge with the mouse

When the drawer is collapsed, drawers can't be manually resized even when interactiveResizeEnabled is true

### interactiveResizing : alias {#interactiveResizing-prop}

True when the user is resizing the drawer with the mouse

### maximumSize : real {#maximumSize-prop}

The maximum size (width or height, depending on the edge) this drawer is allowed to be resized

For left and right drawers the default is the minimum between Platform.Units.gridUnit \* 25 and 80% of the window width For Top and bottom drawers the default is the minimum between Platform.Units.gridUnit \* 15 and half of the window height

### minimumSize : real {#minimumSize-prop}

The minimum size (width or height, depending on the edge) this drawer is allowed to be resized

For left and right drawers the default is Platform.Units.gridUnit \* 8 For top and bottom drawers the default is Platform.Units.gridUnit \* 4

### peeking : bool {#peeking-prop}

This property tells whether the drawer is in a state between open and closed.

The drawer is visible but not completely open. This is usually the case when the user is dragging the drawer from a screen edge, so the user is "peeking" at what's in the drawer.

default: `false`

### preferredSize : real {#preferredSize-prop}

The size (width or height, depending on the edge) the drawer wants to have when on left or right edges and not collapsed.

Wnen [interactiveResizing](qml-org-kde-kirigami-overlaydrawer.md#interactiveResizing-prop) is true and the app wants to restore its saved custom drawer size, it should write to this property, width, height, implicitWidth and implicitHeight should not be touched.

Default value is -1, which means the drawer will be sized following its contents size hints
