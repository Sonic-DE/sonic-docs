---
title: "KBreadcrumbSelectionModel Class"
description: "Selects the parents of selected items to create breadcrumbs."
---

# KBreadcrumbSelectionModel Class

Selects the parents of selected items to create breadcrumbs. [More...](#details)

- **Header:** `#include <KBreadcrumbSelectionModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ItemModels)`  
  `target_link_libraries(mytarget PRIVATE KF6::ItemModels)`
- **Inherits:** [QItemSelectionModel](https://doc.qt.io/qt-6/qitemselectionmodel.html)

[List of all members, including inherited members](kbreadcrumbselectionmodel-members.md)

## Public Types

- [enum KBreadcrumbSelectionModel::BreadcrumbTarget](#BreadcrumbTarget-enum)

## Public Functions

- [KBreadcrumbSelectionModel(QItemSelectionModel \*selectionModel, QObject \*parent = nullptr)](#KBreadcrumbSelectionModel)
- [KBreadcrumbSelectionModel(QItemSelectionModel \*selectionModel, KBreadcrumbSelectionModel::BreadcrumbTarget target, QObject \*parent = nullptr)](#KBreadcrumbSelectionModel-1)
- [int breadcrumbLength() const](#breadcrumbLength)
- [bool isActualSelectionIncluded() const](#isActualSelectionIncluded)
- [void setActualSelectionIncluded(bool isActualSelectionIncluded)](#setActualSelectionIncluded)
- [void setBreadcrumbLength(int breadcrumbLength)](#setBreadcrumbLength)

## Detailed Description {#details}

For example, if the tree is

```cpp
- A
- B
- - C
- - D
- - - E
- - - - F
```

and E is selected, the selection can contain

```cpp
- B
- D
```

or

```cpp
- B
- D
- E
```

if [isActualSelectionIncluded](kbreadcrumbselectionmodel.md#isActualSelectionIncluded) is true.

The depth of the selection may also be set. For example if the [breadcrumbLength](kbreadcrumbselectionmodel.md#breadcrumbLength) is 1:

```cpp
- D
- E
```

And if [breadcrumbLength](kbreadcrumbselectionmodel.md#breadcrumbLength) is 2:

```cpp
- B
- D
- E
```

A KBreadcrumbsSelectionModel with a [breadcrumbLength](kbreadcrumbselectionmodel.md#breadcrumbLength) of 0 and including the actual selection is the same as a [KSelectionProxyModel](kselectionproxymodel.md) in the KSelectionProxyModel::ExactSelection configuration.

```cpp
view1->setModel(rootModel);

QItemSelectionModel *breadcrumbSelectionModel = new QItemSelectionModel(rootModel, this);

KBreadcrumbSelectionModel *breadcrumbProxySelector = new KBreadcrumbSelectionModel(breadcrumbSelectionModel, rootModel, this);

view1->setSelectionModel(breadcrumbProxySelector);

KSelectionProxyModel *breadcrumbSelectionProxyModel = new KSelectionProxyModel( breadcrumbSelectionModel, this);
breadcrumbSelectionProxyModel->setSourceModel( rootModel );
breadcrumbSelectionProxyModel->setFilterBehavior( KSelectionProxyModel::ExactSelection );

view2->setModel(breadcrumbSelectionProxyModel);
```

This can work in two directions. One option is for a single selection in the [KBreadcrumbSelectionModel](kbreadcrumbselectionmodel.md) to invoke the breadcrumb selection in its constructor argument.

The other is for a selection in the itemselectionmodel in the constructor argument to cause a breadcrumb selection in this.

## Member Type Documentation {#member-type-documentation}

### enum KBreadcrumbSelectionModel::BreadcrumbTarget {#BreadcrumbTarget-enum}

| Constant |   |
| --- | --- |
| `KBreadcrumbSelectionModel::MakeBreadcrumbSelectionInOther` | `0` |
| `KBreadcrumbSelectionModel::MakeBreadcrumbSelectionInSelf` | `1` |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KBreadcrumbSelectionModel::KBreadcrumbSelectionModel(QItemSelectionModel \**selectionModel*, QObject \**parent* = nullptr) {#KBreadcrumbSelectionModel}

### KBreadcrumbSelectionModel::KBreadcrumbSelectionModel(QItemSelectionModel \**selectionModel*, KBreadcrumbSelectionModel::BreadcrumbTarget *target*, QObject \**parent* = nullptr) {#KBreadcrumbSelectionModel-1}

### int KBreadcrumbSelectionModel::breadcrumbLength() const {#breadcrumbLength}

Returns the depth that the breadcrumb selection should go to.

*See also* [setBreadcrumbLength](kbreadcrumbselectionmodel.md#setBreadcrumbLength)()

### bool KBreadcrumbSelectionModel::isActualSelectionIncluded() const {#isActualSelectionIncluded}

Returns whether the actual selection in included in the proxy.

The default is true.

### void KBreadcrumbSelectionModel::setActualSelectionIncluded(bool *isActualSelectionIncluded*) {#setActualSelectionIncluded}

Set whether the actual selection in included in the proxy to `isActualSelectionIncluded`.

*See also* [isActualSelectionIncluded](kbreadcrumbselectionmodel.md#isActualSelectionIncluded)()

### void KBreadcrumbSelectionModel::setBreadcrumbLength(int *breadcrumbLength*) {#setBreadcrumbLength}

Sets the depth that the breadcrumb selection should go to.

If the `breadcrumbLength` is -1, all breadcrumbs are selected. The default is -1

*See also* [breadcrumbLength](kbreadcrumbselectionmodel.md#breadcrumbLength)()
