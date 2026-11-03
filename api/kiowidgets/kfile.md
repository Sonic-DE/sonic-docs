---
title: "KFile Class"
description: "KFile is a class which provides a namespace for some enumerated values associated with the kfile library. You will never need to construct a KFile object itself."
---

# KFile Class

[KFile](kfile.md) is a class which provides a namespace for some enumerated values associated with the kfile library. You will never need to construct a [KFile](kfile.md) object itself. [More...](#details)

- **Header:** `#include <KFile>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`

[List of all members, including inherited members](kfile-members.md)

## Public Types

- [enum KFile::FileView](#FileView-enum)
- [enum KFile::Mode](#Mode-enum)
- [enum KFile::SelectionMode](#SelectionMode-enum)

## Static Public Members

- [bool isDefaultView(const KFile::FileView &view)](#isDefaultView)
- [bool isDetailTreeView(const KFile::FileView &view)](#isDetailTreeView)
- [bool isDetailView(const KFile::FileView &view)](#isDetailView)
- [bool isPreviewContents(const KFile::FileView &view)](#isPreviewContents)
- [bool isPreviewInfo(const KFile::FileView &view)](#isPreviewInfo)
- [bool isSeparateDirs(const KFile::FileView &view)](#isSeparateDirs)
- [bool isSimpleView(const KFile::FileView &view)](#isSimpleView)
- [bool isSortByDate(const QDir::SortFlags &sort)](#isSortByDate)
- [bool isSortByName(const QDir::SortFlags &sort)](#isSortByName)
- [bool isSortBySize(const QDir::SortFlags &sort)](#isSortBySize)
- [bool isSortByType(const QDir::SortFlags &sort)](#isSortByType)
- [bool isSortCaseInsensitive(const QDir::SortFlags &sort)](#isSortCaseInsensitive)
- [bool isSortDirsFirst(const QDir::SortFlags &sort)](#isSortDirsFirst)
- [bool isTreeView(const KFile::FileView &view)](#isTreeView)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum KFile::FileView {#FileView-enum}

| Constant |   |
| --- | --- |
| `KFile::Default` | `0` |
| `KFile::Simple` | `1` |
| `KFile::Detail` | `2` |
| `KFile::SeparateDirs` | `4` |
| `KFile::PreviewContents` | `8` |
| `KFile::PreviewInfo` | `16` |
| `KFile::Tree` | `32` |
| `KFile::DetailTree` | `64` |

### enum KFile::Mode {#Mode-enum}

**flags KFile::Modes**

Modes of operation for the dialog.

| Constant | Value | Description |
| --- | --- | --- |
| `KFile::File` | `1` | Get a single file name from the user. |
| `KFile::Directory` | `2` | Get a directory name from the user. |
| `KFile::Files` | `4` | Get multiple file names from the user. |
| `KFile::ExistingOnly` | `8` | Never return a filename which does not exist yet |
| `KFile::LocalOnly` | `16` | Don't return remote filenames |

The `Modes` type is a typedef for `QFlags<Mode>. `It stores an OR combination of `Mode` values.

### enum KFile::SelectionMode {#SelectionMode-enum}

| Constant |   |
| --- | --- |
| `KFile::Single` | `1` |
| `KFile::Multi` | `2` |
| `KFile::Extended` | `4` |
| `KFile::NoSelection` | `8` |

## Member Function Documentation {#member-function-documentation}

### \[static\] bool KFile::isDefaultView(const KFile::FileView &*view*) {#isDefaultView}

### \[static\] bool KFile::isDetailTreeView(const KFile::FileView &*view*) {#isDetailTreeView}

### \[static\] bool KFile::isDetailView(const KFile::FileView &*view*) {#isDetailView}

### \[static\] bool KFile::isPreviewContents(const KFile::FileView &*view*) {#isPreviewContents}

### \[static\] bool KFile::isPreviewInfo(const KFile::FileView &*view*) {#isPreviewInfo}

### \[static\] bool KFile::isSeparateDirs(const KFile::FileView &*view*) {#isSeparateDirs}

### \[static\] bool KFile::isSimpleView(const KFile::FileView &*view*) {#isSimpleView}

### \[static\] bool KFile::isSortByDate(const QDir::SortFlags &*sort*) {#isSortByDate}

### \[static\] bool KFile::isSortByName(const QDir::SortFlags &*sort*) {#isSortByName}

### \[static\] bool KFile::isSortBySize(const QDir::SortFlags &*sort*) {#isSortBySize}

### \[static\] bool KFile::isSortByType(const QDir::SortFlags &*sort*) {#isSortByType}

### \[static\] bool KFile::isSortCaseInsensitive(const QDir::SortFlags &*sort*) {#isSortCaseInsensitive}

### \[static\] bool KFile::isSortDirsFirst(const QDir::SortFlags &*sort*) {#isSortDirsFirst}

### \[static\] bool KFile::isTreeView(const KFile::FileView &*view*) {#isTreeView}
