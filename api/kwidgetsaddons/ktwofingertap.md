---
title: "KTwoFingerTap Class"
description: "A two finger tap gesture."
---

# KTwoFingerTap Class

A two finger tap gesture. [More...](#details)

- **Header:** `#include <KTwoFingerTap>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QGesture](https://doc.qt.io/qt-6/qgesture.html)

[List of all members, including inherited members](ktwofingertap-members.md)

## Properties

- [pos : QPointF](#pos-prop)
- [scenePos : QPointF](#scenePos-prop)
- [screenPos : QPointF](#screenPos-prop)

## Public Functions

- [KTwoFingerTap(QObject \*parent = nullptr)](#KTwoFingerTap)
- [QPointF pos() const](#pos)
- [QPointF scenePos() const](#scenePos)
- [QPointF screenPos() const](#screenPos)
- [void setPos(QPointF pos)](#setPos)
- [void setScenePos(QPointF scenePos)](#setScenePos)
- [void setScreenPos(QPointF screenPos)](#setScreenPos)

## Detailed Description {#details}

Provides a class for a two finger tap gesture.

> **Note:** The QGestureManager need a QMainwindow, to delivery the gesture.

## Property Documentation {#property-documentation}

### pos : QPointF {#pos-prop}

**Access functions:**

- `QPointF` **[pos](ktwofingertap.md#pos)**() const
- `void` **[setPos](ktwofingertap.md#setPos)**(`QPointF` *pos*)

### scenePos : QPointF {#scenePos-prop}

**Access functions:**

- `QPointF` **[scenePos](ktwofingertap.md#scenePos)**() const
- `void` **[setScenePos](ktwofingertap.md#setScenePos)**(`QPointF` *scenePos*)

### screenPos : QPointF {#screenPos-prop}

**Access functions:**

- `QPointF` **[screenPos](ktwofingertap.md#screenPos)**() const
- `void` **[setScreenPos](ktwofingertap.md#setScreenPos)**(`QPointF` *screenPos*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KTwoFingerTap::KTwoFingerTap(QObject \**parent* = nullptr) {#KTwoFingerTap}

The constructor.

### QPointF KTwoFingerTap::pos() const {#pos}

The position of the gesture, relative to the widget that received the gesture.

Note: This is not necessarily the same position as in the widget that grabGesture() uses.

> **Note:** Getter function for property [pos](ktwofingertap.md#pos-prop).

*See also* [setPos](ktwofingertap.md#setPos)()

### QPointF KTwoFingerTap::scenePos() const {#scenePos}

Return the start scene position of the gesture.

> **Note:** Getter function for property [scenePos](ktwofingertap.md#scenePos-prop).

*See also* [setScenePos](ktwofingertap.md#setScenePos)()

### QPointF KTwoFingerTap::screenPos() const {#screenPos}

Sets the screen position.

`screenPos` The screen position.

> **Note:** Getter function for property [screenPos](ktwofingertap.md#screenPos-prop).

*See also* [setScreenPos](ktwofingertap.md#setScreenPos)()

### void KTwoFingerTap::setPos(QPointF *pos*) {#setPos}

Sets the position, relative to the widget.

`pos` The position.

> **Note:** Setter function for property [pos](ktwofingertap.md#pos-prop).

*See also* [pos](ktwofingertap.md#pos)()

### void KTwoFingerTap::setScenePos(QPointF *scenePos*) {#setScenePos}

Sets the scene position.

`scenePos` The scene position, identical to the screen position for widgets.

> **Note:** Setter function for property [scenePos](ktwofingertap.md#scenePos-prop).

*See also* [scenePos](ktwofingertap.md#scenePos)()

### void KTwoFingerTap::setScreenPos(QPointF *screenPos*) {#setScreenPos}

Return the start scene position of the gesture.

> **Note:** Setter function for property [screenPos](ktwofingertap.md#screenPos-prop).

*See also* [screenPos](ktwofingertap.md#screenPos)()
