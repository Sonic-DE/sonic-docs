---
title: "KIO::ThumbnailRequest Class"
description: "Encapsulates the input data for a thumbnail request."
---

# KIO::ThumbnailRequest Class

Encapsulates the input data for a thumbnail request. [More...](#details)

- **Header:** `#include <KIO/ThumbnailCreator>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KIOGui)`

[List of all members, including inherited members](kio-thumbnailrequest-members.md)

## Public Functions

- [ThumbnailRequest(const QUrl &url, const QSize &targetSize, const QString &mimeType, qreal dpr, float sequenceIndex)](#ThumbnailRequest)
- [qreal devicePixelRatio() const](#devicePixelRatio)
- [QString mimeType() const](#mimeType)
- [float sequenceIndex() const](#sequenceIndex)
- [QSize targetSize() const](#targetSize)
- [QUrl url() const](#url)

## Static Public Members

- [KIO::filesize\_t maximumFileSize()](#maximumFileSize) (since 6.23)

## Detailed Description {#details}

This includes the URL of the target file as well as additional data such as the target size

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ThumbnailRequest::ThumbnailRequest(const QUrl &*url*, const QSize &*targetSize*, const QString &*mimeType*, qreal *dpr*, float *sequenceIndex*) {#ThumbnailRequest}

Construct a new [ThumbnailRequest](kio-thumbnailrequest.md) for a given file.

`url` URL of the relevant file.

`targetSize` A size hint for the result image. The actual result size may be different. This already accounts for highdpi scaling, i.e. if a 500x500px thumbnail with a DPR of 2 is requested 1000x1000 is passed here.

`mimeType` The MIME type of the target file.

`dpr` The device pixle ratio for this request. This can be used to adjust the level of detail rendered. For example a thumbnail for text of size 1000x1000 and DPR 1 should have the name number of text lines as for a request of size 2000x2000 and DPR 2.

`sequenceIndex` If the thumbnailer supports sequences this determines which sequence frame is used. Pass 0 otherwise.

### qreal ThumbnailRequest::devicePixelRatio() const {#devicePixelRatio}

The device Pixel Ratio used for thumbnail creation

### \[static, since 6.23\] KIO::filesize\_t ThumbnailRequest::maximumFileSize() {#maximumFileSize}

Returns the maximum file size that should be considered when taking into account thumbnail requests.

This function was introduced in Qt 6.23.

### QString ThumbnailRequest::mimeType() const {#mimeType}

The target file's MIME type

### float ThumbnailRequest::sequenceIndex() const {#sequenceIndex}

If the thumb-creator can create a sequence of thumbnails, it should use this to decide what sequence item to use.

If the value is zero, the standard thumbnail should be created.

This can be used for example to create thumbnails for different timeframes in videos(For example 0m, 10m, 20m, ...).

If the thumb-creator supports a high granularity, like a video, the sub-integer precision coming from the float should be respected.

If the end of the sequence is reached, the sequence should start from the beginning.

### QSize ThumbnailRequest::targetSize() const {#targetSize}

The target thumbnail size

### QUrl ThumbnailRequest::url() const {#url}

URL of the relevant file
