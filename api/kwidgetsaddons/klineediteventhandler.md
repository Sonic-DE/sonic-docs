---
title: "KLineEditEventHandler Namespace"
description: "Event-handling utilities for QLineEdit instances. This namespace was introduced in Qt 6.0."
---

# KLineEditEventHandler Namespace

Event-handling utilities for [QLineEdit](https://doc.qt.io/qt-6/qlineedit.html) instances. This namespace was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <KLineEditEventHandler>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### void KLineEditEventHandler::catchReturnKey(QObject \**lineEdit*) {#catchReturnKey}

Do not propagate Return or Enter key presses in line edits.

[QLineEdit::returnPressed](https://doc.qt.io/qt-6/qlineedit.html#returnPressed)() will still be emitted as normal, but the key event isn't propagated further up the widget hierarchy. This is useful to prevent closing a dialog for example.

### void KLineEditEventHandler::handleUrlDrops(QObject \**lineEdit*) {#handleUrlDrops}

Handle drop events with URLs and replace the current line edit with the dropped URL.
