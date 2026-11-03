---
title: "KExtraColumnsProxyModel Class"
description: "This proxy appends extra columns (after all existing columns)."
---

# KExtraColumnsProxyModel Class

This proxy appends extra columns (after all existing columns). [More...](#details)

- **Header:** `#include <KExtraColumnsProxyModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ItemModels)`  
  `target_link_libraries(mytarget PRIVATE KF6::ItemModels)`
- **Inherits:** [QIdentityProxyModel](https://doc.qt.io/qt-6/qidentityproxymodel.html)

[List of all members, including inherited members](kextracolumnsproxymodel-members.md)

## Public Functions

- [KExtraColumnsProxyModel(QObject \*parent = nullptr)](#KExtraColumnsProxyModel)
- [void appendColumn(const QString &header = QString())](#appendColumn)
- [QVariant extraColumnData(const QModelIndex &parent, int row, int extraColumn, int role = Qt::DisplayRole) const](#extraColumnData)
- [void extraColumnDataChanged(const QModelIndex &parent, int row, int extraColumn, const QList\<int\> &roles)](#extraColumnDataChanged)
- [int extraColumnForProxyColumn(int proxyColumn) const](#extraColumnForProxyColumn)
- [int proxyColumnForExtraColumn(int extraColumn) const](#proxyColumnForExtraColumn)
- [void removeExtraColumn(int idx)](#removeExtraColumn)
- [bool setExtraColumnData(const QModelIndex &parent, int row, int extraColumn, const QVariant &data, int role = Qt::EditRole)](#setExtraColumnData)

## Detailed Description {#details}

The proxy supports source models that have a tree structure. It also supports editing, and propagating changes from the source model. Row insertion/removal, column insertion/removal in the source model are supported.

Not supported: adding/removing extra columns at runtime; having a different number of columns in subtrees; drag-n-drop support in the extra columns; moving columns.

Derive from [KExtraColumnsProxyModel](kextracolumnsproxymodel.md), call [appendColumn](kextracolumnsproxymodel.md#appendColumn)() (typically in the constructor) for each extra column, and reimplement [extraColumnData](kextracolumnsproxymodel.md#extraColumnData)() to allow [KExtraColumnsProxyModel](kextracolumnsproxymodel.md) to retrieve the data to show in the extra columns.

If you want your new column(s) to be somewhere else than at the right of the existing columns, you can use a [KRearrangeColumnsProxyModel](krearrangecolumnsproxymodel.md) on top.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KExtraColumnsProxyModel::KExtraColumnsProxyModel(QObject \**parent* = nullptr) {#KExtraColumnsProxyModel}

Base class constructor. Remember to call setSourceModel afterwards, and [appendColumn](kextracolumnsproxymodel.md#appendColumn).

### void KExtraColumnsProxyModel::appendColumn(const QString &*header* = QString()) {#appendColumn}

Appends an extra column.

`header` an optional text for the horizontal header

This does not emit any signals - do it in the initial setup phase

### \[pure virtual\] QVariant KExtraColumnsProxyModel::extraColumnData(const QModelIndex &*parent*, int *row*, int *extraColumn*, int *role* = Qt::DisplayRole) const {#extraColumnData}

This method is called by [data](https://doc.qt.io/qt-6/qabstractproxymodel.html#data)() for extra columns. Reimplement this method to return the data for the extra columns.

`parent` the parent model index in the proxy model (only useful in tree models)

`row` the row number for which the proxy model is querying for data (child of `parent`, if set)

`extraColumn` the number of the extra column, starting at 0 (this doesn't require knowing how many columns the source model has)

`role` the role being queried

Returns the data at `row` and `extraColumn`

*See also* [setExtraColumnData](kextracolumnsproxymodel.md#setExtraColumnData)()

### void KExtraColumnsProxyModel::extraColumnDataChanged(const QModelIndex &*parent*, int *row*, int *extraColumn*, const QList\<int\> &*roles*) {#extraColumnDataChanged}

This method can be called by your derived class when the data in an extra column has changed. The use case is data that changes "by itself", unrelated to [setData](https://doc.qt.io/qt-6/qabstractproxymodel.html#setData)().

### int KExtraColumnsProxyModel::extraColumnForProxyColumn(int *proxyColumn*) const {#extraColumnForProxyColumn}

Returns the extra column number (0, 1, ...) for a given column number of the proxymodel. This basically means subtracting the amount of columns in the source model.

### int KExtraColumnsProxyModel::proxyColumnForExtraColumn(int *extraColumn*) const {#proxyColumnForExtraColumn}

Returns the proxy column number for a given extra column number (starting at 0). This basically means adding the amount of columns in the source model.

### void KExtraColumnsProxyModel::removeExtraColumn(int *idx*) {#removeExtraColumn}

Removes an extra column.

`idx` index of the extra column (starting from 0).

This does not emit any signals - do it in the initial setup phase

### \[virtual\] bool KExtraColumnsProxyModel::setExtraColumnData(const QModelIndex &*parent*, int *row*, int *extraColumn*, const QVariant &*data*, int *role* = Qt::EditRole) {#setExtraColumnData}

This method is called by [setData](https://doc.qt.io/qt-6/qabstractproxymodel.html#setData)() for extra columns. Reimplement this method to set the data for the extra columns, if editing is supported. Remember to call [extraColumnDataChanged](kextracolumnsproxymodel.md#extraColumnDataChanged)() after changing the data storage. The default implementation returns false.

*See also* [extraColumnData](kextracolumnsproxymodel.md#extraColumnData)()
