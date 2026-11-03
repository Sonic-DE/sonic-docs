---
title: "Prison::Format Namespace"
description: "Barcode formats detectable by Prison::VideoScanner."
---

# Prison::Format Namespace

Barcode formats detectable by [Prison::VideoScanner](prison-videoscanner.md). [More...](#details)

- Header: Prison/Format
- CMake: find\_package(KF6 REQUIRED COMPONENTS Prison) target\_link\_libraries(mytarget PRIVATE KF6::PrisonScanner)

## Detailed Description {#details}

*See also* [Prison::ScanResult](prison-scanresult.md)

## Type Documentation {#type-documentation}

### enum Format::BarcodeFormat {#BarcodeFormat-enum}

**flags Format::BarcodeFormats**

| Constant |   |
| --- | --- |
| `Prison::Format::NoFormat` | `0` |
| `Prison::Format::Aztec` | `1` |
| `Prison::Format::Codabar` | `2` |
| `Prison::Format::Code39` | `4` |
| `Prison::Format::Code93` | `8` |
| `Prison::Format::Code128` | `16` |
| `Prison::Format::DataBar` | `32` |
| `Prison::Format::DataBarExpanded` | `64` |
| `Prison::Format::DataMatrix` | `128` |
| `Prison::Format::EAN8` | `256` |
| `Prison::Format::EAN13` | `512` |
| `Prison::Format::ITF` | `1024` |
| `Prison::Format::MaxiCode` | `2048` |
| `Prison::Format::PDF417` | `4096` |
| `Prison::Format::QRCode` | `8192` |
| `Prison::Format::UPCA` | `16384` |
| `Prison::Format::UPCE` | `32768` |

Barcode formats.

The `BarcodeFormats` type is a typedef for `QFlags<BarcodeFormat>. `It stores an OR combination of `BarcodeFormat` values.
