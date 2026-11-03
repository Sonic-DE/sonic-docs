---
title: "FormTextDelegate QML Type"
description: "A Form delegate that corresponds to a text label and a description."
---

# FormTextDelegate QML Type

A Form delegate that corresponds to a text label and a description. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard
- Inherits: [AbstractFormDelegate](qml-org-kde-kirigamiaddons-formcard-abstractformdelegate.md)

## Detailed Description {#details}

This component is used to create primary text with the inherited [AbstractButton.text](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html#text-prop) property, with an optional description that serves as secondary text/subtitle.

If you need just a secondary text component, use a [FormSectionText](qml-org-kde-kirigamiaddons-formcard-formsectiontext.md) instead.

*See also* [FormSectionText](qml-org-kde-kirigamiaddons-formcard-formsectiontext.md), [AbstractButton](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html)

## Property Documentation {#property-documentation}

### \[default: ""\] description : string {#description-prop}

A label containing secondary text that appears under the inherited text property.

This provides additional information shown in a faint gray color.

### descriptionItem : Label {#descriptionItem-prop}

This property allows for access to the description label item.

### \[default: null\] leading : Item {#leading-prop}

This property holds an item that will be displayed before the delegate's contents.

### \[default: Kirigami.Units.smallSpacing\] leadingPadding : real {#leadingPadding-prop}

This property holds the padding after the leading item.

### textItem : Label {#textItem-prop}

This property holds allows for access to the text label item.

### \[default: null\] trailing : Item {#trailing-prop}

This property holds an item that will be displayed after the delegate's contents.

### \[default: Kirigami.Units.smallSpacing\] trailingPadding : real {#trailingPadding-prop}

This property holds the padding before the trailing item.

## Signal Documentation {#signal-documentation}

### linkActivated(string *link*) {#linkActivated-signal}

This signal is emitted when the `link` is activated.

> **Note:** The corresponding handler is `onLinkActivated`.
