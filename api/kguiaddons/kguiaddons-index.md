---
title: "KGuiAddons"
description: "Additions to Qt Gui."
---

# KGuiAddons

Additions to Qt Gui.

[KGuiAddons](kguiaddons-module.md) are addons to [QtGui](https://doc.qt.io/qt-6/qtgui-module.html). They provide utilities for graphical user interfaces in the areas of colors, fonts, text, images, and keyboard input.

## Color utilities {#color-utilities}

The [KColorUtils](kcolorutils.md) namespace contains various small utilities to work with colors. KColorCollection provides handling of color collections ("pallettes"). [KColorMimeData](kcolormimedata.md) adds drag-and-drop and clipboard mimedata manipulation to [QColor](https://doc.qt.io/qt-6/qcolor.html) objects

## Text utilities {#text-utilities}

[KWordWrap](kwordwrap.md) is a special word wrapping algorithm that takes beauty into account. It can be used directly with [QPainter](https://doc.qt.io/qt-6/qpainter.html) or can return the wrapped text in a [QString](https://doc.qt.io/qt-6/qstring.html).

[KDateValidator](kdatevalidator.md) is a [QValidator](https://doc.qt.io/qt-6/qvalidator.html) that validates user-entered dates.

[KFontUtils::adaptFontSize](kfontutils.md#adaptFontSize)() is a function that calculates the biggest font size (in points) that can be used to draw a text centered in a rectangle using word wrapping.

## Keyboard utilities {#keyboard-utilities}

[KKeySequenceRecorder](kkeysequencerecorder.md) is a utility that records a [QKeySequence](https://doc.qt.io/qt-6/qkeysequence.html) by listening to key events in a window. This can be used to let the user modify predefined keyboard shortcuts for example.

## Icon utilities {#icon-utilities}

[KIconUtils](kiconutils.md) contains functions to add overlays on top of a [QIcon](https://doc.qt.io/qt-6/qicon.html).

## Cursor utilities {#cursor-utilities}

[KCursorSaver](kcursorsaver.md) is used to temporarily set a mouse cursor and restore the previous one on destruction.

## Using the Module {#using-the-module}

Using a Qt module's C++ API requires linking against the module library, either directly or through other dependencies. Several build tools have dedicated support for this, including CMake and [qmake](https://doc.qt.io/qt-6/resources.html#qmake).

### Building with CMake {#building-with-cmake}

Use the `find_package()` command to locate the needed module component in the `Qt6` package:

```cpp
find_package(Qt6 REQUIRED COMPONENTS KF6)
target_link_libraries(mytarget PRIVATE Qt6::KF6)
```

For more details, see the Build with CMake overview.

## API Reference {#api-reference}

- [KGuiAddons C++ Classes](kguiaddons-module.md)
- [KGuiAddons QML Types](org-kde-guiaddons-qmlmodule.md)
