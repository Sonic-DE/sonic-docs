---
title: "XYChart QML Type"
description: "A base class for Charts that are based on an X/Y grid."
---

# XYChart QML Type

A base class for Charts that are based on an X/Y grid. [More...](#details)

- Import Statement: import org.kde.quickcharts
- Inherits: [Chart](qml-org-kde-quickcharts-chart.md)
- Inherited By: [BarChart](qml-org-kde-quickcharts-barchart.md) and [LineChart](qml-org-kde-quickcharts-linechart.md)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### direction : enumeration {#direction-prop}

Which direction this chart's X axis runs.

| Constant | Description |
| --- | --- |
| XYChart.ZeroAtStart | Zero is at the beginning of the chart, values run from begin to end. |
| XYChart.ZeroAtEnd | Zero is at the end of the chart, values run from end to begin. |

### stacked : bool {#stacked-prop}

Whether the values of each value source should be stacked.

When true, Y values will be added on top of each other. The precise meaning of this property depends on the specific chart. The default is false.

### xRange group {#xRange-prop}

**xRange.automatic : bool**

**xRange.distance : real**

**xRange.from : real**

**xRange.increment : real**

**xRange.minimum : real**

**xRange.to : real**

The range of values on the X axis.

from: The start of this range. The default is 0.

to: The end of this range. The default is 100.

automatic: Whether to determine the range based on values of a chart. If true (the default), from and to are ignored and instead calculated from the minimum and maximum values of a chart's valueSources.

distance: The distance between from and to.

minimum: The minimum size of the range. This is mostly relevant when automatic is true. Setting this value will ensure that the range will never be smaller than this value. The default is std::numeric\_limits\<qreal\>::min, which means minimum is disabled.

increment: The amount with which the range increases. The total range will be limited to a multiple of this value. This is mostly useful when automatic is true. The default is 0.0, which means do not limit the range increment.

### yRange group {#yRange-prop}

**yRange.automatic : bool**

**yRange.distance : real**

**yRange.from : real**

**yRange.increment : real**

**yRange.minimum : real**

**yRange.to : real**

The range of values on the Y axis.

from: The start of this range. The default is 0.

to: The end of this range. The default is 100.

automatic: Whether to determine the range based on values of a chart. If true (the default), from and to are ignored and instead calculated from the minimum and maximum values of a chart's valueSources.

distance: The distance between from and to.

minimum: The minimum size of the range. This is mostly relevant when automatic is true. Setting this value will ensure that the range will never be smaller than this value. The default is std::numeric\_limits\<qreal\>::min, which means minimum is disabled.

increment: The amount with which the range increases. The total range will be limited to a multiple of this value. This is mostly useful when automatic is true. The default is 0.0, which means do not limit the range increment.
