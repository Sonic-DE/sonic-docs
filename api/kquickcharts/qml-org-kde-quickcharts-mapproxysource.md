---
title: "MapProxySource QML Type"
description: "A source that uses the values of another source to produce values from a map."
---

# MapProxySource QML Type

A source that uses the values of another source to produce values from a map. [More...](#details)

- Import Statement: import org.kde.quickcharts
- Inherits: [ChartDataSource](qml-org-kde-quickcharts-chartdatasource.md)

## Detailed Description {#details}

This source reads values from another source, then uses those as an index to a map of different values and returns the appropriate value from that map. This source's itemCount matches that of the other source.

## Property Documentation {#property-documentation}

### map : QVariantMap {#map-prop}

The map to index for values.

### source : ChartDataSource {#source-prop}

A [ChartDataSource](qml-org-kde-quickcharts-chartdatasource.md) that is used as map indexes.
