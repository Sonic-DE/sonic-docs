---
title: "KUnitConversion::Converter Class"
description: "Class for converting values between units of measurement."
---

# KUnitConversion::Converter Class

Class for converting values between units of measurement. [More...](#details)

- **Header:** `#include <Converter>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UnitConversion)`  
  `target_link_libraries(mytarget PRIVATE KF6::UnitConversion)`

[List of all members, including inherited members](kunitconversion-converter-members.md)

## Public Functions

- [Converter()](#Converter)
- [QList\<KUnitConversion::UnitCategory\> categories() const](#categories)
- [KUnitConversion::UnitCategory category(KUnitConversion::CategoryId categoryId) const](#category)
- [KUnitConversion::UnitCategory category(const QString &category) const](#category-1)
- [KUnitConversion::UnitCategory categoryForUnit(const QString &unit) const](#categoryForUnit)
- [KUnitConversion::Value convert(const KUnitConversion::Value &value, const QString &toUnit = QString()) const](#convert)
- [KUnitConversion::Value convert(const KUnitConversion::Value &value, KUnitConversion::UnitId toUnit) const](#convert-1)
- [KUnitConversion::Value convert(const KUnitConversion::Value &value, const KUnitConversion::Unit &toUnit) const](#convert-2)
- [KUnitConversion::Unit unit(KUnitConversion::UnitId unitId) const](#unit)
- [KUnitConversion::Unit unit(const QString &unitString) const](#unit-1)

## Detailed Description {#details}

This is a class to convert values between different units of measurement.

*See also* [Unit](kunitconversion-unit.md), [UnitCategory](kunitconversion-unitcategory.md), [Value](kunitconversion-value.md)

## Member Function Documentation {#member-function-documentation}

### Converter::Converter() {#Converter}

Creates a Converter instance.

### QList\<KUnitConversion::UnitCategory\> Converter::categories() const {#categories}

Returns a list of all unit categories.

### KUnitConversion::UnitCategory Converter::category(KUnitConversion::CategoryId *categoryId*) const {#category}

Find unit category.

`categoryId` id of the category to find ([LengthCategory](kunitconversion.md#CategoryId-enum), [AreaCategory](kunitconversion.md#CategoryId-enum), etc.).

Returns unit category which id is categoryId or invalid category.

### KUnitConversion::UnitCategory Converter::category(const QString &*category*) const {#category-1}

Find unit category.

`category` name of the category to find (length, area, mass, etc.).

Returns unit category named category or invalid category.

### KUnitConversion::UnitCategory Converter::categoryForUnit(const QString &*unit*) const {#categoryForUnit}

Find unit category for unit.

`unit` unit to find category for.

Returns unit category for unit

### KUnitConversion::Value Converter::convert(const KUnitConversion::Value &*value*, const QString &*toUnit* = QString()) const {#convert}

Convert value to another unit.

`value` value to convert

`toUnit` unit to convert to. If empty default unit is used.

Returns converted value

### KUnitConversion::Value Converter::convert(const KUnitConversion::Value &*value*, KUnitConversion::UnitId *toUnit*) const {#convert-1}

This function overloads [Converter::convert()](kunitconversion-converter.md#convert).

### KUnitConversion::Value Converter::convert(const KUnitConversion::Value &*value*, const KUnitConversion::Unit &*toUnit*) const {#convert-2}

This function overloads [Converter::convert()](kunitconversion-converter.md#convert).

### KUnitConversion::Unit Converter::unit(KUnitConversion::UnitId *unitId*) const {#unit}

Find unit for unit enum.

`unitId` unit enum to find unit for.

Returns unit for string unit

### KUnitConversion::Unit Converter::unit(const QString &*unitString*) const {#unit-1}

Find unit for string unit.

`unitString` unit string to find unit for.

Returns unit for string unit
