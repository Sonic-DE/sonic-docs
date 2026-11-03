---
title: "KPropertiesDialogPlugin Class"
description: "A Plugin in the Properties dialog."
---

# KPropertiesDialogPlugin Class

A Plugin in the Properties dialog. [More...](#details)

- **Header:** `#include <KPropertiesDialogPlugin>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kpropertiesdialogplugin-members.md)

## Public Functions

- [KPropertiesDialogPlugin(QObject \*parent)](#KPropertiesDialogPlugin)
- [void applyChanges()](#applyChanges)
- [bool isDirty() const](#isDirty)
- [void setDirty(bool b = true)](#setDirty)

## Signals

- [void changed()](#changed)

## Protected Functions

- [int fontHeight() const](#fontHeight)

## Detailed Description {#details}

This is an abstract class. You must inherit from this class to build a new kind of tabbed page for the [KPropertiesDialog](kpropertiesdialog.md). A plugin in itself is just a library containing code, not a dialog's page. It's up to the plugin to insert pages into the parent dialog.

To make a plugin available, ensure it has embedded json metadata using [K\_PLUGIN\_CLASS\_WITH\_JSON](../kcoreaddons/kpluginfactory.md#K_PLUGIN_CLASS_WITH_JSON) and install the plugin in the KDE\_INSTALL\_PLUGINDIR/kf6/propertiesdialog folder from the KDEInstallDirs CMake module.

The metadata can contain the MIME types for which the plugin should be created. For instance:

```cpp
{
    "KPlugin": {
        "MimeTypes": ["text/html", "application/x-mymimetype"]
    },
    "X-KDE-Protocols": ["file"]
}
```

If the MIME types are empty or not specified, the plugin will be created for all MIME types.

You can also include "X-KDE-Protocols" if you want that plugin for instance to be loaded only for local files.

## Member Function Documentation {#member-function-documentation}

### KPropertiesDialogPlugin::KPropertiesDialogPlugin(QObject \**parent*) {#KPropertiesDialogPlugin}

Constructor whose parent will be cast to [KPropertiesDialog](kpropertiesdialog.md) To insert tabs into the properties dialog, use the add methods provided by KPageDialog (the properties dialog is a KPageDialog).

### \[virtual\] void KPropertiesDialogPlugin::applyChanges() {#applyChanges}

Applies all changes to the file. This function is called when the user presses 'Ok'. The last plugin inserted is called first.

### \[signal\] void KPropertiesDialogPlugin::changed() {#changed}

Emit this signal when the user changed anything in the plugin's tabs. The hosting PropertiesDialog will call [applyChanges](kpropertiesdialogplugin.md#applyChanges) only if the PropsPlugin has emitted this signal or if you have called [setDirty](kpropertiesdialogplugin.md#setDirty)() before.

### \[protected\] int KPropertiesDialogPlugin::fontHeight() const {#fontHeight}

Returns the font height.

### bool KPropertiesDialogPlugin::isDirty() const {#isDirty}

### void KPropertiesDialogPlugin::setDirty(bool *b* = true) {#setDirty}

*See also* [isDirty](kpropertiesdialogplugin.md#isDirty)()

## Member Variable Documentation {#member-variable-documentation}

### KPropertiesDialog \*const KPropertiesDialogPlugin::properties {#properties-var}

Pointer to the dialog
