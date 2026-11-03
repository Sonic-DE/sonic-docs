---
title: "DragDropEvent QML Type"
description: "QML helpers for Drag and Drop."
---

# DragDropEvent QML Type

QML helpers for Drag and Drop. [More...](#details)

- Import Statement: import org.kde.draganddrop

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### buttons : int {#buttons-prop}

The pressed mouse buttons. A combination of:

| Constant | Description |
| --- | --- |
| Qt.NoButton | The button state does not refer to any button (see QMouseEvent::button()). |
| Qt.LeftButton | The left button is pressed, or an event refers to the left button. (The left button may be the right button on left-handed mice.) |
| Qt.RightButton | The right button. |
| Qt.MidButton | The middle button. |
| Qt.MiddleButton | MidButton The middle button. |
| Qt.XButton1 | The first X button. |
| Qt.XButton2 | The second X button. |

### mimeData : MimeData {#mimeData-prop}

The mime data of this operation

*See also* [MimeData](qml-org-kde-draganddrop-mimedata.md)

### modifiers : int {#modifiers-prop}

Pressed keyboard modifiers, a combination of:

| Constant | Description |
| --- | --- |
| Qt.NoModifier | No modifier key is pressed. |
| Qt.ShiftModifier | A Shift key on the keyboard is pressed. |
| Qt.ControlModifier | A Ctrl key on the keyboard is pressed. |
| Qt.AltModifier | An Alt key on the keyboard is pressed. |
| Qt.MetaModifier | A Meta key on the keyboard is pressed. |
| Qt.KeypadModifier | A keypad button is pressed. |
| Qt.GroupSwitchModifier | X11 only. A Mode\_switch key on the keyboard is pressed. |

### possibleActions : Qt::DropActions {#possibleActions-prop}

The possible kinds of action that can be done in the drop, a combination of:

| Constant | Description |
| --- | --- |
| Qt.CopyAction | 0x1 Copy the data to the target. |
| Qt.MoveAction | 0x2 Move the data from the source to the target. |
| Qt.LinkAction | 0x4 Create a link from the source to the target. |
| Qt.ActionMask | 0xff |
| Qt.IgnoreAction | 0x0 Ignore the action (do nothing with the data). |
| Qt.TargetMoveAction | 0x8002 On Windows, this value is used when the ownership of the D&D data should be taken over by the target application, i.e., the source application should not delete the data. On X11 this value is used to do a move. TargetMoveAction is not used on the Mac. |

### proposedAction : Qt::DropAction {#proposedAction-prop}

Default action

*See also* [possibleActions](qml-org-kde-draganddrop-dragdropevent.md#possibleActions-prop)

### x : int {#x-prop}

The mouse X position of the event relative to the [DropArea](qml-org-kde-draganddrop-droparea.md) that is receiving the event.

### y : int {#y-prop}

The mouse Y position of the event relative to the [DropArea](qml-org-kde-draganddrop-droparea.md) that is receiving the event.

## Method Documentation {#method-documentation}

### accept(int *action*) {#accept-method}

### ignore() {#ignore-method}
