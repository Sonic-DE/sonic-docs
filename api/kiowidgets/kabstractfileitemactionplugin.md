---
title: "KAbstractFileItemActionPlugin Class"
description: "Base class for KFileItemAction plugins."
---

# KAbstractFileItemActionPlugin Class

Base class for KFileItemAction plugins. [More...](#details)

- **Header:** `#include <KAbstractFileItemActionPlugin>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)
- **Inherited By:** [KFileItemActionPluginV2](kfileitemactionpluginv2.md)

[List of all members, including inherited members](kabstractfileitemactionplugin-members.md)

## Public Functions

- [KAbstractFileItemActionPlugin(QObject \*parent)](#KAbstractFileItemActionPlugin)
- [QList\<QAction \*\> actions(const KFileItemListProperties &fileItemInfos, QWidget \*parentWidget)](#actions)

## Signals

- [void error(const QString &errorMessage)](#error)

## Detailed Description {#details}

KFileItemAction plugins allow dynamic features to be added to the context menus for files and directories when browsing.

Most filetype-based popup menu items can be implemented using servicemenus linked to MIME types, and that should be the preferred way of doing this. However, complex scenarios such as showing submenus with a variable number of actions or only showing an item if exactly two files are selected need to be implemented as a KFileItemAction plugin.

To create such a plugin, subclass [KAbstractFileItemActionPlugin](kabstractfileitemactionplugin.md) and implement [actions](kabstractfileitemactionplugin.md#actions)() to return the actions to want to add to the context menu. Then create a plugin in the usual [KPluginFactory](../kcoreaddons/kpluginfactory.md) based way:

```cpp
K_PLUGIN_CLASS_WITH_JSON(MyActionPlugin, "myactionplugin.json")
#include <thisfile.moc>
```

A desktop file is necessary to register the plugin with the KDE plugin system:

```cpp
[Desktop Entry]
Type=Service
Name=My fancy action plugin
X-KDE-Library=myactionplugin
X-KDE-ServiceTypes=KFileItemAction/Plugin
MimeType=some/mimetype;
```

Note the KFileItemAction/Plugin service type which is used by KFileItemActions::addServicePluginActionsTo() to load all available plugins and the MimeType field which specifies for which types of file items the setup() method should be called.

The desktop file contents must also be compiled into the plugin as JSON data. The following CMake code builds and installs the plugin:

```cpp
kcoreaddons_add_plugin(myactionplugin SOURCES myactionplugin.cpp INSTALL_NAMESPACE "kf6/kfileitemaction")
kcoreaddons_desktop_to_json(myactionplugin myactionplugin.desktop) # generate the json file if necessary

target_link_libraries(myactionplugin KF5::KIOWidgets)
```

> **Note:** The plugin should be installed in the "kf5/kfileitemaction" subfolder of $QT\_PLUGIN\_PATH.

> **Note:** If the plugin has a lower priority and should show up in the "Actions" submenu, you can set the X-KDE-Show-In-Submenu property to true.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KAbstractFileItemActionPlugin::KAbstractFileItemActionPlugin(QObject \**parent*) {#KAbstractFileItemActionPlugin}

### \[pure virtual\] QList\<QAction \*\> KAbstractFileItemActionPlugin::actions(const KFileItemListProperties &*fileItemInfos*, QWidget \**parentWidget*) {#actions}

Implement the actions method in the plugin in order to create actions.

`fileItemInfos` Information about the selected file items.

`parentWidget` To be used as parent for the returned QActions

Returns a list of actions to be added to a contextual menu for the file items.

### \[signal\] void KAbstractFileItemActionPlugin::error(const QString &*errorMessage*) {#error}

Emits an error which will be displayed to the user
