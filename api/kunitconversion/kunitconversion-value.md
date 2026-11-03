---
title: "KUnitConversion::Value Class"
description: "Class to hold a value in a unit of measurement."
---

# KUnitConversion::Value Class

Class to hold a value in a unit of measurement. [More...](#details)

- **Header:** `#include <Value>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UnitConversion)`  
  `target_link_libraries(mytarget PRIVATE KF6::UnitConversion)`

[List of all members, including inherited members](kunitconversion-value-members.md)

## Public Functions

- [Value()](#Value)
- [Value(const QVariant &number, const QString &unitString)](#Value-1)
- [Value(qreal number, KUnitConversion::UnitId unitId)](#Value-2)
- [Value(qreal number, const KUnitConversion::Unit &unit)](#Value-3)
- [Value(qreal number, const QString &unitString)](#Value-4)
- [KUnitConversion::Value convertTo(KUnitConversion::UnitId unit) const](#convertTo)
- [KUnitConversion::Value convertTo(const KUnitConversion::Unit &unit) const](#convertTo-1)
- [KUnitConversion::Value convertTo(const QString &unit) const](#convertTo-2)
- [bool isNull() const](#isNull)
- [bool isValid() const](#isValid)
- [qreal number() const](#number)
- [KUnitConversion::Value &round(uint decimals)](#round)
- [QString toString(int fieldWidth = 0, char format = 'g', int precision = -1, const QChar &fillChar = QLatin1Char(' ')) const](#toString)
- [QString toSymbolString(int fieldWidth = 0, char format = 'g', int precision = -1, const QChar &fillChar = QLatin1Char(' ')) const](#toSymbolString)
- [KUnitConversion::Unit unit() const](#unit)
- [bool Value::operator==(const KUnitConversion::Value &other) const](#operator-eq-eq)

## Detailed Description {#details}

This is a class to hold a value in a unit of measurement.

*See also* [Converter](kunitconversion-converter.md), [Unit](kunitconversion-unit.md), [UnitCategory](kunitconversion-unitcategory.md)

## Member Function Documentation {#member-function-documentation}

### Value::Value() {#Value}

Creates a null value.

### Value::Value(const QVariant &*number*, const QString &*unitString*) {#Value-1}

Creates a value based on a [QVariant](https://doc.qt.io/qt-6/qvariant.html) (calling toReal() on it) with a unit (as a string).

### Value::Value(qreal *number*, KUnitConversion::UnitId *unitId*) {#Value-2}

Creates a value with a unit (as a enum value).

### Value::Value(qreal *number*, const KUnitConversion::Unit &*unit*) {#Value-3}

Creates a value with a unit instance

### Value::Value(qreal *number*, const QString &*unitString*) {#Value-4}

Creates a value with a unit (as a string).

### KUnitConversion::Value Value::convertTo(KUnitConversion::UnitId *unit*) const {#convertTo}

Convert to another unit

### KUnitConversion::Value Value::convertTo(const KUnitConversion::Unit &*unit*) const {#convertTo-1}

Convert to another unit

### KUnitConversion::Value Value::convertTo(const QString &*unit*) const {#convertTo-2}

Convert to another unit

### bool Value::isNull() const {#isNull}

Returns returns true if this Value is null

### bool Value::isValid() const {#isValid}

Returns true if value is valid

### qreal Value::number() const {#number}

Number part of the value

### KUnitConversion::Value &Value::round(uint *decimals*) {#round}

Rounds value to decimal count

`decimals` decimal count.

### QString Value::toString(int *fieldWidth* = 0, char *format* = 'g', int *precision* = -1, const QChar &*fillChar* = QLatin1Char(' ')) const {#toString}

Convert value to a string

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`format` type of floating point formatting, like in [QString::arg](https://doc.qt.io/qt-6/qstring.html#arg)

`precision` number of digits after the decimal separator

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns value as a string

### QString Value::toSymbolString(int *fieldWidth* = 0, char *format* = 'g', int *precision* = -1, const QChar &*fillChar* = QLatin1Char(' ')) const {#toSymbolString}

Convert value to a string with symbol

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left `format` type of floating point formatting, like in [QString::arg](https://doc.qt.io/qt-6/qstring.html#arg)

`precision` number of digits after the decimal separator

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns value as a string

### KUnitConversion::Unit Value::unit() const {#unit}

Unit part of the value

### bool Value::operator==(const KUnitConversion::Value &*other*) const {#operator-eq-eq}

Returns true if this Value is equal to the `other` Value.
