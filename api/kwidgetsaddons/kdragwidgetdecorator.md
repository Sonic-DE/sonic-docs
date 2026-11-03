---
title: "KDragWidgetDecorator Class"
description: "A decorator which adds drag-support to widgets."
---

# KDragWidgetDecorator Class

A decorator which adds drag-support to widgets. [More...](#details)

- **Header:** `#include <KDragWidgetDecorator>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** KDragWidgetDecoratorBase

[List of all members, including inherited members](kdragwidgetdecorator-members.md)

## Public Types

- [KDragWidgetDecorator::DragObjectFactory](#DragObjectFactory-typedef)

## Public Functions

- [KDragWidgetDecorator\<Widget\>::DragObjectFactory dragObjectFactory() const](#dragObjectFactory)
- [void setDragObjectFactory(KDragWidgetDecorator\<Widget\>::DragObjectFactory factory)](#setDragObjectFactory)

## Detailed Description {#details}

This is a decorator using an event filter to implement drag-support in widgets.

You must set the [dragObjectFactory](kdragwidgetdecorator.md#dragObjectFactory) to specify the [QDrag](https://doc.qt.io/qt-6/qdrag.html) to be used.

## Member Type Documentation {#member-type-documentation}

### KDragWidgetDecorator::DragObjectFactory {#DragObjectFactory-typedef}

## Member Function Documentation {#member-function-documentation}

### KDragWidgetDecorator\<Widget\>::DragObjectFactory KDragWidgetDecorator::dragObjectFactory() const {#dragObjectFactory}

Returns the [QDrag](https://doc.qt.io/qt-6/qdrag.html) factory used by this decorator

*See also* [setDragObjectFactory](kdragwidgetdecorator.md#setDragObjectFactory)()

### void KDragWidgetDecorator::setDragObjectFactory(KDragWidgetDecorator\<Widget\>::DragObjectFactory *factory*) {#setDragObjectFactory}

Set a factory to be used by this decorator

`factory` the new [QDrag](https://doc.qt.io/qt-6/qdrag.html) factory to use

*See also* [dragObjectFactory](kdragwidgetdecorator.md#dragObjectFactory)()
