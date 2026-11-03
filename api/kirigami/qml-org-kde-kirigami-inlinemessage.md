---
title: "InlineMessage QML Type"
description: "An inline message item with support for associated actions."
---

# InlineMessage QML Type

An inline message item with support for associated actions. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [Control](https://doc.qt.io/qt-6/qml-qtquick-controls-control.html)

## Detailed Description {#details}

[InlineMessage](qml-org-kde-kirigami-inlinemessage.md) can be used to provide non-modal information or interactivity without requiring the use of a dialog. To learn when to use it, see https://develop.kde.org/hig/status_changes/#in-app-notifications.

[InlineMessage](qml-org-kde-kirigami-inlinemessage.md) has two visibility modes: inline (default) and borderless. The inline version includes outer padding suitable for being displayed amidst page content. The borderless version is best used used as a header or footer where it is expected to touch the edges of its parent view, and is activated using the [position](qml-org-kde-kirigami-inlinemessage.md#position-prop) property.

The [InlineMessage](qml-org-kde-kirigami-inlinemessage.md) item is hidden by default. It also manages its height (and implicitHeight) during an animated reveal when shown. You should avoid setting height on an [InlineMessage](qml-org-kde-kirigami-inlinemessage.md) unless it is already visible.

The [type](qml-org-kde-kirigami-inlinemessage.md#type-prop) property determines the message's coloration and default icon. This icon can be overridden using the [icon](qml-org-kde-kirigami-inlinemessage.md#icon-prop) property.

No close button is shown by default, which means you're responsible for hiding the message when it's no longer relevant. Optionally, a close button can be added using the [showCloseButton](qml-org-kde-kirigami-inlinemessage.md#showCloseButton-prop) property.

Actions are added from leading to trailing, and aligned to the trailing position. If more actions are set than can fit, an overflow menu is provided.

Example displayed inline:

```qml
import org.kde.kirigami as Kirigami

Kirigami.InlineMessage {
    type: Kirigami.MessageType.Error

    text: i18n("My error message")

    actions: [
        Kirigami.Action {
            icon.name: "list-add"
            text: i18n("Add")
            onTriggered: source => {
                // do stuff
            }
        },
        Kirigami.Action {
            icon.name: "edit"
            text: i18n("Edit")
            onTriggered: source => {
                // do stuff
            }
        }
    ]
}
```

Example displayed in the header position:

```qml
import org.kde.kirigami as Kirigami

  Kirigami.Page {
      header: Kirigami.InlineMessage {
          position: Kirigami.InlineMessage.Position.Header
          type: Kirigami.MessageType.Warning

          text: i18n("My warning message")

          actions: [
              Kirigami.Action {
                  icon.name: "edit-undo"
                  text: i18n("Undo")
                  onTriggered: source => {
                      // do stuff
                  }
              }
          ]
      }

      // Add page content here
  }
}
```

## Property Documentation {#property-documentation}

### actions : list\<Action\> {#actions-prop}

This property holds the list of actions to show. Actions are added from leading to trailing. If more actions are set than can fit, an overflow menu is provided.

### \[read-only\] animating : bool {#animating-prop}

This property holds whether the current message item is animating.

### \[read-only\] hoveredLink : string {#hoveredLink-prop}

This property holds the link embedded in the message text that the user is hovering over.

### icon group {#icon-prop}

**icon.color : color**

**icon.fromControlsIcon : function**

**icon.height : real**

**icon.name : string**

**icon.source : var**

**icon.width : real**

This grouped property holds the description of an optional icon.

| Name | Description |
| --- | --- |
| name | This property holds icon name. The icon will be loaded from the platform theme. If the icon is found in the theme, it will always be used; even if icon.source is also set. If the icon is not found, icon.source will be used instead. |
| source | This property holds the icon source. The icon will be loaded as a regular image. |
| width | This property holds the width of the icon. |
| height | This property holds the height of the icon. |
| color | This property holds the icon tint color. The icon is tinted with the specified color, unless the color is set to "transparent". |
| fromControlsIcon | Bind this icon to all matching properties of a Controls icon group. This function automatically binds all properties to matching properties of a controls icon group, since we cannot just reuse the Controls icon group. To use it, you can assign the result to an [IconPropertiesGroup](qml-org-kde-kirigami-primitives-iconpropertiesgroup.md), like so: ```qml icon: icon.fromControlsIcon(control.icon). ``` |

### position : enumeration {#position-prop}

Adjust the look of the message based upon the position. If a message is positioned in the header area or in the footer area of a page, it might be desirable to not have borders but just a line separating it from the content area. In this case, use the Header or Footer position.

Possible values are:

- [InlineMessage](qml-org-kde-kirigami-inlinemessage.md).Position.Inline
- [InlineMessage](qml-org-kde-kirigami-inlinemessage.md).Position.Header
- [InlineMessage](qml-org-kde-kirigami-inlinemessage.md).Position.Footer

Default is [InlineMessage](qml-org-kde-kirigami-inlinemessage.md).Position.Inline

### showCloseButton : bool {#showCloseButton-prop}

This property holds whether the close button is displayed.

The default is `false`.

### text : string {#text-prop}

This property holds the message text.

### type : enumeration {#type-prop}

This property holds the message type. One of

- Information
- Positive
- Warning
- Error

The default is Kirigami.[MessageType](messagetype.md).Information.

## Signal Documentation {#signal-documentation}

### linkActivated(string *link*) {#linkActivated-signal}

This signal is emitted when a link is clicked or tapped in the message text.

`link` The clicked or tapped link.

> **Note:** The corresponding handler is `onLinkActivated`.

### linkHovered(string *link*) {#linkHovered-signal}

This signal is emitted when a link is hovered in the message text.

`link` The hovered link.

> **Note:** The corresponding handler is `onLinkHovered`.
