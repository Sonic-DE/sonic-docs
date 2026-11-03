---
title: "Syndication::Image Class"
description: "This class represents an image file on the web."
---

# Syndication::Image Class

This class represents an image file on the web. [More...](#details)

- **Header:** `#include <Syndication/Image>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`

[List of all members, including inherited members](syndication-image-members.md)

## Public Functions

- [QString debugInfo() const](#debugInfo)
- [QString description() const](#description)
- [uint height() const](#height)
- [bool isNull() const](#isNull)
- [QString link() const](#link)
- [QString title() const](#title)
- [QString url() const](#url)
- [uint width() const](#width)

## Detailed Description {#details}

It is usually some kind of feed logo which can be displayed when showing the feed description.

## Member Function Documentation {#member-function-documentation}

### \[virtual\] QString Image::debugInfo() const {#debugInfo}

returns a description of the image for debugging purposes

### \[pure virtual\] QString Image::description() const {#description}

optional text that can be included in the TITLE attribute of the link formed around the image in HTML rendering.

### \[pure virtual\] uint Image::height() const {#height}

Returns the image height in pixels or 0 of not specified in the feed.

### \[pure virtual\] bool Image::isNull() const {#isNull}

returns whether this image is a null object.

### \[pure virtual\] QString Image::link() const {#link}

The URL of the site, when the channel is rendered, the image should be a link to the site. If not set, use [Feed::link](syndication-feed.md#link)().

Returns the url the rendered image should link to, or a null string if not specified in the feed.

### \[pure virtual\] QString Image::title() const {#title}

Describes the image, can be used in the ALT attribute of the HTML \<img\> tag when the channel is rendered in HTML.

### \[pure virtual\] QString Image::url() const {#url}

the URL of a GIF, JPEG or PNG image

### \[pure virtual\] uint Image::width() const {#width}

Returns the image width in pixels or 0 if not specified in the feed.
