---
title: "MouseEventListener QML Type"
description: "Extensions to Qt Quick Controls."
---

# MouseEventListener QML Type

Extensions to Qt Quick Controls. [More...](#details)

- Import Statement: import org.kde.kquickcontrols.addons

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### acceptedButtons : Qt::MouseButtons {#acceptedButtons-prop}

### containsMouse : bool {#containsMouse-prop}

True if this [MouseEventListener](qml-org-kde-kquickcontrols-addons-mouseeventlistener.md) or any of its children contains the mouse cursor: this property will change only when the mouse button is pressed if [hoverEnabled](qml-org-kde-kquickcontrols-addons-mouseeventlistener.md#hoverEnabled-prop) is false.

### cursorShape : Qt::CursorShape {#cursorShape-prop}

This property holds the cursor shape for this mouse area. Note that on platforms that do not display a mouse cursor this may have no effect.

### hoverEnabled : bool {#hoverEnabled-prop}

This property holds whether hover events are handled. By default hover events are disabled

### pressed : bool {#pressed-prop}

True if the mouse is pressed in the item or any of its children

## Signal Documentation {#signal-documentation}

### acceptedButtonsChanged() {#acceptedButtonsChanged-signal}

> **Note:** The corresponding handler is `onAcceptedButtonsChanged`.

### canceled() {#canceled-signal}

> **Note:** The corresponding handler is `onCanceled`.

### clicked(KDeclarativeMouseEvent *mouse*) {#clicked-signal}

> **Note:** The corresponding handler is `onClicked`.

### containsMouseChanged(bool *containsMouseChanged*) {#containsMouseChanged-signal}

> **Note:** The corresponding handler is `onContainsMouseChanged`.

### cursorShapeChanged() {#cursorShapeChanged-signal}

> **Note:** The corresponding handler is `onCursorShapeChanged`.

### hoverEnabledChanged(bool *hoverEnabled*) {#hoverEnabledChanged-signal}

> **Note:** The corresponding handler is `onHoverEnabledChanged`.

### positionChanged(KDeclarativeMouseEvent *mouse*) {#positionChanged-signal}

> **Note:** The corresponding handler is `onPositionChanged`.

### pressAndHold(KDeclarativeMouseEvent \**mouse*) {#pressAndHold-signal}

> **Note:** The corresponding handler is `onPressAndHold`.

### pressed(*KDeclarativeMouseEventmouse*) {#pressed-signal}

> **Note:** The corresponding handler is `onPressed`.

### pressedChanged() {#pressedChanged-signal}

> **Note:** The corresponding handler is `onPressedChanged`.

### released(KDeclarativeMouseEvent *mouse*) {#released-signal}

> **Note:** The corresponding handler is `onReleased`.

### wheelMoved(KDeclarativeWheelEvent *wheel*) {#wheelMoved-signal}

> **Note:** The corresponding handler is `onWheelMoved`.
