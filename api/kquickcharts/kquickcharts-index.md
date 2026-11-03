---
title: "KQuickCharts"
description: "Charts."
---

# KQuickCharts

Charts.

A [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html) module providing high-performance charts.

## Introduction {#introduction}

The Quick Charts module provides a set of charts that can be used from [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html) applications. They are intended to be used for both simple display of data as well as continuous display of high-volume data (often referred to as plotters). The charts use a system called distance fields for their accelerated rendering, which provides ways of using the GPU for rendering 2D shapes without loss of quality.

### Usage Example {#usage-example}

The following piece of code will render a simple line chart containing three lines:

```qml
import QtQuick
import QtQuick.Controls

import org.kde.quickcharts as Charts

ApplicationWindow {
    width: 500
    height: 500

    Rectangle {
        anchors.centerIn: parent
        width: 300
        height: 200
        border.width: 2

        Charts.LineChart {
            anchors.fill: parent

            colorSource: Charts.ArraySource { array: ["red", "green", "blue"] }
            nameSource: Charts.ArraySource { array: ["First", "Second", "Third"] }

            valueSources: [
                Charts.ArraySource { array: [1, 2, 2, 1] },
                Charts.ArraySource { array: [2, 5, 2, 5] },
                Charts.ArraySource { array: [5, 4, 3, 4] }
            ]
        }
    }
}
```

## Concepts {#concepts}

There are three main concepts to consider when using this module: charts, data sources and decorations.

### Charts {#charts}

These are the main items of the module. They process data and render it in a certain way. Currently there are three main types of charts: pie charts, line charts and bar charts. All charts inherit the Chart class, which provides the most basic chart interface. On top of that is the [XYChart](qml-org-kde-quickcharts-xychart.md) base class, which provides an interface for charts that are based on an X/Y grid.

- [PieChart](qml-org-kde-quickcharts-piechart.md)
- [LineChart](qml-org-kde-quickcharts-linechart.md)
- [BarChart](qml-org-kde-quickcharts-barchart.md)

### Data Sources {#data-sources}

Data sources are objects that provide data to charts. These objects act as adapters to other objects, like Qt's models. All data source objects inherit [ChartDataSource](qml-org-kde-quickcharts-chartdatasource.md), which represents the basic data source interface.

- [SingleValueSource](qml-org-kde-quickcharts-singlevaluesource.md)
- [ArraySource](qml-org-kde-quickcharts-arraysource.md)
- [ModelSource](qml-org-kde-quickcharts-modelsource.md)
- [HistoryProxySource](qml-org-kde-quickcharts-historyproxysource.md)
- [ColorGradientSource](qml-org-kde-quickcharts-colorgradientsource.md)
- [ChartAxisSource](qml-org-kde-quickcharts-chartaxissource.md)

### Decorations {#decorations}

Decorations are items that provide extra information about a chart. These are things like a legend or axis labels. They usually work with multiple types of charts, though some may be limited to X/Y charts.

- [AxisLabels](../kquickchartscontrols/qml-org-kde-quickcharts-controls-axislabels.md)
- [GridLines](../kquickchartscontrols/qml-org-kde-quickcharts-controls-gridlines.md)
- [LegendModel](../kquickchartscontrols/qml-org-kde-quickcharts-controls-legendmodel.md)

## Controls {#controls}

A submodule is provided that contains pre-made controls that are provided as a convenience layer. These controls may be more restrictive in their data sources or how they display things. They are composed of Charts items along with some [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html) Controls items. Some of the controls may use style-specific theming.

- [Legend](../kquickchartscontrols/qml-org-kde-quickcharts-controls-legend.md)
- [LegendDelegate](../kquickchartscontrols/qml-org-kde-quickcharts-controls-legenddelegate.md)
- [LineChartControl](../kquickchartscontrols/qml-org-kde-quickcharts-controls-linechartcontrol.md)
- [PieChartControl](../kquickchartscontrols/qml-org-kde-quickcharts-controls-piechartcontrol.md)

## Supporting Code {#supporting-code}

There are a number of classes and other pieces of code that are not considered public API and thus not part of the public API documentation. Primarily, these are all the [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html) Scene Graph related classes located in \`src/scenegraph/\`, in addition to the shaders that are used for rendering charts.

## API Reference {#api-reference}

- [KQuickCharts QML Types](org-kde-quickcharts-qmlmodule.md)
- [KQuickCharts Controls QML Types](../kquickchartscontrols/org-kde-quickcharts-controls-qmlmodule.md)
