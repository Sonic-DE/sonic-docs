---
title: "KColumnResizer Class"
description: "Maintains consistent column sizes across layouts."
---

# KColumnResizer Class

Maintains consistent column sizes across layouts. [More...](#details)

- **Header:** `#include <KColumnResizer>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kcolumnresizer-members.md)

## Public Functions

- [KColumnResizer(QObject \*parent = nullptr)](#KColumnResizer)
- [void addWidget(QWidget \*widget)](#addWidget)
- [void addWidgetsFromLayout(QLayout \*layout, int column = 0)](#addWidgetsFromLayout)
- [void removeWidget(QWidget \*widget)](#removeWidget)

## Detailed Description {#details}

[KColumnResizer](kcolumnresizer.md) is a helper class which can force columns of different layouts to keep the same width. It is useful to keep label columns consistent.

It works with [QGridLayout](https://doc.qt.io/qt-6/qgridlayout.html) and [QFormLayout](https://doc.qt.io/qt-6/qformlayout.html).

Here is a typical example:

```cpp
void Window::createWidgets()
{
    QVBoxLayout *layout = new QVBoxLayout(this);

    QGroupBox *box1 = new QGroupBox();
    // Fill box1
    // ...
    layout->addWidget(box1);

    QGroupBox *box2 = new QGroupBox();
    // Fill box2
    // ...
    layout->addWidget(box2);

    KColumnResizer *resizer = new KColumnResizer(this);
    resizer->addWidgetsFromLayout(box1->layout(), 0);
    resizer->addWidgetsFromLayout(box2->layout(), 0);
}
```

In this example box1 and box2 children can be organized using [QGridLayout](https://doc.qt.io/qt-6/qgridlayout.html) or [QFormLayout](https://doc.qt.io/qt-6/qformlayout.html), resizer will ensure the first columns of the two [QGroupBox](https://doc.qt.io/qt-6/qgroupbox.html) stay the same width.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KColumnResizer::KColumnResizer(QObject \**parent* = nullptr) {#KColumnResizer}

Constructs a [KColumnResizer](kcolumnresizer.md).

### void KColumnResizer::addWidget(QWidget \**widget*) {#addWidget}

Add a single widget to the list of widgets whose width is monitored.

It is more common to use [addWidgetsFromLayout](kcolumnresizer.md#addWidgetsFromLayout)(), but adding single widgets can be useful if you want to keep a single button the same width as a column in a layout.

`widget` The widget to add

### void KColumnResizer::addWidgetsFromLayout(QLayout \**layout*, int *column* = 0) {#addWidgetsFromLayout}

Add all widgets from `layout` which are in column `column` to the list of widgets to manage.

`layout` The layout containing the widgets to add. [KColumnResizer](kcolumnresizer.md) supports [QGridLayout](https://doc.qt.io/qt-6/qgridlayout.html) and [QFormLayout](https://doc.qt.io/qt-6/qformlayout.html).

`column` The column number which contains the widgets. If layout is a [QFormLayout](https://doc.qt.io/qt-6/qformlayout.html), column should not be higher than [QFormLayout::SpanningRole](https://doc.qt.io/qt-6/qformlayout.html#ItemRole-enum)

### void KColumnResizer::removeWidget(QWidget \**widget*) {#removeWidget}

Remove a widget previously added by [addWidget](kcolumnresizer.md#addWidget) or [addWidgetsFromLayout](kcolumnresizer.md#addWidgetsFromLayout).

`widget` The widget to remove
