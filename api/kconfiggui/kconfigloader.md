---
title: "KConfigLoader Class"
description: "A KConfigSkeleton that populates itself based on KConfigXT XML."
---

# KConfigLoader Class

A [KConfigSkeleton](kconfigskeleton.md) that populates itself based on KConfigXT XML.

- **Header:** `#include <KConfigLoader>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigGui)`
- **Inherits:** [KConfigSkeleton](kconfigskeleton.md)

## Public Functions

- [KConfigLoader(KSharedConfigPtr config, QIODevice \*xml, QObject \*parent = nullptr)](#KConfigLoader)
- [KConfigLoader(const KConfigGroup &config, QIODevice \*xml, QObject \*parent = nullptr)](#KConfigLoader-1)
- [KConfigLoader(const QString &configFile, QIODevice \*xml, QObject \*parent = nullptr)](#KConfigLoader-2)
- [KConfigSkeletonItem \*findItem(const QString &group, const QString &key) const](#findItem)
- [KConfigSkeletonItem \*findItemByName(const QString &name) const](#findItemByName)
- [QStringList groupList() const](#groupList)
- [bool hasGroup(const QString &group) const](#hasGroup)
- [QVariant property(const QString &name) const](#property)

## Detailed Description {#details}

This class allows one to ship an XML file and reconstitute it into a [KConfigSkeleton](kconfigskeleton.md) object at runtime. Common usage might look like this:

```cpp
QFile file(xmlFilePath);
KConfigLoader appletConfig(configFilePath, &file);
```

Alternatively, any [QIODevice](https://doc.qt.io/qt-6/qiodevice.html) may be used in place of [QFile](https://doc.qt.io/qt-6/qfile.html) in the example above.

[KConfigLoader](kconfigloader.md) is useful if it is not possible to use compiled code and by that the kconfig compiler cannot be used. Common examples are scripted plugins which want to provide a configuration interface. With the help of [KConfigLoader](kconfigloader.md) a dynamically loaded ui file can be populated with the stored values and also stored back to the config file.

An example for populating a QDialog with a dynamically populated UI with the help of a KConfigDialogManager:

```cpp
QDialog *dialog = new QDialog();
QFile xmlFile("path/to/kconfigxt.xml");
KConfigGroup cg = KSharedConfig::openConfig()->group(QString());
KConfigLoader *configLoader = new KConfigLoader(cg, &xmlFile, this);

// load the ui file
QUiLoader *loader = new QUiLoader(this);
QFile uiFile("path/to/userinterface.ui");
uiFile.open(QFile::ReadOnly);
QWidget *customConfigForm = loader->load(&uiFile, dialog);
uiFile.close();

KConfigDialogManager *manager = new KConfigDialogManager(customConfigForm, configLoader);
if (dialog->exec() == QDialog::Accepted) {
    manager->updateSettings();
}
```

Currently the following data types are supported:

- bools
- colors
- datetimes
- times
- enumerations
- fonts
- ints
- passwords
- paths
- strings
- stringlists
- uints
- urls
- doubles
- int lists
- longlongs
- path lists
- points
- pointfs
- rects
- rectfs
- sizes
- sizefs
- ulonglongs
- url lists

*See also* [QUiLoader](https://doc.qt.io/qt-6/quiloader.html), [Using KConfigXT](https://develop.kde.org/docs/features/configuration/kconfig_xt/), [Using a Designer UI File in Your C++ Application](https://doc.qt.io/qt-6/designer-using-a-ui-file.html)

## Member Function Documentation {#member-function-documentation}

### KConfigLoader::KConfigLoader(KSharedConfigPtr *config*, QIODevice \**xml*, QObject \**parent* = nullptr) {#KConfigLoader}

Creates a [KConfigSkeleton](kconfigskeleton.md) populated using the definition found in the desired KConfigXT `xml` data, as a child of `parent`.

This will in turn be stored in `config` object.

### KConfigLoader::KConfigLoader(const KConfigGroup &*config*, QIODevice \**xml*, QObject \**parent* = nullptr) {#KConfigLoader-1}

Creates a [KConfigSkeleton](kconfigskeleton.md) populated using the definition found in the desired KConfigXT `xml` data, as a child of `parent`.

This will in turn be stored in the `config` group to be used as the root for configuration items.

### KConfigLoader::KConfigLoader(const QString &*configFile*, QIODevice \**xml*, QObject \**parent* = nullptr) {#KConfigLoader-2}

Creates a [KConfigSkeleton](kconfigskeleton.md) populated using the definition found in the desired KConfigXT `xml` data, as a child of `parent`.

This will in turn be stored in `configFile`.

### KConfigSkeletonItem \*KConfigLoader::findItem(const QString &*group*, const QString &*key*) const {#findItem}

Finds the item for the given `group` and `key` in the config file.

Returns the associated [KConfigSkeletonItem](../kconfigcore/kconfigskeletonitem.md), or `nullptr` if none.

### KConfigSkeletonItem \*KConfigLoader::findItemByName(const QString &*name*) const {#findItemByName}

Finds an item by its `name`.

### QStringList KConfigLoader::groupList() const {#groupList}

Returns the list of groups defined by the KConfigXT schema.

### bool KConfigLoader::hasGroup(const QString &*group*) const {#hasGroup}

Returns whether a `group` exists.

### QVariant KConfigLoader::property(const QString &*name*) const {#property}

Returns the property of the item with the given `name` as a variant.
