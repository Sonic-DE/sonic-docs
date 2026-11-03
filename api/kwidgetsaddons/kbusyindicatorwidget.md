---
title: "KBusyIndicatorWidget Class"
description: "Rotating spinning icon to indicate busyness."
---

# KBusyIndicatorWidget Class

Rotating spinning icon to indicate busyness. [More...](#details)

- **Header:** `#include <KBusyIndicatorWidget>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kbusyindicatorwidget-members.md)

## Properties

- [isRunning : bool](#isRunning-prop)

## Public Functions

- [KBusyIndicatorWidget(QWidget \*parent = nullptr)](#KBusyIndicatorWidget)
- [bool isRunning() const](#isRunning) (since 6.11.0)
- [QSize minimumSizeHint() const](#minimumSizeHint)

## Public Slots

- [void setRunning(const bool enable = true)](#setRunning) (since 6.11.0)
- [void start()](#start) (since 6.10.0)
- [void stop()](#stop) (since 6.10.0)

## Detailed Description {#details}

When you need to communicate to the user that your application is busy with something you'll want to use a [KBusyIndicatorWidget](kbusyindicatorwidget.md) to display an spinnning indicator icon. The spinning animation can be stopped and started.

A way of using this widget is to combine it with a [QLabel](https://doc.qt.io/qt-6/qlabel.html) to construct a status line:

```cpp
auto layout = new QHBoxLayout;
layout->addWidget(new KBusyIndicatorWidget);
layout->addWidget(new QLabel(QStringLiteral("Watering the flowers...")));
```

The [KBusyIndicatorWidget](kbusyindicatorwidget.md) differs from the [KPixmapSequenceWidget](kpixmapsequencewidget.md) by animating a scaled icon instead of rendering a pixmap sequence. It supports multiple, semi-arbitrary sizes, with quality constrained only by the resolution of the available icons.

## Property Documentation {#property-documentation}

### isRunning : bool {#isRunning-prop}

**Access functions:**

- `bool` **[isRunning](kbusyindicatorwidget.md#isRunning)**() const
- `void` **[setRunning](kbusyindicatorwidget.md#setRunning)**(const `bool` *enable* = true)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KBusyIndicatorWidget::KBusyIndicatorWidget(QWidget \**parent* = nullptr) {#KBusyIndicatorWidget}

Create a new [KBusyIndicatorWidget](kbusyindicatorwidget.md) widget

### \[since 6.11.0\] bool KBusyIndicatorWidget::isRunning() const {#isRunning}

Returns whether the spinning animation is running

> **Note:** Getter function for property [isRunning](kbusyindicatorwidget.md#isRunning-prop).

This function was introduced in Qt 6.11.0.

*See also* [setRunning](kbusyindicatorwidget.md#setRunning)()

### \[override virtual\] QSize KBusyIndicatorWidget::minimumSizeHint() const {#minimumSizeHint}

Reimplements an access function for property: [QWidget::minimumSizeHint](https://doc.qt.io/qt-6/qwidget.html#minimumSizeHint-prop).

Return the smallest reasonable size for the widget

### \[slot, since 6.11.0\] void KBusyIndicatorWidget::setRunning(const bool *enable* = true) {#setRunning}

By calling this method with @p enable = true the spinning abnimation will be started. Stopped if false.

> **Note:** Setter function for property [isRunning](kbusyindicatorwidget.md#isRunning-prop).

This function was introduced in Qt 6.11.0.

*See also* [isRunning](kbusyindicatorwidget.md#isRunning)(), [start](kbusyindicatorwidget.md#start)(), [stop](kbusyindicatorwidget.md#stop)()

### \[slot, since 6.10.0\] void KBusyIndicatorWidget::start() {#start}

Start the spinning animation

This function was introduced in Qt 6.10.0.

*See also* [setRunning](kbusyindicatorwidget.md#setRunning)()

### \[slot, since 6.10.0\] void KBusyIndicatorWidget::stop() {#stop}

Stop the spinning animation

This function was introduced in Qt 6.10.0.

*See also* [setRunning](kbusyindicatorwidget.md#setRunning)()
