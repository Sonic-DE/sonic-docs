---
title: "KDescendantsProxyModel QML Type"
description: "Flattens a tree model into a list."
---

# KDescendantsProxyModel QML Type

Flattens a tree model into a list. [More...](#details)

- Import Statement: import org.kde.kitemmodels
- In C++: [KDescendantsProxyModel](../kitemmodels/kdescendantsproxymodel.md)

## Detailed Description {#details}

Set [model](qml-org-kde-kitemmodels-kdescendantsproxymodel.md#model-prop) to the source tree model. Each item in the flattened list can be expanded or collapsed using its row in this proxy model.

## Property Documentation {#property-documentation}

### \[default: " / "\] ancestorSeparator : string {#ancestorSeparator-prop}

The separator between ancestor values when [displayAncestorData](qml-org-kde-kitemmodels-kdescendantsproxymodel.md#displayAncestorData-prop) is true.

### \[default: false\] displayAncestorData : bool {#displayAncestorData-prop}

Whether display data includes the item's ancestors.

### \[default: true\] expandsByDefault : bool {#expandsByDefault-prop}

Whether all items are expanded when the source model is loaded.

### model : var {#model-prop}

The source tree model to flatten.

### sourceModel : var {#sourceModel-prop}

The source tree model to flatten. This inherited property refers to the same model as [model](qml-org-kde-kitemmodels-kdescendantsproxymodel.md#model-prop).

## Method Documentation {#method-documentation}

### void collapseChildren(int *row*) {#collapseChildren-method}

Collapses the children of the item at `row` in this proxy model.

### void expandChildren(int *row*) {#expandChildren-method}

Expands the children of the item at `row` in this proxy model.

### QModelIndex mapFromSource(QModelIndex *sourceIndex*) {#mapFromSource-method}

Returns the proxy model index corresponding to `sourceIndex`.

*See also* [mapToSource](qml-org-kde-kitemmodels-kdescendantsproxymodel.md#mapToSource-method)()

### QItemSelection mapSelectionFromSource(QItemSelection *sourceSelection*) {#mapSelectionFromSource-method}

Returns the proxy model selection corresponding to `sourceSelection`.

### QItemSelection mapSelectionToSource(QItemSelection *proxySelection*) {#mapSelectionToSource-method}

Returns the source model selection corresponding to `proxySelection`.

### QModelIndex mapToSource(QModelIndex *proxyIndex*) {#mapToSource-method}

Returns the source model index corresponding to `proxyIndex`.

*See also* [mapFromSource](qml-org-kde-kitemmodels-kdescendantsproxymodel.md#mapFromSource-method)()

### void toggleChildren(int *row*) {#toggleChildren-method}

Toggles the expansion of the item at `row` in this proxy model.
