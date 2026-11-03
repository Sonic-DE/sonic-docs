---
title: "KFileItemActionPluginV2 Class"
description: "KAbstractFileItemActionPlugin with a QObject-based actions() replacement. This class was introduced in Qt 6.32."
---

# KFileItemActionPluginV2 Class

[KAbstractFileItemActionPlugin](kabstractfileitemactionplugin.md) with a [QObject](https://doc.qt.io/qt-6/qobject.html)-based [actions](kabstractfileitemactionplugin.md#actions)() replacement. This class was introduced in Qt 6.32. [More...](#details)

- **Header:** `#include <KFileItemActionPluginV2>`
- **Since:** Qt 6.32
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [KAbstractFileItemActionPlugin](kabstractfileitemactionplugin.md)

[List of all members, including inherited members](kfileitemactionpluginv2-members.md)

## Public Functions

- [QList\<QAction \*\> actionsForParent(const KFileItemListProperties &fileItemInfos, QObject \*parent, const QUrl &currentWorkingDirectory)](#actionsForParent)

## Detailed Description {#details}

[actions](kabstractfileitemactionplugin.md#actions)() requires a [QWidget](https://doc.qt.io/qt-6/qwidget.html) to parent the returned QActions to, but some callers (e.g. Plasma's desktop containment) have no widget to offer, which leaves those actions without an owner. Plugins that need a guaranteed owner for their actions can inherit from this class instead of [KAbstractFileItemActionPlugin](kabstractfileitemactionplugin.md) directly, and implement [actionsForParent](kfileitemactionpluginv2.md#actionsForParent)() instead of [actions](kabstractfileitemactionplugin.md#actions)(); [KFileItemActions](kfileitemactions.md) calls it with a [QObject](https://doc.qt.io/qt-6/qobject.html) that is never null, even when no [QWidget](https://doc.qt.io/qt-6/qwidget.html) is available (see [KFileItemActions::setParentObject](kfileitemactions.md#setParentObject)()). [actions](kabstractfileitemactionplugin.md#actions)() itself is implemented here to forward to [actionsForParent](kfileitemactionpluginv2.md#actionsForParent)(), so plugins only need to implement the latter.

## Member Function Documentation {#member-function-documentation}

### \[pure virtual\] QList\<QAction \*\> KFileItemActionPluginV2::actionsForParent(const KFileItemListProperties &*fileItemInfos*, QObject \**parent*, const QUrl &*currentWorkingDirectory*) {#actionsForParent}

Like [KAbstractFileItemActionPlugin::actions](kabstractfileitemactionplugin.md#actions)(), but takes a [QObject](https://doc.qt.io/qt-6/qobject.html) instead of a [QWidget](https://doc.qt.io/qt-6/qwidget.html), so the returned actions can always be given a valid owner.

`fileItemInfos` Information about the selected file items.

`parent` Never null. To be used as parent for the returned QActions. May or may not be a [QWidget](https://doc.qt.io/qt-6/qwidget.html); use [qobject\_cast](https://doc.qt.io/qt-6/qobject.html#qobject_cast)\<[QWidget](https://doc.qt.io/qt-6/qwidget.html) \*\> to check.

`currentWorkingDirectory` The folder the actions are being requested for (e.g. the folder currently shown in the view). Lets a plugin tell whether fileItemInfos refers to this folder itself or to item(s) within it, and present different actions accordingly. May be empty if the caller has no such notion, or if invoked through the [actions](kabstractfileitemactionplugin.md#actions)() fallback above.

Returns a list of actions to be added to a contextual menu for the file items.
