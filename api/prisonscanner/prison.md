---
title: "Prison Namespace"
description: "Barcode Scanning."
---

# Prison Namespace

Barcode Scanning. [More...](#details)

- Header: Prison
- CMake: find\_package(KF6 REQUIRED COMPONENTS Prison) target\_link\_libraries(mytarget PRIVATE KF6::PrisonScanner)

## Detailed Description {#details}

## Namespaces {#namespaces}

### namespace Prison::Format

*See also* [Prison::ScanResult](prison-scanresult.md)

### \[since 6.3\] namespace Prison::ImageScanner

This namespace was introduced in Qt 6.3.

## Classes {#classes}

### class [ScanResult](prison-scanresult.md)

Result of a barcode scan attempt.

### class [VideoScanner](prison-videoscanner.md)

Scans a live video feed for barcodes.
