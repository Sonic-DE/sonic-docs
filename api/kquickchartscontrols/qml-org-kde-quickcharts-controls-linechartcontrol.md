---
title: "LineChartControl QML Type"
description: "A line chart with legend, grid and axis labels."
---

# LineChartControl QML Type

A line chart with legend, grid and axis labels. [More...](#details)

- Import Statement: import org.kde.quickcharts.controls
- Inherits: [Control](https://doc.qt.io/qt-6/qml-qtquick-controls-control.html)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### chart : LineChart {#chart-prop}

### color : color {#color-prop}

### fillOpacity : real {#fillOpacity-prop}

### highlightEnabled : bool {#highlightEnabled-prop}

### horizontalLinesVisible : bool {#horizontalLinesVisible-prop}

### legend : Legend {#legend-prop}

### lineWidth : real {#lineWidth-prop}

### names : variant {#names-prop}

### pointDelegate : Component {#pointDelegate-prop}

### stacked : bool {#stacked-prop}

### valueSources : ChartDataSource {#valueSources-prop}

### verticalLinesVisible : bool {#verticalLinesVisible-prop}

### xAxisSource : ChartAxisSource {#xAxisSource-prop}

### xLabels : AxisLabels {#xLabels-prop}

### xRange group {#xRange-prop}

### xRange.automatic : bool {#xRange.automatic-prop}

### xRange.distance : real {#xRange.distance-prop}

### xRange.from : real {#xRange.from-prop}

### xRange.increment : real {#xRange.increment-prop}

### xRange.minimum : real {#xRange.minimum-prop}

### xRange.to : real {#xRange.to-prop}

The range of values on the X axis.

from: The start of this range. The default is 0.

to: The end of this range. The default is 100.

automatic: Whether to determine the range based on values of a chart. If true (the default), from and to are ignored and instead calculated from the minimum and maximum values of a chart's [valueSources](qml-org-kde-quickcharts-controls-linechartcontrol.md#valueSources-prop).

distance: The distance between from and to.

minimum: The minimum size of the range. This is mostly relevant when automatic is true. Setting this value will ensure that the range will never be smaller than this value. The default is std::numeric\_limits\<qreal\>::min, which means minimum is disabled.

increment: The amount with which the range increases. The total range will be limited to a multiple of this value. This is mostly useful when automatic is true. The default is 0.0, which means do not limit the range increment.

### yAxisSource : ChartAxisSource {#yAxisSource-prop}

### yLabels : AxisLabels {#yLabels-prop}

### yRange group {#yRange-prop}

### yRange.automatic : bool {#yRange.automatic-prop}

### yRange.distance : real {#yRange.distance-prop}

### yRange.from : real {#yRange.from-prop}

### yRange.increment : real {#yRange.increment-prop}

### yRange.minimum : real {#yRange.minimum-prop}

### yRange.to : real {#yRange.to-prop}

The range of values on the Y axis.

from: The start of this range. The default is 0.

to: The end of this range. The default is 100.

automatic: Whether to determine the range based on values of a chart. If true (the default), from and to are ignored and instead calculated from the minimum and maximum values of a chart's [valueSources](qml-org-kde-quickcharts-controls-linechartcontrol.md#valueSources-prop).

distance: The distance between from and to.

minimum: The minimum size of the range. This is mostly relevant when automatic is true. Setting this value will ensure that the range will never be smaller than this value. The default is std::numeric\_limits\<qreal\>::min, which means minimum is disabled.

increment: The amount with which the range increases. The total range will be limited to a multiple of this value. This is mostly useful when automatic is true. The default is 0.0, which means do not limit the range increment.
