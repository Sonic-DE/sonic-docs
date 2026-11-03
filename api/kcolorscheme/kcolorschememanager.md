---
title: "KColorSchemeManager Class"
description: "A small helper to get access to all available color schemes and activating a scheme in the QApplication."
---

# KColorSchemeManager Class

A small helper to get access to all available color schemes and activating a scheme in the [QApplication](https://doc.qt.io/qt-6/qapplication.html). [More...](#details)

- **Header:** `#include <KColorSchemeManager>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ColorScheme)`  
  `target_link_libraries(mytarget PRIVATE KF6::ColorScheme)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kcolorschememanager-members.md)  
[Deprecated members](kcolorschememanager-obsolete.md)

## Public Functions

- [QString activeSchemeId() const](#activeSchemeId)
- [QString activeSchemeName() const](#activeSchemeName) (since 6.6)
- [QModelIndex indexForScheme(const QString &name) const](#indexForScheme)
- [QModelIndex indexForSchemeId(const QString &id) const](#indexForSchemeId) (since 6.6)
- [QAbstractItemModel \*model() const](#model)
- [void saveSchemeIdToConfigFile(const QString &schemeId) const](#saveSchemeIdToConfigFile) (since 6.19)
- [void setAutosaveChanges(bool autosaveChanges)](#setAutosaveChanges)

## Public Slots

- [void activateScheme(const QModelIndex &index)](#activateScheme)
- [void activateSchemeId(const QString &schemeId)](#activateSchemeId) (since 6.19)

## Static Public Members

- [KColorSchemeManager \*instance()](#instance) (since 6.6)

## Detailed Description {#details}

This is useful for applications which want to provide a selection of custom color schemes to their user. For example it is very common for photo and painting applications to use a dark color scheme even if the default is a light scheme. Since version 5.67 it also allows going back to following the system color scheme.

The [model](kcolorschememanager.md#model)() member function provides access to the [KColorSchemeModel](kcolorschememodel.md) that the [KColorSchemeManager](kcolorschememanager.md) uses which holds all the available color schemes. A possible usage looks like the following:

```cpp
KColorSchemeManager *manager = new KColorSchemeManager(this);
QListView *view = new QListView(this);
view->setModel(manager->model());
connect(view, &QListView::activated, manager, [manager] (const QModelIndex &index) {
    manager->activateSchemeId(index.data(KColorSchemeModel::IdRole).toString());
 });
```

A convenience function that creates a KActionMenu that contains and activates color schemes exists in [KColorSchemeMenu::createMenu](../kconfigwidgets/kcolorschememenu.md#createMenu)

By default [KColorSchemeManager](kcolorschememanager.md) remembers the activated color scheme and restores it on the next start of the application. Use [setAutosaveChanges](kcolorschememanager.md#setAutosaveChanges)() to change this behavior.

*See also* [KColorSchemeMenu::createMenu](../kconfigwidgets/kcolorschememenu.md#createMenu), [KColorSchemeModel](kcolorschememodel.md)

## Member Function Documentation {#member-function-documentation}

### \[slot\] void KColorSchemeManager::activateScheme(const QModelIndex &*index*) {#activateScheme}

Activates the [KColorScheme](kcolorscheme-module.md) identified by the provided *index*.

Installs the [KColorScheme](kcolorscheme-module.md) as the [QApplication](https://doc.qt.io/qt-6/qapplication.html)'s [QPalette](https://doc.qt.io/qt-6/qpalette.html).

*index* The index for the [KColorScheme](kcolorscheme-module.md) to activate. The index must reference the [QAbstractItemModel](https://doc.qt.io/qt-6/qabstractitemmodel.html) provided by [model](kcolorschememanager.md#model)(). Since version 5.67 passing an invalid index activates the system scheme.

*See also* [model](kcolorschememanager.md#model)()

### \[slot, since 6.19\] void KColorSchemeManager::activateSchemeId(const QString &*schemeId*) {#activateSchemeId}

Activates the [KColorScheme](kcolorscheme-module.md) identified by the provided *schemeId*.

Installs the [KColorScheme](kcolorscheme-module.md) as the [QApplication](https://doc.qt.io/qt-6/qapplication.html)'s [QPalette](https://doc.qt.io/qt-6/qpalette.html).

*schemeId* The id for the [KColorScheme](kcolorscheme-module.md) to activate. Passing an empty id activates the system scheme.

This function was introduced in Qt 6.19.

*See also* [model](kcolorschememanager.md#model)()

### QString KColorSchemeManager::activeSchemeId() const {#activeSchemeId}

Returns the id of the currently active scheme or an empty string if the default scheme is active.

### \[since 6.6\] QString KColorSchemeManager::activeSchemeName() const {#activeSchemeName}

Returns the name of the currently active scheme or an empty string if the default scheme is active.

This function was introduced in Qt 6.6.

### QModelIndex KColorSchemeManager::indexForScheme(const QString &*name*) const {#indexForScheme}

Returns the model index for the scheme with the given *name*. If no such scheme exists an invalid index is returned. If you pass an empty string the index that is equivalent to going back to following the system scheme is returned for versions 5.67 and newer.

*See also* [model](kcolorschememanager.md#model)

### \[since 6.6\] QModelIndex KColorSchemeManager::indexForSchemeId(const QString &*id*) const {#indexForSchemeId}

Returns the model index for the scheme with the given *id*. If no such scheme exists an invalid index is returned. If you pass an empty string the index returned is equivalent to going back to following the system scheme.

This function was introduced in Qt 6.6.

*See also* [model](kcolorschememanager.md#model)

### \[static, since 6.6\] KColorSchemeManager \*KColorSchemeManager::instance() {#instance}

Returns the manager for the current application instance. If no instance is existing, it will be constructed. Must be called after construction of the gui application instance.

Returns color scheme manager for the current application instance

This function was introduced in Qt 6.6.

### QAbstractItemModel \*KColorSchemeManager::model() const {#model}

A [QAbstractItemModel](https://doc.qt.io/qt-6/qabstractitemmodel.html) of all available color schemes.

The model provides the name of the scheme in [Qt::DisplayRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum), a preview in Qt::DelegateRole and the full path to the scheme file in [Qt::UserRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum). The system theme has an empty [Qt::UserRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum).

Returns Model of all available color schemes.

*See also* [KColorSchemeModel](kcolorschememodel.md)

### \[since 6.19\] void KColorSchemeManager::saveSchemeIdToConfigFile(const QString &*schemeId*) const {#saveSchemeIdToConfigFile}

Saves the color scheme to config file. The scheme is saved by default whenever it's changed. Use this method when autosaving is turned off, see [setAutosaveChanges](kcolorschememanager.md#setAutosaveChanges)().

This function was introduced in Qt 6.19.

### void KColorSchemeManager::setAutosaveChanges(bool *autosaveChanges*) {#setAutosaveChanges}

Sets color scheme autosaving. Default value is `true`. If this is set to `false`, the scheme is not going to be remembered when the application is restarted.

*autosaveChanges* Enables/Disables autosaving of the color scheme.
