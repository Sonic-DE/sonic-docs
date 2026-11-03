---
title: "PluginSelector QML Type"
description: "ListView for showing plugins with their info and configuration."
---

# PluginSelector QML Type

[ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html) for showing plugins with their info and configuration. [More...](#details)

- Import Statement: import org.kde.kcmutils
- Inherits: [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html)

## Detailed Description {#details}

If extra butons should be added, a custom KPluginDelegate with the additionalActions property should be defined.

Renamed from KPluginSelector to [PluginSelector](qml-org-kde-kcmutils-pluginselector.md) in 6.0.

## Property Documentation {#property-documentation}

### query : string {#query-prop}

\* Query that is typed into the search field. Ideally, this is part of the KCM header

### \[required\] sourceModel : QtObject {#sourceModel-prop}

\* **\<Unknown command\>`qmproperty`** model PluginSelector::sourceModel \* \* [KPluginModel](kpluginmodel.md) which contains the plugins that should be displayed
