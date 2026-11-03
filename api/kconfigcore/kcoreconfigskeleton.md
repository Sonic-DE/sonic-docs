---
title: "KCoreConfigSkeleton Class"
description: "Class for handling preferences settings for an application."
---

# KCoreConfigSkeleton Class

Class for handling preferences settings for an application. [More...](#details)

- **Header:** `#include <KCoreConfigSkeleton>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kcoreconfigskeleton-members.md)

## Public Types

- [enum KCoreConfigSkeleton::DisambiguateConstructor](#DisambiguateConstructor-enum)

## Public Functions

- [KCoreConfigSkeleton(KSharedConfig::Ptr config, QObject \*parent = nullptr)](#KCoreConfigSkeleton)
- [KCoreConfigSkeleton(const QString &configname = QString(), QObject \*parent = nullptr)](#KCoreConfigSkeleton-1)
- [KCoreConfigSkeleton(std::unique\_ptr\<KConfig\> config, KCoreConfigSkeleton::DisambiguateConstructor value, QObject \*parent = nullptr)](#KCoreConfigSkeleton-2) (since 6.23)
- [void addItem(KConfigSkeletonItem \*item, const QString &name = QString())](#addItem)
- [KCoreConfigSkeleton::ItemBool \*addItemBool(const QString &name, bool &reference, bool defaultValue = false, const QString &key = QString())](#addItemBool)
- [KCoreConfigSkeleton::ItemDateTime \*addItemDateTime(const QString &name, QDateTime &reference, const QDateTime &defaultValue = QDateTime(), const QString &key = QString())](#addItemDateTime)
- [KCoreConfigSkeleton::ItemDouble \*addItemDouble(const QString &name, double &reference, double defaultValue = 0.0, const QString &key = QString())](#addItemDouble)
- [KCoreConfigSkeleton::ItemInt \*addItemInt(const QString &name, qint32 &reference, qint32 defaultValue = 0, const QString &key = QString())](#addItemInt)
- [KCoreConfigSkeleton::ItemIntList \*addItemIntList(const QString &name, QList\<int\> &reference, const QList\<int\> &defaultValue = QList\<int\>(), const QString &key = QString())](#addItemIntList)
- [KCoreConfigSkeleton::ItemLongLong \*addItemLongLong(const QString &name, qint64 &reference, qint64 defaultValue = 0, const QString &key = QString())](#addItemLongLong)
- [KCoreConfigSkeleton::ItemPassword \*addItemPassword(const QString &name, QString &reference, const QString &defaultValue = QLatin1String(""), const QString &key = QString())](#addItemPassword)
- [KCoreConfigSkeleton::ItemPath \*addItemPath(const QString &name, QString &reference, const QString &defaultValue = QLatin1String(""), const QString &key = QString())](#addItemPath)
- [KCoreConfigSkeleton::ItemPathList \*addItemPathList(const QString &name, QList\<QString\> &reference, const QList\<QString\> &defaultValue = QList\<QString\>(), const QString &key = QString())](#addItemPathList) (since 6.27)
- [KCoreConfigSkeleton::ItemPoint \*addItemPoint(const QString &name, QPoint &reference, const QPoint &defaultValue = QPoint(), const QString &key = QString())](#addItemPoint)
- [KCoreConfigSkeleton::ItemPointF \*addItemPointF(const QString &name, QPointF &reference, const QPointF &defaultValue = QPointF(), const QString &key = QString())](#addItemPointF)
- [KCoreConfigSkeleton::ItemProperty \*addItemProperty(const QString &name, QVariant &reference, const QVariant &defaultValue = QVariant(), const QString &key = QString())](#addItemProperty)
- [KCoreConfigSkeleton::ItemRect \*addItemRect(const QString &name, QRect &reference, const QRect &defaultValue = QRect(), const QString &key = QString())](#addItemRect)
- [KCoreConfigSkeleton::ItemRectF \*addItemRectF(const QString &name, QRectF &reference, const QRectF &defaultValue = QRectF(), const QString &key = QString())](#addItemRectF)
- [KCoreConfigSkeleton::ItemSize \*addItemSize(const QString &name, QSize &reference, const QSize &defaultValue = QSize(), const QString &key = QString())](#addItemSize)
- [KCoreConfigSkeleton::ItemSizeF \*addItemSizeF(const QString &name, QSizeF &reference, const QSizeF &defaultValue = QSizeF(), const QString &key = QString())](#addItemSizeF)
- [KCoreConfigSkeleton::ItemString \*addItemString(const QString &name, QString &reference, const QString &defaultValue = QLatin1String(""), const QString &key = QString())](#addItemString)
- [KCoreConfigSkeleton::ItemStringList \*addItemStringList(const QString &name, QStringList &reference, const QStringList &defaultValue = QStringList(), const QString &key = QString())](#addItemStringList)
- [KCoreConfigSkeleton::ItemTime \*addItemTime(const QString &name, QTime &reference, QTime defaultValue = QTime(), const QString &key = QString())](#addItemTime) (since 6.16)
- [KCoreConfigSkeleton::ItemUInt \*addItemUInt(const QString &name, quint32 &reference, quint32 defaultValue = 0, const QString &key = QString())](#addItemUInt)
- [KCoreConfigSkeleton::ItemULongLong \*addItemULongLong(const QString &name, quint64 &reference, quint64 defaultValue = 0, const QString &key = QString())](#addItemULongLong)
- [KCoreConfigSkeleton::ItemUrlList \*addItemUrlList(const QString &name, QList\<QUrl\> &reference, const QList\<QUrl\> &defaultValue = QList\<QUrl\>(), const QString &key = QString())](#addItemUrlList) (since 6.27)
- [void clearItems()](#clearItems)
- [KConfig \*config()](#config)
- [const KConfig \*config() const](#config-1)
- [QString currentGroup() const](#currentGroup)
- [KConfigSkeletonItem \*findItem(const QString &name) const](#findItem)
- [bool isDefaults() const](#isDefaults)
- [bool isImmutable(const QString &name) const](#isImmutable)
- [bool isSaveNeeded() const](#isSaveNeeded)
- [KConfigSkeletonItem::List items() const](#items)
- [void load()](#load)
- [void read()](#read)
- [void removeItem(const QString &name)](#removeItem)
- [void setConfig(std::unique\_ptr\<KConfig\> config)](#setConfig) (since 6.23)
- [void setCurrentGroup(const QString &group)](#setCurrentGroup)
- [void setDefaults()](#setDefaults)
- [void setSharedConfig(KSharedConfig::Ptr pConfig)](#setSharedConfig)
- [KSharedConfig::Ptr sharedConfig() const](#sharedConfig)
- [bool useDefaults(bool b)](#useDefaults)

## Public Slots

- [bool save()](#save)

## Signals

- [void configChanged()](#configChanged)

## Protected Functions

- [void usrRead()](#usrRead)
- [bool usrSave()](#usrSave)
- [void usrSetDefaults()](#usrSetDefaults)
- [bool usrUseDefaults(bool b)](#usrUseDefaults)

## Detailed Description {#details}

This class provides an interface to settings that can be used to create preferences UIs. Use [KConfigSkeleton](../kconfiggui/kconfigskeleton.md) if you need GUI types like QColor and QFont as well.

Preferences items can be registered by the [addItem](kcoreconfigskeleton.md#addItem)() function corresponding to the data type of the setting. [KCoreConfigSkeleton](kcoreconfigskeleton.md) then handles reading and writing of config files and setting of default values.

Normally you will subclass [KCoreConfigSkeleton](kcoreconfigskeleton.md), add data members for the preferences settings and register the members in the constructor of the subclass.

Example:

```cpp
class MyPrefs : public KCoreConfigSkeleton
{
  public:
    MyPrefs()
    {
      setCurrentGroup("MyGroup");
      addItemBool("MySetting1", mMyBool, false);
      addItemPoint("MySetting2", mMyPoint, QPoint(100, 200));

      setCurrentGroup("MyOtherGroup");
      addItemDouble("MySetting3", mMyDouble, 3.14);
    }

    bool mMyBool;
    QPoint mMyPoint;
    double mMyDouble;
}
```

It might be convenient in many cases to make this subclass of [KCoreConfigSkeleton](kcoreconfigskeleton.md) a singleton for global access from all over the application without passing references to the [KCoreConfigSkeleton](kcoreconfigskeleton.md) object around.

You can write the data to the configuration file by calling [save](kcoreconfigskeleton.md#save)() and read the data from the configuration file by calling readConfig(). If you want to watch for config changes, use the [configChanged](kcoreconfigskeleton.md#configChanged)() signal.

If you have items which are not covered by the existing [addItem](kcoreconfigskeleton.md#addItem)() functions you can add customized code for reading, writing and default setting by implementing the functions [usrUseDefaults](kcoreconfigskeleton.md#usrUseDefaults)(), [usrRead](kcoreconfigskeleton.md#usrRead)() and [usrSave](kcoreconfigskeleton.md#usrSave)().

Internally preferences settings are stored in instances of subclasses of [KConfigSkeletonItem](kconfigskeletonitem.md). You can also add [KConfigSkeletonItem](kconfigskeletonitem.md) subclasses for your own types and call the generic [addItem](kcoreconfigskeleton.md#addItem)() to register them.

In many cases you don't have to write the specific [KCoreConfigSkeleton](kcoreconfigskeleton.md) subclasses yourself, but you can use [The KDE Configuration Compiler](kconfigcompiler.md) to automatically generate the C++ code from an XML description of the configuration options.

*See also* [KConfigSkeletonItem](kconfigskeletonitem.md)

## Member Type Documentation {#member-type-documentation}

### enum KCoreConfigSkeleton::DisambiguateConstructor {#DisambiguateConstructor-enum}

It is added to disambiguate with the other constructor otherwise ambiguate in case of default nullptr [KCoreConfigSkeleton](kcoreconfigskeleton.md)([KSharedConfig::Ptr](ksharedconfig.md#Ptr-typedef)(nullptr)) or [KCoreConfigSkeleton](kcoreconfigskeleton.md)(std::unique\_ptr\<[KConfig](kconfig.md)\> (nullptr)) with parent = nullptr.

| Constant |   |
| --- | --- |
| `KCoreConfigSkeleton::IsStdUniqPtr` | `0` |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KCoreConfigSkeleton::KCoreConfigSkeleton(KSharedConfig::Ptr *config*, QObject \**parent* = nullptr) {#KCoreConfigSkeleton}

Constructs a [KCoreConfigSkeleton](kcoreconfigskeleton.md) object with the given [KSharedConfig](ksharedconfig.md) `config` and `parent`.

### \[explicit\] KCoreConfigSkeleton::KCoreConfigSkeleton(const QString &*configname* = QString(), QObject \**parent* = nullptr) {#KCoreConfigSkeleton-1}

Constructs a [KCoreConfigSkeleton](kcoreconfigskeleton.md) object with the given `configname` and `parent`.

If no name is given, the default config file as returned by [KSharedConfig::openConfig](ksharedconfig.md#openConfig)() is used.

### \[explicit, since 6.23\] KCoreConfigSkeleton::KCoreConfigSkeleton(std::unique\_ptr\<KConfig\> *config*, KCoreConfigSkeleton::DisambiguateConstructor *value*, QObject \**parent* = nullptr) {#KCoreConfigSkeleton-2}

Constructs a [KCoreConfigSkeleton](kcoreconfigskeleton.md) object with the given [KConfig](kconfig.md) `config` and `parent`.

The `value` must be [DisambiguateConstructor::IsStdUniqPtr](kcoreconfigskeleton.md#DisambiguateConstructor-enum).

This function was introduced in Qt 6.23.

### void KCoreConfigSkeleton::addItem(KConfigSkeletonItem \**item*, const QString &*name* = QString()) {#addItem}

Registers a custom [KConfigSkeletonItem](kconfigskeletonitem.md) `item` with a given `name`.

If `name` is a null string, take the name from [KConfigSkeletonItem::key](kconfigskeletonitem.md#key)().

> **Note:** All names must be unique but multiple entries can have the same key if they reside in different groups.

[KCoreConfigSkeleton](kcoreconfigskeleton.md) takes ownership of `item`.

### KCoreConfigSkeleton::ItemBool \*KCoreConfigSkeleton::addItemBool(const QString &*name*, bool &*reference*, bool *defaultValue* = false, const QString &*key* = QString()) {#addItemBool}

Registers a bool item with a unique `name` by passing a `reference` pointer to the variable and the given `defaultValue` for the `key` used in the config file.

If `key` is a null string, `name` is used as key.

Returns the created item.

### KCoreConfigSkeleton::ItemDateTime \*KCoreConfigSkeleton::addItemDateTime(const QString &*name*, QDateTime &*reference*, const QDateTime &*defaultValue* = QDateTime(), const QString &*key* = QString()) {#addItemDateTime}

Registers a [QDateTime](https://doc.qt.io/qt-6/qdatetime.html) item with a unique `name` by passing a `reference` pointer to the variable and the given `defaultValue` for the `key` used in the config file.

If `key` is a null string, `name` is used as key.

Returns the created item.

### KCoreConfigSkeleton::ItemDouble \*KCoreConfigSkeleton::addItemDouble(const QString &*name*, double &*reference*, double *defaultValue* = 0.0, const QString &*key* = QString()) {#addItemDouble}

Registers a double item with a unique `name` by passing a `reference` pointer to the variable and the given `defaultValue` for the `key` used in the config file.

If `key` is a null string, `name` is used as key.

Returns the created item.

### KCoreConfigSkeleton::ItemInt \*KCoreConfigSkeleton::addItemInt(const QString &*name*, qint32 &*reference*, qint32 *defaultValue* = 0, const QString &*key* = QString()) {#addItemInt}

Registers a qint32 item with a unique `name` by passing a `reference` pointer to the variable and the given `defaultValue` for the `key` used in the config file.

If `key` is a null string, `name` is used as key.

Returns the created item.

### KCoreConfigSkeleton::ItemIntList \*KCoreConfigSkeleton::addItemIntList(const QString &*name*, QList\<int\> &*reference*, const QList\<int\> &*defaultValue* = QList\<int\>(), const QString &*key* = QString()) {#addItemIntList}

Registers an int list item with a unique `name` by passing a `reference` pointer to the variable and the given `defaultValue` for the `key` used in the config file.

If `key` is a null string, `name` is used as key.

Returns the created item.

### KCoreConfigSkeleton::ItemLongLong \*KCoreConfigSkeleton::addItemLongLong(const QString &*name*, qint64 &*reference*, qint64 *defaultValue* = 0, const QString &*key* = QString()) {#addItemLongLong}

Registers a qint64 item with a unique `name` by passing a `reference` pointer to the variable and the given `defaultValue` for the `key` used in the config file.

If `key` is a null string, `name` is used as key.

Returns the created item.

### KCoreConfigSkeleton::ItemPassword \*KCoreConfigSkeleton::addItemPassword(const QString &*name*, QString &*reference*, const QString &*defaultValue* = QLatin1String(""), const QString &*key* = QString()) {#addItemPassword}

Registers a password item of type [QString](https://doc.qt.io/qt-6/qstring.html) with a unique `name` by passing a `reference` pointer to the variable and the given `defaultValue` for the `key` used in the config file.

If `key` is a null string, `name` is used as key.

The string value is written encrypted to the config file.

Returns the created item.

> **Note:** The current encryption scheme is very weak.

### KCoreConfigSkeleton::ItemPath \*KCoreConfigSkeleton::addItemPath(const QString &*name*, QString &*reference*, const QString &*defaultValue* = QLatin1String(""), const QString &*key* = QString()) {#addItemPath}

Registers a path item of type [QString](https://doc.qt.io/qt-6/qstring.html) with a unique `name` by passing a `reference` pointer to the variable and the given `defaultValue` for the `key` used in the config file.

If `key` is a null string, `name` is used as key.

The string value is interpreted as a path. This means dollar expansion is activated for this value, so that for example `$HOME` gets expanded.

Returns the created item.

### \[since 6.27\] KCoreConfigSkeleton::ItemPathList \*KCoreConfigSkeleton::addItemPathList(const QString &*name*, QList\<QString\> &*reference*, const QList\<QString\> &*defaultValue* = QList\<QString\>(), const QString &*key* = QString()) {#addItemPathList}

Registers an int list item with a unique `name` by passing a `reference` pointer to the variable and the given `defaultValue` for the `key` used in the config file.

If `key` is a null string, `name` is used as key.

Returns the created item.

This function was introduced in Qt 6.27.

### KCoreConfigSkeleton::ItemPoint \*KCoreConfigSkeleton::addItemPoint(const QString &*name*, QPoint &*reference*, const QPoint &*defaultValue* = QPoint(), const QString &*key* = QString()) {#addItemPoint}

Registers a [QPoint](https://doc.qt.io/qt-6/qpoint.html) item with a unique `name` by passing a `reference` pointer to the variable and the given `defaultValue` for the `key` used in the config file.

If `key` is a null string, `name` is used as key.

Returns the created item.

### KCoreConfigSkeleton::ItemPointF \*KCoreConfigSkeleton::addItemPointF(const QString &*name*, QPointF &*reference*, const QPointF &*defaultValue* = QPointF(), const QString &*key* = QString()) {#addItemPointF}

Registers a [QPointF](https://doc.qt.io/qt-6/qpointf.html) item with a unique `name` by passing a `reference` pointer to the variable and the given `defaultValue` for the `key` used in the config file.

If `key` is a null string, `name` is used as key.

Returns the created item.

### KCoreConfigSkeleton::ItemProperty \*KCoreConfigSkeleton::addItemProperty(const QString &*name*, QVariant &*reference*, const QVariant &*defaultValue* = QVariant(), const QString &*key* = QString()) {#addItemProperty}

Registers a property item of type [QVariant](https://doc.qt.io/qt-6/qvariant.html) with a unique `name` by passing a `reference` pointer to the variable and the given `defaultValue` for the `key` used in the config file.

If `key` is a null string, `name` is used as key.

Returns the created item.

> **Note:** The following [QVariant](https://doc.qt.io/qt-6/qvariant.html) types are allowed: String, StringList, Font, Point, PointF, Rect, RectF, Size, SizeF, Color, Int, UInt, Bool, Double, DateTime and Date.

### KCoreConfigSkeleton::ItemRect \*KCoreConfigSkeleton::addItemRect(const QString &*name*, QRect &*reference*, const QRect &*defaultValue* = QRect(), const QString &*key* = QString()) {#addItemRect}

Registers a [QRect](https://doc.qt.io/qt-6/qrect.html) item with a unique `name` by passing a `reference` pointer to the variable and the given `defaultValue` for the `key` used in the config file.

If `key` is a null string, `name` is used as key.

Returns the created item.

### KCoreConfigSkeleton::ItemRectF \*KCoreConfigSkeleton::addItemRectF(const QString &*name*, QRectF &*reference*, const QRectF &*defaultValue* = QRectF(), const QString &*key* = QString()) {#addItemRectF}

Registers a [QRectF](https://doc.qt.io/qt-6/qrectf.html) item with a unique `name` by passing a `reference` pointer to the variable and the given `defaultValue` for the `key` used in the config file.

If `key` is a null string, `name` is used as key.

Returns the created item.

### KCoreConfigSkeleton::ItemSize \*KCoreConfigSkeleton::addItemSize(const QString &*name*, QSize &*reference*, const QSize &*defaultValue* = QSize(), const QString &*key* = QString()) {#addItemSize}

Registers a [QSize](https://doc.qt.io/qt-6/qsize.html) item with a unique `name` by passing a `reference` pointer to the variable and the given `defaultValue` for the `key` used in the config file.

If `key` is a null string, `name` is used as key.

Returns the created item.

### KCoreConfigSkeleton::ItemSizeF \*KCoreConfigSkeleton::addItemSizeF(const QString &*name*, QSizeF &*reference*, const QSizeF &*defaultValue* = QSizeF(), const QString &*key* = QString()) {#addItemSizeF}

Registers a [QSizeF](https://doc.qt.io/qt-6/qsizef.html) item with a unique `name` by passing a `reference` pointer to the variable and the given `defaultValue` for the `key` used in the config file.

If `key` is a null string, `name` is used as key.

Returns the created item.

### KCoreConfigSkeleton::ItemString \*KCoreConfigSkeleton::addItemString(const QString &*name*, QString &*reference*, const QString &*defaultValue* = QLatin1String(""), const QString &*key* = QString()) {#addItemString}

Registers a string item with a unique `name` by passing a `reference` pointer to the variable and the given `defaultValue` for the `key` used in the config file.

If `key` is a null string, `name` is used as key.

Returns the created item.

### KCoreConfigSkeleton::ItemStringList \*KCoreConfigSkeleton::addItemStringList(const QString &*name*, QStringList &*reference*, const QStringList &*defaultValue* = QStringList(), const QString &*key* = QString()) {#addItemStringList}

Registers a string list item with a unique `name` by passing a `reference` pointer to the variable and the given `defaultValue` for the `key` used in the config file.

If `key` is a null string, `name` is used as key.

Returns the created item.

### \[since 6.16\] KCoreConfigSkeleton::ItemTime \*KCoreConfigSkeleton::addItemTime(const QString &*name*, QTime &*reference*, QTime *defaultValue* = QTime(), const QString &*key* = QString()) {#addItemTime}

Registers a [QTime](https://doc.qt.io/qt-6/qtime.html) item with a unique `name` by passing a `reference` pointer to the variable and the given `defaultValue` for the `key` used in the config file.

If `key` is a null string, `name` is used as key.

Returns the created item.

This function was introduced in Qt 6.16.

### KCoreConfigSkeleton::ItemUInt \*KCoreConfigSkeleton::addItemUInt(const QString &*name*, quint32 &*reference*, quint32 *defaultValue* = 0, const QString &*key* = QString()) {#addItemUInt}

Registers a quint32 item with a unique `name` by passing a `reference` pointer to the variable and the given `defaultValue` for the `key` used in the config file.

If `key` is a null string, `name` is used as key.

Returns the created item.

### KCoreConfigSkeleton::ItemULongLong \*KCoreConfigSkeleton::addItemULongLong(const QString &*name*, quint64 &*reference*, quint64 *defaultValue* = 0, const QString &*key* = QString()) {#addItemULongLong}

Registers a quint64 item with a unique `name` by passing a `reference` pointer to the variable and the given `defaultValue` for the `key` used in the config file.

If `key` is a null string, `name` is used as key.

Returns the created item.

### \[since 6.27\] KCoreConfigSkeleton::ItemUrlList \*KCoreConfigSkeleton::addItemUrlList(const QString &*name*, QList\<QUrl\> &*reference*, const QList\<QUrl\> &*defaultValue* = QList\<QUrl\>(), const QString &*key* = QString()) {#addItemUrlList}

Registers an int list item with a unique `name` by passing a `reference` pointer to the variable and the given `defaultValue` for the `key` used in the config file.

If `key` is a null string, `name` is used as key.

Returns the created item.

This function was introduced in Qt 6.27.

### void KCoreConfigSkeleton::clearItems() {#clearItems}

Removes and deletes all items.

### KConfig \*KCoreConfigSkeleton::config() {#config}

Returns the [KConfig](kconfig.md) object used for reading and writing the settings.

*See also* [setConfig](kcoreconfigskeleton.md#setConfig)()

### const KConfig \*KCoreConfigSkeleton::config() const {#config-1}

Returns the const [KConfig](kconfig.md) object used for reading and writing the settings.

### \[signal\] void KCoreConfigSkeleton::configChanged() {#configChanged}

This signal is emitted when the configuration changes.

*See also* [KConfigBase::WriteConfigFlags](kconfigbase.md#WriteConfigFlag-enum)

### QString KCoreConfigSkeleton::currentGroup() const {#currentGroup}

Returns the current group used for [addItem](kcoreconfigskeleton.md#addItem)() calls.

*See also* [setCurrentGroup](kcoreconfigskeleton.md#setCurrentGroup)()

### KConfigSkeletonItem \*KCoreConfigSkeleton::findItem(const QString &*name*) const {#findItem}

Looks up an item by `name`.

### bool KCoreConfigSkeleton::isDefaults() const {#isDefaults}

Returns if all the registered items are set to their default value.

### \[invokable\] bool KCoreConfigSkeleton::isImmutable(const QString &*name*) const {#isImmutable}

Returns whether the item with the given `name` is immutable.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### bool KCoreConfigSkeleton::isSaveNeeded() const {#isSaveNeeded}

Returns if any registered item has a different value than the previously loaded value.

### KConfigSkeletonItem::List KCoreConfigSkeleton::items() const {#items}

Returns the list of items managed by this [KCoreConfigSkeleton](kcoreconfigskeleton.md) object.

### void KCoreConfigSkeleton::load() {#load}

Reads preferences from the config file. All registered items are set to the values read from disk.

This method calls [usrRead](kcoreconfigskeleton.md#usrRead)() after reading the settings of the registered items from the [KConfig](kconfig.md). You can override [usrRead](kcoreconfigskeleton.md#usrRead)() in derived classes if you have special requirements.

### void KCoreConfigSkeleton::read() {#read}

Reads preferences from the [KConfig](kconfig.md) object. This method assumes that the [KConfig](kconfig.md) object was previously loaded, i.e. it uses the in-memory values from [KConfig](kconfig.md) without reloading from disk.

This method calls [usrRead](kcoreconfigskeleton.md#usrRead)() after reading the settings of the registered items from the [KConfig](kconfig.md). You can override [usrRead](kcoreconfigskeleton.md#usrRead)() in derived classes if you have special requirements.

### void KCoreConfigSkeleton::removeItem(const QString &*name*) {#removeItem}

Removes and deletes an item by `name`.

### \[slot\] bool KCoreConfigSkeleton::save() {#save}

Writes preferences to the config file. The values of all registered items are written to disk and returns true upon success.

This method calls [usrSave](kcoreconfigskeleton.md#usrSave)() after writing the settings from the registered items to the [KConfig](kconfig.md).

You can override [usrSave](kcoreconfigskeleton.md#usrSave)() in derived classes if you have special requirements.

### \[since 6.23\] void KCoreConfigSkeleton::setConfig(std::unique\_ptr\<KConfig\> *config*) {#setConfig}

Sets the [KConfig](kconfig.md) `config` object used for reading and writing the settings.

This function was introduced in Qt 6.23.

*See also* [config](kcoreconfigskeleton.md#config)()

### void KCoreConfigSkeleton::setCurrentGroup(const QString &*group*) {#setCurrentGroup}

Set the config file `group` for subsequent [addItem](kcoreconfigskeleton.md#addItem)() calls.

It is valid until setCurrentGroup() is called with a new argument. Call this before you add any items.

The default value is "No Group".

*See also* [currentGroup](kcoreconfigskeleton.md#currentGroup)()

### \[virtual\] void KCoreConfigSkeleton::setDefaults() {#setDefaults}

Sets all registered items to their default values.

This method calls [usrSetDefaults](kcoreconfigskeleton.md#usrSetDefaults)() after setting the defaults for the registered items. You can override [usrSetDefaults](kcoreconfigskeleton.md#usrSetDefaults)() in derived classes if you have special requirements.

If you need more fine-grained control of setting the default values of the registered items you can override setDefaults() in a derived class.

*See also* [isDefaults](kcoreconfigskeleton.md#isDefaults)()

### void KCoreConfigSkeleton::setSharedConfig(KSharedConfig::Ptr *pConfig*) {#setSharedConfig}

Sets the [KSharedConfig](ksharedconfig.md) `pConfig` object used for reading and writing the settings.

*See also* [sharedConfig](kcoreconfigskeleton.md#sharedConfig)()

### KSharedConfig::Ptr KCoreConfigSkeleton::sharedConfig() const {#sharedConfig}

Returns the [KSharedConfig](ksharedconfig.md) object used for reading and writing the settings.

This might return null if the internal config is a std::unique\_ptr\<[KConfig](kconfig.md)\>.

*See also* [setSharedConfig](kcoreconfigskeleton.md#setSharedConfig)(), [config](kcoreconfigskeleton.md#config)(), [KCoreConfigSkeleton::DisambiguateConstructor](kcoreconfigskeleton.md#DisambiguateConstructor-enum)

### \[virtual\] bool KCoreConfigSkeleton::useDefaults(bool *b*) {#useDefaults}

Changes the state of this object to reflect the default values (`b` = true) or replaces the default values with the current values (`b` = false).

This method is implemented by [usrUseDefaults](kcoreconfigskeleton.md#usrUseDefaults)(), which can be overridden in derived classes if you have special requirements and can call [usrUseDefaults](kcoreconfigskeleton.md#usrUseDefaults)() directly.

If you don't have control whether useDefaults() or [usrUseDefaults](kcoreconfigskeleton.md#usrUseDefaults)() is called override useDefaults() directly.

Returns the state prior to this call.

### \[virtual protected\] void KCoreConfigSkeleton::usrRead() {#usrRead}

Performs the actual reading of the configuration file.

Override in derived classes to read special config values.

Called from [read](kcoreconfigskeleton.md#read)().

### \[virtual protected\] bool KCoreConfigSkeleton::usrSave() {#usrSave}

Performs the actual writing of the configuration file and returns true upon success.

Override in derived classes to write special config values.

Called from [save](kcoreconfigskeleton.md#save)().

### \[virtual protected\] void KCoreConfigSkeleton::usrSetDefaults() {#usrSetDefaults}

Performs the actual setting of default values.

Override in derived classes to set special default values.

Called from [setDefaults](kcoreconfigskeleton.md#setDefaults)().

### \[virtual protected\] bool KCoreConfigSkeleton::usrUseDefaults(bool *b*) {#usrUseDefaults}

Changes the state of this object to reflect the default values (`b` = true) or replaces the default values with the current values (`b` = false).

Called from [useDefaults](kcoreconfigskeleton.md#useDefaults)().

Implemented by subclasses that use special defaults.

Returns the state prior to this call.
