---
title: "KViewStateMaintainerBase Class"
description: "Large set of desktop widgets."
---

# KViewStateMaintainerBase Class

Large set of desktop widgets. [More...](#details)

- **Header:** `#include <KViewStateMaintainerBase>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kviewstatemaintainerbase-members.md)

## Public Functions

- [KViewStateMaintainerBase(QObject \*parent = nullptr)](#KViewStateMaintainerBase)
- [void restoreState()](#restoreState)
- [void saveState()](#saveState)
- [QItemSelectionModel \*selectionModel() const](#selectionModel)
- [void setSelectionModel(QItemSelectionModel \*selectionModel)](#setSelectionModel)
- [void setView(QAbstractItemView \*view)](#setView)
- [QAbstractItemView \*view() const](#view)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### KViewStateMaintainerBase::KViewStateMaintainerBase(QObject \**parent* = nullptr) {#KViewStateMaintainerBase}

### \[pure virtual\] void KViewStateMaintainerBase::restoreState() {#restoreState}

### \[pure virtual\] void KViewStateMaintainerBase::saveState() {#saveState}

### QItemSelectionModel \*KViewStateMaintainerBase::selectionModel() const {#selectionModel}

*See also* [setSelectionModel](kviewstatemaintainerbase.md#setSelectionModel)()

### void KViewStateMaintainerBase::setSelectionModel(QItemSelectionModel \**selectionModel*) {#setSelectionModel}

*See also* [selectionModel](kviewstatemaintainerbase.md#selectionModel)()

### void KViewStateMaintainerBase::setView(QAbstractItemView \**view*) {#setView}

*See also* [view](kviewstatemaintainerbase.md#view)()

### QAbstractItemView \*KViewStateMaintainerBase::view() const {#view}

*See also* [setView](kviewstatemaintainerbase.md#setView)()
