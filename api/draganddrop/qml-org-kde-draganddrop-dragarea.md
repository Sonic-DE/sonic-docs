---
title: "DragArea QML Type"
description: "QML helpers for Drag and Drop."
---

# DragArea QML Type

QML helpers for Drag and Drop. [More...](#details)

- Import Statement: import org.kde.draganddrop

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### defaultAction : Qt::DropAction {#defaultAction-prop}

The default action will be performed during a drag when no modificators are pressed.

### delegate : Item {#delegate-prop}

The delegate is the item that will be displayed next to the mouse cursor during the drag and drop operation. It usually consists of a large, semi-transparent icon representing the data being dragged.

### delegateImage : var {#delegateImage-prop}

An image to be used as delegate.

If present, it overrides the delegate property.

It can be either a QImage or a QIcon.

### dragActive : bool {#dragActive-prop}

Whether a drag currently originates from this drag area.

### enabled : bool {#enabled-prop}

If false no drag operation will be generate

### mimedata : MimeData {#mimedata-prop}

the mime data of the drag operation

*See also* [MimeData](qml-org-kde-draganddrop-mimedata.md)

### source : Item {#source-prop}

The QML element that is the source of the resulting drag and drop operation. This can be defined to any item, and will be available to the [DropArea](qml-org-kde-draganddrop-droparea.md) as event.data.source

### startDragDistance : int {#startDragDistance-prop}

distance in pixel after which a drag event will get started

### supportedActions : Qt::DropActions {#supportedActions-prop}

Supported operations, a combination of:

- Qt.CopyAction
- Qt.MoveAction
- Qt.LinkAction
- Qt.ActionMask
- Qt.IgnoreAction
- Qt.TargetMoveAction

### target : Item {#target-prop}

## Signal Documentation {#signal-documentation}

### dataChanged() {#dataChanged-signal}

> **Note:** The corresponding handler is `onDataChanged`.

### defaultActionChanged() {#defaultActionChanged-signal}

> **Note:** The corresponding handler is `onDefaultActionChanged`.

### delegateChanged() {#delegateChanged-signal}

> **Note:** The corresponding handler is `onDelegateChanged`.

### delegateImageChanged() {#delegateImageChanged-signal}

> **Note:** The corresponding handler is `onDelegateImageChanged`.

### dragActiveChanged() {#dragActiveChanged-signal}

> **Note:** The corresponding handler is `onDragActiveChanged`.

### dragStarted() {#dragStarted-signal}

> **Note:** The corresponding handler is `onDragStarted`.

### drop(int *action*) {#drop-signal}

> **Note:** The corresponding handler is `onDrop`.

### enabledChanged() {#enabledChanged-signal}

> **Note:** The corresponding handler is `onEnabledChanged`.

### sourceChanged() {#sourceChanged-signal}

> **Note:** The corresponding handler is `onSourceChanged`.

### startDragDistanceChanged() {#startDragDistanceChanged-signal}

> **Note:** The corresponding handler is `onStartDragDistanceChanged`.

### supportedActionsChanged() {#supportedActionsChanged-signal}

> **Note:** The corresponding handler is `onSupportedActionsChanged`.

### targetChanged() {#targetChanged-signal}

> **Note:** The corresponding handler is `onTargetChanged`.
