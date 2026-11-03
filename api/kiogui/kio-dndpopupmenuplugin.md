---
title: "KIO::DndPopupMenuPlugin Class"
description: "Base class for drag and drop popup menus."
---

# KIO::DndPopupMenuPlugin Class

Base class for drag and drop popup menus. [More...](#details)

- **Header:** `#include <KIO/DndPopupMenuPlugin>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KIOGui)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kio-dndpopupmenuplugin-members.md)

## Public Functions

- [DndPopupMenuPlugin(QObject \*parent)](#DndPopupMenuPlugin)
- [QList\<QAction \*\> setup(const KFileItemListProperties &popupMenuInfo, const QUrl &destination)](#setup)

## Detailed Description {#details}

This can be used for adding dynamic menu items to the normal copy/move/link here menu appearing in KIO-based file managers. In the setup method you may check the properties of the dropped files, and if applicable, append your own [QAction](https://doc.qt.io/qt-6/qaction.html) that the user may trigger in the menu.

The plugin should have Json metadata and be installed into kf6/kio\_dnd/.

## Member Function Documentation {#member-function-documentation}

### DndPopupMenuPlugin::DndPopupMenuPlugin(QObject \**parent*) {#DndPopupMenuPlugin}

Constructor.

### \[pure virtual\] QList\<QAction \*\> DndPopupMenuPlugin::setup(const KFileItemListProperties &*popupMenuInfo*, const QUrl &*destination*) {#setup}

Implement the setup method in the plugin in order to create actions in the given actionCollection and add it to the menu using menu-\>addAction(). The popup menu will be set as parent of the actions.

`popupMenuInfo` all the information about the source URLs being dropped

`destination` the URL to where the file(s) were dropped

Returns a [QList](https://doc.qt.io/qt-6/qlist.html) with the QActions that will be plugged into the menu.
