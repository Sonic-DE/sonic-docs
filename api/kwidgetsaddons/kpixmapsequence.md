---
title: "KPixmapSequence Class"
description: "Loads and gives access to the frames of a typical multi-row pixmap as often used for spinners."
---

# KPixmapSequence Class

Loads and gives access to the frames of a typical multi-row pixmap as often used for spinners. [More...](#details)

- **Header:** `#include <KPixmapSequence>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`

[List of all members, including inherited members](kpixmapsequence-members.md)

## Public Functions

- [KPixmapSequence()](#KPixmapSequence)
- [KPixmapSequence(const QPixmap &pixmap, const QSize &frameSize = QSize())](#KPixmapSequence-1)
- [KPixmapSequence(const QString &fullPath, int size)](#KPixmapSequence-2)
- [QPixmap frameAt(int index) const](#frameAt)
- [int frameCount() const](#frameCount)
- [QSize frameSize() const](#frameSize)
- [bool isEmpty() const](#isEmpty)
- [bool isValid() const](#isValid)
- [KPixmapSequence &KPixmapSequence::operator=(const KPixmapSequence &other)](#operator-eq)

## Detailed Description {#details}

[KPixmapSequence](kpixmapsequence.md) is implicitly shared. Copying is fast.

## Member Function Documentation {#member-function-documentation}

### KPixmapSequence::KPixmapSequence() {#KPixmapSequence}

Create an empty sequence

### \[explicit\] KPixmapSequence::KPixmapSequence(const QPixmap &*pixmap*, const QSize &*frameSize* = QSize()) {#KPixmapSequence-1}

Create a sequence from a pixmap.

`pixmap` Pixmap to load

`frameSize` The size of the frames to load. The width of the file has to be a multiple of the frame width; the same is true for the height. If an invalid size is specified the file is considered to be one column of square frames.

### KPixmapSequence::KPixmapSequence(const QString &*fullPath*, int *size*) {#KPixmapSequence-2}

Create a sequence from an icon name.

`fullPath` The full path of the icon

`size` The icon/frame size

### QPixmap KPixmapSequence::frameAt(int *index*) const {#frameAt}

Retrieve the frame at `index`.

`index` The index of the frame in question starting at 0.

### int KPixmapSequence::frameCount() const {#frameCount}

The number of frames in this sequence.

### QSize KPixmapSequence::frameSize() const {#frameSize}

Returns The size of an individual frame in the sequence.

### bool KPixmapSequence::isEmpty() const {#isEmpty}

Returns `true` if no sequence was loaded successfully.

*See also* [isValid](kpixmapsequence.md#isValid)()

### bool KPixmapSequence::isValid() const {#isValid}

Returns `true` if a sequence was loaded successfully.

*See also* [isEmpty](kpixmapsequence.md#isEmpty)()

### KPixmapSequence &KPixmapSequence::operator=(const KPixmapSequence &*other*) {#operator-eq}

Create a copy of `other`. The data is implicitly shared.
