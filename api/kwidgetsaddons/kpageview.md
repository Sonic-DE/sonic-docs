---
title: "KPageView Class"
description: "A base class which can handle multiple pages."
---

# KPageView Class

A base class which can handle multiple pages. [More...](#details)

- **Header:** `#include <KPageView>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)
- **Inherited By:** [KPageWidget](kpagewidget.md)

[List of all members, including inherited members](kpageview-members.md)

## Public Types

- [enum KPageView::FaceType](#FaceType-enum)

## Properties

- [faceType : FaceType](#faceType-prop)
- [pageFooter : QWidget\*](#pageFooter-prop)
- [pageHeader : QWidget\*](#pageHeader-prop)

## Public Functions

- [KPageView(QWidget \*parent = nullptr)](#KPageView)
- [QModelIndex currentPage() const](#currentPage)
- [KPageView::FaceType faceType() const](#faceType)
- [QAbstractItemDelegate \*itemDelegate() const](#itemDelegate)
- [QAbstractItemModel \*model() const](#model)
- [QWidget \*pageFooter() const](#pageFooter)
- [QWidget \*pageHeader() const](#pageHeader)
- [void setCurrentPage(const QModelIndex &index)](#setCurrentPage)
- [void setDefaultWidget(QWidget \*widget)](#setDefaultWidget)
- [void setFaceType(KPageView::FaceType faceType)](#setFaceType)
- [void setItemDelegate(QAbstractItemDelegate \*delegate)](#setItemDelegate)
- [void setModel(QAbstractItemModel \*model)](#setModel)
- [void setPageFooter(QWidget \*footer)](#setPageFooter)
- [void setPageHeader(QWidget \*header)](#setPageHeader)

## Signals

- [void currentPageChanged(const QModelIndex &current, const QModelIndex &previous)](#currentPageChanged)

## Protected Functions

- [QAbstractItemView \*createView()](#createView)
- [bool showPageHeader() const](#showPageHeader)
- [Qt::Alignment viewPosition() const](#viewPosition)

## Detailed Description {#details}

This class provides a widget base class which handles multiple pages and allows the user to switch between these pages in different ways.

Currently, Auto, Plain, List, Tree, [FlatList](kpageview.md#FaceType-enum) and Tabbed face types are available (cmp. [KPageWidget](kpagewidget.md)).

Example:

```cpp
KPageModel *model = new MyPageModel();

auto view = new KPageView(this);
view->setModel(model);

view->setFaceType(KPageView::List);
```

## Member Type Documentation {#member-type-documentation}

### enum KPageView::FaceType {#FaceType-enum}

This enum is used to decide which type of navigation view shall be used in the page view.

| Constant | Value | Description |
| --- | --- | --- |
| `KPageView::Auto` | `0` | Depending on the number of pages in the model, the Plain (one page), the List (several pages) the Tree face (nested pages) will be used. This is the default face type. |
| `KPageView::Plain` | `1` | No navigation view will be visible and only the first page of the model will be shown. |
| `KPageView::List` | `2` | An icon list is used as navigation view |
| `KPageView::Tree` | `3` | A tree list is used as navigation view |
| `KPageView::Tabbed` | `4` | A tab widget is used as navigation view |
| `KPageView::FlatList` | `5` | A flat list with small icons is used as navigation view |

## Property Documentation {#property-documentation}

### faceType : FaceType {#faceType-prop}

**Access functions:**

- `KPageView::FaceType` **[faceType](kpageview.md#faceType)**() const
- `void` **[setFaceType](kpageview.md#setFaceType)**(`KPageView::FaceType` *faceType*)

### pageFooter : QWidget\* {#pageFooter-prop}

**Access functions:**

- `QWidget` \***[pageFooter](kpageview.md#pageFooter)**() const
- `void` **[setPageFooter](kpageview.md#setPageFooter)**(`QWidget` \**footer*)

### pageHeader : QWidget\* {#pageHeader-prop}

**Access functions:**

- `QWidget` \***[pageHeader](kpageview.md#pageHeader)**() const
- `void` **[setPageHeader](kpageview.md#setPageHeader)**(`QWidget` \**header*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KPageView::KPageView(QWidget \**parent* = nullptr) {#KPageView}

Creates a page view with given parent.

### \[virtual protected\] QAbstractItemView \*KPageView::createView() {#createView}

Returns the navigation view, depending on the current face type.

This method can be reimplemented to provide custom navigation views.

### QModelIndex KPageView::currentPage() const {#currentPage}

Returns the index for the current page or an invalid index if no current page exists.

*See also* [setCurrentPage](kpageview.md#setCurrentPage)()

### \[signal\] void KPageView::currentPageChanged(const QModelIndex &*current*, const QModelIndex &*previous*) {#currentPageChanged}

This signal is emitted whenever the current page changes. The previous page index is replaced by the current index.

### KPageView::FaceType KPageView::faceType() const {#faceType}

Returns the face type of the page view.

> **Note:** Getter function for property [faceType](kpageview.md#faceType-prop).

*See also* [setFaceType](kpageview.md#setFaceType)()

### QAbstractItemDelegate \*KPageView::itemDelegate() const {#itemDelegate}

Returns the item delegate of the page view.

*See also* [setItemDelegate](kpageview.md#setItemDelegate)()

### QAbstractItemModel \*KPageView::model() const {#model}

Returns the model of the page view.

*See also* [setModel](kpageview.md#setModel)()

### QWidget \*KPageView::pageFooter() const {#pageFooter}

Widget of the footer for this page view

> **Note:** Getter function for property [pageFooter](kpageview.md#pageFooter-prop).

*See also* [setPageFooter](kpageview.md#setPageFooter)()

### QWidget \*KPageView::pageHeader() const {#pageHeader}

Widget of the header for this page view

> **Note:** Getter function for property [pageHeader](kpageview.md#pageHeader-prop).

*See also* [setPageHeader](kpageview.md#setPageHeader)()

### void KPageView::setCurrentPage(const QModelIndex &*index*) {#setCurrentPage}

Sets the page with `index` to be the current page and emits the signal [currentPageChanged](kpageview.md#currentPageChanged).

*See also* [currentPage](kpageview.md#currentPage)()

### void KPageView::setDefaultWidget(QWidget \**widget*) {#setDefaultWidget}

Sets the `widget` which will be shown when a page is selected that has no own widget set.

### void KPageView::setFaceType(KPageView::FaceType *faceType*) {#setFaceType}

Sets the face type of the page view.

> **Note:** Setter function for property [faceType](kpageview.md#faceType-prop).

*See also* [faceType](kpageview.md#faceType)()

### void KPageView::setItemDelegate(QAbstractItemDelegate \**delegate*) {#setItemDelegate}

Sets the item `delegate` which can be used customize the page view.

*See also* [itemDelegate](kpageview.md#itemDelegate)()

### void KPageView::setModel(QAbstractItemModel \**model*) {#setModel}

Sets the `model` of the page view.

The model has to provide data for the roles defined in [KPageModel::Role](kpagemodel.md#Role-enum).

*See also* [model](kpageview.md#model)()

### void KPageView::setPageFooter(QWidget \**footer*) {#setPageFooter}

Set a widget as the footer for this Page view

> **Note:** Setter function for property [pageFooter](kpageview.md#pageFooter-prop).

*See also* [pageFooter](kpageview.md#pageFooter)()

### void KPageView::setPageHeader(QWidget \**header*) {#setPageHeader}

Set a widget as the header for this Page view It will replace the standard page title

> **Note:** Setter function for property [pageHeader](kpageview.md#pageHeader-prop).

*See also* [pageHeader](kpageview.md#pageHeader)()

### \[virtual protected\] bool KPageView::showPageHeader() const {#showPageHeader}

Returns whether the page header should be visible.

This method can be reimplemented for adapting custom views.

### \[virtual protected\] Qt::Alignment KPageView::viewPosition() const {#viewPosition}

Returns the position where the navigation view should be located according to the page stack.

This method can be reimplemented for adapting custom views.
