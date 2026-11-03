---
title: "KNumberModel Class"
description: "Creates a model of entries from N to M with rows at a given interval."
---

# KNumberModel Class

Creates a model of entries from N to M with rows at a given interval. [More...](#details)

- **Header:** `#include <KNumberModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ItemModels)`  
  `target_link_libraries(mytarget PRIVATE KF6::ItemModels)`
- **Inherits:** [QAbstractListModel](https://doc.qt.io/qt-6/qabstractlistmodel.html)

[List of all members, including inherited members](knumbermodel-members.md)

## Public Types

- [enum KNumberModel::Roles](#Roles-enum)

## Properties

- [formattingOptions : QLocale::NumberOptions](#formattingOptions-prop)
- [maximumValue : qreal](#maximumValue-prop)
- [minimumValue : qreal](#minimumValue-prop)
- [stepSize : qreal](#stepSize-prop)

## Public Functions

- [KNumberModel(QObject \*parent = nullptr)](#KNumberModel)
- [qreal value(const QModelIndex &index) const](#value)

## Detailed Description {#details}

The model contains two roles:

- display - the number represented as a string
- value - the actual value as a number

## Member Type Documentation {#member-type-documentation}

### enum KNumberModel::Roles {#Roles-enum}

| Constant |   |
| --- | --- |
| `KNumberModel::DisplayRole` | `Qt::DisplayRole` |
| `KNumberModel::ValueRole` | `Qt::UserRole` |

## Property Documentation {#property-documentation}

### formattingOptions : QLocale::NumberOptions {#formattingOptions-prop}

Defines the string representation of the number, e.g. "1,000" or "1000".

Default is `QLocale::Default`.

**Access functions:**

- `QLocale::NumberOptions` **formattingOptions**() const
- `void` **setFormattingOptions**(`QLocale::NumberOptions` *options*)

**Notifier signal:**

- `void` **formattingOptionsChanged**()

### maximumValue : qreal {#maximumValue-prop}

The maximum value for the model

The default value is `0.0`.

> **Note:** If `maximumValue` is a multiple of `stepSize` added to `minimumValue` it will be included. Otherwise it will not be reached. E.g. in a model with a `minimumValue` of 0.0, a `maximumValue` of 1.0 and a `stepSize` of 0.3, the final row will be 0.9.

**Access functions:**

- `qreal` **maximumValue**() const
- `void` **setMaximumValue**(`qreal` *maximumValue*)

**Notifier signal:**

- `void` **maximumValueChanged**()

### minimumValue : qreal {#minimumValue-prop}

The minimum value for the model

The default value is `0.0`.

**Access functions:**

- `qreal` **minimumValue**() const
- `void` **setMinimumValue**(`qreal` *minimumValue*)

**Notifier signal:**

- `void` **minimumValueChanged**()

### stepSize : qreal {#stepSize-prop}

Step between listed entries

The default value is `1.0`.

**Access functions:**

- `qreal` **stepSize**() const
- `void` **setStepSize**(`qreal` *stepSize*)

**Notifier signal:**

- `void` **stepSizeChanged**()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KNumberModel::KNumberModel(QObject \**parent* = nullptr) {#KNumberModel}

### qreal KNumberModel::value(const QModelIndex &*index*) const {#value}

Returns the value represented at the given index.
