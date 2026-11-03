---
title: "KFileMetaData::EmbeddedImageData Class"
description: "EmbeddedImageData defines enums for different image types that can be extracted from the metadata of e.g. music files."
---

# KFileMetaData::EmbeddedImageData Class

[EmbeddedImageData](kfilemetadata-embeddedimagedata.md) defines enums for different image types that can be extracted from the metadata of e.g. music files. [More...](#details)

- **Header:** `#include <KFileMetaData/EmbeddedImageData>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS FileMetaData)`  
  `target_link_libraries(mytarget PRIVATE KF6::FileMetaData)`

[List of all members, including inherited members](kfilemetadata-embeddedimagedata-members.md)

## Public Types

- [enum EmbeddedImageData::ImageType](#ImageType-enum)

## Public Functions

- [EmbeddedImageData()](#EmbeddedImageData)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum EmbeddedImageData::ImageType {#ImageType-enum}

**flags EmbeddedImageData::ImageTypes**

| Constant |   |
| --- | --- |
| `KFileMetaData::EmbeddedImageData::FrontCover` | `1 << 0x0` |
| `KFileMetaData::EmbeddedImageData::Other` | `1 << 0x01` |
| `KFileMetaData::EmbeddedImageData::FileIcon` | `1 << 0x02` |
| `KFileMetaData::EmbeddedImageData::OtherFileIcon` | `1 << 0x03` |
| `KFileMetaData::EmbeddedImageData::BackCover` | `1 << 0x04` |
| `KFileMetaData::EmbeddedImageData::LeafletPage` | `1 << 0x05` |
| `KFileMetaData::EmbeddedImageData::Media` | `1 << 0x06` |
| `KFileMetaData::EmbeddedImageData::LeadArtist` | `1 << 0x07` |
| `KFileMetaData::EmbeddedImageData::Artist` | `1 << 0x08` |
| `KFileMetaData::EmbeddedImageData::Conductor` | `1 << 0x09` |
| `KFileMetaData::EmbeddedImageData::Band` | `1 << 0x0A` |
| `KFileMetaData::EmbeddedImageData::Composer` | `1 << 0x0B` |
| `KFileMetaData::EmbeddedImageData::Lyricist` | `1 << 0x0C` |
| `KFileMetaData::EmbeddedImageData::RecordingLocation` | `1 << 0x0D` |
| `KFileMetaData::EmbeddedImageData::DuringRecording` | `1 << 0x0E` |
| `KFileMetaData::EmbeddedImageData::DuringPerformance` | `1 << 0x0F` |
| `KFileMetaData::EmbeddedImageData::MovieScreenCapture` | `1 << 0x10` |
| `KFileMetaData::EmbeddedImageData::ColouredFish` | `1 << 0x11` |
| `KFileMetaData::EmbeddedImageData::Illustration` | `1 << 0x12` |
| `KFileMetaData::EmbeddedImageData::BandLogo` | `1 << 0x13` |
| `KFileMetaData::EmbeddedImageData::PublisherLogo` | `1 << 0x14` |
| `KFileMetaData::EmbeddedImageData::Unknown` | `1 << 30` |
| `KFileMetaData::EmbeddedImageData::AllImages` | `0x7fffffff` |

The `ImageTypes` type is a typedef for `QFlags<ImageType>. `It stores an OR combination of `ImageType` values.

## Member Function Documentation {#member-function-documentation}

### EmbeddedImageData::EmbeddedImageData() {#EmbeddedImageData}
