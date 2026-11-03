---
title: "KIO::ThumbnailCreator Class"
description: "Base class for thumbnail generator plugins."
---

# KIO::ThumbnailCreator Class

Base class for thumbnail generator plugins. [More...](#details)

- **Header:** `#include <KIO/ThumbnailCreator>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KIOGui)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kio-thumbnailcreator-members.md)

## Public Functions

- [KIO::ThumbnailResult create(const KIO::ThumbnailRequest &request)](#create)

## Detailed Description {#details}

[KIO::PreviewJob](kio-previewjob.md), via the "thumbnail" KIO worker, uses instances of this class to generate the thumbnail previews.

To add support for a new document type, subclass [KIO::ThumbnailCreator](kio-thumbnailcreator.md) and implement [create](kio-thumbnailcreator.md#create)() to generate a thumbnail for a given path.

Compile your ThumbCreator as a plugin; for example, the relevant CMake code for a thumbnailer for the "foo" filetype might look like

```cpp
kcoreaddons_add_plugin(foothumbnail SOURCES foothumbnail.cpp INSTALL_NAMESPACE "kf6/thumbcreator")
target_link_libraries(foothumbnail PRIVATE KF5::KIOGui)
```

You also need a JSON file containing the metadata:

```cpp
{
  "CacheThumbnail": true,
  "KPlugin": {
      "MimeTypes": [
          "image/x-foo"
      ],
      "Name": "Foo Documents"
  }
}
```

MIME types can also use simple wildcards, like "text/\*"

If the thumbnail creation is cheap (such as text previews), you can set

```cpp
"CacheThumbnail": false
```

in metadata to prevent your thumbnails from being cached on disk.

You can also use the "ThumbnailerVersion" optional property in the .desktop file, like

```cpp
"ThumbnailerVersion": 5
```

When this is incremented (or defined when it previously was not), all the previously-cached thumbnails for this creator will be discarded. You should increase the version if and only if old thumbnails need to be regenerated.

## Member Function Documentation {#member-function-documentation}

### \[pure virtual\] KIO::ThumbnailResult ThumbnailCreator::create(const KIO::ThumbnailRequest &*request*) {#create}

Creates a thumbnail for a given request
