---
title: "Prison::ImageScanner Namespace"
description: "Scans a still image for barcodes. This namespace was introduced in Qt 6.3."
---

# Prison::ImageScanner Namespace

Scans a still image for barcodes. This namespace was introduced in Qt 6.3. [More...](#details)

- Header: Prison/ImageScanner
- Since: Qt 6.3
- CMake: find\_package(KF6 REQUIRED COMPONENTS Prison) target\_link\_libraries(mytarget PRIVATE KF6::PrisonScanner)

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### \[since 6.3\] Prison::ScanResult ImageScanner::scan(const QImage &*image*, Format::BarcodeFormats *formats* = {}) {#scan}

Scan `image` for a barcode.

This method is synchronous and expensive. For use in the main thread running this on a secondary thread is strongly recommended when processing larger images.

```cpp
QtConcurrent::run([&img]() { return ImageScanner::scan(img); }).then([](const ScanResult &result) {
  ...
});
```

`image` The image to scan for barcodes, in any format.

`formats` The barcode formats to look for. By default all supported formats are searched, limiting this improves performance and can improve result quality.

This function was introduced in Qt 6.3.
