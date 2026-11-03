---
title: "HistoryProxySource QML Type"
description: "A data source that provides a history of a single item of a different data source."
---

# HistoryProxySource QML Type

A data source that provides a history of a single item of a different data source. [More...](#details)

- Import Statement: import org.kde.quickcharts
- Inherits: [ChartDataSource](qml-org-kde-quickcharts-chartdatasource.md)

## Detailed Description {#details}

This data source will monitor a single item of another data source for changes and record them, exposing historical values as

## Property Documentation {#property-documentation}

### fillMode : enumeration {#fillMode-prop}

The fill mode.

This determines what happens when there is not enough history yet.

The default is DoNotFill.

> **Note:** Changing this property will clear the existing history.

| Constant | Description |
| --- | --- |
| HistoryProxySource.DoNotFill | Do not fill with any items. The source's itemCount will be equal to the number of items in the history. |
| HistoryProxySource.FillFromStart | Fill with empty values, starting at 0. The source's itemCount will be equal to [maximumHistory](qml-org-kde-quickcharts-historyproxysource.md#maximumHistory-prop). Items that do not have a value in the history will return a default-constructed value based on the first item of the source. |
| HistoryProxySource.FillFromEnd | Fill with empty values, placing partial history at the end. This means that the first recorded history item will be shown at position `maximumHistory - 1`, the second at `maximumHistory - 2` and so on, until [maximumHistory](qml-org-kde-quickcharts-historyproxysource.md#maximumHistory-prop) is reached, after which items will be discarded normally. |

### interval : int {#interval-prop}

The interval, in milliseconds, with which to query the data source.

If set to a value \<= 0, a new item will be added whenever [source](qml-org-kde-quickcharts-historyproxysource.md#source-prop) changes. Otherwise, source will be sampled every interval milliseconds and a new item will be added with whatever value it has at that point, even if it did not change.

The default is 0.

### item : int {#item-prop}

The item of the data source to read data from.

This item will be read either when the source's dataChanged has been emitted or on an interval if [interval](qml-org-kde-quickcharts-historyproxysource.md#interval-prop) has been set.

The default is 0.

> **Note:** Changing this property will clear the existing history.

### maximumHistory : int {#maximumHistory-prop}

The maximum amount of history to keep.

The default is 10.

### source : ChartDataSource {#source-prop}

The data source to read data from.

This will use the item at [item](qml-org-kde-quickcharts-historyproxysource.md#item-prop) from the provided source and use that to fill the history of this source.

> **Note:** Changing this property will clear the existing history.
