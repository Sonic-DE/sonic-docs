---
title: "Prison::ScanResult Class"
description: "Result of a barcode scan attempt."
---

# Prison::ScanResult Class

Result of a barcode scan attempt. [More...](#details)

- **Header:** `#include <Prison/ScanResult>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Prison)`  
  `target_link_libraries(mytarget PRIVATE KF6::PrisonScanner)`
- **In QML:** [scanResult](qml-scanresult.md)

[List of all members, including inherited members](prison-scanresult-members.md)

## Properties

- [\[read-only\] binaryData : QByteArray](#binaryData-prop)
- [\[read-only\] boundingRect : QRect](#boundingRect-prop)
- [\[read-only\] content : QVariant](#content-prop)
- [\[read-only\] format : Prison::Format::BarcodeFormat](#format-prop)
- [\[read-only\] hasBinaryData : bool](#hasBinaryData-prop)
- [\[read-only\] hasContent : bool](#hasContent-prop)
- [\[read-only\] hasText : bool](#hasText-prop)
- [\[read-only\] text : QString](#text-prop)

## Public Functions

- [ScanResult()](#ScanResult)
- [QByteArray binaryData() const](#binaryData)
- [QRect boundingRect() const](#boundingRect)
- [QVariant content() const](#content)
- [Prison::Format::BarcodeFormat format() const](#format)
- [bool hasBinaryData() const](#hasBinaryData)
- [bool hasContent() const](#hasContent)
- [bool hasText() const](#hasText)
- [QString text() const](#text)
- [bool ScanResult::operator==(const Prison::ScanResult &other) const](#operator-eq-eq)

## Detailed Description {#details}

A scan result consists of the barcode content (which can be text or binary data), the barcode format and the position in the video frame the barcode was detected.

## Property Documentation {#property-documentation}

### \[read-only\] binaryData : QByteArray {#binaryData-prop}

**Access functions:**

- `QByteArray` **[binaryData](prison-scanresult.md#binaryData)**() const

### \[read-only\] boundingRect : QRect {#boundingRect-prop}

**Access functions:**

- `QRect` **[boundingRect](prison-scanresult.md#boundingRect)**() const

### \[read-only\] content : QVariant {#content-prop}

**Access functions:**

- `QVariant` **[content](prison-scanresult.md#content)**() const

### \[read-only\] format : Prison::Format::BarcodeFormat {#format-prop}

**Access functions:**

- `Prison::Format::BarcodeFormat` **[format](prison-scanresult.md#format)**() const

### \[read-only\] hasBinaryData : bool {#hasBinaryData-prop}

**Access functions:**

- `bool` **[hasBinaryData](prison-scanresult.md#hasBinaryData)**() const

### \[read-only\] hasContent : bool {#hasContent-prop}

**Access functions:**

- `bool` **[hasContent](prison-scanresult.md#hasContent)**() const

### \[read-only\] hasText : bool {#hasText-prop}

**Access functions:**

- `bool` **[hasText](prison-scanresult.md#hasText)**() const

### \[read-only\] text : QString {#text-prop}

**Access functions:**

- `QString` **[text](prison-scanresult.md#text)**() const

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ScanResult::ScanResult() {#ScanResult}

### QByteArray ScanResult::binaryData() const {#binaryData}

Returns the binary data content, if the content was binary data rather than text, otherwise returns an empty [QByteArray](https://doc.qt.io/qt-6/qbytearray.html).

> **Note:** Getter function for property [binaryData](prison-scanresult.md#binaryData-prop).

### QRect ScanResult::boundingRect() const {#boundingRect}

The bounding rectangle of the detected barcode in source coordinates.

> **Note:** When using this to display an overlay in a view finder, this needs to be mapped to item coordinates.

> **Note:** Getter function for property [boundingRect](prison-scanresult.md#boundingRect-prop).

### QVariant ScanResult::content() const {#content}

The barcode content, either a [QString](https://doc.qt.io/qt-6/qstring.html) or a [QByteArray](https://doc.qt.io/qt-6/qbytearray.html).

> **Note:** Getter function for property [content](prison-scanresult.md#content-prop).

### Prison::Format::BarcodeFormat ScanResult::format() const {#format}

The format of the detected barcode.

> **Note:** Getter function for property [format](prison-scanresult.md#format-prop).

### bool ScanResult::hasBinaryData() const {#hasBinaryData}

Returns `true` if the found barcode contained a binary data payload.

> **Note:** Getter function for property [hasBinaryData](prison-scanresult.md#hasBinaryData-prop).

### bool ScanResult::hasContent() const {#hasContent}

Returns `true` if a barcode has been found.

> **Note:** Getter function for property [hasContent](prison-scanresult.md#hasContent-prop).

### bool ScanResult::hasText() const {#hasText}

Returns `true` if the found barcode contained a textual payload.

> **Note:** Getter function for property [hasText](prison-scanresult.md#hasText-prop).

### QString ScanResult::text() const {#text}

Returns the textual barcode content, if the content was text rather than binary data, otherwise returns an empty string.

> **Note:** Getter function for property [text](prison-scanresult.md#text-prop).

### bool ScanResult::operator==(const Prison::ScanResult &*other*) const {#operator-eq-eq}
