---
title: "Solid::Predicate Class"
description: "This class implements predicates for devices."
---

# Solid::Predicate Class

This class implements predicates for devices. [More...](#details)

- **Header:** `#include <Solid/Predicate>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Solid)`  
  `target_link_libraries(mytarget PRIVATE KF6::Solid)`

[List of all members, including inherited members](solid-predicate-members.md)

## Public Types

- [enum Predicate::ComparisonOperator](#ComparisonOperator-enum)
- [enum Predicate::NotOperator](#NotOperator-enum)
- [enum Predicate::Type](#Type-enum)

## Public Functions

- [Predicate()](#Predicate)
- [Predicate(const QString &ifaceName)](#Predicate-1)
- [Predicate(const Solid::DeviceInterface::Type &ifaceType)](#Predicate-2)
- [Predicate(QStringView ifaceName, Solid::Predicate::NotOperator op)](#Predicate-3) (since 6.17)
- [Predicate(const QString &ifaceName, const QString &property, const QVariant &value, Solid::Predicate::ComparisonOperator compOperator = Equals)](#Predicate-4)
- [Predicate(const Solid::DeviceInterface::Type &ifaceType, const QString &property, const QVariant &value, Solid::Predicate::ComparisonOperator compOperator = Equals)](#Predicate-5)
- [Solid::Predicate::ComparisonOperator comparisonOperator() const](#comparisonOperator)
- [Solid::Predicate firstOperand() const](#firstOperand)
- [Solid::DeviceInterface::Type interfaceType() const](#interfaceType)
- [bool isInterfaceTypeNegated() const](#isInterfaceTypeNegated) (since 6.17)
- [bool isValid() const](#isValid)
- [bool matches(const Solid::Device &device) const](#matches)
- [QVariant matchingValue() const](#matchingValue)
- [QString propertyName() const](#propertyName)
- [Solid::Predicate secondOperand() const](#secondOperand)
- [QString toString() const](#toString)
- [Solid::Predicate::Type type() const](#type)
- [QSet\<Solid::DeviceInterface::Type\> usedTypes() const](#usedTypes)
- [Solid::Predicate Predicate::operator&(const Solid::Predicate &other)](#operator-and)
- [Solid::Predicate &Predicate::operator&=(const Solid::Predicate &other)](#operator-and-eq)
- [Solid::Predicate Predicate::operator\|(const Solid::Predicate &other)](#operator-7c)
- [Solid::Predicate &Predicate::operator\|=(const Solid::Predicate &other)](#operator-7c-eq)

## Static Public Members

- [Solid::Predicate fromString(const QString &predicate)](#fromString)

## Detailed Description {#details}

A predicate is a logical condition that a given device can match or not. It's a constraint about the value a property must have in a given device interface, or any combination (conjunction, disjunction) of such constraints.

Predicates are used both in code and in Solid action files (present in `/usr/share/solid/actions` or `~/.local/share/solid/actions`). When used in Solid action files, they must be present in the `X-KDE-Solid-Predicate=` key in the Desktop Entry section of the file.

A predicate can be:

- a single comparison
- a conjunction of exactly two predicates ("AND")
- a disjunction of exactly two predicates ("OR")

Since these can be nested, it is possible to express "a [StorageVolume](solid-storagevolume.md) that is not ignored AND that [StorageVolume](solid-storagevolume.md) contains a FileSystem AND that [StorageVolume](solid-storagevolume.md) is removable". Since conjunctions use exactly two predicates (and this expression has three), square brackets are used to group the nested predicates when writing them out in full:

```cpp
[ [ StorageVolume.ignored == false AND StorageVolume.usage == 'FileSystem' ]
  AND StorageVolume.removable == true ]
```

Predicates can be constructed programmatically by creating single comparisons with the [Predicate](solid-predicate.md#Predicate)() constructor, and then building conjunctions with `operator&` and disjunctions with `operator|`.

Predicates can be constructed from a string by calling [fromString](solid-predicate.md#fromString)() which returns a predicate. If there are any errors in parsing the string, an empty predicate is returned; use [isValid](solid-predicate.md#isValid)() to detect whether that is the case.

The string language is described exactly in [predicate\_parser.y](https://invent.kde.org/frameworks/solid/-/blob/master/src/solid/devices/predicate_parser.y), but boils down to:

- a single comparison is written as `<interface>.<property> == <value>`
- a single bitmask check is written as `<interface>.<property> & <value>`
- a conjunction is written as `[ <predicate> AND <predicate> ]`
- a disjunction is written as `[ <predicate> OR <predicate> ]`

Note the mandatory use of `[` and `]` around conjunctions and disjunctions.

*See also* [Solid tutorial](https://develop.kde.org/docs/features/solid/)

## Member Type Documentation {#member-type-documentation}

### enum Predicate::ComparisonOperator {#ComparisonOperator-enum}

The comparison operator which can be used for matching within the predicate.

| Constant | Value | Description |
| --- | --- | --- |
| `Solid::Predicate::Equals` | `0` | The property and the value will match for strict equality |
| `Solid::Predicate::Mask` | `1` | The property and the value will match if the bitmasking is not null |

### enum Predicate::NotOperator {#NotOperator-enum}

Argument for the [Predicate](solid-predicate.md#Predicate)() constructor.

| Constant |   |
| --- | --- |
| `Solid::Predicate::NOT` | `0` |

### enum Predicate::Type {#Type-enum}

The predicate type which controls how the predicate is handled.

| Constant | Value | Description |
| --- | --- | --- |
| `Solid::Predicate::PropertyCheck` | `0` | The predicate contains a comparison that needs to be matched using a [ComparisonOperator](solid-predicate.md#ComparisonOperator-enum) |
| `Solid::Predicate::Conjunction` | `1` | The two contained predicates need to be true for this predicate to be true |
| `Solid::Predicate::Disjunction` | `2` | Either of the two contained predicates may be true for this predicate to be true |
| `Solid::Predicate::InterfaceCheck` | `3` | The device type is compared |

## Member Function Documentation {#member-function-documentation}

### Predicate::Predicate() {#Predicate}

Constructs an invalid predicate.

### \[explicit\] Predicate::Predicate(const QString &*ifaceName*) {#Predicate-1}

Constructs a predicate matching devices of a particular device interface `ifaceName`.

### \[explicit\] Predicate::Predicate(const Solid::DeviceInterface::Type &*ifaceType*) {#Predicate-2}

Constructs a predicate matching devices of a particular device interface `ifaceType`.

### \[explicit, since 6.17\] Predicate::Predicate(QStringView *ifaceName*, Solid::Predicate::NotOperator *op*) {#Predicate-3}

Constructs a predicate that checks that a device does **not** have the `ifaceName`.

The operator `op` is always NOT.

This function was introduced in Qt 6.17.

### Predicate::Predicate(const QString &*ifaceName*, const QString &*property*, const QVariant &*value*, Solid::Predicate::ComparisonOperator *compOperator* = Equals) {#Predicate-4}

Constructs a predicate matching the `value` of a `property` in a given device interface `ifaceType`.

The optional `compOperator` applies between the property and the value when matching.

### Predicate::Predicate(const Solid::DeviceInterface::Type &*ifaceType*, const QString &*property*, const QVariant &*value*, Solid::Predicate::ComparisonOperator *compOperator* = Equals) {#Predicate-5}

Constructs a predicate matching the `value` of a `property` in a given device interface `ifaceType`.

The optional `compOperator` applies between the property and the value when matching.

### Solid::Predicate::ComparisonOperator Predicate::comparisonOperator() const {#comparisonOperator}

Returns the comparison operator used to compare a property's value.

> **Note:** This is only valid for Conjunction and Disjunction types.

### Solid::Predicate Predicate::firstOperand() const {#firstOperand}

A smaller, inner predicate which is the first to appear and is compared with the second one in a comparison operation.

> **Note:** This is only valid for Conjunction and Disjunction types.

### \[static\] Solid::Predicate Predicate::fromString(const QString &*predicate*) {#fromString}

Returns a new valid predicate if the given `predicate` string is syntactically correct, [Predicate](solid-predicate.md#Predicate)() otherwise.

```cpp
Solid::Predicate equalPredicate =
    Solid::Predicate::fromString("IS OpticalDisc");
```

### Solid::DeviceInterface::Type Predicate::interfaceType() const {#interfaceType}

Returns a device interface type used by the predicate.

> **Note:** This is only valid for [InterfaceCheck](solid-predicate.md#Type-enum) and [PropertyCheck](solid-predicate.md#Type-enum) types.

### \[since 6.17\] bool Predicate::isInterfaceTypeNegated() const {#isInterfaceTypeNegated}

Returns if the interface type check is negated.

This function was introduced in Qt 6.17.

### bool Predicate::isValid() const {#isValid}

Returns if the predicate is valid.

[Predicate](solid-predicate.md#Predicate)() is the only invalid predicate.

### bool Predicate::matches(const Solid::Device &*device*) const {#matches}

Returns if a `device` matches the predicate.

### QVariant Predicate::matchingValue() const {#matchingValue}

Returns the value used when comparing a devices property to see if it matches the predicate.

> **Note:** This is only valid for the [PropertyCheck](solid-predicate.md#Type-enum) type.

### QString Predicate::propertyName() const {#propertyName}

Returns the property name used when retrieving the value to compare against.

> **Note:** This is only valid for the [PropertyCheck](solid-predicate.md#Type-enum) type.

### Solid::Predicate Predicate::secondOperand() const {#secondOperand}

A smaller, inner predicate which is the second to appear and is compared with the first one in a comparison operation.

> **Note:** This is only valid for Conjunction and Disjunction types.

### QString Predicate::toString() const {#toString}

Returns a string representation of the predicate.

### Solid::Predicate::Type Predicate::type() const {#type}

Retrieves the predicate type, used to determine how to handle the predicate.

### QSet\<Solid::DeviceInterface::Type\> Predicate::usedTypes() const {#usedTypes}

Returns the device interface types used in this predicate.

### Solid::Predicate Predicate::operator&(const Solid::Predicate &*other*) {#operator-and}

'And' operator.

Returns a new 'and' predicate having this and `other` as operands.

### Solid::Predicate &Predicate::operator&=(const Solid::Predicate &*other*) {#operator-and-eq}

'AndEquals' operator.

Assigns to this a new 'and' predicate having this and `other` as operands.

### Solid::Predicate Predicate::operator\|(const Solid::Predicate &*other*) {#operator-7c}

'Or' operator.

Returns a new 'or' predicate having this and `other` as operands.

### Solid::Predicate &Predicate::operator\|=(const Solid::Predicate &*other*) {#operator-7c-eq}

'OrEquals' operator.

Assigns to this a new 'or' predicate having this and `other` as operands.
