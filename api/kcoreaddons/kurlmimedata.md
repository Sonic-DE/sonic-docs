---
title: "KUrlMimeData Namespace"
description: "Utility functions for using URLs in QMimeData."
---

# KUrlMimeData Namespace

Utility functions for using URLs in [QMimeData](https://doc.qt.io/qt-6/qmimedata.html). [More...](#details)

- Header: KUrlMimeData
- CMake: find\_package(KF6 REQUIRED COMPONENTS CoreAddons) target\_link\_libraries(mytarget PRIVATE KF6::CoreAddons)

## Detailed Description {#details}

In addition to [QMimeData::setUrls](https://doc.qt.io/qt-6/qmimedata.html#setUrls)() and [QMimeData::urls](https://doc.qt.io/qt-6/qmimedata.html#urls)(), these functions allow to:

- Store two sets of URLs, the KDE-specific URLs and the equivalent local-file URLs for compatibility with non-KDE applications
- Store KIO metadata, such as the HTTP referrer for a given URL (some websites require it for downloading e.g. an image)

## Type Documentation {#type-documentation}

### enum KUrlMimeData::DecodeOption {#DecodeOption-enum}

**flags KUrlMimeData::DecodeOptions**

Flags to be used in [urlsFromMimeData](kurlmimedata.md#urlsFromMimeData).

| Constant | Value | Description |
| --- | --- | --- |
| `KUrlMimeData::PreferKdeUrls` | `0` | When the mimedata contains both KDE-style URLs (eg: desktop:/foo) and the "most local" version of the URLs (eg: file:///home/dfaure/Desktop/foo), decode it as the KDE-style URL. Useful in DnD code e.g. when moving icons, and the kde-style url is used as identifier for the icons. |
| `KUrlMimeData::PreferLocalUrls` | `1` | When the mimedata contains both KDE-style URLs (eg: desktop:/foo) and the "most local" version of the URLs (eg: file:///home/dfaure/Desktop/foo), decode it as local urls. Useful in paste/drop operations that end up calling KIO, so that urls from other users work as well. |

The `DecodeOptions` type is a typedef for `QFlags<DecodeOption>. `It stores an OR combination of `DecodeOption` values.

### KUrlMimeData::MetaDataMap {#MetaDataMap-typedef}

Alias for [QMap](https://doc.qt.io/qt-6/qmap.html)\<[QString](https://doc.qt.io/qt-6/qstring.html), [QString](https://doc.qt.io/qt-6/qstring.html)\>

## Function Documentation {#function-documentation}

### bool KUrlMimeData::exportUrlsToPortal(QMimeData \**mimeData*) {#exportUrlsToPortal}

Export URLs through the XDG Documents Portal to allow interaction from/with sandbox code.

This implements the application/vnd.portal.filetransfer mimetype extension.

When built without dbus support or the portal isn't installed on the target system, then this is no-op and returns false.

Remote URLs are automatically mounted into the file system using kio-fuse

Returns whether all URLS were exported through the portal

### QStringList KUrlMimeData::mimeDataTypes() {#mimeDataTypes}

Return the list of mimeTypes that can be decoded by [urlsFromMimeData](kurlmimedata.md#urlsFromMimeData)

### void KUrlMimeData::setMetaData(const KUrlMimeData::MetaDataMap &*metaData*, QMimeData \**mimeData*) {#setMetaData}

`metaData` KIO metadata shipped in the mime data, which is used for instance to set a correct HTTP referrer (some websites require it for downloading e.g. an image)

### void KUrlMimeData::setUrls(const QList\<QUrl\> &*urls*, const QList\<QUrl\> &*mostLocalUrls*, QMimeData \**mimeData*) {#setUrls}

Adds URLs and KIO metadata into the given [QMimeData](https://doc.qt.io/qt-6/qmimedata.html).

> **Warning:** do not call this method multiple times on the same mimedata object, you can add urls only once. But you can add other things, e.g. images, XML...

`mimeData` the [QMimeData](https://doc.qt.io/qt-6/qmimedata.html) instance used to drag or copy this URL

### QList\<QUrl\> KUrlMimeData::urlsFromMimeData(const QMimeData \**mimeData*, KUrlMimeData::DecodeOptions *decodeOptions* = PreferKdeUrls, KUrlMimeData::MetaDataMap \**metaData* = nullptr) {#urlsFromMimeData}

Extract a list of urls from the contents of `mimeData`.

Compared to [QMimeData::urls](https://doc.qt.io/qt-6/qmimedata.html#urls)(), this method has support for retrieving KDE-specific URLs when urls() would retrieve "most local URLs" instead as well as support for the XDG Documents Portal via the application/vnd.portal.filetransfer mimedata extension.

Decoding will fail if `mimeData` does not contain any URLs, or if at least one extracted URL is not valid.

When application/vnd.portal.filetransfer is set you'll only receive URLs retrieved from the XDG Documents Portal. When the portal is not available application/vnd.portal.filetransfer gets ignored.

`mimeData` the mime data to extract from; cannot be 0

`decodeOptions` options for decoding

`metaData` optional pointer to a map which will hold the metadata after this call

Returns the list of urls
