---
title: "KTwoFingerTapRecognizer Class"
description: "The recognizer for a two finger tap gesture."
---

# KTwoFingerTapRecognizer Class

The recognizer for a two finger tap gesture. [More...](#details)

- **Header:** `#include <KTwoFingerTap>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QGestureRecognizer](https://doc.qt.io/qt-6/qgesturerecognizer.html)

[List of all members, including inherited members](ktwofingertaprecognizer-members.md)

## Public Functions

- [KTwoFingerTapRecognizer()](#KTwoFingerTapRecognizer)
- [QGesture \*create(QObject \*target)](#create)
- [QGestureRecognizer::Result recognize(QGesture \*gesture, QObject \*watched, QEvent \*event)](#recognize)
- [void setTapRadius(int i)](#setTapRadius)
- [int tapRadius() const](#tapRadius)

## Detailed Description {#details}

Provides the recognizer for a two finger tap gesture.

## Member Function Documentation {#member-function-documentation}

### KTwoFingerTapRecognizer::KTwoFingerTapRecognizer() {#KTwoFingerTapRecognizer}

The constructor.

### \[override virtual\] QGesture \*KTwoFingerTapRecognizer::create(QObject \**target*) {#create}

Reimplements: [QGestureRecognizer::create(QObject \*target)](https://doc.qt.io/qt-6/qgesturerecognizer.html#create).

Qt called this member to create a new [QGesture](https://doc.qt.io/qt-6/qgesture.html) object.

`target` The target for the gesture.

Returns the new [QGesture](https://doc.qt.io/qt-6/qgesture.html) object.

### \[override virtual\] QGestureRecognizer::Result KTwoFingerTapRecognizer::recognize(QGesture \**gesture*, QObject \**watched*, QEvent \**event*) {#recognize}

Reimplements: [QGestureRecognizer::recognize(QGesture \*gesture, QObject \*watched, QEvent \*event)](https://doc.qt.io/qt-6/qgesturerecognizer.html#recognize).

Handles the given event for the watched object and update the gesture object.

`gesture` The gesture object.

`watched` The watched object.

`event` The event.

Returns the result reflects how much of the gesture has been recognized.

### void KTwoFingerTapRecognizer::setTapRadius(int *i*) {#setTapRadius}

Set the maximum wiggle room for a touch point. If `i` is negative, it will be set to null.

`i` The maximum wiggle room.

*See also* [tapRadius](ktwofingertaprecognizer.md#tapRadius)()

### int KTwoFingerTapRecognizer::tapRadius() const {#tapRadius}

Returns the maximum wiggle room for a touch point.

*See also* [setTapRadius](ktwofingertaprecognizer.md#setTapRadius)()
