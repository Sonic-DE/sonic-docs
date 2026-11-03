---
title: "Plasma::PluginLoader Class"
description: "Loader for Plasma plugins."
---

# Plasma::PluginLoader Class

Loader for Plasma plugins. [More...](#details)

- **Header:** `#include <Plasma/PluginLoader>`
- **CMake:** `find_package(Plasma REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Plasma::Plasma)`

[List of all members, including inherited members](plasma-pluginloader-members.md)

## Public Functions

- [QList\<KPluginMetaData\> listAppletMetaData(const QString &category)](#listAppletMetaData)
- [QList\<KPluginMetaData\> listAppletMetaDataForMimeType(const QString &mimetype)](#listAppletMetaDataForMimeType)
- [QList\<KPluginMetaData\> listAppletMetaDataForUrl(const QUrl &url)](#listAppletMetaDataForUrl)
- [QList\<KPluginMetaData\> listContainmentActionsMetaData(const QString &parentApp)](#listContainmentActionsMetaData)
- [Plasma::Applet \*loadApplet(const QString &name, uint appletId = 0, const QVariantList &args = QVariantList())](#loadApplet)
- [Plasma::ContainmentActions \*loadContainmentActions(Plasma::Containment \*parent, const QString &containmentActionsName, const QVariantList &args = QVariantList())](#loadContainmentActions)

## Static Public Members

- [QList\<KPluginMetaData\> listContainmentsMetaData(std::function\<bool (const KPluginMetaData &)\> filter = {})](#listContainmentsMetaData)
- [QList\<KPluginMetaData\> listContainmentsMetaDataOfType(const QString &type)](#listContainmentsMetaDataOfType)
- [Plasma::PluginLoader \*self()](#self)

## Detailed Description {#details}

This class is used to list and load various Plasma-related plugins.

## Member Function Documentation {#member-function-documentation}

### QList\<KPluginMetaData\> PluginLoader::listAppletMetaData(const QString &*category*) {#listAppletMetaData}

Returns a list of all known applets.

This may skip applets based on security settings and ExcludeCategories in the application's config.

`category` Only applets matching this category will be returned. If "Misc" is passed in, then applets without a Categories= entry are also returned. If an empty string is passed in, all applets are returned.

### QList\<KPluginMetaData\> PluginLoader::listAppletMetaDataForMimeType(const QString &*mimetype*) {#listAppletMetaDataForMimeType}

Returns a list of all known applets associated with a certain mimetype.

### QList\<KPluginMetaData\> PluginLoader::listAppletMetaDataForUrl(const QUrl &*url*) {#listAppletMetaDataForUrl}

Returns a list of all known applets associated with a certain URL.

### QList\<KPluginMetaData\> PluginLoader::listContainmentActionsMetaData(const QString &*parentApp*) {#listContainmentActionsMetaData}

Returns a list of all known [ContainmentActions](plasma-containmentactions.md).

`parentApp` the application to filter [ContainmentActions](plasma-containmentactions.md) on. Uses the X-KDE-ParentApp entry (if any) in the plugin metadata. The default value of QString() will result in a list of all [ContainmentActions](plasma-containmentactions.md).

### \[static\] QList\<KPluginMetaData\> PluginLoader::listContainmentsMetaData(std::function\<bool (const KPluginMetaData &)\> *filter* = {}) {#listContainmentsMetaData}

Returns a list of all known containments.

`filter` An optional predicate that can be used for filtering.

### \[static\] QList\<KPluginMetaData\> PluginLoader::listContainmentsMetaDataOfType(const QString &*type*) {#listContainmentsMetaDataOfType}

Returns a list of containments of the specified type.

`type` The target containment type

### Plasma::Applet \*PluginLoader::loadApplet(const QString &*name*, uint *appletId* = 0, const QVariantList &*args* = QVariantList()) {#loadApplet}

Load an Applet plugin.

`name` the plugin id, as returned by KPluginMetaData::pluginId()

`appletId` unique ID to assign the applet, or zero to have one assigned automatically.

`args` to send the applet extra arguments

Returns a pointer to the loaded applet. Should never return `nullptr`

### Plasma::ContainmentActions \*PluginLoader::loadContainmentActions(Plasma::Containment \**parent*, const QString &*containmentActionsName*, const QVariantList &*args* = QVariantList()) {#loadContainmentActions}

Load a [ContainmentActions](plasma-containmentactions.md) plugin.

Returns a pointer to the containmentactions if successful.

The caller takes responsibility for the containmentactions, including deleting it when no longer needed.

`parent` the parent containment, or `nullptr`

`name` the plugin name, as returned by KPluginMetaData::pluginId()

`args` to send the containmentactions extra arguments

### \[static\] Plasma::PluginLoader \*PluginLoader::self() {#self}

Return the plugin loader instance
