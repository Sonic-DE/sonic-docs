---
title: "KAbstractViewAdapter Class"
description: "Interface used by KFilePreviewGenerator to generate previews for files."
---

# KAbstractViewAdapter Class

Interface used by [KFilePreviewGenerator](kfilepreviewgenerator.md) to generate previews for files. [More...](#details)

- **Header:** `#include <KAbstractViewAdapter>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOFileWidgets)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kabstractviewadapter-members.md)

## Public Types

- [enum KAbstractViewAdapter::Signal](#Signal-enum)

## Public Functions

- [KAbstractViewAdapter(QObject \*parent)](#KAbstractViewAdapter)
- [void connect(KAbstractViewAdapter::Signal signal, QObject \*receiver, const char \*slot)](#connect)
- [QSize iconSize() const](#iconSize)
- [QAbstractItemModel \*model() const](#model)
- [QPalette palette() const](#palette)
- [QRect visibleArea() const](#visibleArea)
- [QRect visualRect(const QModelIndex &index) const](#visualRect)

## Detailed Description {#details}

The interface allows [KFilePreviewGenerator](kfilepreviewgenerator.md) to be independent from the view implementation.

## Member Type Documentation {#member-type-documentation}

### enum KAbstractViewAdapter::Signal {#Signal-enum}

| Constant |   |
| --- | --- |
| `KAbstractViewAdapter::ScrollBarValueChanged` | `0` |
| `KAbstractViewAdapter::IconSizeChanged` | `1` |

## Member Function Documentation {#member-function-documentation}

### KAbstractViewAdapter::KAbstractViewAdapter(QObject \**parent*) {#KAbstractViewAdapter}

### \[pure virtual\] void KAbstractViewAdapter::connect(KAbstractViewAdapter::Signal *signal*, QObject \**receiver*, const char \**slot*) {#connect}

### \[pure virtual\] QSize KAbstractViewAdapter::iconSize() const {#iconSize}

### \[pure virtual\] QAbstractItemModel \*KAbstractViewAdapter::model() const {#model}

### \[pure virtual\] QPalette KAbstractViewAdapter::palette() const {#palette}

### \[pure virtual\] QRect KAbstractViewAdapter::visibleArea() const {#visibleArea}

### \[pure virtual\] QRect KAbstractViewAdapter::visualRect(const QModelIndex &*index*) const {#visualRect}
