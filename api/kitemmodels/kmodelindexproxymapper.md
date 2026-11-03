---
title: "KModelIndexProxyMapper Class"
description: "This class facilitates easy mapping of indexes and selections through proxy models."
---

# KModelIndexProxyMapper Class

This class facilitates easy mapping of indexes and selections through proxy models. [More...](#details)

- **Header:** `#include <KModelIndexProxyMapper>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ItemModels)`  
  `target_link_libraries(mytarget PRIVATE KF6::ItemModels)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kmodelindexproxymapper-members.md)

## Properties

- [\[read-only\] isConnected : bool](#isConnected-prop)

## Public Functions

- [KModelIndexProxyMapper(const QAbstractItemModel \*leftModel, const QAbstractItemModel \*rightModel, QObject \*parent = nullptr)](#KModelIndexProxyMapper)
- [QModelIndex mapLeftToRight(const QModelIndex &index) const](#mapLeftToRight)
- [QModelIndex mapRightToLeft(const QModelIndex &index) const](#mapRightToLeft)
- [QItemSelection mapSelectionLeftToRight(const QItemSelection &selection) const](#mapSelectionLeftToRight)
- [QItemSelection mapSelectionRightToLeft(const QItemSelection &selection) const](#mapSelectionRightToLeft)

## Detailed Description {#details}

In a complex system of proxy models there can be a need to map indexes and selections between them, and sometimes to do so without knowledge of the path from one model to another.

For example,

```cpp
Root model
      |
    /    \
Proxy 1   Proxy 3
   |       |
Proxy 2   Proxy 4
```

If there is a need to map indexes between proxy 2 and proxy 4, a [KModelIndexProxyMapper](kmodelindexproxymapper.md) can be created to facilitate mapping of indexes between them.

```cpp
m_indexMapper = new KModelIndexProxyMapper(proxy2, proxy4, this);

...

 const QModelIndex proxy4Index = m_mapLeftToRight(proxy2->index(0, 0));
 Q_ASSERT(proxy4Index.model() == proxy4);
```

Note that the aim is to achieve black box connections so that there is no need for application code to know the structure of proxy models in the path between left and right and attempt to manually map them.

```cpp
Root model
      |
---------------
|  Black Box  |
---------------
   |       |
Proxy 2   Proxy 4
```

The [isConnected](kmodelindexproxymapper.md#isConnected-prop) property indicates whether there is a path from the left side to the right side.

## Property Documentation {#property-documentation}

### \[read-only\] isConnected : bool {#isConnected-prop}

Indicates whether there is a chain that can be followed from leftModel to rightModel.

This value can change if the sourceModel of an intermediate proxy is changed.

**Access functions:**

- `bool` **isConnected**() const

**Notifier signal:**

- `void` **isConnectedChanged**()

## Member Function Documentation {#member-function-documentation}

### KModelIndexProxyMapper::KModelIndexProxyMapper(const QAbstractItemModel \**leftModel*, const QAbstractItemModel \**rightModel*, QObject \**parent* = nullptr) {#KModelIndexProxyMapper}

Constructor

### QModelIndex KModelIndexProxyMapper::mapLeftToRight(const QModelIndex &*index*) const {#mapLeftToRight}

Maps the `index` from the left model to the right model.

### QModelIndex KModelIndexProxyMapper::mapRightToLeft(const QModelIndex &*index*) const {#mapRightToLeft}

Maps the `index` from the right model to the left model.

### QItemSelection KModelIndexProxyMapper::mapSelectionLeftToRight(const QItemSelection &*selection*) const {#mapSelectionLeftToRight}

Maps the `selection` from the left model to the right model.

### QItemSelection KModelIndexProxyMapper::mapSelectionRightToLeft(const QItemSelection &*selection*) const {#mapSelectionRightToLeft}

Maps the `selection` from the right model to the left model.
