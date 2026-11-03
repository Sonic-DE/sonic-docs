---
title: "Chart QML Type"
description: "Abstract base class for all charts."
---

# Chart QML Type

Abstract base class for all charts. [More...](#details)

- Import Statement: import org.kde.quickcharts
- Inherited By: [PieChart](qml-org-kde-quickcharts-piechart.md) and [XYChart](qml-org-kde-quickcharts-xychart.md)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### colorSource : ChartDataSource {#colorSource-prop}

The data source to use for colors of chart items.

### highlight : int {#highlight-prop}

The index of a value source to highlight.

Highlighting is dependant on Chart type, but will generally mean that other value sources are rendered with lower opacity.

By default, this is -1 which means nothing is highlighted.

### indexingMode : enumeration {#indexingMode-prop}

The indexing mode used for indexing colors and names.

The default value is `Chart.IndexEachSource`.

| Constant | Description |
| --- | --- |
| Chart.IndexSourceValues | Index each value, restart indexing for each value source. |
| Chart.IndexEachSource | Index each value source, never index individual values. |
| Chart.IndexAllValues | Index each value, continuing with the index for each value source. |

### nameSource : ChartDataSource {#nameSource-prop}

The data source to use for names of chart items.

### shortNameSource : ChartDataSource {#shortNameSource-prop}

The data source to use for short names of chart items.

### valueSources : list\<ChartDataSource\> {#valueSources-prop}

The data sources providing the data this chart needs to render.
