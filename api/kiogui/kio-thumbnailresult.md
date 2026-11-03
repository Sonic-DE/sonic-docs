---
title: "KIO::ThumbnailResult Class"
description: "Encapsulates the output of a thumbnail request."
---

# KIO::ThumbnailResult Class

Encapsulates the output of a thumbnail request. [More...](#details)

- **Header:** `#include <KIO/ThumbnailCreator>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KIOGui)`

[List of all members, including inherited members](kio-thumbnailresult-members.md)

## Public Functions

- [QImage image() const](#image)
- [bool isValid() const](#isValid)
- [float sequenceIndexWraparoundPoint() const](#sequenceIndexWraparoundPoint)
- [void setSequenceIndexWraparoundPoint(float wraparoundPoint)](#setSequenceIndexWraparoundPoint)

## Static Public Members

- [KIO::ThumbnailResult fail()](#fail)
- [KIO::ThumbnailResult pass(const QImage &image)](#pass)

## Detailed Description {#details}

It contains information on whether the request was successful and, if successful, the requested thumbnail

To create a result use [KIO::ThumbnailResult::pass](kio-thumbnailresult.md#pass)(image) or [KIO::ThumbnailResult::fail](kio-thumbnailresult.md#fail)()

## Member Function Documentation {#member-function-documentation}

### \[static\] KIO::ThumbnailResult ThumbnailResult::fail() {#fail}

Create an error result, i.e. the thumbnail creation failed

### QImage ThumbnailResult::image() const {#image}

The requested thumbnail.

If the request failed the image is null

### bool ThumbnailResult::isValid() const {#isValid}

Whether the request was successful.

### \[static\] KIO::ThumbnailResult ThumbnailResult::pass(const QImage &*image*) {#pass}

Create a successful result with a given image

### float ThumbnailResult::sequenceIndexWraparoundPoint() const {#sequenceIndexWraparoundPoint}

Returns the point at which this thumb-creator's sequence indices will wrap around (loop).

Usually, the frontend will call setSequenceIndex() with indices that increase indefinitely with time, e.g. as long as the user keeps hovering a video file. Most thumb-creators however only want to display a finite sequence of thumbs, after which their sequence repeats.

This method can return the sequence index at which this thumb-creator's sequence starts wrapping around to the start again ("looping"). The frontend may use this to generate only thumbs up to this index, and then use cached versions for the repeating sequence instead.

Like sequenceIndex(), fractional values can be used if the wraparound does not happen at an integer position, but frontends handling only integer sequence indices may choose to round it down.

By default, this method returns a negative index, which signals the frontend that it can't rely on this fixed-length sequence.

*See also* [setSequenceIndexWraparoundPoint](kio-thumbnailresult.md#setSequenceIndexWraparoundPoint)()

### void ThumbnailResult::setSequenceIndexWraparoundPoint(float *wraparoundPoint*) {#setSequenceIndexWraparoundPoint}

Sets the point at which this thumb-creator's sequence indices will wrap around.

*See also* [sequenceIndexWraparoundPoint](kio-thumbnailresult.md#sequenceIndexWraparoundPoint)()
