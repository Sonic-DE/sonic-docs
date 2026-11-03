---
title: "KCoreConfigSkeleton::ItemEnum Class"
description: "Class for handling enums."
---

# KCoreConfigSkeleton::ItemEnum Class

Class for handling enums.

- **Header:** `#include <ItemEnum>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KCoreConfigSkeleton::ItemInt](kcoreconfigskeleton-itemint.md)

## Public Functions

- [ItemEnum(const QString &\_group, const QString &\_key, qint32 &reference, const QList\<KCoreConfigSkeleton::ItemEnum::Choice\> &choices, qint32 defaultValue = 0)](#ItemEnum)
- [QList\<KCoreConfigSkeleton::ItemEnum::Choice\> choices() const](#choices)
- [void setValueForChoice(const QString &name, const QString &valueForChoice)](#setValueForChoice)
- [QString valueForChoice(const QString &name) const](#valueForChoice)

## Detailed Description {#details}

Enums specified with KConfigXT should be mapped to enums in the C++ codebase, as the generated getter for the [ItemEnum](kcoreconfigskeleton-itemenum.md) will return an int.

*See also* [Using KConfig XT](https://develop.kde.org/docs/features/configuration/kconfig_xt/), [Choice](kcoreconfigskeleton-itemenum-choice.md)

## Member Function Documentation {#member-function-documentation}

### ItemEnum::ItemEnum(const QString &*\_group*, const QString &*\_key*, qint32 &*reference*, const QList\<KCoreConfigSkeleton::ItemEnum::Choice\> &*choices*, qint32 *defaultValue* = 0) {#ItemEnum}

Constructs an enum item with the given `_group`, `_key`, the initial value `reference` to hold in the item, the list of enum `choices`, and the `defaultValue` for the item.

### QList\<KCoreConfigSkeleton::ItemEnum::Choice\> ItemEnum::choices() const {#choices}

Specifies a list of enum choices.

The name given to the choices list should match an equivalent enum in your C++ codebase, including the namespace. For example:

```cpp
<choices name="KWin::Layer">
```

Each individual choice in the XML file should then be mapped to the same C++ code enum values in the same order.

### void ItemEnum::setValueForChoice(const QString &*name*, const QString &*valueForChoice*) {#setValueForChoice}

Stores a choice value `valueForChoice` for an enum entry with the given `name`.

*See also* [valueForChoice](kcoreconfigskeleton-itemenum.md#valueForChoice)()

### QString ItemEnum::valueForChoice(const QString &*name*) const {#valueForChoice}

Returns the value for the choice with the given `name`.

*See also* [setValueForChoice](kcoreconfigskeleton-itemenum.md#setValueForChoice)()
