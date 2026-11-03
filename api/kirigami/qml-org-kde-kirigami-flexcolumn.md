---
title: "FlexColumn QML Type"
description: "FlexColumn is a column that grows in width to a fixed cap."
---

# FlexColumn QML Type

[FlexColumn](qml-org-kde-kirigami-flexcolumn.md) is a column that grows in width to a fixed cap. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### alignment : int {#alignment-prop}

This property sets column's alignment when it hits its maximum width.

default: Qt.AlignHCenter \| Qt.AlignTop

*See also* Qt.Alignment

### innerWidth : real {#innerWidth-prop}

This property holds the inner column's width.

### maximumWidth : real {#maximumWidth-prop}

This property holds maximum column width.

default: Kirigami.Units.gridUnit \* 50

### padding : real {#padding-prop}

This property holds the column's offset from the cross axis.

Note that padding is applied on both sides when the column is aligned to a centered cross axis.

default: Kirigami.Units.largeSpacing
