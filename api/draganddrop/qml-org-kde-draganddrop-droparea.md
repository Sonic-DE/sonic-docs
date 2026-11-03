---
title: "DropArea QML Type"
description: "QML helpers for Drag and Drop."
---

# DropArea QML Type

QML helpers for Drag and Drop. [More...](#details)

- Import Statement: import org.kde.draganddrop

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### containsDrag : bool {#containsDrag-prop}

### enabled : bool {#enabled-prop}

If false the area will receive no drop events

### preventStealing : bool {#preventStealing-prop}

## Signal Documentation {#signal-documentation}

### dragEnter(DeclarativeDragDropEvent \**event*) {#dragEnter-signal}

Emitted when the mouse cursor dragging something enters in the drag area

`event` description of the dragged content

> **Note:** The corresponding handler is `onDragEnter`.

*See also* [DragDropEvent](qml-org-kde-draganddrop-dragdropevent.md)

### dragLeave(DeclarativeDragDropEvent \**event*) {#dragLeave-signal}

Emitted when the mouse cursor dragging something leaves the drag area

`event` description of the dragged content

> **Note:** The corresponding handler is `onDragLeave`.

*See also* [DragDropEvent](qml-org-kde-draganddrop-dragdropevent.md)

### dragMove(DeclarativeDragDropEvent \**event*) {#dragMove-signal}

Emitted when the mouse cursor dragging something moves over the drag area

`event` description of the dragged content

> **Note:** The corresponding handler is `onDragMove`.

*See also* [DragDropEvent](qml-org-kde-draganddrop-dragdropevent.md)

### drop(DeclarativeDragDropEvent \**event*) {#drop-signal}

Emitted when the user drops something in the area

`event` description of the dragged content

> **Note:** The corresponding handler is `onDrop`.

*See also* [DragDropEvent](qml-org-kde-draganddrop-dragdropevent.md)
