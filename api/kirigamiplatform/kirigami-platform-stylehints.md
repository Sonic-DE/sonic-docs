---
title: "Kirigami::Platform::StyleHints Class"
description: "A class providing an attached property to set hints for styles to use."
---

# Kirigami::Platform::StyleHints Class

A class providing an attached property to set hints for styles to use. [More...](#details)

- **Header:** `#include <Kirigami/Platform/StyleHints>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KirigamiPlatform)`  
  `target_link_libraries(mytarget PRIVATE KF6::KirigamiPlatform)`
- **In QML:** [StyleHints](qml-org-kde-kirigami-platform-stylehints.md)
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kirigami-platform-stylehints-members.md)

## Static Public Members

- [void setMakeStyleHintsFunction(const std::function\<StyleHints \*(QObject \*)\> &function)](#setMakeStyleHintsFunction)

## Protected Functions

- [void propertyChanged(Kirigami::Platform::StyleHints::ChangedProperty change)](#propertyChanged)

## Detailed Description {#details}

This is mostly a class for [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html) API. However, if you need to trigger specific behaviour in a custom style, you can call [setMakeStyleHintsFunction](kirigami-platform-stylehints.md#setMakeStyleHintsFunction)() with a custom factory function to create a custom subclass of this class. The subclass can then respond to property changes of instances of this class.

## Member Function Documentation {#member-function-documentation}

### \[virtual protected\] void StyleHints::propertyChanged(Kirigami::Platform::StyleHints::ChangedProperty *change*) {#propertyChanged}

Helper function to notify subclasses of a property change.

Reimplement this in a subclass to handle a change to one of the properties, without the overhead of making separate signal connections for each property.

### \[static\] void StyleHints::setMakeStyleHintsFunction(const std::function\<StyleHints \*(QObject \*)\> &*function*) {#setMakeStyleHintsFunction}

Set a different function to be used by qmlAttachedProperties() to create a [StyleHints](kirigami-platform-stylehints.md) instance.

This is provided to allow different platform plugins to provide their own [StyleHints](kirigami-platform-stylehints.md) subclass.
