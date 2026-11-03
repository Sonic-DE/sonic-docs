---
title: "Banner QML Type"
description: "An banner Item with support for informational, positive, warning and error types, and with support for associated actions. This type is deprecated. We strongly advise against using it in new code."
---

# Banner QML Type

An banner Item with support for informational, positive, warning and error types, and with support for associated actions. **This type is deprecated. We strongly advise against using it in new code.** [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.labs.components
- Status: Deprecated

**This type is deprecated. We strongly advise against using it in new code.**

## Detailed Description {#details}

Banner can be used to inform or interact with the user without requiring the use of a dialog and are positionned in the footer or header of a page. For inline content, see Kirigami.[InlineMessage](../kirigami/qml-org-kde-kirigami-inlinemessage.md).

The Banner is hidden by default.

Optionally, actions can be added which are shown alongside an optional close button on the right side of the Item. If more actions are set than can fit, an overflow menu is provided.

Example usage:

```qml
Banner {
    type: Kirigami.MessageType.Error

    text: "My error message"

    actions: [
        Kirigami.Action {
            icon.name: "edit"
            text: "Action text"
            onTriggered: {
                // do stuff
            }
        },
        Kirigami.Action {
            icon.name: "edit"
            text: "Action text"
            onTriggered: {
                // do stuff
            }
        }
    ]
}
```

Since 1.5.0, use Kirigami.[InlineMessage](../kirigami/qml-org-kde-kirigami-inlinemessage.md) with the appropriate `position` property.

## Property Documentation {#property-documentation}

### actions : list\<Kirigami.Action\> {#actions-prop}

This property holds the list of Kirigami Actions to show in the banner's internal [ActionToolBar](../kirigami/qml-org-kde-kirigami-actiontoolbar.md).

Actions are added from left to right. If more actions are set than can fit, an overflow menu is provided.

### \[read-only\] hoveredLink : string {#hoveredLink-prop}

This property holds the link embedded in the message text that the user is hovering over.

### \[default: false\] showCloseButton : bool {#showCloseButton-prop}

This property holds whether the close button is displayed.

### text : string {#text-prop}

This property holds the message text.

### title : string {#title-prop}

This property holds the message title.

### \[default: Kirigami.MessageType.Information\] type : Kirigami.MessageType {#type-prop}

This property holds the message type.

The following values are allowed:

| Constant |
| --- |
| Kirigami.MessageType.Information |
| Kirigami.MessageType.Positive |
| Kirigami.MessageType.Warning |
| Kirigami.MessageType.Error |

## Signal Documentation {#signal-documentation}

### linkActivated(string *link*) {#linkActivated-signal}

This signal is emitted when a `link` is clicked or tapped in the message text.

> **Note:** The corresponding handler is `onLinkActivated`.

### linkHovered(string *link*) {#linkHovered-signal}

This signal is emitted when a `link` is hovered in the message text.

> **Note:** The corresponding handler is `onLinkHovered`.
