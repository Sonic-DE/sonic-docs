---
title: "KSvg::ImageSet Class"
description: "Interface to the Svg image set."
---

# KSvg::ImageSet Class

Interface to the Svg image set. [More...](#details)

- **Header:** `#include <KSvg/ImageSet>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Svg)`  
  `target_link_libraries(mytarget PRIVATE KF6::Svg)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](ksvg-imageset-members.md)  
[Deprecated members](ksvg-imageset-obsolete.md)

## Properties

- [basePath : QString](#basePath-prop)
- [imageSetName : QString](#imageSetName-prop)

## Public Functions

- [ImageSet(QObject \*parent = nullptr)](#ImageSet)
- [ImageSet(const QString &imageSetName, const QString &basePath = {}, QObject \*parent = nullptr)](#ImageSet-1)
- [QString basePath() const](#basePath)
- [bool currentImageSetHasImage(const QString &name) const](#currentImageSetHasImage)
- [QString filePath(const QString &name) const](#filePath)
- [QString imagePath(const QString &name) const](#imagePath)
- [QString imageSetName() const](#imageSetName)
- [QStringList selectors() const](#selectors)
- [void setBasePath(const QString &basePath)](#setBasePath)
- [void setImageSetName(const QString &imageSetName)](#setImageSetName)
- [void setSelectors(const QStringList &selectors)](#setSelectors)

## Signals

- [void basePathChanged(const QString &basePath)](#basePathChanged)
- [void imageSetChanged(const QString &imageSetName)](#imageSetChanged)

## Detailed Description {#details}

[KSvg::ImageSet](ksvg-imageset.md) provides access to a common and standardized set of graphic elements stored in SVG format. This allows artists to create single packages of SVGs that will affect the look and feel of all workspace components.

[KSvg::Svg](ksvg-svg.md) uses [KSvg::ImageSet](ksvg-imageset.md) internally to locate and load the appropriate SVG data. Alternatively, [KSvg::ImageSet](ksvg-imageset.md) can be used directly to retrieve file system paths to SVGs by name.

## Property Documentation {#property-documentation}

### basePath : QString {#basePath-prop}

**Access functions:**

- `QString` **[basePath](ksvg-imageset.md#basePath)**() const
- `void` **[setBasePath](ksvg-imageset.md#setBasePath)**(const `QString` &*basePath*)

**Notifier signal:**

- `void` **[imageSetChanged](ksvg-imageset.md#imageSetChanged)**(const `QString` &*imageSetName*)

### imageSetName : QString {#imageSetName-prop}

**Access functions:**

- `QString` **[imageSetName](ksvg-imageset.md#imageSetName)**() const
- `void` **[setImageSetName](ksvg-imageset.md#setImageSetName)**(const `QString` &*imageSetName*)

**Notifier signal:**

- `void` **[imageSetChanged](ksvg-imageset.md#imageSetChanged)**(const `QString` &*imageSetName*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ImageSet::ImageSet(QObject \**parent* = nullptr) {#ImageSet}

Default constructor.

`parent` the parent object

### \[explicit\] ImageSet::ImageSet(const QString &*imageSetName*, const QString &*basePath* = {}, QObject \**parent* = nullptr) {#ImageSet-1}

This method constructs a theme which will be a custom theme instance of [imageSetName](ksvg-imageset.md#imageSetName).

`imageSetName` the name of the theme to create `basePath` base path for the theme to look for svgs. if empty, the default will be used. `parent` the parent object

### QString ImageSet::basePath() const {#basePath}

This method returns the base path of the theme where the SVGs will be looked for.

> **Note:** Getter function for property [basePath](ksvg-imageset.md#basePath-prop).

*See also* [setBasePath](ksvg-imageset.md#setBasePath)()

### \[signal\] void ImageSet::basePathChanged(const QString &*basePath*) {#basePathChanged}

This signal is emitted when the user changes the base path of the image set.

### bool ImageSet::currentImageSetHasImage(const QString &*name*) const {#currentImageSetHasImage}

This method checks whether this theme contains an image with the given name.

`name` the name of the file in the theme directory (without the ".svg" part or a leading slash)

Returns true if the image exists for this theme

### QString ImageSet::filePath(const QString &*name*) const {#filePath}

This method returns the path for a generic file in the current theme.

The theme can also ship any generic file, such as configuration files.

`name` the name of the file in the theme directory (without a leading slash)

Returns the full path to the requested file for the current theme

### QString ImageSet::imagePath(const QString &*name*) const {#imagePath}

This method returns the path for an SVG image in the current theme.

`name` the name of the file in the theme directory (without the ".svg" part or a leading slash).

Returns the full path to the requested file for the current theme

### \[signal\] void ImageSet::imageSetChanged(const QString &*imageSetName*) {#imageSetChanged}

This signal is emitted when the user makes changes to the theme.

Rendered images, colors, etc. should be updated at this point. However, SVGs should \*not\* be repainted in response to this signal; connect to [Svg::repaintNeeded](ksvg-svg.md#repaintNeeded)() instead for that, as SVG objects need repainting not only when imageSetChanged() is emitted; moreover SVG objects connect to and respond appropriately to imageSetChanged() internally, emitting [Svg::repaintNeeded](ksvg-svg.md#repaintNeeded)() at an appropriate time.

> **Note:** Notifier signal for properties [basePath](ksvg-imageset.md#basePath-prop) and [imageSetName](ksvg-imageset.md#imageSetName-prop).

### QString ImageSet::imageSetName() const {#imageSetName}

This method returns the name of the current theme.

> **Note:** Getter function for property [imageSetName](ksvg-imageset.md#imageSetName-prop).

*See also* [setImageSetName](ksvg-imageset.md#setImageSetName)()

### QStringList ImageSet::selectors() const {#selectors}

This method returns the current selectors in order of preference.

*See also* [setSelectors](ksvg-imageset.md#setSelectors)()

### void ImageSet::setBasePath(const QString &*basePath*) {#setBasePath}

This method sets a base path for the theme to look for SVGs.

It can be a path relative to [QStandardPaths::GenericDataLocation](https://doc.qt.io/qt-6/qstandardpaths.html#StandardLocation-enum) or an absolute path.

`basePath` the base path

> **Note:** Setter function for property [basePath](ksvg-imageset.md#basePath-prop).

*See also* [basePath](ksvg-imageset.md#basePath)()

### void ImageSet::setImageSetName(const QString &*imageSetName*) {#setImageSetName}

This method sets the current theme.

> **Note:** Setter function for property [imageSetName](ksvg-imageset.md#imageSetName-prop).

*See also* [imageSetName](ksvg-imageset.md#imageSetName)()

### void ImageSet::setSelectors(const QStringList &*selectors*) {#setSelectors}

This method sets the file selectors.

The theme can have different svgs with the same name for different situations and platforms. The Plasma desktop for instance uses "opaque" or "translucent" based on presence of compositing and KWin blur effects. Other uses may be platform, like android-specific graphics.

`selectors` selectors in order of preference

*See also* [selectors](ksvg-imageset.md#selectors)()
