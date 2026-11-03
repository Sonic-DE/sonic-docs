---
title: "KIO::KUriFilterSearchProviderActions Class"
description: "This class is a manager for web shortcuts."
---

# KIO::KUriFilterSearchProviderActions Class

This class is a manager for web shortcuts. [More...](#details)

- **Header:** `#include <KIO/KUriFilterSearchProviderActions>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kio-kurifiltersearchprovideractions-members.md)

## Public Functions

- [KUriFilterSearchProviderActions(QObject \*parent = nullptr)](#KUriFilterSearchProviderActions)
- [void addWebShortcutsToMenu(QMenu \*menu)](#addWebShortcutsToMenu)
- [QString selectedText() const](#selectedText)
- [void setSelectedText(const QString &selectedText)](#setSelectedText)

## Detailed Description {#details}

It will provide a list of web shortcuts against a selected text

You can set the selected text with [setSelectedText](kio-kurifiltersearchprovideractions.md#setSelectedText)() function

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KUriFilterSearchProviderActions::KUriFilterSearchProviderActions(QObject \**parent* = nullptr) {#KUriFilterSearchProviderActions}

Constructs a webshorts menu manager.

`parent` The [QObject](https://doc.qt.io/qt-6/qobject.html) parent.

### void KUriFilterSearchProviderActions::addWebShortcutsToMenu(QMenu \**menu*) {#addWebShortcutsToMenu}

Add web shortcut actions to existing menu. `menu` menu to add shortcuts to

### QString KUriFilterSearchProviderActions::selectedText() const {#selectedText}

Returns the selected text

*See also* [setSelectedText](kio-kurifiltersearchprovideractions.md#setSelectedText)()

### void KUriFilterSearchProviderActions::setSelectedText(const QString &*selectedText*) {#setSelectedText}

Set selected text `selectedText` the text to search for

*See also* [selectedText](kio-kurifiltersearchprovideractions.md#selectedText)()
