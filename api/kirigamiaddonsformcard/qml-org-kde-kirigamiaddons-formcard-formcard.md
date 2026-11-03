---
title: "FormCard QML Type"
description: "A single card that follows a form style."
---

# FormCard QML Type

A single card that follows a form style. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

This is the entrypoint component for [FormCard](qml-org-kde-kirigamiaddons-formcard-formcard.md).

A [FormCard](qml-org-kde-kirigamiaddons-formcard-formcard.md) consists of a container that can be used to create your own Settings pages. It has a different color than the background.

Each [FormCard](qml-org-kde-kirigamiaddons-formcard-formcard.md) can contain one or more Form delegates in its contentItem. To add more than one Form delegate to a [FormCard](qml-org-kde-kirigamiaddons-formcard-formcard.md), use a [ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html) to group them.

Multiple FormCards can be grouped with a [ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html) to represent different Settings sections.

Each section is expected to contain a [FormHeader](qml-org-kde-kirigamiaddons-formcard-formheader.md) as the first delegate, which serves the role of a section title.

The height of the [FormCard](qml-org-kde-kirigamiaddons-formcard-formcard.md) matches the implicit height of the contentItem and does not need to be set, while the width is expected to be given by the parent, for example, via a [Layout.fillWidth](https://doc.qt.io/qt-6/qml-qtquick-layouts-layout.html#fillWidth-attached-prop).

## Property Documentation {#property-documentation}

### \[default: false\] autoSeparators : bool {#autoSeparators-prop}

Whether to insert a [FormDelegateSeparator](qml-org-kde-kirigamiaddons-formcard-formdelegateseparator.md) between visible delegates.

This also works for delegates created by a Repeater. Do not add explicit separators when this property is enabled.

### \[default: 0\] bottomPadding : real {#bottomPadding-prop}

Padding property used around the content edges.

### \[read-only\] cardWidthRestricted : bool {#cardWidthRestricted-prop}

Whether the card's width is being restricted.

### \[default\] delegates : alias {#delegates-prop}

The delegates inside the Form card.

This is where you should add new Form delegates.

### \[default: 0\] horizontalPadding : real {#horizontalPadding-prop}

Padding property used around the content edges.

### \[default: 0\] leftPadding : real {#leftPadding-prop}

Padding property used around the content edges.

### \[default: Kirigami.Units.gridUnit \* 30\] maximumWidth : real {#maximumWidth-prop}

The maximum width of the card.

This can be set to a specific value to force its delegates to wrap instead of using the entire width of the parent.

*See also* [cardWidthRestricted](qml-org-kde-kirigamiaddons-formcard-formcard.md#cardWidthRestricted-prop)

### \[default: 0\] padding : real {#padding-prop}

Padding property used around the content edges.

### \[default: 0\] rightPadding : real {#rightPadding-prop}

Padding property used around the content edges.

### \[default: 0\] topPadding : real {#topPadding-prop}

Padding property used around the content edges.

### \[default: 0\] verticalPadding : real {#verticalPadding-prop}

Padding property used around the content edges.
