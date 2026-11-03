---
title: "KTreeWidgetSearchLineWidget Class"
description: "Creates a widget featuring a KTreeWidgetSearchLine, a label with the text \"Search\" and a button to clear the search."
---

# KTreeWidgetSearchLineWidget Class

Creates a widget featuring a [KTreeWidgetSearchLine](ktreewidgetsearchline.md), a label with the text "Search" and a button to clear the search. [More...](#details)

- **Header:** `#include <KTreeWidgetSearchLineWidget>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ItemViews)`  
  `target_link_libraries(mytarget PRIVATE KF6::ItemViews)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](ktreewidgetsearchlinewidget-members.md)

## Public Functions

- [KTreeWidgetSearchLineWidget(QWidget \*parent = nullptr, QTreeWidget \*treeWidget = nullptr)](#KTreeWidgetSearchLineWidget)
- [KTreeWidgetSearchLine \*searchLine() const](#searchLine)

## Public Slots

- [void createWidgets()](#createWidgets)

## Protected Functions

- [KTreeWidgetSearchLine \*createSearchLine(QTreeWidget \*treeWidget) const](#createSearchLine)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KTreeWidgetSearchLineWidget::KTreeWidgetSearchLineWidget(QWidget \**parent* = nullptr, QTreeWidget \**treeWidget* = nullptr) {#KTreeWidgetSearchLineWidget}

Creates a [KTreeWidgetSearchLineWidget](ktreewidgetsearchlinewidget.md) for `treeWidget` with `parent` as the parent.

### \[virtual protected\] KTreeWidgetSearchLine \*KTreeWidgetSearchLineWidget::createSearchLine(QTreeWidget \**treeWidget*) const {#createSearchLine}

Creates the search line. This can be useful to reimplement in cases where a [KTreeWidgetSearchLine](ktreewidgetsearchline.md) subclass is used.

It is const because it is be called from [searchLine](ktreewidgetsearchlinewidget.md#searchLine)(), which to the user doesn't conceptually alter the widget.

### \[virtual protected slot\] void KTreeWidgetSearchLineWidget::createWidgets() {#createWidgets}

Creates the widgets inside of the widget. This is called from the constructor via a single shot timer so that it it guaranteed to run after construction is complete. This makes it suitable for overriding in subclasses.

### KTreeWidgetSearchLine \*KTreeWidgetSearchLineWidget::searchLine() const {#searchLine}

Returns a pointer to the search line.
