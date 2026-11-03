---
title: "PieChartControl QML Type"
description: "A pie chart with text in the middle."
---

# PieChartControl QML Type

A pie chart with text in the middle. [More...](#details)

- Import Statement: import org.kde.quickcharts.controls
- Inherits: [Control](https://doc.qt.io/qt-6/qml-qtquick-controls-control.html)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### chart : PieChart {#chart-prop}

### color : color {#color-prop}

### highlight : int {#highlight-prop}

### names : variant {#names-prop}

### range group {#range-prop}

**range.automatic : bool**

**range.distance : real**

**range.from : real**

**range.increment : real**

**range.minimum : real**

**range.to : real**

The range of values to display in this [PieChartControl](qml-org-kde-quickcharts-controls-piechartcontrol.md).

from: The start of this range. The default is 0.

to: The end of this range. The default is 100.

automatic: Whether to determine the range based on values of a chart. If true (the default), from and to are ignored and instead calculated from the minimum and maximum values of a chart's [valueSources](qml-org-kde-quickcharts-controls-piechartcontrol.md#valueSources-prop).

distance: The distance between from and to

minimum: The minimum size of the range. This is mostly relevant when automatic is true. Setting this value will ensure that the range will never be smaller than this value. The default is std::numeric\_limits\<qreal\>::min, which means minimum is disabled.

increment: The amount with which the range increases. The total range will be limited to a multiple of this value. This is mostly useful when automatic is true. The default is 0.0, which means do not limit the range increment.

When set to "automatic", the values will be divided across the entire chart.

### text : string {#text-prop}

### valueSources : ChartDataSource {#valueSources-prop}
