---
title: "KPageWidget Class"
description: "Page widget with many layouts (faces)."
---

# KPageWidget Class

Page widget with many layouts (faces). [More...](#details)

- **Header:** `#include <KPageWidget>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [KPageView](kpageview.md)

[List of all members, including inherited members](kpagewidget-members.md)

## Public Functions

- [KPageWidget(QWidget \*parent = nullptr)](#KPageWidget)
- [void addPage(KPageWidgetItem \*item)](#addPage)
- [KPageWidgetItem \*addPage(QWidget \*widget, const QString &name)](#addPage-1)
- [void addSubPage(KPageWidgetItem \*parent, KPageWidgetItem \*item)](#addSubPage)
- [KPageWidgetItem \*addSubPage(KPageWidgetItem \*parent, QWidget \*widget, const QString &name)](#addSubPage-1)
- [KPageWidgetItem \*currentPage() const](#currentPage)
- [void insertPage(KPageWidgetItem \*before, KPageWidgetItem \*item)](#insertPage)
- [KPageWidgetItem \*insertPage(KPageWidgetItem \*before, QWidget \*widget, const QString &name)](#insertPage-1)
- [void removePage(KPageWidgetItem \*item)](#removePage)
- [void setCurrentPage(KPageWidgetItem \*item)](#setCurrentPage)

## Signals

- [void currentPageChanged(KPageWidgetItem \*current, KPageWidgetItem \*before)](#currentPageChanged)
- [void pageRemoved(KPageWidgetItem \*page)](#pageRemoved)
- [void pageToggled(KPageWidgetItem \*page, bool checked)](#pageToggled)

## Detailed Description {#details}

A [KPageView](kpageview.md) with hierarchical page model.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KPageWidget::KPageWidget(QWidget \**parent* = nullptr) {#KPageWidget}

Creates a new page widget.

`parent` The parent widget.

### void KPageWidget::addPage(KPageWidgetItem \**item*) {#addPage}

Adds a new top level page to the widget.

`item` The [KPageWidgetItem](kpagewidgetitem.md) which describes the page.

### KPageWidgetItem \*KPageWidget::addPage(QWidget \**widget*, const QString &*name*) {#addPage-1}

Adds a new top level page to the widget.

`widget` The widget of the page.

`name` The name which is displayed in the navigation view.

Returns The associated [KPageWidgetItem](kpagewidgetitem.md).

### void KPageWidget::addSubPage(KPageWidgetItem \**parent*, KPageWidgetItem \**item*) {#addSubPage}

Inserts a new sub page in the widget.

`parent` The new page will be insert as child of this [KPageWidgetItem](kpagewidgetitem.md).

`item` The [KPageWidgetItem](kpagewidgetitem.md) which describes the page.

### KPageWidgetItem \*KPageWidget::addSubPage(KPageWidgetItem \**parent*, QWidget \**widget*, const QString &*name*) {#addSubPage-1}

Inserts a new sub page in the widget.

`parent` The new page will be insert as child of this [KPageWidgetItem](kpagewidgetitem.md).

`widget` The widget of the page.

`name` The name which is displayed in the navigation view.

Returns the associated [KPageWidgetItem](kpagewidgetitem.md).

### KPageWidgetItem \*KPageWidget::currentPage() const {#currentPage}

Returns the [KPageWidgetItem](kpagewidgetitem.md) for the current page or a null pointer if there is no current page.

*See also* [setCurrentPage](kpagewidget.md#setCurrentPage)()

### \[signal\] void KPageWidget::currentPageChanged(KPageWidgetItem \**current*, KPageWidgetItem \**before*) {#currentPageChanged}

This signal is emitted whenever the current page has changed.

`current` The new current page or a null pointer if no current page is available.

`before` The page that was current before the new current page has changed.

### void KPageWidget::insertPage(KPageWidgetItem \**before*, KPageWidgetItem \**item*) {#insertPage}

Inserts a new page in the widget.

`before` The new page will be insert before this [KPageWidgetItem](kpagewidgetitem.md) on the same level in hierarchy.

`item` The [KPageWidgetItem](kpagewidgetitem.md) which describes the page.

### KPageWidgetItem \*KPageWidget::insertPage(KPageWidgetItem \**before*, QWidget \**widget*, const QString &*name*) {#insertPage-1}

Inserts a new page in the widget.

`before` The new page will be insert before this [KPageWidgetItem](kpagewidgetitem.md) on the same level in hierarchy.

`widget` The widget of the page.

`name` The name which is displayed in the navigation view.

Returns the associated [KPageWidgetItem](kpagewidgetitem.md).

### \[signal\] void KPageWidget::pageRemoved(KPageWidgetItem \**page*) {#pageRemoved}

This signal is emitted when a page is removed.

`page` The page which is removed

### \[signal\] void KPageWidget::pageToggled(KPageWidgetItem \**page*, bool *checked*) {#pageToggled}

This signal is emitted whenever a checkable page changes its state. `checked` is true when the `page` is checked, or false if the `page` is unchecked.

### void KPageWidget::removePage(KPageWidgetItem \**item*) {#removePage}

Removes the page associated with the given [KPageWidgetItem](kpagewidgetitem.md).

### void KPageWidget::setCurrentPage(KPageWidgetItem \**item*) {#setCurrentPage}

Sets the page which is associated with the given [KPageWidgetItem](kpagewidgetitem.md) to be the current page and emits the [currentPageChanged](kpagewidget.md#currentPageChanged)() signal.

*See also* [currentPage](kpagewidget.md#currentPage)()
