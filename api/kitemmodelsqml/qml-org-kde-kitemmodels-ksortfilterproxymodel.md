---
title: "KSortFilterProxyModel QML Type"
description: "Filter and sort an existing QAbstractItemModel."
---

# KSortFilterProxyModel QML Type

Filter and sort an existing [QAbstractItemModel](https://doc.qt.io/qt-6/qabstractitemmodel.html). [More...](#details)

- Import Statement: import org.kde.kitemmodels
- In C++: [QSortFilterProxyModel](https://doc.qt.io/qt-6/qsortfilterproxymodel.html)

## Detailed Description {#details}

For example, filter and sort a list by its name role:

```qml
import QtQuick
import org.kde.kitemmodels

ListView {
    width: 200
    height: 200
    model: KSortFilterProxyModel {
        sourceModel: ListModel {
            ListElement { name: "Alice" }
            ListElement { name: "Bob" }
            ListElement { name: "Charlie" }
        }
        filterRoleName: "name"
        filterString: "li"
        filterCaseSensitivity: Qt.CaseInsensitive
        sortRoleName: "name"
        sortCaseSensitivity: Qt.CaseInsensitive
        sortColumn: 0
    }
    delegate: Text { text: name }
}
```

## Property Documentation {#property-documentation}

### \[default: false\] autoAcceptChildRows : bool {#autoAcceptChildRows-prop}

Whether all children of an accepted row remain visible, even if they do not match the filter themselves.

### count : int {#count-prop}

The number of top level rows.

### \[default: true\] dynamicSortFilter : bool {#dynamicSortFilter-prop}

Whether the proxy updates its sorting and filtering when [sourceModel](qml-org-kde-kitemmodels-ksortfilterproxymodel.md#sourceModel-prop) changes.

### \[default: Qt.CaseSensitive\] filterCaseSensitivity : Qt::CaseSensitivity {#filterCaseSensitivity-prop}

The case sensitivity used when filtering strings.

### filterColumnCallback : var {#filterColumnCallback-prop}

A JavaScript callable that can be used to perform advanced filters on a given column. The callback is passed the source column, and source parent for a given column as arguments.

*See also* [filterRowCallback](qml-org-kde-kitemmodels-ksortfilterproxymodel.md#filterRowCallback-prop)

### \[default: 0\] filterKeyColumn : int {#filterKeyColumn-prop}

The source column used for filtering. A value of -1 checks all columns.

### filterRegularExpression : var {#filterRegularExpression-prop}

The regular expression used to filter source rows. Setting [filterString](qml-org-kde-kitemmodels-ksortfilterproxymodel.md#filterString-prop) replaces it with a fixed-string filter.

### \[default: Qt.DisplayRole\] filterRole : int {#filterRole-prop}

The source role ID used for filtering. Setting this also updates [filterRoleName](qml-org-kde-kitemmodels-ksortfilterproxymodel.md#filterRoleName-prop).

### filterRoleName : string {#filterRoleName-prop}

The name of the source role used for filtering. Use [filterRole](qml-org-kde-kitemmodels-ksortfilterproxymodel.md#filterRole-prop) to set a numerical role ID instead.

### filterRowCallback : var {#filterRowCallback-prop}

A JavaScript callable that can be used to perform advanced filters on a given row. The callback is passed the source row, and source parent for a given row as arguments

The callable's return value is evaluated as boolean to determine whether the row is accepted (true) or filtered out (false). It overrides the default row filter, so [filterString](qml-org-kde-kitemmodels-ksortfilterproxymodel.md#filterString-prop) and [filterRegularExpression](qml-org-kde-kitemmodels-ksortfilterproxymodel.md#filterRegularExpression-prop) have no effect while filterRowCallback is set. Attempts to write a non-callable to this property are silently ignored, but you can set it to null.

```qml
filterRowCallback: function(source_row, source_parent) {
  return sourceModel.data(sourceModel.index(source_row, 0, source_parent), Qt.DisplayRole) == "...";
};
```

### filterString : string {#filterString-prop}

A fixed string used to filter rows by [filterRole](qml-org-kde-kitemmodels-ksortfilterproxymodel.md#filterRole-prop). Only matching rows are displayed.

### \[default: false\] isSortLocaleAware : bool {#isSortLocaleAware-prop}

Whether string sorting follows the current locale.

### \[default: false\] recursiveFilteringEnabled : bool {#recursiveFilteringEnabled-prop}

Whether a parent remains visible when one of its descendants matches the filter.

### \[default: Qt.CaseSensitive\] sortCaseSensitivity : Qt::CaseSensitivity {#sortCaseSensitivity-prop}

The case sensitivity used when sorting strings.

### \[default: -1\] sortColumn : int {#sortColumn-prop}

Specify which column should be used for sorting Setting [sortRoleName](qml-org-kde-kitemmodels-ksortfilterproxymodel.md#sortRoleName-prop) sorts column 0 if no column has been selected.

### sortOrder : Qt::SortOrder {#sortOrder-prop}

One of Qt.AscendingOrder or Qt.DescendingOrder

### \[default: Qt.DisplayRole\] sortRole : int {#sortRole-prop}

The source role ID used for sorting. Setting this also updates [sortRoleName](qml-org-kde-kitemmodels-ksortfilterproxymodel.md#sortRoleName-prop).

### sortRoleName : string {#sortRoleName-prop}

The name of the source role used for sorting. Use [sortRole](qml-org-kde-kitemmodels-ksortfilterproxymodel.md#sortRole-prop) to set a numerical role ID instead. An empty name leaves rows unsorted.

### sourceModel : var {#sourceModel-prop}

The model whose rows are filtered and sorted.

## Method Documentation {#method-documentation}

### void invalidate() {#invalidate-method}

Reapplies sorting and filtering to the source model.

### void invalidateFilter() {#invalidateFilter-method}

Invalidates the current filtering.

This function should be called if you are implementing custom filtering through [filterRowCallback](qml-org-kde-kitemmodels-ksortfilterproxymodel.md#filterRowCallback-prop) or [filterColumnCallback](qml-org-kde-kitemmodels-ksortfilterproxymodel.md#filterColumnCallback-prop), and your filter parameters have changed.

### QModelIndex mapFromSource(QModelIndex *sourceIndex*) {#mapFromSource-method}

Returns the proxy model index corresponding to `sourceIndex`. A filtered-out item has no corresponding proxy index.

*See also* [mapToSource](qml-org-kde-kitemmodels-ksortfilterproxymodel.md#mapToSource-method)()

### QItemSelection mapSelectionFromSource(QItemSelection *sourceSelection*) {#mapSelectionFromSource-method}

Returns the proxy model selection corresponding to `sourceSelection`.

### QItemSelection mapSelectionToSource(QItemSelection *proxySelection*) {#mapSelectionToSource-method}

Returns the source model selection corresponding to `proxySelection`.

### QModelIndex mapToSource(QModelIndex *proxyIndex*) {#mapToSource-method}

Returns the source model index corresponding to `proxyIndex`.

*See also* [mapFromSource](qml-org-kde-kitemmodels-ksortfilterproxymodel.md#mapFromSource-method)()

### void setFilterFixedString(string *pattern*) {#setFilterFixedString-method}

Filters rows using the literal string `pattern`.

### void setFilterRegularExpression(string *pattern*) {#setFilterRegularExpression-method}

Filters rows using the regular expression `pattern`.

### void setFilterRegularExpression(var *regularExpression*) {#setFilterRegularExpression-method-1}

Filters rows using `regularExpression`.

### void setFilterWildcard(string *pattern*) {#setFilterWildcard-method}

Filters rows using the wildcard `pattern`.
