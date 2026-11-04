---
title: "Prison Namespace"
description: "Provides classes and methods for generating barcodes."
---

# Prison Namespace

Provides classes and methods for generating barcodes. [More...](#details)

- **Header:** `#include <Prison/Prison>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Prison)`  
  `target_link_libraries(mytarget PRIVATE KF6::Prison)`

## Detailed Description {#details}

## Classes {#classes}

### class [Barcode](prison-barcode.md)

### class [MeCard](prison-mecard.md)

## Type Documentation {#type-documentation}

### enum Prison::BarcodeType {#BarcodeType-enum}

possible supported barcode types

| Constant | Value | Description |
| --- | --- | --- |
| `Prison::QRCode` | `0` | QRCode 2d barcode |
| `Prison::DataMatrix` | `1` | DataMatrix 2d barcode |
| `Prison::Aztec` | `2` | Aztec 2d barcode |
| `Prison::Code39` | `3` | Code39 barcode |
| `Prison::Code93` | `4` | Code93 barcode |
| `Prison::Code128` | `5` | Code 128 barcode |
| `Prison::PDF417` | `6` | PDF417 barcode |
| `Prison::EAN13` | `7` | EAN13 barcode |
| `Prison::ITF (since Qt 6.28)` | `8` | Industrial 2 of 5 barcode |
| `Prison::Codabar (since Qt 6.28)` | `9` | Codabar barcode |
