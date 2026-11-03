---
title: "ListSectionHeader QML Type"
description: "A section delegate for the primitive ListView component."
---

# ListSectionHeader QML Type

A section delegate for the primitive [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html) component. [More...](#details)

- Import Statement: import org.kde.plasma.extras
- Inherits: [ItemDelegate](../plasmacomponents/qml-org-kde-plasma-components-itemdelegate.md)

## Detailed Description {#details}

It's intended to make all listviews look coherent, mirroring the style of the Kirigami version, but with the separator line being an SVG from the Plasma theme rather than a simple line.

Any additional content items will be positioned in a row at the trailing side of this component.

Example usage:

```qml
import QtQuick
import org.kde.plasma.components as PlasmaComponents
import org.kde.plasma.extras as PlasmaExtras

ListView {
    section.delegate: PlasmaExtras.ListSectionHeader {
        label: section

        PlasmaComponents.Button {
            text: "Button 1"
        }
        PlasmaComponents.Button {
            text: "Button 2"
        }
    }
}
```

TODO qdoc how to document inheritance

## Property Documentation {#property-documentation}

### label : string {#label-prop}

This property sets the text of the [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html)'s section header.
