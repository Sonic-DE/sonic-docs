---
title: "ArraySource QML Type"
description: "A data source that provides entries of an array as data."
---

# ArraySource QML Type

A data source that provides entries of an array as data. [More...](#details)

- Import Statement: import org.kde.quickcharts
- Inherits: [ChartDataSource](qml-org-kde-quickcharts-chartdatasource.md)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### array : list\<variant\> {#array-prop}

The array to use to provide entries from.

### wrap : bool {#wrap-prop}

Wraparound when indexing past the array's bounds.

If true, when an item is requested at an index outside of the array's bounds, wrap around to the start or end of the array and continue from there. This ensures we always return an entry from the array.

If false (the default), requesting an item at an index outside of the array's'bounds, we return an empty item instead.
