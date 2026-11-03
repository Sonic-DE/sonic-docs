---
title: "KPixmapSequenceWidget Class"
description: "A simple widget showing a fixed size pixmap sequence."
---

# KPixmapSequenceWidget Class

A simple widget showing a fixed size pixmap sequence. [More...](#details)

- **Header:** `#include <KPixmapSequenceWidget>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kpixmapsequencewidget-members.md)

## Public Functions

- [KPixmapSequenceWidget(QWidget \*parent = nullptr)](#KPixmapSequenceWidget)
- [KPixmapSequenceWidget(const KPixmapSequence &seq, QWidget \*parent = nullptr)](#KPixmapSequenceWidget-1)
- [int interval() const](#interval)
- [KPixmapSequence sequence() const](#sequence)

## Public Slots

- [void setInterval(int msecs)](#setInterval)
- [void setSequence(const KPixmapSequence &seq)](#setSequence)

## Detailed Description {#details}

The [KPixmapSequenceWidget](kpixmapsequencewidget.md) uses the [KPixmapSequenceOverlayPainter](kpixmapsequenceoverlaypainter.md) to show a sequence of pixmaps. It is intended as a simple wrapper around the [KPixmapSequenceOverlayPainter](kpixmapsequenceoverlaypainter.md) in case a widget is more appropriate than an event filter.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KPixmapSequenceWidget::KPixmapSequenceWidget(QWidget \**parent* = nullptr) {#KPixmapSequenceWidget}

Constructor

### KPixmapSequenceWidget::KPixmapSequenceWidget(const KPixmapSequence &*seq*, QWidget \**parent* = nullptr) {#KPixmapSequenceWidget-1}

### int KPixmapSequenceWidget::interval() const {#interval}

The interval between frames.

> **Note:** Getter function for property interval.

*See also* [setInterval](kpixmapsequencewidget.md#setInterval), [KPixmapSequenceOverlayPainter::interval](kpixmapsequenceoverlaypainter.md#interval)

### KPixmapSequence KPixmapSequenceWidget::sequence() const {#sequence}

The sequence used to draw the overlay.

*See also* [setSequence](kpixmapsequencewidget.md#setSequence)

### \[slot\] void KPixmapSequenceWidget::setInterval(int *msecs*) {#setInterval}

Set the interval between frames. The default is 200.

> **Note:** Setter function for property interval.

*See also* [interval](kpixmapsequencewidget.md#interval), [KPixmapSequenceOverlayPainter::setInterval](kpixmapsequenceoverlaypainter.md#setInterval)

### \[slot\] void KPixmapSequenceWidget::setSequence(const KPixmapSequence &*seq*) {#setSequence}

Set the sequence to be used. By default the KDE busy sequence is used.

*See also* [sequence](kpixmapsequencewidget.md#sequence)()
