---
title: "KUnitConversion::Unit Class"
description: "Class to define a unit of measurement."
---

# KUnitConversion::Unit Class

Class to define a unit of measurement. [More...](#details)

- **Header:** `#include <Unit>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UnitConversion)`  
  `target_link_libraries(mytarget PRIVATE KF6::UnitConversion)`

[List of all members, including inherited members](kunitconversion-unit-members.md)

## Public Functions

- [Unit()](#Unit)
- [KUnitConversion::UnitCategory category() const](#category)
- [KUnitConversion::CategoryId categoryId() const](#categoryId)
- [QString description() const](#description)
- [KUnitConversion::UnitId id() const](#id)
- [bool isNull() const](#isNull)
- [bool isValid() const](#isValid)
- [QString symbol() const](#symbol)
- [QString toString(qreal value, int fieldWidth = 0, char format = 'g', int precision = -1, const QChar &fillChar = QLatin1Char(' ')) const](#toString)
- [QString toSymbolString(qreal value, int fieldWidth = 0, char format = 'g', int precision = -1, const QChar &fillChar = QLatin1Char(' ')) const](#toSymbolString)
- [bool Unit::operator==(const KUnitConversion::Unit &other) const](#operator-eq-eq)

## Detailed Description {#details}

This is a class to define a unit of measurement.

*See also* [Converter](kunitconversion-converter.md), [UnitCategory](kunitconversion-unitcategory.md), [Value](kunitconversion-value.md)

## Member Function Documentation {#member-function-documentation}

### Unit::Unit() {#Unit}

Null constructor

### KUnitConversion::UnitCategory Unit::category() const {#category}

Returns unit category.

### KUnitConversion::CategoryId Unit::categoryId() const {#categoryId}

Returns category id.

### QString Unit::description() const {#description}

Returns translated name for unit.

### KUnitConversion::UnitId Unit::id() const {#id}

Returns unit id.

### bool Unit::isNull() const {#isNull}

Returns returns true if this Unit is null

### bool Unit::isValid() const {#isValid}

Returns if unit is valid.

### QString Unit::symbol() const {#symbol}

Returns symbol for the unit.

### QString Unit::toString(qreal *value*, int *fieldWidth* = 0, char *format* = 'g', int *precision* = -1, const QChar &*fillChar* = QLatin1Char(' ')) const {#toString}

`value` number value

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`format` type of floating point formatting, like in [QString::arg](https://doc.qt.io/qt-6/qstring.html#arg)

`precision` number of digits after the decimal separator

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns value + unit string

### QString Unit::toSymbolString(qreal *value*, int *fieldWidth* = 0, char *format* = 'g', int *precision* = -1, const QChar &*fillChar* = QLatin1Char(' ')) const {#toSymbolString}

`value` number value

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`format` type of floating point formatting, like in [QString::arg](https://doc.qt.io/qt-6/qstring.html#arg)

`precision` number of digits after the decimal separator

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns value + unit string

### bool Unit::operator==(const KUnitConversion::Unit &*other*) const {#operator-eq-eq}

Returns true if this Unit is equal to the `other` Unit.
