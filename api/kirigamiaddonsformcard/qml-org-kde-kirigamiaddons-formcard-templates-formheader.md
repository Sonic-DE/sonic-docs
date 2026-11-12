---
title: "FormHeader QML Type"
description: "A header item for a form card."
---

# FormHeader QML Type

A header item for a form card. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard.templates
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html) (QtQuick)
- Inherited By: [FormHeader](qml-org-kde-kirigamiaddons-formcard-formheader.md) (org.kde.kirigamiaddons.formcard)

## Detailed Description {#details}

> **Note:** The header should be placed above the card in a layout not as a child.

## Property Documentation {#property-documentation}

### actions : list\<Action\> {#actions-prop}

The [Action](../kirigami/qml-org-kde-kirigami-action.md) components to be presented in the header.

### bottomPadding : real {#bottomPadding-prop}

Padding property.

The default value is based on [Kirigami.Units](../kirigamiplatform/qml-org-kde-kirigami-platform-units.md). To ensure consistency it's recommended that you do not change this property.

### \[read-only\] cardWidthRestricted : bool {#cardWidthRestricted-prop}

Whether the card's width is being restricted.

### leftPadding : real {#leftPadding-prop}

Padding property.

The default value is based on [Kirigami.Units](../kirigamiplatform/qml-org-kde-kirigami-platform-units.md). To ensure consistency it's recommended that you do not change this property.

### maximumWidth : real {#maximumWidth-prop}

The maximum width of the header.

### rightPadding : real {#rightPadding-prop}

Padding property.

The default value is based on [Kirigami.Units](../kirigamiplatform/qml-org-kde-kirigami-platform-units.md). To ensure consistency it's recommended that you do not change this property.

### title : string {#title-prop}

This property holds the header title.

### topPadding : real {#topPadding-prop}

Padding property.

The default value is based on [Kirigami.Units](../kirigamiplatform/qml-org-kde-kirigami-platform-units.md). To ensure consistency it's recommended that you do not change this property.

### trailing : alias {#trailing-prop}

The component that appears to the right-most side of the header.
