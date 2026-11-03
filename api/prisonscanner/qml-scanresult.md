---
title: "scanResult QML Value Type"
description: "Result of a barcode scan attempt."
---

# scanResult QML Value Type

Result of a barcode scan attempt. [More...](#details)

- Import Statement: import org.kde.prison.scanner
- In C++: [ScanResult](prison-scanresult.md)

## Detailed Description {#details}

A scan result consists of the barcode content (which can be text or binary data), the barcode format and the position in the video frame the barcode was detected.

## Property Documentation {#property-documentation}

### \[read-only\] binaryData : bool {#binaryData-prop}

### \[read-only\] boundingRect : rect {#boundingRect-prop}

### \[read-only\] content : variant {#content-prop}

### \[read-only\] format : enumeration {#format-prop}

| Constant |
| --- |
| scanResult.NoFormat |
| scanResult.Aztec |
| scanResult.Codabar |
| scanResult.Code39 |
| scanResult.Code93 |
| scanResult.Code128 |
| scanResult.DataBar |
| scanResult.DataBarExpanded |
| scanResult.DataMatrix |
| scanResult.EAN8 |
| scanResult.EAN13 |
| scanResult.ITF |
| scanResult.MaxiCode |
| scanResult.PDF417 |
| scanResult.QRCode |
| scanResult.UPCA |
| scanResult.UPCE |

### \[read-only\] hasBinaryData : bool {#hasBinaryData-prop}

### \[read-only\] hasContent : bool {#hasContent-prop}

### \[read-only\] hasText : bool {#hasText-prop}

### \[read-only\] text : string {#text-prop}
