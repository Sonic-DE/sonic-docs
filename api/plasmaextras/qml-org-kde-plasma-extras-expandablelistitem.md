---
title: "ExpandableListItem QML Type"
description: "A list item that expands when clicked to show additional actions and/or a custom view."
---

# ExpandableListItem QML Type

A list item that expands when clicked to show additional actions and/or a custom view. [More...](#details)

- Import Statement: import org.kde.plasma.extras
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

The list item has a standardized appearance, with an icon on the left badged with an optional emblem, a title and optional subtitle to the right, an optional default action button, and a button to expand and collapse the list item.

When expanded, the list item shows a list of contextually-appropriate actions if [contextualActions](qml-org-kde-plasma-extras-expandablelistitem.md#contextualActions-prop) has been defined. If [customExpandedViewContent](qml-org-kde-plasma-extras-expandablelistitem.md#customExpandedViewContent-prop) has been defined, it will show a custom view. If both have been defined, it shows both, with the actions above the custom view.

It is not valid to define neither; define one or both.

> **Note:** this component should only be used for lists where the maximum number of items is very low, ideally less than 10. For longer lists, consider using a different paradigm.

Example usage:

```qml
import QtQuick
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami
import org.kde.plasma.extras as PlasmaExtras
import org.kde.plasma.components as PlasmaComponents

PlasmaComponents.ScrollView {
    ListView {
        anchors.fill: parent
        focus: true
        currentIndex: -1
        clip: true
        model: myModel
        highlight: PlasmaExtras.Highlight {}
        highlightMoveDuration: Kirigami.Units.shortDuration
        highlightResizeDuration: Kirigami.Units.shortDuration
        delegate: PlasmaExtras.ExpandableListItem {
            icon: model.iconName
            iconEmblem: model.isPaused ? "emblem-pause" : ""
            title: model.name
            subtitle: model.subtitle
            isDefault: model.isDefault
            defaultActionButtonAction: QQC2.Action {
                icon.name: model.isPaused ? "media-playback-start" : "media-playback-pause"
                text: model.isPaused ? "Resume" : "Pause"
                onTriggered: {
                    if (model.isPaused) {
                        model.resume(model.name);
                    } else {
                        model.pause(model.name);
                    }
                }
            }
            contextualActions: [
                QQC2.Action {
                    icon.name: "configure"
                    text: "Configure…"
                    onTriggered: model.configure(model.name);
                }
            ]
        }
    }
}
```

## Property Documentation {#property-documentation}

### allowStyledText : bool {#allowStyledText-prop}

Whether to allow the title, subtitle, and tooltip to contain styled text. For performance and security reasons, keep this off unless needed.

Optional, defaults to false.

### contextualActions : list\<T.Action\> {#contextualActions-prop}

A list of standard QQC2.Action objects that describes additional actions that can be performed on this list item. For example:

```qml
contextualActions: [
    Action {
        text: "Do something"
        icon.name: "document-edit"
        onTriggered: doSomething()
    },
    Action {
        text: "Do something else"
        icon.name: "draw-polygon"
        onTriggered: doSomethingElse()
    },
    Action {
        text: "Do something completely different"
        icon.name: "games-highscores"
        onTriggered: doSomethingCompletelyDifferent()
    }
]
```

Optional; if not defined, no contextual actions will be displayed and you should instead assign a custom view to [customExpandedViewContent](qml-org-kde-plasma-extras-expandablelistitem.md#customExpandedViewContent-prop), which will be shown when the user expands the list item.

### customExpandedViewContent : Component {#customExpandedViewContent-prop}

A custom view to display when the user expands the list item.

This component must define width and height properties. Width should be equal to the width of the list item itself, while height: will depend on the component itself.

Optional; if not defined, no custom view actions will be displayed and you should instead define [contextualActions](qml-org-kde-plasma-extras-expandablelistitem.md#contextualActions-prop), and then actions will be shown when the user expands the list item.

### customExpandedViewContentItem : Item {#customExpandedViewContentItem-prop}

The actual instance of the custom view content, if loaded.

### defaultActionButtonAction : Action {#defaultActionButtonAction-prop}

The Action to execute when the default button is clicked.

Optional; if not defined, no default action button will be displayed.

### defaultActionButtonVisible : bool {#defaultActionButtonVisible-prop}

When/whether to show to default action button. Useful for making it conditionally appear or disappear.

Optional; defaults to true

### \[read-only\] expanded : bool {#expanded-prop}

Whether the expanded view is visible.

### \[read-only\] hasExpandableContent : bool {#hasExpandableContent-prop}

Whether or not this expandable list item is actually expandable. True if this item has either a custom view or else at least one enabled action. Otherwise false.

### icon : icon {#icon-prop}

The name of the icon used in the list item.

Required.

*See also* Kirigami.Icon::source

### iconEmblem : icon {#iconEmblem-prop}

The name of the emblem to badge the icon with.

Optional, defaults to nothing, in which case there is no emblem.

*See also* Kirigami.Icon::source

### \[since 6.6\] index : int {#index-prop}

The index of this item in the view

This property was introduced in Qt 6.6.

### isBusy : bool {#isBusy-prop}

Whether or not to display a busy indicator on the list item. Set to true while the item should be non-interactive because things are processing.

Optional; defaults to false.

### isDefault : bool {#isDefault-prop}

Whether or not this list item should be considered the "default" or "Current" item in the list. When set to true, and the list itself has more than one item in it, the list item's title and subtitle will be drawn in a bold style.

Optional; defaults to false.

### showDefaultActionButtonWhenBusy : bool {#showDefaultActionButtonWhenBusy-prop}

Whether to continue showing the default action button while the busy indicator is visible. Useful for cancelable actions that could take a few seconds and show a busy indicator while processing.

Optional; defaults to false

### subtitle : string {#subtitle-prop}

The subtitle for this list item, displayed under the title.

Optional; if not defined, there will be no subtitle and the title will be vertically centered in the list item.

### subtitleCanWrap : bool {#subtitleCanWrap-prop}

Whether to allow the subtitle to become a multi-line string instead of eliding when the text is very long.

Optional, defaults to false.

### subtitleColor : color {#subtitleColor-prop}

subtitleColor: color The color of the subtitle text

Optional; if not defined, the subtitle will use the default text color

### \[since 6.9\] subtitleMaximumLineCount : int {#subtitleMaximumLineCount-prop}

The maximum number of lines the subtitle can have when [subtitleCanWrap](qml-org-kde-plasma-extras-expandablelistitem.md#subtitleCanWrap-prop) is true.

Optional, defaults to -1, which means no limit.

This property was introduced in Qt 6.9.

### title : string {#title-prop}

The name or title for this list item.

Optional; if not defined, there will be no title and the subtitle will be vertically centered in the list item.

## Signal Documentation {#signal-documentation}

### itemCollapsed() {#itemCollapsed-signal}

> **Note:** The corresponding handler is `onItemCollapsed`.

### itemExpanded() {#itemExpanded-signal}

> **Note:** The corresponding handler is `onItemExpanded`.

## Method Documentation {#method-documentation}

### collapse() {#collapse-method}

Hide the expanded view and collapse the list item to its shorter size.

### expand() {#expand-method}

Show the expanded view, growing the list item to its taller size.

### toggleExpanded() {#toggleExpanded-method}

Expand or collapse the list item depending on its current state.
