---
title: "KLinkItemSelectionModel Class"
description: "Makes it possible to share a selection in multiple views which do not have the same source model."
---

# KLinkItemSelectionModel Class

Makes it possible to share a selection in multiple views which do not have the same source model. [More...](#details)

- **Header:** `#include <KLinkItemSelectionModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ItemModels)`  
  `target_link_libraries(mytarget PRIVATE KF6::ItemModels)`
- **Inherits:** [QItemSelectionModel](https://doc.qt.io/qt-6/qitemselectionmodel.html)

[List of all members, including inherited members](klinkitemselectionmodel-members.md)

## Properties

- [linkedItemSelectionModel : QItemSelectionModel\*](#linkedItemSelectionModel-prop)

## Public Functions

- [KLinkItemSelectionModel(QObject \*parent = nullptr)](#KLinkItemSelectionModel)
- [KLinkItemSelectionModel(QAbstractItemModel \*targetModel, QItemSelectionModel \*linkedItemSelectionModel, QObject \*parent = nullptr)](#KLinkItemSelectionModel-1)

## Detailed Description {#details}

Although [multiple views can share the same QItemSelectionModel](https://doc.qt.io/qt-6/model-view-programming.html#handling-selections-of-items), the views then need to have the same source model.

If there is a proxy model between the model and one of the views, or different proxy models in each, this class makes it possible to share the selection between the views.

```cpp
QAbstractItemModel *model = getModel();

QSortFilterProxyModel *proxy = new QSortFilterProxyModel();
proxy->setSourceModel(model);

QTreeView *view1 = new QTreeView(splitter);
view1->setModel(model);

KLinkItemSelectionModel *view2SelectionModel = new KLinkItemSelectionModel( proxy, view1->selectionModel());

QTreeView *view2 = new QTreeView(splitter);
// Note that the QAbstractItemModel passed to KLinkItemSelectionModel must be the same as what is used in the view
view2->setModel(proxy);
view2->setSelectionModel( view2SelectionModel );
```

```cpp
QAbstractItemModel *model = getModel();

QSortFilterProxyModel *proxy1 = new QSortFilterProxyModel();
proxy1->setSourceModel(model);
QSortFilterProxyModel *proxy2 = new QSortFilterProxyModel();
proxy2->setSourceModel(proxy1);
QSortFilterProxyModel *proxy3 = new QSortFilterProxyModel();
proxy3->setSourceModel(proxy2);

QTreeView *view1 = new QTreeView(splitter);
view1->setModel(proxy3);

QSortFilterProxyModel *proxy4 = new QSortFilterProxyModel();
proxy4->setSourceModel(model);
QSortFilterProxyModel *proxy5 = new QSortFilterProxyModel();
proxy5->setSourceModel(proxy4);

KLinkItemSelectionModel *view2SelectionModel = new KLinkItemSelectionModel( proxy5, view1->selectionModel());

QTreeView *view2 = new QTreeView(splitter);
// Note that the QAbstractItemModel passed to KLinkItemSelectionModel must be the same as what is used in the view
view2->setModel(proxy5);
view2->setSelectionModel( view2SelectionModel );
```

See also [kitemmodels: tests/proxymodeltestapp/proxyitemselectionwidget.cpp](https://commits.kde.org/kitemmodels?path=tests/proxymodeltestapp/proxyitemselectionwidget.cpp).

## Property Documentation {#property-documentation}

### linkedItemSelectionModel : QItemSelectionModel\* {#linkedItemSelectionModel-prop}

**Access functions:**

- `QItemSelectionModel` \***linkedItemSelectionModel**() const
- `void` **setLinkedItemSelectionModel**(`QItemSelectionModel` \**selectionModel*)

**Notifier signal:**

- `void` **linkedItemSelectionModelChanged**()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KLinkItemSelectionModel::KLinkItemSelectionModel(QObject \**parent* = nullptr) {#KLinkItemSelectionModel}

### KLinkItemSelectionModel::KLinkItemSelectionModel(QAbstractItemModel \**targetModel*, QItemSelectionModel \**linkedItemSelectionModel*, QObject \**parent* = nullptr) {#KLinkItemSelectionModel-1}

Constructor.
