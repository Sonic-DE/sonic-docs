---
title: "KNumberModel QML Type"
description: "Provides a list of numbers at a fixed interval."
---

# KNumberModel QML Type

Provides a list of numbers at a fixed interval. [More...](#details)

- Import Statement: import org.kde.kitemmodels
- In C++: [KNumberModel](../kitemmodels/knumbermodel.md)

## Detailed Description {#details}

The `display` role contains a locale-formatted string, and the `value` role contains the number. The list starts at [minimumValue](qml-org-kde-kitemmodels-knumbermodel.md#minimumValue-prop) and advances by [stepSize](qml-org-kde-kitemmodels-knumbermodel.md#stepSize-prop) toward [maximumValue](qml-org-kde-kitemmodels-knumbermodel.md#maximumValue-prop). The end value is included only when a step reaches it exactly.

## Property Documentation {#property-documentation}

### \[default: QLocale::DefaultNumberOptions\] formattingOptions : QLocale::NumberOptions {#formattingOptions-prop}

The [QLocale](https://doc.qt.io/qt-6/qlocale.html) number formatting options used by the `display` role.

### \[default: 0.0\] maximumValue : real {#maximumValue-prop}

The upper bound for values in the model. The model includes this value only when it falls on a step from [minimumValue](qml-org-kde-kitemmodels-knumbermodel.md#minimumValue-prop).

### \[default: 0.0\] minimumValue : real {#minimumValue-prop}

The first value in the model.

### \[default: 1.0\] stepSize : real {#stepSize-prop}

The interval between values.
