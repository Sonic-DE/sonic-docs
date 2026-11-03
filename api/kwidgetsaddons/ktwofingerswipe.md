---
title: "KTwoFingerSwipe Class"
description: "A two finger swipe gesture."
---

# KTwoFingerSwipe Class

A two finger swipe gesture. [More...](#details)

- **Header:** `#include <KTwoFingerSwipe>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QGesture](https://doc.qt.io/qt-6/qgesture.html)

[List of all members, including inherited members](ktwofingerswipe-members.md)

## Properties

- [pos : QPointF](#pos-prop)
- [scenePos : QPointF](#scenePos-prop)
- [screenPos : QPointF](#screenPos-prop)
- [swipeAngle : qreal](#swipeAngle-prop)

## Public Functions

- [KTwoFingerSwipe(QObject \*parent = nullptr)](#KTwoFingerSwipe)
- [QPointF pos() const](#pos)
- [QPointF scenePos() const](#scenePos)
- [QPointF screenPos() const](#screenPos)
- [void setPos(QPointF pos)](#setPos)
- [void setScenePos(QPointF scenePos)](#setScenePos)
- [void setScreenPos(QPointF screenPos)](#setScreenPos)
- [void setSwipeAngle(qreal swipeAngle)](#setSwipeAngle)
- [qreal swipeAngle() const](#swipeAngle)

## Detailed Description {#details}

Provides a class for a two finger swipe gesture.

Note: The QGestureManager need a QMainwindow, to delivery the gesture.

## Property Documentation {#property-documentation}

### pos : QPointF {#pos-prop}

**Access functions:**

- `QPointF` **[pos](ktwofingerswipe.md#pos)**() const
- `void` **[setPos](ktwofingerswipe.md#setPos)**(`QPointF` *pos*)

### scenePos : QPointF {#scenePos-prop}

**Access functions:**

- `QPointF` **[scenePos](ktwofingerswipe.md#scenePos)**() const
- `void` **[setScenePos](ktwofingerswipe.md#setScenePos)**(`QPointF` *scenePos*)

### screenPos : QPointF {#screenPos-prop}

**Access functions:**

- `QPointF` **[screenPos](ktwofingerswipe.md#screenPos)**() const
- `void` **[setScreenPos](ktwofingerswipe.md#setScreenPos)**(`QPointF` *screenPos*)

### swipeAngle : qreal {#swipeAngle-prop}

**Access functions:**

- `qreal` **[swipeAngle](ktwofingerswipe.md#swipeAngle)**() const
- `void` **[setSwipeAngle](ktwofingerswipe.md#setSwipeAngle)**(`qreal` *swipeAngle*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KTwoFingerSwipe::KTwoFingerSwipe(QObject \**parent* = nullptr) {#KTwoFingerSwipe}

The constructor.

### QPointF KTwoFingerSwipe::pos() const {#pos}

Returns the start position of the gesture, relative to the widget that received the gesture.

> **Note:** This is not necessarily the same position as in the widget that grabGesture() uses.

> **Note:** Getter function for property [pos](ktwofingerswipe.md#pos-prop).

*See also* [setPos](ktwofingerswipe.md#setPos)()

### QPointF KTwoFingerSwipe::scenePos() const {#scenePos}

Return the start scene position of the gesture.

> **Note:** Getter function for property [scenePos](ktwofingerswipe.md#scenePos-prop).

*See also* [setScenePos](ktwofingerswipe.md#setScenePos)()

### QPointF KTwoFingerSwipe::screenPos() const {#screenPos}

Returns the start screen position of the gesture.

> **Note:** Getter function for property [screenPos](ktwofingerswipe.md#screenPos-prop).

*See also* [setScreenPos](ktwofingerswipe.md#setScreenPos)()

### void KTwoFingerSwipe::setPos(QPointF *pos*) {#setPos}

Sets the position, relative to the widget.

`pos` The position.

> **Note:** Setter function for property [pos](ktwofingerswipe.md#pos-prop).

*See also* [pos](ktwofingerswipe.md#pos)()

### void KTwoFingerSwipe::setScenePos(QPointF *scenePos*) {#setScenePos}

Sets the scene position.

`scenePos` The scene position, identical to the screen position for widgets.

> **Note:** Setter function for property [scenePos](ktwofingerswipe.md#scenePos-prop).

*See also* [scenePos](ktwofingerswipe.md#scenePos)()

### void KTwoFingerSwipe::setScreenPos(QPointF *screenPos*) {#setScreenPos}

Sets the screen position.

`screenPos` The screen position.

> **Note:** Setter function for property [screenPos](ktwofingerswipe.md#screenPos-prop).

*See also* [screenPos](ktwofingerswipe.md#screenPos)()

### void KTwoFingerSwipe::setSwipeAngle(qreal *swipeAngle*) {#setSwipeAngle}

Sets the angle of the swipe gesture

`swipeAngle` The angle.

> **Note:** Setter function for property [swipeAngle](ktwofingerswipe.md#swipeAngle-prop).

*See also* [swipeAngle](ktwofingerswipe.md#swipeAngle)()

### qreal KTwoFingerSwipe::swipeAngle() const {#swipeAngle}

Returns the angle of the swipe gesture.

> **Note:** Getter function for property [swipeAngle](ktwofingerswipe.md#swipeAngle-prop).

*See also* [setSwipeAngle](ktwofingerswipe.md#setSwipeAngle)()
