---
title: "KSystemClipboard Class"
description: "Clipboard access for unfocussed windows."
---

# KSystemClipboard Class

Clipboard access for unfocussed windows. [More...](#details)

- **Header:** `#include <KSystemClipboard>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS GuiAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::GuiAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](ksystemclipboard-members.md)

## Public Functions

- [void clear(QClipboard::Mode mode)](#clear)
- [const QMimeData \*mimeData(QClipboard::Mode mode) const](#mimeData)
- [bool ownsClipboard() const](#ownsClipboard) (since 6.29)
- [bool ownsSelection() const](#ownsSelection) (since 6.29)
- [void setMimeData(QMimeData \*mime, QClipboard::Mode mode)](#setMimeData)
- [QString text(QClipboard::Mode mode)](#text)

## Signals

- [void changed(QClipboard::Mode mode)](#changed)

## Static Public Members

- [KSystemClipboard \*instance()](#instance)

## Detailed Description {#details}

This class mimics [QClipboard](https://doc.qt.io/qt-6/qclipboard.html) but unlike [QClipboard](https://doc.qt.io/qt-6/qclipboard.html) it will continue to get updates even when our window does not have focus.

This may require extra access permissions

## Member Function Documentation {#member-function-documentation}

### \[signal\] void KSystemClipboard::changed(QClipboard::Mode *mode*) {#changed}

Emitted when the clipboard changes similar to [QClipboard::changed](https://doc.qt.io/qt-6/qclipboard.html#changed)

### \[pure virtual\] void KSystemClipboard::clear(QClipboard::Mode *mode*) {#clear}

Clears the current clipboard

### \[static\] KSystemClipboard \*KSystemClipboard::instance() {#instance}

Returns a shared global SystemClipboard instance

### \[pure virtual\] const QMimeData \*KSystemClipboard::mimeData(QClipboard::Mode *mode*) const {#mimeData}

Returns the current mime data received by the clipboard

*See also* [setMimeData](ksystemclipboard.md#setMimeData)()

### \[since 6.29\] bool KSystemClipboard::ownsClipboard() const {#ownsClipboard}

Returns true if this process owns the current clipboard selection.

This function was introduced in Qt 6.29.

### \[since 6.29\] bool KSystemClipboard::ownsSelection() const {#ownsSelection}

Returns true if this process owns the current primary selection.

This function was introduced in Qt 6.29.

### \[pure virtual\] void KSystemClipboard::setMimeData(QMimeData \**mime*, QClipboard::Mode *mode*) {#setMimeData}

Sets the clipboard to the new contents The clipboard takes ownership of mime

*See also* [mimeData](ksystemclipboard.md#mimeData)()

### QString KSystemClipboard::text(QClipboard::Mode *mode*) {#text}

Returns the text content of the Clipboard

Similar to [QClipboard::text](https://doc.qt.io/qt-6/qclipboard.html#text)([QClipboard::Mode](https://doc.qt.io/qt-6/qclipboard.html#Mode-enum) mode)
