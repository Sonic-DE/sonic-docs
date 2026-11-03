---
title: "KExiv2Iface::KExiv2Previews Class"
description: "Todo."
---

# KExiv2Iface::KExiv2Previews Class

Todo. [More...](#details)

- **Header:** `#include <KExiv2/KExiv2Previews>`
- **CMake:** `find_package(KExiv2Qt6 REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE KExiv2Qt6)`

[List of all members, including inherited members](kexiv2iface-kexiv2previews-members.md)

## Public Functions

- [KExiv2Previews(const QByteArray &imgData)](#KExiv2Previews)
- [KExiv2Previews(const QString &filePath)](#KExiv2Previews-1)
- [~KExiv2Previews()](#dtor.KExiv2Previews)
- [int count()](#count)
- [QByteArray data(int index = 0)](#data)
- [int dataSize(int index = 0)](#dataSize)
- [QString fileExtension(int index = 0)](#fileExtension)
- [int height(int index = 0)](#height)
- [QImage image(int index = 0)](#image)
- [bool isEmpty()](#isEmpty)
- [QString mimeType(int index = 0)](#mimeType)
- [QString originalMimeType() const](#originalMimeType)
- [QSize originalSize() const](#originalSize)
- [int size()](#size)
- [int width(int index = 0)](#width)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### KExiv2Previews::KExiv2Previews(const QByteArray &*imgData*) {#KExiv2Previews}

Open the given image data and scan the image for embedded preview images.

### KExiv2Previews::KExiv2Previews(const QString &*filePath*) {#KExiv2Previews-1}

Open the given file and scan for embedded preview images.

### \[noexcept\] KExiv2Previews::~KExiv2Previews() {#dtor.KExiv2Previews}

### int KExiv2Previews::count() {#count}

Returns how many embedded previews are available.

### QByteArray KExiv2Previews::data(int *index* = 0) {#data}

Retrieve the image data for the specified embedded preview image.

### int KExiv2Previews::dataSize(int *index* = 0) {#dataSize}

For each contained preview image, return the size of the image data in bytes, width and height of the preview, the [mimeType](kexiv2iface-kexiv2previews.md#mimeType) and the file extension.

Ensure that index \< [count](kexiv2iface-kexiv2previews.md#count)().

Previews are sorted by width\*height, largest first.

### QString KExiv2Previews::fileExtension(int *index* = 0) {#fileExtension}

### int KExiv2Previews::height(int *index* = 0) {#height}

### QImage KExiv2Previews::image(int *index* = 0) {#image}

Loads the data of the specified preview and creates a QImage from this data.

Returns a null QImage if the loading failed.

### bool KExiv2Previews::isEmpty() {#isEmpty}

Returns if there are any preview images available.

### QString KExiv2Previews::mimeType(int *index* = 0) {#mimeType}

### QString KExiv2Previews::originalMimeType() const {#originalMimeType}

Returns the [mimeType](kexiv2iface-kexiv2previews.md#mimeType) of the original image, detected from the file's content.

### QSize KExiv2Previews::originalSize() const {#originalSize}

Returns the pixel size of the original image, as read from the file (not the metadata).

### int KExiv2Previews::size() {#size}

### int KExiv2Previews::width(int *index* = 0) {#width}
