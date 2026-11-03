---
title: "KUnitConversion::UnitCategory Class"
description: "Class to define a category of units of measurement."
---

# KUnitConversion::UnitCategory Class

Class to define a category of units of measurement. [More...](#details)

- **Header:** `#include <UnitCategory>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UnitConversion)`  
  `target_link_libraries(mytarget PRIVATE KF6::UnitConversion)`

[List of all members, including inherited members](kunitconversion-unitcategory-members.md)

## Public Functions

- [UnitCategory()](#UnitCategory)
- [QStringList allUnits() const](#allUnits)
- [KUnitConversion::Value convert(const KUnitConversion::Value &value, const QString &toUnit = QString()) const](#convert)
- [KUnitConversion::Value convert(const KUnitConversion::Value &value, KUnitConversion::UnitId toUnit) const](#convert-1)
- [KUnitConversion::Value convert(const KUnitConversion::Value &value, const KUnitConversion::Unit &toUnit) const](#convert-2)
- [KUnitConversion::Unit defaultUnit() const](#defaultUnit)
- [QString description() const](#description)
- [bool hasOnlineConversionTable() const](#hasOnlineConversionTable)
- [bool hasUnit(const QString &unit) const](#hasUnit)
- [KUnitConversion::CategoryId id() const](#id)
- [bool isNull() const](#isNull)
- [QList\<KUnitConversion::Unit\> mostCommonUnits() const](#mostCommonUnits)
- [QString name() const](#name)
- [KUnitConversion::UpdateJob \*syncConversionTable(std::chrono::seconds updateSkipPeriod = std::hours(24))](#syncConversionTable) (since 6.0)
- [KUnitConversion::Unit unit(KUnitConversion::UnitId unitId) const](#unit)
- [KUnitConversion::Unit unit(const QString &s) const](#unit-1)
- [QList\<KUnitConversion::Unit\> units() const](#units)
- [bool UnitCategory::operator==(const KUnitConversion::UnitCategory &other) const](#operator-eq-eq)

## Detailed Description {#details}

This is a class to define a category of units of measurement.

*See also* [Converter](kunitconversion-converter.md), [Unit](kunitconversion-unit.md), [Value](kunitconversion-value.md)

## Member Function Documentation {#member-function-documentation}

### UnitCategory::UnitCategory() {#UnitCategory}

Null constructor

### QStringList UnitCategory::allUnits() const {#allUnits}

Returns all unit names, short names and unit synonyms in this category.

### KUnitConversion::Value UnitCategory::convert(const KUnitConversion::Value &*value*, const QString &*toUnit* = QString()) const {#convert}

Convert value to another unit selected by string.

`value` value to convert

`toUnit` unit to convert to. If empty default unit is used.

Returns converted value

### KUnitConversion::Value UnitCategory::convert(const KUnitConversion::Value &*value*, KUnitConversion::UnitId *toUnit*) const {#convert-1}

Convert value to another unit selected by enum.

`value` value to convert

`toUnit` unit to convert to.

Returns converted value

This function overloads [UnitCategory::convert()](kunitconversion-unitcategory.md#convert).

### KUnitConversion::Value UnitCategory::convert(const KUnitConversion::Value &*value*, const KUnitConversion::Unit &*toUnit*) const {#convert-2}

Convert value to another unit.

`value` value to convert

`toUnit` unit to be used for conversion

Returns converted value

This function overloads [UnitCategory::convert()](kunitconversion-unitcategory.md#convert).

### KUnitConversion::Unit UnitCategory::defaultUnit() const {#defaultUnit}

Returns default unit.

### QString UnitCategory::description() const {#description}

Returns unit category description

### bool UnitCategory::hasOnlineConversionTable() const {#hasOnlineConversionTable}

Returns true if category has conversion table that needs to be updated via online access, otherwise false

*See also* [syncConversionTable](kunitconversion-unitcategory.md#syncConversionTable)()

### bool UnitCategory::hasUnit(const QString &*unit*) const {#hasUnit}

Returns if unit category has a unit.

### KUnitConversion::CategoryId UnitCategory::id() const {#id}

Returns category id.

### bool UnitCategory::isNull() const {#isNull}

Returns true if this [UnitCategory](kunitconversion-unitcategory.md) is null

### QList\<KUnitConversion::Unit\> UnitCategory::mostCommonUnits() const {#mostCommonUnits}

Returns most common units in this category.

### QString UnitCategory::name() const {#name}

Returns translated name for the unit category.

### \[since 6.0\] KUnitConversion::UpdateJob \*UnitCategory::syncConversionTable(std::chrono::seconds *updateSkipPeriod* = std::chrono::hours(24)) {#syncConversionTable}

Request an update of the online conversion table when it is older than `updateSkipPeriod`.

Returned jobs are automatically deleted, ie. it is safe to ignore the return value if you do not care about being notified about the completion (or failure) of the update process. Calling this method while another update is already in progress will not trigger another update but instead allows you to watch the already ongoing update.

Performing conversions before the update has completed will return results based on the old conversion table, if available.

> **Note:** This method must be called from the main thread!

Returns an [UpdateJob](kunitconversion-updatejob.md) if an update is necessary or already running, nullptr otherwise.

This function was introduced in Qt 6.0.

*See also* [UpdateJob](kunitconversion-updatejob.md)

### KUnitConversion::Unit UnitCategory::unit(KUnitConversion::UnitId *unitId*) const {#unit}

Returns unit for unit enum.

### KUnitConversion::Unit UnitCategory::unit(const QString &*s*) const {#unit-1}

Returns unit for string.

### QList\<KUnitConversion::Unit\> UnitCategory::units() const {#units}

Returns units in this category.

### bool UnitCategory::operator==(const KUnitConversion::UnitCategory &*other*) const {#operator-eq-eq}

Returns true if this [UnitCategory](kunitconversion-unitcategory.md) is equal to the `other` [UnitCategory](kunitconversion-unitcategory.md).
