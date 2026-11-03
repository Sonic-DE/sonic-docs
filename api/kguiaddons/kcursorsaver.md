---
title: "KCursorSaver Class"
description: "Class to temporarily set a mouse cursor and restore the previous one on destruction."
---

# KCursorSaver Class

Class to temporarily set a mouse cursor and restore the previous one on destruction. [More...](#details)

- **Header:** `#include <KCursorSaver>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS GuiAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::GuiAddons)`

[List of all members, including inherited members](kcursorsaver-members.md)

## Public Functions

- [KCursorSaver(Qt::CursorShape shape)](#KCursorSaver)
- [~KCursorSaver()](#dtor.KCursorSaver)
- [void restoreCursor()](#restoreCursor)

## Detailed Description {#details}

Create a [KCursorSaver](kcursorsaver.md) object when you want to set the cursor. As soon as it gets out of scope, it will restore the original cursor.

```cpp
KCursorSaver saver(Qt::WaitCursor);
... long-running operation here ...
```

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KCursorSaver::KCursorSaver(Qt::CursorShape *shape*) {#KCursorSaver}

Creates a [KCursorSaver](kcursorsaver.md), setting the mouse cursor to `shape`.

### \[noexcept\] KCursorSaver::~KCursorSaver() {#dtor.KCursorSaver}

restore the cursor

### void KCursorSaver::restoreCursor() {#restoreCursor}

call this to explicitly restore the cursor
