---
title: "KSharedPixmapCacheMixin Class"
description: "A simple wrapping layer over KSharedDataCache to support caching images and pixmaps."
---

# KSharedPixmapCacheMixin Class

A simple wrapping layer over [KSharedDataCache](../kcoreaddons/kshareddatacache.md) to support caching images and pixmaps. [More...](#details)

- **Header:** `#include <KImageCache>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS GuiAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::GuiAddons)`

[List of all members, including inherited members](ksharedpixmapcachemixin-members.md)

## Public Functions

- [KSharedPixmapCacheMixin(const QString &cacheName, unsigned int defaultCacheSize, unsigned int expectedItemSize = 0)](#KSharedPixmapCacheMixin)
- [void clear()](#clear)
- [bool findImage(const QString &key, QImage \*destination) const](#findImage)
- [bool findPixmap(const QString &key, QPixmap \*destination) const](#findPixmap)
- [bool insertImage(const QString &key, const QImage &image)](#insertImage)
- [bool insertPixmap(const QString &key, const QPixmap &pixmap)](#insertPixmap)
- [QDateTime lastModifiedTime() const](#lastModifiedTime)
- [bool pixmapCaching() const](#pixmapCaching)
- [void setPixmapCacheLimit(int size)](#setPixmapCacheLimit)
- [void setPixmapCaching(bool enable)](#setPixmapCaching)

## Detailed Description {#details}

This class can be used to share images between different processes, which is useful when it is known that such images will be used across many processes, or when creating the image is expensive.

In addition, the class also supports caching QPixmaps *in a single process* using the [setPixmapCaching](ksharedpixmapcachemixin.md#setPixmapCaching)() function.

Tips for use: If you already have QPixmaps that you intend to use, and you do not need access to the actual image data, then try to store and retrieve QPixmaps for use.

On the other hand, if you will need to store and retrieve actual image data (to modify the image after retrieval for instance) then you should use [QImage](https://doc.qt.io/qt-6/qimage.html) to save the conversion cost from [QPixmap](https://doc.qt.io/qt-6/qpixmap.html) to [QImage](https://doc.qt.io/qt-6/qimage.html).

[KSharedPixmapCacheMixin](ksharedpixmapcachemixin.md) is a subclass of [KSharedDataCache](../kcoreaddons/kshareddatacache.md), so all of the methods that can be used with [KSharedDataCache](../kcoreaddons/kshareddatacache.md) can be used with [KSharedPixmapCacheMixin](ksharedpixmapcachemixin.md), *with the exception of [KSharedDataCache::insert](../kcoreaddons/kshareddatacache.md#insert)() and [KSharedDataCache::find](../kcoreaddons/kshareddatacache.md#find)()*.

## Member Function Documentation {#member-function-documentation}

### KSharedPixmapCacheMixin::KSharedPixmapCacheMixin(const QString &*cacheName*, unsigned int *defaultCacheSize*, unsigned int *expectedItemSize* = 0) {#KSharedPixmapCacheMixin}

Constructs an image cache, named by `cacheName`, with a default size of `defaultCacheSize`.

`cacheName` Name of the cache to use.

`defaultCacheSize` The default size, in bytes, of the cache.

The actual on-disk size will be slightly larger. If the cache already exists, it will not be resized. If it is required to resize the cache then use the deleteCache() function to remove that cache first.

`expectedItemSize` The expected general size of the items to be added to the image cache, in bytes. Use 0 if you just want a default item size.

### void KSharedPixmapCacheMixin::clear() {#clear}

Removes all entries from the cache. In addition any cached pixmaps (as per [setPixmapCaching](ksharedpixmapcachemixin.md#setPixmapCaching)()) are also removed.

### bool KSharedPixmapCacheMixin::findImage(const QString &*key*, QImage \**destination*) const {#findImage}

Copies the cached image identified by `key` to `destination`. If no such image exists `destination` is unchanged.

Returns `true` if the image identified by `key` existed, `false` otherwise.

### bool KSharedPixmapCacheMixin::findPixmap(const QString &*key*, QPixmap \**destination*) const {#findPixmap}

Copies the cached pixmap identified by `key` to `destination`. If no such pixmap exists `destination` is unchanged.

Returns `true` if the pixmap identified by `key` existed, `false` otherwise.

*See also* [setPixmapCaching](ksharedpixmapcachemixin.md#setPixmapCaching)()

### bool KSharedPixmapCacheMixin::insertImage(const QString &*key*, const QImage &*image*) {#insertImage}

Inserts the `image` into the shared cache, accessible with `key`. This variant is preferred over [insertPixmap](ksharedpixmapcachemixin.md#insertPixmap)() if your source data is already a [QImage](https://doc.qt.io/qt-6/qimage.html), if it is essential that the image be in shared memory (such as for SVG icons which have a high render time), or if it will need to be in [QImage](https://doc.qt.io/qt-6/qimage.html) form after it is retrieved from the cache.

`key` Name to access `image` with.

`image` The image to add to the shared cache.

Returns `true` if the image was successfully cached, `false` otherwise.

### bool KSharedPixmapCacheMixin::insertPixmap(const QString &*key*, const QPixmap &*pixmap*) {#insertPixmap}

Inserts the pixmap given by `pixmap` to the cache, accessible with `key`. The pixmap must be converted to a [QImage](https://doc.qt.io/qt-6/qimage.html) in order to be stored into shared memory. In order to prevent unnecessary conversions from taking place `pixmap` will also be cached (but not in shared memory) and would be accessible using [findPixmap](ksharedpixmapcachemixin.md#findPixmap)() if pixmap caching is enabled.

`key` Name to access `pixmap` with.

`pixmap` The pixmap to add to the cache.

Returns `true` if the pixmap was successfully cached, `false` otherwise.

*See also* [setPixmapCaching](ksharedpixmapcachemixin.md#setPixmapCaching)()

### QDateTime KSharedPixmapCacheMixin::lastModifiedTime() const {#lastModifiedTime}

Returns the time that an image or pixmap was last inserted into a cache.

### bool KSharedPixmapCacheMixin::pixmapCaching() const {#pixmapCaching}

Returns if QPixmaps added with [insertPixmap](ksharedpixmapcachemixin.md#insertPixmap)() will be stored in a local pixmap cache as well as the shared image cache. The default is to cache pixmaps locally.

*See also* [setPixmapCaching](ksharedpixmapcachemixin.md#setPixmapCaching)()

### void KSharedPixmapCacheMixin::setPixmapCacheLimit(int *size*) {#setPixmapCacheLimit}

Sets the highest memory size the pixmap cache should use.

`size` The size in bytes

### void KSharedPixmapCacheMixin::setPixmapCaching(bool *enable*) {#setPixmapCaching}

Enables or disables local pixmap caching. If it is anticipated that a pixmap will be frequently needed then this can actually save memory overall since the X server or graphics card will not have to store duplicate copies of the same image.

`enable` Enables pixmap caching if true, disables otherwise.

*See also* [pixmapCaching](ksharedpixmapcachemixin.md#pixmapCaching)()
