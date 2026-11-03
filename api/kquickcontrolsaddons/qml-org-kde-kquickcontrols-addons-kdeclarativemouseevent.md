---
title: "KDeclarativeMouseEvent QML Type"
description: "This item spies on mouse events from all child objects including child MouseAreas regardless of whether the child MouseArea propagates events. It does not accept the event."
---

# KDeclarativeMouseEvent QML Type

This item spies on mouse events from all child objects including child MouseAreas regardless of whether the child [MouseArea](https://doc.qt.io/qt-6/qml-qtquick-mousearea.html) propagates events. It does not accept the event. [More...](#details)

- Import Statement: import org.kde.kquickcontrols.addons

## Detailed Description {#details}

In addition unlike [MouseArea](https://doc.qt.io/qt-6/qml-qtquick-mousearea.html) events include the mouse position in global coordinates and provides the screen the mouse is in.

## Property Documentation {#property-documentation}

### accepted : bool {#accepted-prop}

### button : bool {#button-prop}

### buttons : Qt::MouseButtons {#buttons-prop}

### modifiers : Qt::KeyboardModifiers {#modifiers-prop}

### screen : QScreen {#screen-prop}

### screenX : bool {#screenX-prop}

### screenY : bool {#screenY-prop}

### source : int {#source-prop}

### x : bool {#x-prop}

### y : bool {#y-prop}

## Signal Documentation {#signal-documentation}

### acceptedChanged() {#acceptedChanged-signal}

> **Note:** The corresponding handler is `onAcceptedChanged`.
