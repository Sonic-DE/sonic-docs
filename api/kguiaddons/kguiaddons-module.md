---
title: "KGuiAddons C++ Classes"
description: "Addons to QtGui."
---

# KGuiAddons C++ Classes

Addons to [QtGui](https://doc.qt.io/qt-6/qtgui-module.html). [More...](#details)

## Namespaces {#namespaces}

- [KColorMimeData](kcolormimedata.md): Drag-and-drop and clipboard mimedata manipulation for QColor objects.
- [KColorUtils](kcolorutils.md): A set of methods used to work with colors.
- [KFontUtils](kfontutils.md): Provides utility functions for font data.
- [KIconUtils](kiconutils.md): Provides utility functions for icons.
- [KJobWindows](kjobwindows.md): Associate jobs with a window.

## Classes {#classes}

- [KCountryFlagEmojiIconEngine](kcountryflagemojiiconengine.md): Provides emoji flags as icons This is a special icon engine that internally paints flags using emoji fonts. It provides access to country and region flags from the system emoji font.
- [KCursorSaver](kcursorsaver.md): Class to temporarily set a mouse cursor and restore the previous one on destruction.
- [KDateValidator](kdatevalidator.md): Validates user-entered dates.
- [KKeySequenceRecorder](kkeysequencerecorder.md): Record a QKeySequence by listening to key events in a window.
- [KModifierKeyInfo](kmodifierkeyinfo.md): Get information about the state of the keyboard's modifier keys.
- [KSharedPixmapCacheMixin](ksharedpixmapcachemixin.md): A simple wrapping layer over KSharedDataCache to support caching images and pixmaps.
- [KSystemClipboard](ksystemclipboard.md): Clipboard access for unfocussed windows.
- [KSystemInhibitor](ksysteminhibitor.md): Inhibit system actions such as logout, suspend, etc.
- [KWindowInsetsController](kwindowinsetscontroller.md): Access to window insets colors.
- [KWordWrap](kwordwrap.md): Word-wrap algorithm that takes into account beautifulness.

## Detailed Description {#details}

They provide utilities for graphical user interfaces in the areas of colors, fonts, text, images, keyboard input.

### Color utilities {#color-utilities}

The [KColorUtils](kcolorutils.md) namespace contains various small utilities to work with colors. KColorCollection provides handling of color collections ("pallettes"). [KColorMimeData](kcolormimedata.md) adds drag-and-drop and clipboard mimedata manipulation to [QColor](https://doc.qt.io/qt-6/qcolor.html) objects

### Text utilities {#text-utilities}

[KWordWrap](kwordwrap.md) is a special word wrapping algorithm that takes beauty into account. It can be used directly with [QPainter](https://doc.qt.io/qt-6/qpainter.html) or can return the wrapped text in a [QString](https://doc.qt.io/qt-6/qstring.html).

[KDateValidator](kdatevalidator.md) is a [QValidator](https://doc.qt.io/qt-6/qvalidator.html) that validates user-entered dates.

[KFontUtils::adaptFontSize](kfontutils.md#adaptFontSize)() is a function that calculates the biggest font size (in points) that can be used to draw a text centered in a rectangle using word wrapping.

### Keyboard utilities {#keyboard-utilities}

[KKeySequenceRecorder](kkeysequencerecorder.md) is a utility that records a [QKeySequence](https://doc.qt.io/qt-6/qkeysequence.html) by listening to key events in a window. This can be used to let the user modify predefined keyboard shortcuts for example.

### Icon utilities {#icon-utilities}

[KIconUtils](kiconutils.md) contains functions to add overlays on top of a [QIcon](https://doc.qt.io/qt-6/qicon.html).

### Cursor utilities {#cursor-utilities}

[KCursorSaver](kcursorsaver.md) is used to temporarily set a mouse cursor and restore the previous one on destruction.
