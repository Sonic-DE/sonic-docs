---
title: "KTwoFingerSwipeRecognizer Class"
description: "The recognizer for a two finger swipe gesture."
---

# KTwoFingerSwipeRecognizer Class

The recognizer for a two finger swipe gesture. [More...](#details)

- **Header:** `#include <KTwoFingerSwipe>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QGestureRecognizer](https://doc.qt.io/qt-6/qgesturerecognizer.html)

[List of all members, including inherited members](ktwofingerswiperecognizer-members.md)

## Public Functions

- [KTwoFingerSwipeRecognizer()](#KTwoFingerSwipeRecognizer)
- [QGesture \*create(QObject \*target)](#create)
- [int maxSwipeTime() const](#maxSwipeTime)
- [int minSswipeDistance() const](#minSswipeDistance)
- [QGestureRecognizer::Result recognize(QGesture \*gesture, QObject \*watched, QEvent \*event)](#recognize)
- [void setMaxSwipeTime(int i)](#setMaxSwipeTime)
- [void setSwipeDistance(int i)](#setSwipeDistance)

## Detailed Description {#details}

Provides the recognizer for a two finger swipe gesture. To adjust the maximum swipe time and the minimum swipe distance, for a valid swipe gesture:

*See also* [setMaxSwipeTime](ktwofingerswiperecognizer.md#setMaxSwipeTime), [setSwipeDistance](ktwofingerswiperecognizer.md#setSwipeDistance)

## Member Function Documentation {#member-function-documentation}

### KTwoFingerSwipeRecognizer::KTwoFingerSwipeRecognizer() {#KTwoFingerSwipeRecognizer}

The constructor.

### \[override virtual\] QGesture \*KTwoFingerSwipeRecognizer::create(QObject \**target*) {#create}

Reimplements: [QGestureRecognizer::create(QObject \*target)](https://doc.qt.io/qt-6/qgesturerecognizer.html#create).

Qt called this member to create a new [QGesture](https://doc.qt.io/qt-6/qgesture.html) object.

`target` The target for the gesture.

Returns the new [QGesture](https://doc.qt.io/qt-6/qgesture.html) object.

### int KTwoFingerSwipeRecognizer::maxSwipeTime() const {#maxSwipeTime}

Returns the maximum duration for the swipe gesture, in milliseconds.

*See also* [setMaxSwipeTime](ktwofingerswiperecognizer.md#setMaxSwipeTime)()

### int KTwoFingerSwipeRecognizer::minSswipeDistance() const {#minSswipeDistance}

Returns the minimum distance for the swipe gesture.

### \[override virtual\] QGestureRecognizer::Result KTwoFingerSwipeRecognizer::recognize(QGesture \**gesture*, QObject \**watched*, QEvent \**event*) {#recognize}

Reimplements: [QGestureRecognizer::recognize(QGesture \*gesture, QObject \*watched, QEvent \*event)](https://doc.qt.io/qt-6/qgesturerecognizer.html#recognize).

Handles the given event for the watched object and update the gesture object.

`gesture` The gesture object.

`watched` The watched object.

`event` The event.

Returns the result reflects how much of the gesture has been recognized.

### void KTwoFingerSwipeRecognizer::setMaxSwipeTime(int *i*) {#setMaxSwipeTime}

Set the maximum duration of the swipe gesture. If `i` is negative, it will be set to null.

`i` The maximum duration in milliseconds.

*See also* [maxSwipeTime](ktwofingerswiperecognizer.md#maxSwipeTime)()

### void KTwoFingerSwipeRecognizer::setSwipeDistance(int *i*) {#setSwipeDistance}

Set the minimum distance of the swipe gesture. If `i` is negative, it will be set to null.

`i` The minimum distance.
