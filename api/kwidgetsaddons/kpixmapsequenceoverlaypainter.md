---
title: "KPixmapSequenceOverlayPainter Class"
description: "Paints a KPixmapSequence on top of any widget at any position."
---

# KPixmapSequenceOverlayPainter Class

Paints a [KPixmapSequence](kpixmapsequence.md) on top of any widget at any position. [More...](#details)

- **Header:** `#include <KPixmapSequenceOverlayPainter>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kpixmapsequenceoverlaypainter-members.md)

## Public Functions

- [KPixmapSequenceOverlayPainter(QObject \*parent = nullptr)](#KPixmapSequenceOverlayPainter)
- [KPixmapSequenceOverlayPainter(const KPixmapSequence &seq, QObject \*parent = nullptr)](#KPixmapSequenceOverlayPainter-1)
- [Qt::Alignment alignment() const](#alignment)
- [int interval() const](#interval)
- [QPoint offset() const](#offset)
- [QRect rect() const](#rect)
- [KPixmapSequence sequence() const](#sequence)

## Public Slots

- [void setAlignment(Qt::Alignment align)](#setAlignment)
- [void setInterval(int msecs)](#setInterval)
- [void setOffset(const QPoint &offset)](#setOffset)
- [void setRect(const QRect &rect)](#setRect)
- [void setSequence(const KPixmapSequence &seq)](#setSequence)
- [void setWidget(QWidget \*w)](#setWidget)
- [void start()](#start)
- [void stop()](#stop)

## Detailed Description {#details}

The [KPixmapSequenceOverlayPainter](kpixmapsequenceoverlaypainter.md) paints an overlay on top of an arbitrary [QWidget](https://doc.qt.io/qt-6/qwidget.html) using a [KPixmapSequence](kpixmapsequence.md). This is typically used for spinners indicating that a process is not finished yet.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KPixmapSequenceOverlayPainter::KPixmapSequenceOverlayPainter(QObject \**parent* = nullptr) {#KPixmapSequenceOverlayPainter}

Constructor

### KPixmapSequenceOverlayPainter::KPixmapSequenceOverlayPainter(const KPixmapSequence &*seq*, QObject \**parent* = nullptr) {#KPixmapSequenceOverlayPainter-1}

### Qt::Alignment KPixmapSequenceOverlayPainter::alignment() const {#alignment}

The alignment of the pixmaps in the rect.

*See also* [setAlignment](kpixmapsequenceoverlaypainter.md#setAlignment)

### int KPixmapSequenceOverlayPainter::interval() const {#interval}

The interval between frames.

*See also* [setInterval](kpixmapsequenceoverlaypainter.md#setInterval)

### QPoint KPixmapSequenceOverlayPainter::offset() const {#offset}

The optional offset within the rect.

*See also* [setOffset](kpixmapsequenceoverlaypainter.md#setOffset)

### QRect KPixmapSequenceOverlayPainter::rect() const {#rect}

The optional rect to draw the pixmaps in.

*See also* [setRect](kpixmapsequenceoverlaypainter.md#setRect)

### KPixmapSequence KPixmapSequenceOverlayPainter::sequence() const {#sequence}

The sequence used to draw the overlay.

*See also* [setSequence](kpixmapsequenceoverlaypainter.md#setSequence)

### \[slot\] void KPixmapSequenceOverlayPainter::setAlignment(Qt::Alignment *align*) {#setAlignment}

Set the alignment of the sequence in rect.

`align` alignment of the overlay. [Qt::AlignJustify](https://doc.qt.io/qt-6/qt.html#AlignmentFlag-enum) does not make sense here.

Defaults to Qt::Center.

*See also* [alignment](kpixmapsequenceoverlaypainter.md#alignment)()

### \[slot\] void KPixmapSequenceOverlayPainter::setInterval(int *msecs*) {#setInterval}

Set the interval between frames. The default is 200.

*See also* [interval](kpixmapsequenceoverlaypainter.md#interval)()

### \[slot\] void KPixmapSequenceOverlayPainter::setOffset(const QPoint &*offset*) {#setOffset}

Set the offset relative to the placement determined by alignment and rect.

`offset` An optional offset which allows an absolute placement.

Defaults to an empty point.

*See also* [offset](kpixmapsequenceoverlaypainter.md#offset)()

### \[slot\] void KPixmapSequenceOverlayPainter::setRect(const QRect &*rect*) {#setRect}

Set the rect in which to place the sequence. Be aware that this optional property does not scale the pixmaps (except if it is smaller) but allows to change the placement.

`rect` The rect in which to draw the pixmap using alignment and offset. Be aware that setting a rect bigger than the widget can lead to weird painting errors.

Defaults to the widget's rect.

*See also* [rect](kpixmapsequenceoverlaypainter.md#rect)()

### \[slot\] void KPixmapSequenceOverlayPainter::setSequence(const KPixmapSequence &*seq*) {#setSequence}

Set the sequence to be used. By default the KDE busy sequence is used.

*See also* [sequence](kpixmapsequenceoverlaypainter.md#sequence)()

### \[slot\] void KPixmapSequenceOverlayPainter::setWidget(QWidget \**w*) {#setWidget}

Set the widget to draw the overlay on.

### \[slot\] void KPixmapSequenceOverlayPainter::start() {#start}

Start drawing the sequence.

The overlay will be drawn until a call to [stop](kpixmapsequenceoverlaypainter.md#stop)()

### \[slot\] void KPixmapSequenceOverlayPainter::stop() {#stop}

Stop drawing the overlay.
