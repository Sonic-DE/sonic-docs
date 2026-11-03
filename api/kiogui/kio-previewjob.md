---
title: "KIO::PreviewJob Class"
description: "KIO Job to get a thumbnail picture."
---

# KIO::PreviewJob Class

KIO Job to get a thumbnail picture. [More...](#details)

- **Header:** `#include <KIO/PreviewJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KIOGui)`
- **Inherits:** [KIO::Job](../kiocore/kio-job.md)

[List of all members, including inherited members](kio-previewjob-members.md)  
[Deprecated members](kio-previewjob-obsolete.md)

## Public Types

- [enum PreviewJob::ScaleType](#ScaleType-enum)

## Public Functions

- [PreviewJob(const KFileItemList &items, const QSize &size, const QStringList \*enabledPlugins = nullptr)](#PreviewJob)
- [bool handlesSequences() const](#handlesSequences)
- [KIO::PreviewJob::ScaleType scaleType() const](#scaleType)
- [int sequenceIndex() const](#sequenceIndex)
- [float sequenceIndexWraparoundPoint() const](#sequenceIndexWraparoundPoint)
- [void setDevicePixelRatio(qreal dpr)](#setDevicePixelRatio)
- [void setIgnoreMaximumSize(bool ignoreSize = true)](#setIgnoreMaximumSize)
- [void setScaleType(KIO::PreviewJob::ScaleType type)](#setScaleType)
- [void setSequenceIndex(int index)](#setSequenceIndex)

## Signals

- [void failed(const KFileItem &item)](#failed)
- [void generated(const KFileItem &item, const QImage &preview)](#generated) (since 6.15)
- [void gotPreview(const KFileItem &item, const QPixmap &preview)](#gotPreview)

## Static Public Members

- [QStringList availablePlugins()](#availablePlugins)
- [QList\<KPluginMetaData\> availableThumbnailerPlugins()](#availableThumbnailerPlugins)
- [QStringList defaultPlugins()](#defaultPlugins)
- [void setDefaultDevicePixelRatio(qreal devicePixelRatio)](#setDefaultDevicePixelRatio)
- [QStringList supportedMimeTypes()](#supportedMimeTypes)

## Detailed Description {#details}

This class catches a preview (thumbnail) for files.

## Member Type Documentation {#member-type-documentation}

### enum PreviewJob::ScaleType {#ScaleType-enum}

Specifies the type of scaling that is applied to the generated preview. For HiDPI, pixel density scaling, see [setDevicePixelRatio](kio-previewjob.md#setDevicePixelRatio)

| Constant | Value | Description |
| --- | --- | --- |
| `KIO::PreviewJob::Unscaled` | `0` | The original size of the preview will be returned. Most previews will return a size of 256 x 256 pixels. |
| `KIO::PreviewJob::Scaled` | `1` | The preview will be scaled to the size specified when constructing the [PreviewJob](kio-previewjob.md). The aspect ratio will be kept. |
| `KIO::PreviewJob::ScaledAndCached` | `2` | The preview will be scaled to the size specified when constructing the [PreviewJob](kio-previewjob.md). The result will be cached for later use. Per default ScaledAndCached is set. |

## Member Function Documentation {#member-function-documentation}

### PreviewJob::PreviewJob(const KFileItemList &*items*, const QSize &*size*, const QStringList \**enabledPlugins* = nullptr) {#PreviewJob}

`items` List of files to create previews for. `size` Desired size of the preview. `enabledPlugins` If non-zero it defines the list of plugins that are considered for generating the preview. If enabledPlugins is zero the plugins specified in the [KConfigGroup](../kconfigcore/kconfiggroup.md) "PreviewSettings" are used.

### \[static\] QStringList PreviewJob::availablePlugins() {#availablePlugins}

Returns a list of all available preview plugins. The list contains the basenames of the plugins' .desktop files (no path, no .desktop). Returns the list of all available plugins

### \[static\] QList\<KPluginMetaData\> PreviewJob::availableThumbnailerPlugins() {#availableThumbnailerPlugins}

Returns all plugins that are considered when a preview is generated The result is internally cached, meaning any further method call will not reload the plugins

### \[static\] QStringList PreviewJob::defaultPlugins() {#defaultPlugins}

Returns a list of plugins that should be enabled by default, which is all plugins Minus the plugins specified in an internal blacklist Returns the list of plugins that should be enabled by default

### \[signal\] void PreviewJob::failed(const KFileItem &*item*) {#failed}

Emitted when a thumbnail for `item` could not be created, either because a ThumbCreator for its MIME type does not exist, or because something went wrong.

`item` the file that failed

### \[signal, since 6.15\] void PreviewJob::generated(const KFileItem &*item*, const QImage &*preview*) {#generated}

Emitted when a `preview` for `item` has been successfully generated.

This function was introduced in Qt 6.15.

### \[signal\] void PreviewJob::gotPreview(const KFileItem &*item*, const QPixmap &*preview*) {#gotPreview}

Emitted when a thumbnail picture for `item` has been successfully retrieved.

`item` the file of the preview

`preview` the preview image

> **Note:** If you need a preview as a [QImage](https://doc.qt.io/qt-6/qimage.html) object, use the [generated](kio-previewjob.md#generated)() signal.

*See also* [generated](kio-previewjob.md#generated)()

### bool PreviewJob::handlesSequences() const {#handlesSequences}

Determines whether the ThumbCreator in use is a ThumbSequenceCreator.

### KIO::PreviewJob::ScaleType PreviewJob::scaleType() const {#scaleType}

Returns The scale type for the generated preview.

*See also* [setScaleType](kio-previewjob.md#setScaleType)(), [PreviewJob::ScaleType](kio-previewjob.md#ScaleType-enum)

### int PreviewJob::sequenceIndex() const {#sequenceIndex}

Returns the currently set sequence index

*See also* [setSequenceIndex](kio-previewjob.md#setSequenceIndex)()

### float PreviewJob::sequenceIndexWraparoundPoint() const {#sequenceIndexWraparoundPoint}

Returns the index at which the thumbs of a ThumbSequenceCreator start wrapping around ("looping"). Fractional values may be returned if the ThumbSequenceCreator supports sub-integer precision, but frontends supporting only integer sequence indices may choose to round it down.

### \[static\] void PreviewJob::setDefaultDevicePixelRatio(qreal *devicePixelRatio*) {#setDefaultDevicePixelRatio}

Sets a default device Pixel Ratio used for Previews

Defaults to 1

*See also* [setDevicePixelRatio](kio-previewjob.md#setDevicePixelRatio)

### void PreviewJob::setDevicePixelRatio(qreal *dpr*) {#setDevicePixelRatio}

Request preview to use the device pixel ratio `dpr`. The returned thumbnail may not respect the device pixel ratio requested. Use [QPixmap::devicePixelRatio](https://doc.qt.io/qt-6/qpixmap.html#devicePixelRatio) to check, or paint as necessary.

### void PreviewJob::setIgnoreMaximumSize(bool *ignoreSize* = true) {#setIgnoreMaximumSize}

If `ignoreSize` is true, then the preview is always generated regardless of the settings

### void PreviewJob::setScaleType(KIO::PreviewJob::ScaleType *type*) {#setScaleType}

Sets the scale type for the generated preview. Per default [PreviewJob::ScaledAndCached](kio-previewjob.md#ScaleType-enum) is set.

*See also* [scaleType](kio-previewjob.md#scaleType)(), [PreviewJob::ScaleType](kio-previewjob.md#ScaleType-enum)

### void PreviewJob::setSequenceIndex(int *index*) {#setSequenceIndex}

Sets the sequence `index` given to the thumb creators. Use the sequence index, it is possible to create alternative icons for the same item. For example it may allow iterating through the items of a directory, or the frames of a video.

*See also* [sequenceIndex](kio-previewjob.md#sequenceIndex)()

### \[static\] QStringList PreviewJob::supportedMimeTypes() {#supportedMimeTypes}

Returns a list of all supported MIME types. The list can contain entries like text/ \* (without the space). Returns the list of MIME types

## Related Non-Members {#related-non-members}

### KIO::PreviewJob \*filePreview(const KFileItemList &*items*, const QSize &*size*, const QStringList \**enabledPlugins* = nullptr) {#filePreview}

Creates a [PreviewJob](kio-previewjob.md) to generate a preview image for the given items.

`items` List of files to create previews for.

`size` Desired size of the preview.

`enabledPlugins` If non-zero it defines the list of plugins that are considered for generating the preview. If enabledPlugins is zero the plugins specified in the [KConfigGroup](../kconfigcore/kconfiggroup.md) "PreviewSettings" are used.
