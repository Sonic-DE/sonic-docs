---
title: "VideoScanner QML Type"
description: "Scans a live video feed for barcodes."
---

# VideoScanner QML Type

Scans a live video feed for barcodes. [More...](#details)

- Import Statement: import org.kde.prison.scanner
- In C++: [VideoScanner](prison-videoscanner.md)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### formats : flags {#formats-prop}

| Constant |
| --- |
| VideoScanner.NoFormat |
| VideoScanner.Aztec |
| VideoScanner.Codabar |
| VideoScanner.Code39 |
| VideoScanner.Code93 |
| VideoScanner.Code128 |
| VideoScanner.DataBar |
| VideoScanner.DataBarExpanded |
| VideoScanner.DataMatrix |
| VideoScanner.EAN8 |
| VideoScanner.EAN13 |
| VideoScanner.ITF |
| VideoScanner.MaxiCode |
| VideoScanner.PDF417 |
| VideoScanner.QRCode |
| VideoScanner.UPCA |
| VideoScanner.UPCE |

### \[read-only\] result : scanResult {#result-prop}

### videoSink : QVideoSink {#videoSink-prop}

## Signal Documentation {#signal-documentation}

### resultChanged(scanResult *scanResult*) {#resultChanged-signal}

> **Note:** The corresponding handler is `onResultChanged`.

### resultContentChanged(scanResult *scanResult*) {#resultContentChanged-signal}

> **Note:** The corresponding handler is `onResultContentChanged`.
