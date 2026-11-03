---
title: "KFilePlaceEditDialog Class"
description: "A dialog that allows editing entries of a KFilePlacesModel. This class is deprecated since 6.27. We strongly advise against using it in new code."
---

# KFilePlaceEditDialog Class

A dialog that allows editing entries of a [KFilePlacesModel](kfileplacesmodel.md). **This class is deprecated since 6.27. We strongly advise against using it in new code.** [More...](#details)

- **Header:** `#include <KFilePlaceEditDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOFileWidgets)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)
- **Status:** Deprecated since 6.27

[List of all members, including inherited members](kfileplaceeditdialog-members.md)

## Public Functions

- [KFilePlaceEditDialog(bool allowGlobal, const QUrl &url, const QString &label, const QString &icon, bool isAddingNewPlace, bool appLocal = true, int iconSize = 32, QWidget \*parent = nullptr)](#KFilePlaceEditDialog)
- [bool applicationLocal() const](#applicationLocal)
- [QString icon() const](#icon)
- [QString label() const](#label)
- [QUrl url() const](#url)

## Public Slots

- [void urlChanged(const QString &)](#urlChanged)

## Static Public Members

- [bool getInformation(bool allowGlobal, QUrl &url, QString &label, QString &icon, bool isAddingNewPlace, bool &appLocal, int iconSize, QWidget \*parent = nullptr)](#getInformation)

**This class is deprecated since 6.27. We strongly advise against using it in new code.**

## Detailed Description {#details}

The dialog offers to configure a given url, label and icon. See the class-method [getInformation](kfileplaceeditdialog.md#getInformation)() for easy usage.

Only internally used.

## Member Function Documentation {#member-function-documentation}

### KFilePlaceEditDialog::KFilePlaceEditDialog(bool *allowGlobal*, const QUrl &*url*, const QString &*label*, const QString &*icon*, bool *isAddingNewPlace*, bool *appLocal* = true, int *iconSize* = 32, QWidget \**parent* = nullptr) {#KFilePlaceEditDialog}

Constructs a [KFilePlaceEditDialog](kfileplaceeditdialog.md).

`allowGlobal` if you set this to true, the dialog will have a checkbox for the user to decide if he wants the entry to be available globally or just for the current application.

`url` the url of the item

`label` a short, translated description of the item

`icon` an icon for the item

`appLocal` tells whether the item should be local for this application or be available globally

`iconSize` determines the size of the icon that is shown/selectable

`parent` the parent-widget for the dialog

If you leave the icon empty, the default icon for the given url will be used (KMimeType::pixmapForUrl()).

### bool KFilePlaceEditDialog::applicationLocal() const {#applicationLocal}

Returns whether the item should be local to the application or global. If allowGlobal was set to false in the constructor, this will always return true.

### \[static\] bool KFilePlaceEditDialog::getInformation(bool *allowGlobal*, QUrl &*url*, QString &*label*, QString &*icon*, bool *isAddingNewPlace*, bool &*appLocal*, int *iconSize*, QWidget \**parent* = nullptr) {#getInformation}

A convenience method to show the dialog and retrieve all the properties via the given parameters. The parameters are used to initialize the dialog and then return the user-configured values.

`allowGlobal` if you set this to true, the dialog will have a checkbox for the user to decide if he wants the entry to be available globally or just for the current application.

`url` the url of the item

`label` a short, translated description of the item

`icon` an icon for the item

`appLocal` tells whether the item should be local for this application or be available globally

`iconSize` determines the size of the icon that is shown/selectable

`parent` the parent-widget for the dialog

If you leave the icon empty, the default icon for the given url will be used (KMimeType::pixmapForUrl()).

### QString KFilePlaceEditDialog::icon() const {#icon}

Returns the configured icon

### QString KFilePlaceEditDialog::label() const {#label}

Returns the configured label

### QUrl KFilePlaceEditDialog::url() const {#url}

Returns the configured url

### \[slot\] void KFilePlaceEditDialog::urlChanged(*const QString &*) {#urlChanged}
