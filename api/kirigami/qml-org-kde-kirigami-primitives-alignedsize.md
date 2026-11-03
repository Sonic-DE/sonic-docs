---
title: "AlignedSize QML Type"
description: "An attached property that aligns a size on the physical pixel grid. This type was introduced in Qt 6.20."
---

# AlignedSize QML Type

An attached property that aligns a size on the physical pixel grid. This type was introduced in Qt 6.20. [More...](#details)

- Import Statement: import org.kde.kirigami.primitives
- Since: Qt 6.20

## Detailed Description {#details}

Adjusts a size to the nearest one perfectly aligned to the pixel grid in case fractional scaling in used.

```qml
import org.kde.kirigami as Kirigami

Rectangle {
   AlignedSize.width: Units.gridUnit
   AlignedSize.height: 1
}
```

## Attached Property Documentation {#attached-property-documentation}

### AlignedSize.height : real {#height-attached-prop}

The height of the item in logical pixels

### AlignedSize.width : real {#width-attached-prop}

The width of the item in logical pixels
