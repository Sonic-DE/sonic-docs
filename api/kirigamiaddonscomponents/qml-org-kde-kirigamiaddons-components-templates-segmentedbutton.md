---
title: "SegmentedButton QML Type"
description: "Shared actions and layout for segmented buttons."
---

# SegmentedButton QML Type

Shared actions and layout for segmented buttons. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.components.templates
- Inherits: [RowLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-rowlayout.html) (QtQuick.Layouts)
- Inherited By: [SegmentedButton](qml-org-kde-kirigamiaddons-components-segmentedbutton.md) (org.kde.kirigamiaddons.components)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### actions : list\<T.Action\> {#actions-prop}

This property holds the actions represented by the segments.

### delegate : Component {#delegate-prop}

The component used to display each segment. It receives the action as modelData and its position as index.
