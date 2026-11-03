---
title: "KSplitterCollapserButton Class"
description: "A button which appears on the side of a splitter handle and allows easy collapsing of the widget on the opposite side."
---

# KSplitterCollapserButton Class

A button which appears on the side of a splitter handle and allows easy collapsing of the widget on the opposite side. [More...](#details)

- **Header:** `#include <KSplitterCollapserButton>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QToolButton](https://doc.qt.io/qt-6/qtoolbutton.html)

[List of all members, including inherited members](ksplittercollapserbutton-members.md)

## Public Functions

- [KSplitterCollapserButton(QWidget \*childWidget, QSplitter \*splitter)](#KSplitterCollapserButton)
- [bool isWidgetCollapsed() const](#isWidgetCollapsed)

## Public Slots

- [void collapse()](#collapse)
- [void restore()](#restore)
- [void setCollapsed(bool collapsed)](#setCollapsed)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KSplitterCollapserButton::KSplitterCollapserButton(QWidget \**childWidget*, QSplitter \**splitter*) {#KSplitterCollapserButton}

[KSplitterCollapserButton](ksplittercollapserbutton.md) create a splitter collapser

`childWidget` the widget, child of the splitter, whose size is controlled by this collapser

`splitter` the splitter which this collapser should be associated with.

### \[slot\] void KSplitterCollapserButton::collapse() {#collapse}

This function collapses the splitter if splitter is not collapsed.

### bool KSplitterCollapserButton::isWidgetCollapsed() const {#isWidgetCollapsed}

Returns `true` if splitter is collapsed.

### \[slot\] void KSplitterCollapserButton::restore() {#restore}

Call this function to restore previous splitter position.

### \[slot\] void KSplitterCollapserButton::setCollapsed(bool *collapsed*) {#setCollapsed}

This function allows to collapse or not the splitter.

`collapsed` if the splitter should be collapsed
