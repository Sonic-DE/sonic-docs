---
title: "WheelEvent QML Type"
description: "Describes the mouse wheel event."
---

# WheelEvent QML Type

Describes the mouse wheel event. [More...](#details)

- Import Statement: import org.kde.kirigami

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### accepted : bool {#accepted-prop}

If set, the event shouldn't be managed anymore, for instance it can be used to block the handler to manage the scroll of a view on some scenarios.

```cpp
// This handler handles automatically the scroll of
// flickableItem, unless Ctrl is pressed, in this case the
// app has custom code to handle Ctrl+wheel zooming
Kirigami.WheelHandler {
  target: flickableItem
  blockTargetWheel: true
  scrollFlickableTarget: true
  onWheel: {
       if (wheel.modifiers & Qt.ControlModifier) {
           wheel.accepted = true;
           // Handle scaling of the view
      }
  }
}
```

### angleDelta : point {#angleDelta-prop}

The distance the wheel is rotated in degrees. The x and y coordinates indicate the horizontal and vertical wheels respectively. A positive value indicates it was rotated up/right, negative, bottom/left This value is more likely to be set in traditional mice.

### buttons : int {#buttons-prop}

It contains an OR combination of the buttons that were pressed during the wheel, they can be:

- Qt.LeftButton
- Qt.MiddleButton
- Qt.RightButton

### inverted : bool {#inverted-prop}

Whether the delta values are inverted On some platformsthe returned delta are inverted, so positive values would mean bottom/left

### modifiers : int {#modifiers-prop}

Keyboard modifiers that were pressed during the wheel event, such as: Qt.NoModifier (default, no modifiers) Qt.ControlModifier Qt.ShiftModifier ...

### pixelDelta : point {#pixelDelta-prop}

Provides the delta in screen pixels available on high resolution trackpads.

### x : double {#x-prop}

X coordinate of the mouse pointer.

### y : double {#y-prop}

Y coordinate of the mouse pointer.
