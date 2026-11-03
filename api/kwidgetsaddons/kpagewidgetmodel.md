---
title: "KPageWidgetModel Class"
description: "This page model is used by KPageWidget to provide a hierarchical layout of pages."
---

# KPageWidgetModel Class

This page model is used by [KPageWidget](kpagewidget.md) to provide a hierarchical layout of pages. [More...](#details)

- **Header:** `#include <KPageWidgetModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [KPageModel](kpagemodel.md)

[List of all members, including inherited members](kpagewidgetmodel-members.md)

## Public Functions

- [KPageWidgetModel(QObject \*parent = nullptr)](#KPageWidgetModel)
- [~KPageWidgetModel()](#dtor.KPageWidgetModel)
- [void addPage(KPageWidgetItem \*item)](#addPage)
- [KPageWidgetItem \*addPage(QWidget \*widget, const QString &name)](#addPage-1)
- [void addSubPage(KPageWidgetItem \*parent, KPageWidgetItem \*item)](#addSubPage)
- [KPageWidgetItem \*addSubPage(KPageWidgetItem \*parent, QWidget \*widget, const QString &name)](#addSubPage-1)
- [QModelIndex index(const KPageWidgetItem \*item) const](#index)
- [void insertPage(KPageWidgetItem \*before, KPageWidgetItem \*item)](#insertPage)
- [KPageWidgetItem \*insertPage(KPageWidgetItem \*before, QWidget \*widget, const QString &name)](#insertPage-1)
- [KPageWidgetItem \*item(const QModelIndex &index) const](#item)
- [void removePage(KPageWidgetItem \*item)](#removePage)

## Signals

- [void toggled(KPageWidgetItem \*page, bool checked)](#toggled)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KPageWidgetModel::KPageWidgetModel(QObject \**parent* = nullptr) {#KPageWidgetModel}

Creates a new page widget model.

`parent` The parent object.

### \[override virtual noexcept\] KPageWidgetModel::~KPageWidgetModel() {#dtor.KPageWidgetModel}

Destroys the page widget model.

### void KPageWidgetModel::addPage(KPageWidgetItem \**item*) {#addPage}

Adds a new top level page to the model.

`item` The [KPageWidgetItem](kpagewidgetitem.md) which describes the page.

### KPageWidgetItem \*KPageWidgetModel::addPage(QWidget \**widget*, const QString &*name*) {#addPage-1}

Adds a new top level page to the model.

`widget` The widget of the page.

`name` The name which is displayed in the navigation view.

Returns the associated [KPageWidgetItem](kpagewidgetitem.md).

### void KPageWidgetModel::addSubPage(KPageWidgetItem \**parent*, KPageWidgetItem \**item*) {#addSubPage}

Inserts a new sub page in the model.

`parent` The new page will be insert as child of this [KPageWidgetItem](kpagewidgetitem.md).

`item` The [KPageWidgetItem](kpagewidgetitem.md) which describes the page.

### KPageWidgetItem \*KPageWidgetModel::addSubPage(KPageWidgetItem \**parent*, QWidget \**widget*, const QString &*name*) {#addSubPage-1}

Inserts a new sub page in the model.

`parent` The new page will be insert as child of this [KPageWidgetItem](kpagewidgetitem.md).

`widget` The widget of the page.

`name` The name which is displayed in the navigation view.

Returns the associated [KPageWidgetItem](kpagewidgetitem.md).

### QModelIndex KPageWidgetModel::index(const KPageWidgetItem \**item*) const {#index}

Returns the index for a given [KPageWidgetItem](kpagewidgetitem.md). The index is invalid if the item can't be found in the model.

### void KPageWidgetModel::insertPage(KPageWidgetItem \**before*, KPageWidgetItem \**item*) {#insertPage}

Inserts a new page in the model.

`before` The new page will be insert before this [KPageWidgetItem](kpagewidgetitem.md) on the same level in hierarchy.

`item` The [KPageWidgetItem](kpagewidgetitem.md) which describes the page.

### KPageWidgetItem \*KPageWidgetModel::insertPage(KPageWidgetItem \**before*, QWidget \**widget*, const QString &*name*) {#insertPage-1}

Inserts a new page in the model.

`before` The new page will be insert before this [KPageWidgetItem](kpagewidgetitem.md) on the same level in hierarchy. `widget` The widget of the page.

`name` The name which is displayed in the navigation view.

Returns the associated [KPageWidgetItem](kpagewidgetitem.md).

### KPageWidgetItem \*KPageWidgetModel::item(const QModelIndex &*index*) const {#item}

Returns the [KPageWidgetItem](kpagewidgetitem.md) for a given index or a null pointer if the index is invalid.

### void KPageWidgetModel::removePage(KPageWidgetItem \**item*) {#removePage}

Removes the page associated with the given [KPageWidgetItem](kpagewidgetitem.md).

### \[signal\] void KPageWidgetModel::toggled(KPageWidgetItem \**page*, bool *checked*) {#toggled}

This signal is emitted whenever a checkable page changes its state. `checked` is true when the `page` is checked, or false if the `page` is unchecked.
