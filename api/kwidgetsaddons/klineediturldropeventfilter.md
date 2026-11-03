---
title: "KLineEditUrlDropEventFilter Class"
description: "This class provides an event filter that can be installed on a QLineEdit or a subclass of it (KLineEdit) to make it handle URL drop events so when a URL is dropped it replaces the existing content. This class was introduced in Qt 6.0."
---

# KLineEditUrlDropEventFilter Class

This class provides an event filter that can be installed on a [QLineEdit](https://doc.qt.io/qt-6/qlineedit.html) or a subclass of it (KLineEdit) to make it handle URL drop events so when a URL is dropped it replaces the existing content. This class was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <KLineEditUrlDropEventFilter>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](klineediturldropeventfilter-members.md)

## Public Functions

- [KLineEditUrlDropEventFilter(QObject \*parent = nullptr)](#KLineEditUrlDropEventFilter)

## Detailed Description {#details}

Porting from KF5 to KF6:

The class LineEditUrlDropEventFilter was renamed to [KLineEditUrlDropEventFilter](klineediturldropeventfilter.md).

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KLineEditUrlDropEventFilter::KLineEditUrlDropEventFilter(QObject \**parent* = nullptr) {#KLineEditUrlDropEventFilter}
