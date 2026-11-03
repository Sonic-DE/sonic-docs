---
title: "TitleSubtitleWithActions QML Type"
description: "A simple title delegate that has trailing actions. This type was introduced in Qt 6.22."
---

# TitleSubtitleWithActions QML Type

A simple title delegate that has trailing actions. This type was introduced in Qt 6.22. [More...](#details)

- Import Statement: import org.kde.kirigami.delegates
- Since: Qt 6.22
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

This is meant to be used in lists for items that have actions. For example lists of usernames, with any related actions after them, such as rename and delete actions.

Example usage as contentItem of an [ItemDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-itemdelegate.html):

```qml
ItemDelegate {
    id: itemDelegate
    icon: "user"
    text: i18nc("@title:row", "Konqi")
    readonly property string subtitle: i18nc("@label", "The Konqueror")
    Accessible.description: subtitle
    Kirigami.Theme.useAlternateBackgroundColor: true

    onClicked: [...]

    contentItem: Kirigami.TitleSubtitleWithActions {
        title: itemDelegate.title
        subtitle: itemDelegate.subtitle
        elide: Text.ElideRight
        selected: itemDelegate.pressed || itemDelegate.highlighted
        actions: [
            Kirigami.Action {
                icon.name: "edit-entry-symbolic"
                text: i18nc("@action:button", "Modify user…")
                onTriggered: [...]
                tooltip: text
            },
            Kirigami.Action {
                icon.name: "edit-delete-remove-symbolic"
                text: i18nc("@action:button", "Remove user…")
                onTriggered: [...]
                tooltip: text
                displayHint: Kirigami.DisplayHint.IconOnly
            }
        ]
    }
}
```

*See also* [IconTitleSubtitle](qml-org-kde-kirigami-delegates-icontitlesubtitle.md), [TitleSubtitle](qml-org-kde-kirigami-delegates-titlesubtitle.md), [ActionToolBar](qml-org-kde-kirigami-actiontoolbar.md)

## Property Documentation {#property-documentation}

### actions : list\<Action\> {#actions-prop}

This property holds a list of visible actions.

These actions will be given to [ActionToolBar](qml-org-kde-kirigami-actiontoolbar.md). To make an action be icons-only, set `displayHint`: Kirigami.[DisplayHint](qml-org-kde-kirigami-layouts-displayhint.md).IconOnly on it.

Empty by default, so no actions will be present.

*See also* [ActionToolBar](qml-org-kde-kirigami-actiontoolbar.md)

### displayHint : enumeration {#displayHint-prop}

This property determines how the icon and text are displayed within the button.

Permitted values are:

- Button.IconOnly
- Button.TextOnly
- Button.TextBesideIcon
- Button.TextUnderIcon

default: `Button.TextBesideIcon`

*See also* [ActionToolBar](qml-org-kde-kirigami-actiontoolbar.md), [AbstractButton](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html)

### elide : enumeration {#elide-prop}

The text elision mode used for both the title and subtitle.

default: `Text.ElideRight`

### selected : bool {#selected-prop}

Should this item be displayed in a selected style?

default: `false`

### subtitle : string {#subtitle-prop}

The subtitle to display.

default: Empty `string`, so no subtitle is shown

### \[since 6.31\] textFormat : alias {#textFormat-prop}

\* The way the text property for the title and subtitle should be displayed. \*

This property was introduced in Qt 6.31.

### \[required\] title : string {#title-prop}

The title to display.
