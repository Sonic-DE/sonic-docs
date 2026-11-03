---
title: "KAdjustingScrollArea Class"
description: "Special scroll area widget which adjust its size to avoid scroll bars as much as possible. This class was introduced in Qt 6.9."
---

# KAdjustingScrollArea Class

Special scroll area widget which adjust its size to avoid scroll bars as much as possible. This class was introduced in Qt 6.9. [More...](#details)

- **Header:** `#include <KAdjustingScrollArea>`
- **Since:** Qt 6.9
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QScrollArea](https://doc.qt.io/qt-6/qscrollarea.html)

[List of all members, including inherited members](kadjustingscrollarea-members.md)

## Public Functions

- [KAdjustingScrollArea(QWidget \*parent = nullptr)](#KAdjustingScrollArea)

## Detailed Description {#details}

This widget improves a few aspects of [QScrollArea](https://doc.qt.io/qt-6/qscrollarea.html) in particular, for vertically scrollable widgets and dialogs.

If sizeAdjustPolicy is set to [QAbstractScrollArea::AdjustToContents](https://doc.qt.io/qt-6/qabstractscrollarea.html#SizeAdjustPolicy-enum), then the scroll area will (try to) adjust its size to the widget to avoid scroll bars as much as possible.

In particular, this widget will automatically increase the height of its window when the content of the scroll area grows in height (e.g. because more widgets are added dynamically). The automatic resizing stops at 2/3 of the screen's height.

Instead of setting the scrollarea's content via [QScrollArea::setWidget](https://doc.qt.io/qt-6/qscrollarea.html#setWidget), add the child widgets to the [QVBoxLayout](https://doc.qt.io/qt-6/qvboxlayout.html) of the scrollarea's widget.

```cpp
auto scrollArea = new KAdjustingScrollArea(this);
scrollArea->setSizeAdjustPolicy(QScrollArea::AdjustToContents);
scrollArea->setFocusPolicy(Qt::NoFocus);
scrollArea->setHorizontalScrollBarPolicy(Qt::ScrollBarAlwaysOff);
scrollArea->setWidget(new QWidget);

auto scrollAreaLayout = new QVBoxLayout(scrollArea->widget());
```

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KAdjustingScrollArea::KAdjustingScrollArea(QWidget \**parent* = nullptr) {#KAdjustingScrollArea}

Creates a scroll area with a [QWidget](https://doc.qt.io/qt-6/qwidget.html) with [QVBoxLayout](https://doc.qt.io/qt-6/qvboxlayout.html) that is flagged as resizable.
