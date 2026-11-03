---
title: "PieChart QML Type"
description: "An item to render a pie chart."
---

# PieChart QML Type

An item to render a pie chart. [More...](#details)

- Import Statement: import org.kde.quickcharts
- Inherits: [Chart](qml-org-kde-quickcharts-chart.md)

## Detailed Description {#details}

This item will render a Pie chart based on the valueSources supplied to it. By default it will set indexingMode to IndexSourceValues, meaning that it will use the individual values of the valueSources to render sections of the chart.

### Usage example {#usage-example}

```qml
import QtQuick
import QtQuick.Controls

import org.kde.quickcharts as Charts

Charts.PieChart {
    width: 400
    height: 300

    valueSources: Charts.ModelSource {
        roleName: "data";
        model: ListModel {
            id: listModel
            ListElement { data: 12 }
            ListElement { data: 19 }
            ListElement { data: 10 }
            ListElement { data: 13 }
            ListElement { data: 13 }
        }
    }
    colorSource: Charts.ArraySource { array: ["red", "green", "blue", "yellow", "cyan"] }
    nameSource: Charts.ArraySource { array: ["Red", "Green", "Blue", "Yellow", "Cyan"] }

    thickness: 50
}
```

### Multiple Value Sources {#multiple-value-sources}

Multiple valueSources are rendered as consecutive pie charts in the same item. The first valueSource will become the outermost circle and consecutive valueSources will be rendered as continuously smaller circles. When rendering multiple value sources, filled will only affect the last value source. All other value sources will be rendered according to thickness, with spacing amount of space between them.

## Property Documentation {#property-documentation}

### backgroundColor : color {#backgroundColor-prop}

Sets a color to use to fill remaining space on the pie.

The default is transparent.

### filled : bool {#filled-prop}

Whether to use a filled pie or not.

If true, the last pie rendered will be rendered as a filled circle. The default is false.

### fromAngle : real {#fromAngle-prop}

The starting angle of the arc used for the entire pie.

When set, instead of rendering a full circle, the pie will be rendered as an arc. The default is 0.

### range group {#range-prop}

**range.automatic : bool**

**range.distance : real**

**range.from : real**

**range.increment : real**

**range.minimum : real**

**range.to : real**

The range of values to display in this [PieChart](qml-org-kde-quickcharts-piechart.md).

from: The start of this range. The default is 0.

to: The end of this range. The default is 100.

automatic: Whether to determine the range based on values of a chart. If true (the default), from and to are ignored and instead calculated from the minimum and maximum values of a chart's valueSources.

distance: The distance between from and to

minimum: The minimum size of the range. This is mostly relevant when automatic is true. Setting this value will ensure that the range will never be smaller than this value. The default is std::numeric\_limits\<qreal\>::min, which means minimum is disabled.

increment: The amount with which the range increases. The total range will be limited to a multiple of this value. This is mostly useful when automatic is true. The default is 0.0, which means do not limit the range increment.

When set to "automatic", the values will be divided across the entire chart.

### smoothEnds : bool {#smoothEnds-prop}

Smooth the ends of pie sections.

When true, this will try to smooth the ends of sections. This works best when filled is false. The default is false.

### spacing : real {#spacing-prop}

The amount of spacing between pies when rendering multiple value sources.

The default is 0.

### thickness : real {#thickness-prop}

The thickness of an individual pie, in pixels.

If filled is set, this is ignored for the last pie. The default is 10px.

### toAngle : real {#toAngle-prop}

The end angle of the arc used for the entire pie.

When set, instead of rendering a full circle, the pie will be rendered as an arc. The default is 360.
