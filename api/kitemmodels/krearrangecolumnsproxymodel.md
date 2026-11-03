---
title: "KRearrangeColumnsProxyModel Class"
description: "This proxy shows specific columns from the source model, in any order."
---

# KRearrangeColumnsProxyModel Class

This proxy shows specific columns from the source model, in any order. [More...](#details)

- **Header:** `#include <KRearrangeColumnsProxyModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ItemModels)`  
  `target_link_libraries(mytarget PRIVATE KF6::ItemModels)`
- **Inherits:** [QIdentityProxyModel](https://doc.qt.io/qt-6/qidentityproxymodel.html)

[List of all members, including inherited members](krearrangecolumnsproxymodel-members.md)

## Public Functions

- [KRearrangeColumnsProxyModel(QObject \*parent = nullptr)](#KRearrangeColumnsProxyModel)
- [int proxyColumnForSourceColumn(int sourceColumn) const](#proxyColumnForSourceColumn)
- [void setSourceColumns(const QList\<int\> &columns)](#setSourceColumns)
- [int sourceColumnForProxyColumn(int proxyColumn) const](#sourceColumnForProxyColumn)

## Detailed Description {#details}

This allows to reorder columns, as well as not showing all of them.

The proxy supports source models that have a tree structure. It also supports editing, and propagating changes from the source model.

Showing the same source column more than once is not supported.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KRearrangeColumnsProxyModel::KRearrangeColumnsProxyModel(QObject \**parent* = nullptr) {#KRearrangeColumnsProxyModel}

Creates a [KRearrangeColumnsProxyModel](krearrangecolumnsproxymodel.md) proxy. Remember to call [setSourceModel](https://doc.qt.io/qt-6/qidentityproxymodel.html#setSourceModel)() afterwards.

### int KRearrangeColumnsProxyModel::proxyColumnForSourceColumn(int *sourceColumn*) const {#proxyColumnForSourceColumn}

Returns the proxy column for the given source column or -1 if the source column isn't shown in the proxy.

### void KRearrangeColumnsProxyModel::setSourceColumns(const QList\<int\> &*columns*) {#setSourceColumns}

Set the chosen source columns, in the desired order for the proxy columns columns\[proxyColumn=0\] is the source column to show in the first proxy column, etc.

Example: [QList](https://doc.qt.io/qt-6/qlist.html)\<int\>() \<\< 2 \<\< 1; This examples configures the proxy to hide column 0, show column 2 from the source model, then show column 1 from the source model.

### int KRearrangeColumnsProxyModel::sourceColumnForProxyColumn(int *proxyColumn*) const {#sourceColumnForProxyColumn}

Returns the source column for the given proxy column.
