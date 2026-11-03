---
title: "Prison::MeCard Class"
description: "Barcode Rendering."
---

# Prison::MeCard Class

Barcode Rendering. [More...](#details)

- **Header:** `#include <Prison/MeCard>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Prison)`  
  `target_link_libraries(mytarget PRIVATE KF6::Prison)`

[List of all members, including inherited members](prison-mecard-members.md)

## Public Functions

- [QString header() const](#header)
- [QStringView headerView() const](#headerView)
- [QVariantMap toVariantMap() const](#toVariantMap)
- [QString value(QStringView key) const](#value)
- [QStringList values(QStringView key) const](#values)

## Static Public Members

- [std::optional\<Prison::MeCard\> parse(const QString &data)](#parse)

## Detailed Description {#details}

Parser for the [MeCard](prison-mecard.md) format. This was originally used for a more compact vCard representation, but today is mostly relevant for Wifi configuration QR codes.

*See also* [https://en.wikipedia.org/wiki/MeCard_(QR_code)](https://en.wikipedia.org/wiki/MeCard_(QR_code)), [https://github.com/zxing/zxing/wiki/Barcode-Contents#wi-fi-network-config-android-ios-11](https://github.com/zxing/zxing/wiki/Barcode-Contents#wi-fi-network-config-android-ios-11)

## Member Function Documentation {#member-function-documentation}

### QString MeCard::header() const {#header}

Get the [MeCard](prison-mecard.md) header.

If you just want to identify the card, use [headerView](prison-mecard.md#headerView)() instead.

### QStringView MeCard::headerView() const {#headerView}

Get the [MeCard](prison-mecard.md) header as a string view.

Useful for identifying the type of card.

### \[static\] std::optional\<Prison::MeCard\> MeCard::parse(const QString &*data*) {#parse}

Parse the given string

`data` The string to parse

Returns a [MeCard](prison-mecard.md), if parsing was successful, a nullopt otherwise.

### QVariantMap MeCard::toVariantMap() const {#toVariantMap}

Get the parsed data as [QVariantMap](https://doc.qt.io/qt-6/qvariant.html#QVariantMap-typedef).

### QString MeCard::value(QStringView *key*) const {#value}

Get the value for a given key.

Convenience method for getting the first value if only one value is expected.

### QStringList MeCard::values(QStringView *key*) const {#values}

Get the list of values for a given key.
