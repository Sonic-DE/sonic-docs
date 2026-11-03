---
title: "Prison::VideoScanner Class"
description: "Scans a live video feed for barcodes."
---

# Prison::VideoScanner Class

Scans a live video feed for barcodes. [More...](#details)

- **Header:** `#include <Prison/VideoScanner>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Prison)`  
  `target_link_libraries(mytarget PRIVATE KF6::PrisonScanner)`
- **In QML:** [VideoScanner](qml-org-kde-prison-scanner-videoscanner.md)
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](prison-videoscanner-members.md)

## Properties

- [formats : Prison::Format::BarcodeFormats](#formats-prop)
- [\[read-only\] result : Prison::ScanResult](#result-prop)
- [videoSink : QVideoSink\*](#videoSink-prop)

## Public Functions

- [VideoScanner(QObject \*parent = nullptr)](#VideoScanner)
- [Format::BarcodeFormats formats() const](#formats)
- [Prison::ScanResult result() const](#result)
- [void setFormats(Format::BarcodeFormats formats)](#setFormats)
- [void setVideoSink(QVideoSink \*sink)](#setVideoSink)
- [QVideoSink \*videoSink() const](#videoSink)

## Signals

- [void formatsChanged()](#formatsChanged)
- [void resultChanged(const Prison::ScanResult &scanResult)](#resultChanged)
- [void resultContentChanged(const Prison::ScanResult &scanResult)](#resultContentChanged)
- [void videoSinkChanged()](#videoSinkChanged)

## Detailed Description {#details}

This can be connected to a [QVideoSink](https://doc.qt.io/qt-6/qvideosink.html) object.

## Property Documentation {#property-documentation}

### formats : Prison::Format::BarcodeFormats {#formats-prop}

**Access functions:**

- `Format::BarcodeFormats` **[formats](prison-videoscanner.md#formats)**() const
- `void` **[setFormats](prison-videoscanner.md#setFormats)**(`Format::BarcodeFormats` *formats*)

**Notifier signal:**

- `void` **[formatsChanged](prison-videoscanner.md#formatsChanged)**()

### \[read-only\] result : Prison::ScanResult {#result-prop}

**Access functions:**

- `Prison::ScanResult` **[result](prison-videoscanner.md#result)**() const

**Notifier signal:**

- `void` **[resultChanged](prison-videoscanner.md#resultChanged)**(const `Prison::ScanResult` &*scanResult*)

### videoSink : QVideoSink\* {#videoSink-prop}

**Access functions:**

- `QVideoSink` \***[videoSink](prison-videoscanner.md#videoSink)**() const
- `void` **[setVideoSink](prison-videoscanner.md#setVideoSink)**(`QVideoSink` \**sink*)

**Notifier signal:**

- `void` **[videoSinkChanged](prison-videoscanner.md#videoSinkChanged)**()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] VideoScanner::VideoScanner(QObject \**parent* = nullptr) {#VideoScanner}

### Format::BarcodeFormats VideoScanner::formats() const {#formats}

The barcode formats the scanner should look for. By default all supported formats are enabled.

> **Note:** Getter function for property [formats](prison-videoscanner.md#formats-prop).

*See also* [setFormats](prison-videoscanner.md#setFormats)()

### \[signal\] void VideoScanner::formatsChanged() {#formatsChanged}

> **Note:** Notifier signal for property [formats](prison-videoscanner.md#formats-prop).

### Prison::ScanResult VideoScanner::result() const {#result}

The latest result of the barcode scan.

> **Note:** Getter function for property [result](prison-videoscanner.md#result-prop).

### \[signal\] void VideoScanner::resultChanged(const Prison::ScanResult &*scanResult*) {#resultChanged}

Emitted whenever we get a new scan result, as long as any property of the result changes. On a live video feed this can be very frequently due to the changes of the position of the detected barcode. This is therefore useful e.g. for marking the position of the detected barcode.

> **Note:** Notifier signal for property [result](prison-videoscanner.md#result-prop).

*See also* [resultContentChanged](prison-videoscanner.md#resultContentChanged)

### \[signal\] void VideoScanner::resultContentChanged(const Prison::ScanResult &*scanResult*) {#resultContentChanged}

Emitted when a barcode with a new content has been detected, but not when merely the position of a barcode changes in the video stream. This is useful e.g. for continuously scanning multiple codes in one go.

*See also* [resultChanged](prison-videoscanner.md#resultChanged)

### void VideoScanner::setFormats(Format::BarcodeFormats *formats*) {#setFormats}

Sets the barcode formats to detect.

`formats` can be OR'ed values from [Format::BarcodeFormats](prison-format.md#BarcodeFormat-enum).

> **Note:** Setter function for property [formats](prison-videoscanner.md#formats-prop).

*See also* [formats](prison-videoscanner.md#formats)()

### void VideoScanner::setVideoSink(QVideoSink \**sink*) {#setVideoSink}

Sets the video sink to scan for barcodes.

> **Note:** Setter function for property [videoSink](prison-videoscanner.md#videoSink-prop).

*See also* [videoSink](prison-videoscanner.md#videoSink)()

### QVideoSink \*VideoScanner::videoSink() const {#videoSink}

The video sink being scanned for barcodes.

> **Note:** Getter function for property [videoSink](prison-videoscanner.md#videoSink-prop).

*See also* [setVideoSink](prison-videoscanner.md#setVideoSink)()

### \[signal\] void VideoScanner::videoSinkChanged() {#videoSinkChanged}

> **Note:** Notifier signal for property [videoSink](prison-videoscanner.md#videoSink-prop).
