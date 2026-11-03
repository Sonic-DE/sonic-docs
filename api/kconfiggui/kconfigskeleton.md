---
title: "KConfigSkeleton Class"
description: "Class for handling preferences settings for an application."
---

# KConfigSkeleton Class

Class for handling preferences settings for an application. [More...](#details)

- **Header:** `#include <KConfigSkeleton>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigGui)`
- **Inherits:** [KCoreConfigSkeleton](../kconfigcore/kcoreconfigskeleton.md)
- **Inherited By:** [KConfigLoader](kconfigloader.md)

[List of all members, including inherited members](kconfigskeleton-members.md)

## Public Functions

- [KConfigSkeleton(KSharedConfig::Ptr config, QObject \*parent = nullptr)](#KConfigSkeleton)
- [KConfigSkeleton(const QString &configname = QString(), QObject \*parent = nullptr)](#KConfigSkeleton-1)
- [KConfigSkeleton(std::unique\_ptr\<KConfig\> config, KCoreConfigSkeleton::DisambiguateConstructor value, QObject \*parent = nullptr)](#KConfigSkeleton-2) (since 6.23)
- [KConfigSkeleton::ItemColor \*addItemColor(const QString &name, QColor &reference, const QColor &defaultValue = QColor(128, 128, 128), const QString &key = QString())](#addItemColor)
- [KConfigSkeleton::ItemFont \*addItemFont(const QString &name, QFont &reference, const QFont &defaultValue = QFont(), const QString &key = QString())](#addItemFont)

## Detailed Description {#details}

This class extends [KCoreConfigSkeleton](../kconfigcore/kcoreconfigskeleton.md) with support for GUI types.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KConfigSkeleton::KConfigSkeleton(KSharedConfig::Ptr *config*, QObject \**parent* = nullptr) {#KConfigSkeleton}

Constructs a configuration skeleton with the given `config` object as a child of `parent`.

### \[explicit\] KConfigSkeleton::KConfigSkeleton(const QString &*configname* = QString(), QObject \**parent* = nullptr) {#KConfigSkeleton-1}

Constructs a configuration skeleton with the given `configname` as a child of `parent`.

If no name is given, the default config as returned by [KSharedConfig::openConfig](../kconfigcore/ksharedconfig.md#openConfig)() is used.

### \[explicit, since 6.23\] KConfigSkeleton::KConfigSkeleton(std::unique\_ptr\<KConfig\> *config*, KCoreConfigSkeleton::DisambiguateConstructor *value*, QObject \**parent* = nullptr) {#KConfigSkeleton-2}

Constructs a configuration skeleton with a given `config` object as a child of `parent`.

The `value` must be [KCoreConfigSkeleton::IsStdUniqPtr](../kconfigcore/kcoreconfigskeleton.md#DisambiguateConstructor-enum).

The use of this single-valued enum is mandatory to disambiguate with the other constructor that may otherwise be ambiguous in case of default nullptr [KCoreConfigSkeleton](../kconfigcore/kcoreconfigskeleton.md)([KSharedConfig::Ptr](../kconfigcore/ksharedconfig.md#Ptr-typedef)(nullptr)) or [KCoreConfigSkeleton](../kconfigcore/kcoreconfigskeleton.md)(std::unique\_ptr\<[KConfig](../kconfigcore/kconfig.md)\> (nullptr)) with parent = nullptr.

This function was introduced in Qt 6.23.

*See also* [KCoreConfigSkeleton::DisambiguateConstructor](../kconfigcore/kcoreconfigskeleton.md#DisambiguateConstructor-enum)

### KConfigSkeleton::ItemColor \*KConfigSkeleton::addItemColor(const QString &*name*, QColor &*reference*, const QColor &*defaultValue* = QColor(128, 128, 128), const QString &*key* = QString()) {#addItemColor}

Registers a [QColor](https://doc.qt.io/qt-6/qcolor.html) item with the given `name`, the initial value `reference` to hold in the item, and the `defaultValue` for the item used when the config file does not yet contain the `key` of this item.

The `reference` should be a pointer to the variable that is set by [read](../kconfigcore/kcoreconfigskeleton.md#read)() calls and read by [save](../kconfigcore/kcoreconfigskeleton.md#save)() calls.

If `key` is a null string, `name` is used as key.

### KConfigSkeleton::ItemFont \*KConfigSkeleton::addItemFont(const QString &*name*, QFont &*reference*, const QFont &*defaultValue* = QFont(), const QString &*key* = QString()) {#addItemFont}

Registers a [QFont](https://doc.qt.io/qt-6/qfont.html) item with the given `name`, the initial value `reference` to hold in the item, and the `defaultValue` for the item used when the config file does not yet contain the `key` of this item.

The `reference` should be a pointer to the variable that is set by [read](../kconfigcore/kcoreconfigskeleton.md#read)() calls and read by [save](../kconfigcore/kcoreconfigskeleton.md#save)() calls.

If `key` is a null string, `name` is used as key.
