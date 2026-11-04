---
title: "KUndoActions Namespace"
description: "Provides functions that creates undo/redo actions for a QUndoStack with KDE's default icons and shortcuts."
---

# KUndoActions Namespace

Provides functions that creates undo/redo actions for a [QUndoStack](https://doc.qt.io/qt-6/qundostack.html) with KDE's default icons and shortcuts. [More...](#details)

- **Header:** `#include <KUndoActions>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS XmlGui)`  
  `target_link_libraries(mytarget PRIVATE KF6::XmlGui)`

## Detailed Description {#details}

See [QUndoStack](https://doc.qt.io/qt-6/qundostack.html) for more information.

## Function Documentation {#function-documentation}

### QAction \*KUndoActions::createRedoAction(QUndoStack \**undoStack*, KActionCollection \**actionCollection*, const QString &*actionName* = QString()) {#createRedoAction}

Creates an redo action with the default shortcut and icon and adds it to `actionCollection`.

`undoStack` the [QUndoStack](https://doc.qt.io/qt-6/qundostack.html) the action triggers the redo on

`actionCollection` the [KActionCollection](kactioncollection.md) that should be the parent of the action

`actionName` the created action's object name, empty string will set it to the KDE default

Returns the created action.

### QAction \*KUndoActions::createUndoAction(QUndoStack \**undoStack*, KActionCollection \**actionCollection*, const QString &*actionName* = QString()) {#createUndoAction}

Creates an undo action with the default KDE shortcut and icon and adds it to `actionCollection`.

Returns the created action.

`undoStack` The [QUndoStack](https://doc.qt.io/qt-6/qundostack.html) the action triggers the undo on.

`actionCollection` The [KActionCollection](kactioncollection.md) that should be the parent of the action.

`actionName` The created action's object name, empty string will set it to the KDE default.
