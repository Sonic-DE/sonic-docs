---
title: "LineChart QML Type"
description: "A line chart."
---

# LineChart QML Type

A line chart. [More...](#details)

- Import Statement: import org.kde.quickcharts
- Inherits: [XYChart](qml-org-kde-quickcharts-xychart.md)

## Detailed Description {#details}

### Usage example {#usage-example}

```qml
import QtQuick
import QtQuick.Controls

import org.kde.quickcharts as Charts

Charts.LineChart {
    width: 400
    height: 300

    valueSources: [
        Charts.ModelSource { roleName: "value1"; model: listModel },
        Charts.ModelSource { roleName: "value2"; model: listModel },
        Charts.ModelSource { roleName: "value3"; model: listModel }
    ]
    colorSource: Charts.ArraySource { array: ["red", "green", "blue"] }
    nameSource: Charts.ArraySource { array: ["Example 1", "Example 2", "Example 3"]}

    ListModel {
        id: listModel

        ListElement { value1: 19; value2: 2; value3: 6 }
        ListElement { value1: 14; value2: 20; value3: 17 }
        ListElement { value1: 4; value2: 10; value3: 11 }
        ListElement { value1: 5; value2: 11; value3: 9 }
        ListElement { value1: 20; value2: 7; value3: 13 }
    }
}
```

## Property Documentation {#property-documentation}

### fillColorSource : ChartDataSource {#fillColorSource-prop}

A data source that supplies color values for the line charts' fill area.

If this is not set (the default), the normal color source will be used, with the [fillOpacity](qml-org-kde-quickcharts-linechart.md#fillOpacity-prop) used as its opacity.

### fillOpacity : real {#fillOpacity-prop}

The opacity of the area below a line.

The default is 0.0. Note that if [fillColorSource](qml-org-kde-quickcharts-linechart.md#fillColorSource-prop) is set, this value is ignored.

### interpolate : bool {#interpolate-prop}

Interpolate the values in the chart so that the lines become smoothed.

### lineWidth : real {#lineWidth-prop}

The width of a line in the chart.

### pointDelegate : Component {#pointDelegate-prop}

A delegate that will be placed at each line chart point.

When this is not null, the specified component will be used to instantiate an object for each point in the chart. These objects will then be placed centered at positions corresponding to the points on the chart. Each instance will have access to the attached properties of LineChartAttached through [LineChart](qml-org-kde-quickcharts-linechart.md) attached object.

> **Note:** The component assigned to this property is expected to create a [QQuickItem](https://doc.qt.io/qt-6/qquickitem.html), since the created object needs to be positioned.

## Attached Property Documentation {#attached-property-documentation}

### LineChart.color : color {#color-attached-prop}

The color at the current point.

### LineChart.name : string {#name-attached-prop}

The name at the current point.

### LineChart.shortName : string {#shortName-attached-prop}

The short name at the current point.

### LineChart.value : var {#value-attached-prop}

The value at the current point.
