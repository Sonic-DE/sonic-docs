---
title: "PlasmaQuick::ConfigModel Class"
description: "This model contains all the possible config categories for a dialog, such as categories of the config dialog for an Applet."
---

# PlasmaQuick::ConfigModel Class

This model contains all the possible config categories for a dialog, such as categories of the config dialog for an Applet. [More...](#details)

- **Header:** `#include <PlasmaQuick/ConfigModel>`
- **CMake:** `find_package(PlasmaQuick REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Plasma::PlasmaQuick)`
- **In QML:** [ConfigModel](qml-org-kde-plasma-configuration-configmodel.md)
- **Inherits:** [QAbstractListModel](https://doc.qt.io/qt-6/qabstractlistmodel.html)

[List of all members, including inherited members](plasmaquick-configmodel-members.md)

## Public Types

- [enum ConfigModel::Roles](#Roles-enum)

## Properties

- [\[read-only\] categories : const QQmlListProperty\<PlasmaQuick::ConfigCategory\>](#categories-prop)
- [\[read-only\] count : int](#count-prop)

## Public Functions

- [ConfigModel(QObject \*parent = nullptr)](#ConfigModel)
- [void appendCategory(PlasmaQuick::ConfigCategory \*category)](#appendCategory)
- [void appendCategory(const QString &iconName, const QString &name, const QString &path, const QString &pluginName)](#appendCategory-1)
- [void appendCategory(const QString &iconName, const QString &name, const QString &path, const QString &pluginName, bool visible)](#appendCategory-2)
- [Plasma::Applet \*applet() const](#applet)
- [QQmlListProperty\<PlasmaQuick::ConfigCategory\> categories()](#categories)
- [void clear()](#clear)
- [int count()](#count)
- [QVariant get(int row) const](#get)
- [void removeCategory(PlasmaQuick::ConfigCategory \*category)](#removeCategory)
- [void removeCategoryAt(int index)](#removeCategoryAt)
- [void setApplet(Plasma::Applet \*interface)](#setApplet)

## Signals

- [void countChanged()](#countChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum ConfigModel::Roles {#Roles-enum}

| Constant |   |
| --- | --- |
| `PlasmaQuick::ConfigModel::NameRole` | `Qt::UserRole + 1` |
| `PlasmaQuick::ConfigModel::IconRole` | `258` |
| `PlasmaQuick::ConfigModel::SourceRole` | `259` |
| `PlasmaQuick::ConfigModel::PluginNameRole` | `260` |
| `PlasmaQuick::ConfigModel::VisibleRole` | `261` |
| `PlasmaQuick::ConfigModel::ConfigUiModule` | `262` |
| `PlasmaQuick::ConfigModel::ConfigUiComponent` | `263` |

## Property Documentation {#property-documentation}

### \[read-only\] categories : const QQmlListProperty\<PlasmaQuick::ConfigCategory\> {#categories-prop}

**Access functions:**

- `QQmlListProperty`\<`PlasmaQuick::ConfigCategory`\> **[categories](plasmaquick-configmodel.md#categories)**()

### \[read-only\] count : int {#count-prop}

**Access functions:**

- `int` **[count](plasmaquick-configmodel.md#count)**()

**Notifier signal:**

- `void` **[countChanged](plasmaquick-configmodel.md#countChanged)**()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ConfigModel::ConfigModel(QObject \**parent* = nullptr) {#ConfigModel}

### \[invokable\] void ConfigModel::appendCategory(PlasmaQuick::ConfigCategory \**category*) {#appendCategory}

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### void ConfigModel::appendCategory(const QString &*iconName*, const QString &*name*, const QString &*path*, const QString &*pluginName*) {#appendCategory-1}

Add a new category in the model.

`ConfigCategory` the new category

### \[invokable\] void ConfigModel::appendCategory(const QString &*iconName*, const QString &*name*, const QString &*path*, const QString &*pluginName*, bool *visible*) {#appendCategory-2}

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### Plasma::Applet \*ConfigModel::applet() const {#applet}

*See also* [setApplet](plasmaquick-configmodel.md#setApplet)()

### QQmlListProperty\<PlasmaQuick::ConfigCategory\> ConfigModel::categories() {#categories}

Returns the categories of the model

> **Note:** Getter function for property [categories](plasmaquick-configmodel.md#categories-prop).

### void ConfigModel::clear() {#clear}

clears the model

### int ConfigModel::count() {#count}

> **Note:** Getter function for property [count](plasmaquick-configmodel.md#count-prop).

### \[signal\] void ConfigModel::countChanged() {#countChanged}

> **Note:** Notifier signal for property [count](plasmaquick-configmodel.md#count-prop).

### \[invokable\] QVariant ConfigModel::get(int *row*) const {#get}

`row` The row for which the data will be returned

Returns the data of the specified row

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void ConfigModel::removeCategory(PlasmaQuick::ConfigCategory \**category*) {#removeCategory}

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void ConfigModel::removeCategoryAt(int *index*) {#removeCategoryAt}

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### void ConfigModel::setApplet(Plasma::Applet \**interface*) {#setApplet}

*See also* [applet](plasmaquick-configmodel.md#applet)()
