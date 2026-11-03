---
title: "KDescendantsProxyModel Class"
description: "Proxy Model for restructuring a Tree into a list."
---

# KDescendantsProxyModel Class

Proxy Model for restructuring a Tree into a list. [More...](#details)

- **Header:** `#include <KDescendantsProxyModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ItemModels)`  
  `target_link_libraries(mytarget PRIVATE KF6::ItemModels)`
- **Inherits:** [QAbstractProxyModel](https://doc.qt.io/qt-6/qabstractproxymodel.html)

[List of all members, including inherited members](kdescendantsproxymodel-members.md)

## Properties

- [ancestorSeparator : QString](#ancestorSeparator-prop)
- [displayAncestorData : bool](#displayAncestorData-prop)
- [expandsByDefault : bool](#expandsByDefault-prop)
- [model : QAbstractItemModel\*](#model-prop)

## Public Functions

- [KDescendantsProxyModel(QObject \*parent = nullptr)](#KDescendantsProxyModel)
- [~KDescendantsProxyModel()](#dtor.KDescendantsProxyModel)
- [QString ancestorSeparator() const](#ancestorSeparator)
- [void collapseSourceIndex(const QModelIndex &sourceIndex)](#collapseSourceIndex)
- [bool displayAncestorData() const](#displayAncestorData)
- [void expandSourceIndex(const QModelIndex &sourceIndex)](#expandSourceIndex)
- [bool expandsByDefault() const](#expandsByDefault)
- [bool isSourceIndexExpanded(const QModelIndex &sourceIndex) const](#isSourceIndexExpanded)
- [bool isSourceIndexVisible(const QModelIndex &sourceIndex) const](#isSourceIndexVisible)
- [QModelIndexList match(const QModelIndex &start, int role, const QVariant &value, int hits = 1, Qt::MatchFlags flags = MatchFlags(Qt::MatchStartsWith \| Qt::MatchWrap)) const](#match)
- [void setAncestorSeparator(const QString &separator)](#setAncestorSeparator)
- [void setDisplayAncestorData(bool display)](#setDisplayAncestorData)
- [void setExpandsByDefault(bool expand)](#setExpandsByDefault)
- [void setSourceModel(QAbstractItemModel \*model)](#setSourceModel)

## Detailed Description {#details}

A [KDescendantsProxyModel](kdescendantsproxymodel.md) may be used to alter how the items in the tree are presented.

Given a model which is represented as a tree:

The [KDescendantsProxyModel](kdescendantsproxymodel.md) restructures the sourceModel to represent it as a flat list.

```cpp
// ... Create an entityTreeModel
KDescendantsProxyModel *descProxy = new KDescendantsProxyModel(this);
descProxy->setSourceModel(entityTree);
view->setModel(descProxy);
```

KDescendantEntitiesProxyModel can also display the ancestors of the index in the source model as part of its display.

```cpp
// ... Create an entityTreeModel
KDescendantsProxyModel *descProxy = new KDescendantsProxyModel(this);
descProxy->setSourceModel(entityTree);

// #### This is new
descProxy->setDisplayAncestorData(true);
descProxy->setAncestorSeparator(QString(" / "));

view->setModel(descProxy);
```

## Property Documentation {#property-documentation}

### ancestorSeparator : QString {#ancestorSeparator-prop}

**Access functions:**

- `QString` **[ancestorSeparator](kdescendantsproxymodel.md#ancestorSeparator)**() const
- `void` **[setAncestorSeparator](kdescendantsproxymodel.md#setAncestorSeparator)**(const `QString` &*separator*)

**Notifier signal:**

- `void` **ancestorSeparatorChanged**()

### displayAncestorData : bool {#displayAncestorData-prop}

**Access functions:**

- `bool` **[displayAncestorData](kdescendantsproxymodel.md#displayAncestorData)**() const
- `void` **[setDisplayAncestorData](kdescendantsproxymodel.md#setDisplayAncestorData)**(`bool` *display*)

**Notifier signal:**

- `void` **displayAncestorDataChanged**()

### expandsByDefault : bool {#expandsByDefault-prop}

If true, all the nodes in the whole tree will be expanded upon loading and all items of the source model will be shown in the proxy. The default value is true.

**Access functions:**

- `bool` **[expandsByDefault](kdescendantsproxymodel.md#expandsByDefault)**() const
- `void` **[setExpandsByDefault](kdescendantsproxymodel.md#setExpandsByDefault)**(`bool` *expand*)

**Notifier signal:**

- `void` **expandsByDefaultChanged**(`bool` *expands*)

### model : QAbstractItemModel\* {#model-prop}

**Access functions:**

- virtual `void` **[setSourceModel](kdescendantsproxymodel.md#setSourceModel)**(`QAbstractItemModel` \**model*) override

**Notifier signal:**

- `void` **sourceModelChanged**()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KDescendantsProxyModel::KDescendantsProxyModel(QObject \**parent* = nullptr) {#KDescendantsProxyModel}

Creates a new descendant entities proxy model.

`parent` The parent object.

### \[override virtual noexcept\] KDescendantsProxyModel::~KDescendantsProxyModel() {#dtor.KDescendantsProxyModel}

Destroys the descendant entities proxy model.

### QString KDescendantsProxyModel::ancestorSeparator() const {#ancestorSeparator}

Separator used between data of ancestors.

> **Note:** Getter function for property [ancestorSeparator](kdescendantsproxymodel.md#ancestorSeparator-prop).

*See also* [setAncestorSeparator](kdescendantsproxymodel.md#setAncestorSeparator)()

### void KDescendantsProxyModel::collapseSourceIndex(const QModelIndex &*sourceIndex*) {#collapseSourceIndex}

Maps a source index as collapsed in the proxy, all its children will be hidden. `sourceIndex` an index of the source model.

### bool KDescendantsProxyModel::displayAncestorData() const {#displayAncestorData}

Whether ancestor data will be displayed.

> **Note:** Getter function for property [displayAncestorData](kdescendantsproxymodel.md#displayAncestorData-prop).

*See also* [setDisplayAncestorData](kdescendantsproxymodel.md#setDisplayAncestorData)()

### void KDescendantsProxyModel::expandSourceIndex(const QModelIndex &*sourceIndex*) {#expandSourceIndex}

Maps a source index as expanded in the proxy, all its children will become visible. `sourceIndex` an index of the source model.

### bool KDescendantsProxyModel::expandsByDefault() const {#expandsByDefault}

Returns true if all the tree nodes are expanded by default upon loading

> **Note:** Getter function for property [expandsByDefault](kdescendantsproxymodel.md#expandsByDefault-prop).

*See also* [setExpandsByDefault](kdescendantsproxymodel.md#setExpandsByDefault)()

### bool KDescendantsProxyModel::isSourceIndexExpanded(const QModelIndex &*sourceIndex*) const {#isSourceIndexExpanded}

Returns true if the source index is mapped in the proxy as expanded, therefore it will show its children

### bool KDescendantsProxyModel::isSourceIndexVisible(const QModelIndex &*sourceIndex*) const {#isSourceIndexVisible}

Returns true if the source index is visible in the proxy, meaning all its parent hierarchy is expanded.

### \[override virtual\] QModelIndexList KDescendantsProxyModel::match(const QModelIndex &*start*, int *role*, const QVariant &*value*, int *hits* = 1, Qt::MatchFlags *flags* = Qt::MatchFlags(Qt::MatchStartsWith \| Qt::MatchWrap)) const {#match}

Reimplements: [QAbstractItemModel::match(const QModelIndex &start, int role, const QVariant &value, int hits, Qt::MatchFlags flags) const](https://doc.qt.io/qt-6/qabstractitemmodel.html#match).

Reimplemented to match all descendants.

### void KDescendantsProxyModel::setAncestorSeparator(const QString &*separator*) {#setAncestorSeparator}

Sets the ancestor `separator` used between data of ancestors.

> **Note:** Setter function for property [ancestorSeparator](kdescendantsproxymodel.md#ancestorSeparator-prop).

*See also* [ancestorSeparator](kdescendantsproxymodel.md#ancestorSeparator)()

### void KDescendantsProxyModel::setDisplayAncestorData(bool *display*) {#setDisplayAncestorData}

Set whether to show ancestor data in the model. If `display` is true, then a source model which is displayed as

```cpp
-> "Item 0-0" (this is row-depth)
-> -> "Item 0-1"
-> -> "Item 1-1"
-> -> -> "Item 0-2"
-> -> -> "Item 1-2"
-> "Item 1-0"
```

will be displayed as

```cpp
-> *Item 0-0"
-> "Item 0-0 / Item 0-1"
-> "Item 0-0 / Item 1-1"
-> "Item 0-0 / Item 1-1 / Item 0-2"
-> "Item 0-0 / Item 1-1 / Item 1-2"
-> "Item 1-0"
```

If `display` is false, the proxy will show

```cpp
-> *Item 0-0"
-> "Item 0-1"
-> "Item 1-1"
-> "Item 0-2"
-> "Item 1-2"
-> "Item 1-0"
```

Default is false.

> **Note:** Setter function for property [displayAncestorData](kdescendantsproxymodel.md#displayAncestorData-prop).

*See also* [displayAncestorData](kdescendantsproxymodel.md#displayAncestorData)()

### void KDescendantsProxyModel::setExpandsByDefault(bool *expand*) {#setExpandsByDefault}

If true, all the nodes in the whole tree will be expanded upon loading (default) `expand` whether we want everything expanded upon load

> **Note:** Setter function for property [expandsByDefault](kdescendantsproxymodel.md#expandsByDefault-prop).

*See also* [expandsByDefault](kdescendantsproxymodel.md#expandsByDefault)()

### \[override virtual\] void KDescendantsProxyModel::setSourceModel(QAbstractItemModel \**model*) {#setSourceModel}

Reimplements: [QAbstractProxyModel::setSourceModel(QAbstractItemModel \*sourceModel)](https://doc.qt.io/qt-6/qabstractproxymodel.html#setSourceModel).

Sets the source `model` of the proxy.

> **Note:** Setter function for property [model](kdescendantsproxymodel.md#model-prop).
