---
title: "KCheckableProxyModel Class"
description: "Adds a checkable capability to a source model."
---

# KCheckableProxyModel Class

Adds a checkable capability to a source model. [More...](#details)

- **Header:** `#include <KCheckableProxyModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ItemModels)`  
  `target_link_libraries(mytarget PRIVATE KF6::ItemModels)`
- **Inherits:** [QIdentityProxyModel](https://doc.qt.io/qt-6/qidentityproxymodel.html)

[List of all members, including inherited members](kcheckableproxymodel-members.md)

## Public Functions

- [KCheckableProxyModel(QObject \*parent = nullptr)](#KCheckableProxyModel)
- [QItemSelectionModel \*selectionModel() const](#selectionModel)
- [void setSelectionModel(QItemSelectionModel \*itemSelectionModel)](#setSelectionModel)

## Protected Functions

- [bool select(const QItemSelection &selection, QItemSelectionModel::SelectionFlags command)](#select)

## Detailed Description {#details}

Items is standard Qt views such as [QTreeView](https://doc.qt.io/qt-6/qtreeview.html) and [QListView](https://doc.qt.io/qt-6/qlistview.html) can have a checkable capability and draw checkboxes. Adding such a capability requires specific implementations of the [data](https://doc.qt.io/qt-6/qabstractproxymodel.html#data)() and [flags](https://doc.qt.io/qt-6/qabstractproxymodel.html#flags)() virtual methods. This class implements those methods generically so that it is not necessary to implement them in your model.

This can be combined with a [KSelectionProxyModel](kselectionproxymodel.md) showing the items currently selected

```cpp
QItemSelectionModel *checkModel = new QItemSelectionModel(rootModel, this);
KCheckableProxyModel *checkable = new KCheckableProxyModel(this);
checkable->setSourceModel(rootModel);
checkable->setSelectionModel(checkModel);

QTreeView *tree1 = new QTreeView(vSplitter);
tree1->setModel(checkable);
tree1->expandAll();

KSelectionProxyModel *selectionProxy = new KSelectionProxyModel(checkModel, this);
selectionProxy->setFilterBehavior(KSelectionProxyModel::ExactSelection);
selectionProxy->setSourceModel(rootModel);

QTreeView *tree2 = new QTreeView(vSplitter);
tree2->setModel(selectionProxy);
```

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KCheckableProxyModel::KCheckableProxyModel(QObject \**parent* = nullptr) {#KCheckableProxyModel}

### \[virtual protected\] bool KCheckableProxyModel::select(const QItemSelection &*selection*, QItemSelectionModel::SelectionFlags *command*) {#select}

### QItemSelectionModel \*KCheckableProxyModel::selectionModel() const {#selectionModel}

*See also* [setSelectionModel](kcheckableproxymodel.md#setSelectionModel)()

### void KCheckableProxyModel::setSelectionModel(QItemSelectionModel \**itemSelectionModel*) {#setSelectionModel}

*See also* [selectionModel](kcheckableproxymodel.md#selectionModel)()
