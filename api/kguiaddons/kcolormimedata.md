---
title: "KColorMimeData Namespace"
description: "Drag-and-drop and clipboard mimedata manipulation for QColor objects."
---

# KColorMimeData Namespace

Drag-and-drop and clipboard mimedata manipulation for [QColor](https://doc.qt.io/qt-6/qcolor.html) objects. [More...](#details)

- Header: KColorMimeData
- CMake: find\_package(KF6 REQUIRED COMPONENTS GuiAddons) target\_link\_libraries(mytarget PRIVATE KF6::GuiAddons)

## Detailed Description {#details}

The according MIME type is set to application/x-color.

See the Qt drag'n'drop documentation.

## Function Documentation {#function-documentation}

### bool KColorMimeData::canDecode(const QMimeData \**mimeData*) {#canDecode}

Returns true if the MIME data `mimeData` contains a color object. First checks for application/x-color and if that fails, for a text/plain entry, which represents a color in the format \#hexnumbers

### QDrag \*KColorMimeData::createDrag(const QColor &*color*, QObject \**dragsource*) {#createDrag}

Creates a color drag object. Either you have to start this drag or delete it The drag object's mime data has the application/x-color and text/plain type set and a pixmap filled with the specified color, which is going to be displayed next to the mouse cursor

### QColor KColorMimeData::fromMimeData(const QMimeData \**mimeData*) {#fromMimeData}

Decodes the MIME data `mimeData` and returns the resulting color. First tries application/x-color and if that fails, a text/plain entry, which represents a color in the format \#hexnumbers. If this fails too, an invalid [QColor](https://doc.qt.io/qt-6/qcolor.html) object is returned, use [QColor::isValid](https://doc.qt.io/qt-6/qcolor.html#isValid)() to test it.

### void KColorMimeData::populateMimeData(QMimeData \**mimeData*, const QColor &*color*) {#populateMimeData}

Sets the color and text representation fields for the specified color in the mimedata object: application/x-color and text/plain types are set
