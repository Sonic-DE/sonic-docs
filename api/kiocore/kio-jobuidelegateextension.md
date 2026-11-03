---
title: "KIO::JobUiDelegateExtension Class"
description: "Network transparent access to files and data."
---

# KIO::JobUiDelegateExtension Class

Network transparent access to files and data. [More...](#details)

- **Header:** `#include <KIO/JobUiDelegateExtension>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`

[List of all members, including inherited members](kio-jobuidelegateextension-members.md)

## Public Types

- [enum JobUiDelegateExtension::ClipboardUpdaterMode](#ClipboardUpdaterMode-enum)
- [enum JobUiDelegateExtension::ConfirmationType](#ConfirmationType-enum)
- [enum JobUiDelegateExtension::DeletionType](#DeletionType-enum)

## Public Functions

- [bool askDeleteConfirmation(const QList\<QUrl\> &urls, KIO::JobUiDelegateExtension::DeletionType deletionType, KIO::JobUiDelegateExtension::ConfirmationType confirmationType)](#askDeleteConfirmation)
- [KIO::ClipboardUpdater \*createClipboardUpdater(KIO::Job \*job, KIO::JobUiDelegateExtension::ClipboardUpdaterMode mode)](#createClipboardUpdater)
- [void updateUrlInClipboard(const QUrl &src, const QUrl &dest)](#updateUrlInClipboard)

## Protected Functions

- [JobUiDelegateExtension()](#JobUiDelegateExtension)

## Detailed Description {#details}

An abstract class defining interaction with users from KIO jobs:

- asking for confirmation before deleting files or directories

## Member Type Documentation {#member-type-documentation}

### enum JobUiDelegateExtension::ClipboardUpdaterMode {#ClipboardUpdaterMode-enum}

| Constant |   |
| --- | --- |
| `KIO::JobUiDelegateExtension::UpdateContent` | `0` |
| `KIO::JobUiDelegateExtension::OverwriteContent` | `1` |
| `KIO::JobUiDelegateExtension::RemoveContent` | `2` |

### enum JobUiDelegateExtension::ConfirmationType {#ConfirmationType-enum}

ForceConfirmation: always ask the user for confirmation DefaultConfirmation: don't ask the user if he/she said "don't ask again".

Used by [askDeleteConfirmation](kio-jobuidelegateextension.md#askDeleteConfirmation).

| Constant |   |
| --- | --- |
| `KIO::JobUiDelegateExtension::DefaultConfirmation` | `0` |
| `KIO::JobUiDelegateExtension::ForceConfirmation` | `1` |

### enum JobUiDelegateExtension::DeletionType {#DeletionType-enum}

The type of deletion: real deletion, moving the files to the trash or emptying the trash Used by [askDeleteConfirmation](kio-jobuidelegateextension.md#askDeleteConfirmation).

| Constant |   |
| --- | --- |
| `KIO::JobUiDelegateExtension::Delete` | `0` |
| `KIO::JobUiDelegateExtension::Trash` | `1` |
| `KIO::JobUiDelegateExtension::EmptyTrash` | `2` |

## Member Function Documentation {#member-function-documentation}

### \[protected\] JobUiDelegateExtension::JobUiDelegateExtension() {#JobUiDelegateExtension}

Constructor

### \[pure virtual\] bool JobUiDelegateExtension::askDeleteConfirmation(const QList\<QUrl\> &*urls*, KIO::JobUiDelegateExtension::DeletionType *deletionType*, KIO::JobUiDelegateExtension::ConfirmationType *confirmationType*) {#askDeleteConfirmation}

Ask for confirmation before deleting/trashing `urls`.

Note that this method is not called automatically by KIO jobs. It's the application's responsibility to ask the user for confirmation before calling [KIO::del](kio-deletejob.md#del)() or [KIO::trash](kio-copyjob.md#trash)().

`urls` the urls about to be deleted/trashed

`deletionType` the type of deletion (Delete for real deletion, Trash otherwise)

`confirmationType` see [ConfirmationType](kio-jobuidelegateextension.md#ConfirmationType-enum). Normally set to [DefaultConfirmation](kio-jobuidelegateextension.md#ConfirmationType-enum).

> **Note:** the window passed to setWindow is used as the parent for the message box.

Returns `true` if confirmed

### \[virtual\] KIO::ClipboardUpdater \*JobUiDelegateExtension::createClipboardUpdater(KIO::Job \**job*, KIO::JobUiDelegateExtension::ClipboardUpdaterMode *mode*) {#createClipboardUpdater}

Creates a clipboard updater as a child of the given job.

### \[virtual\] void JobUiDelegateExtension::updateUrlInClipboard(const QUrl &*src*, const QUrl &*dest*) {#updateUrlInClipboard}

Update URL in clipboard, if present

## Related Non-Members {#related-non-members}

### KIO::JobUiDelegateExtension \*defaultJobUiDelegateExtension() {#defaultJobUiDelegateExtension}

Returns the default job UI delegate extension to be used by all KIO jobs (in which [HideProgressInfo](kio.md#JobFlag-enum) is not set) Can return nullptr, if no kio GUI library is loaded.

*See also* [setDefaultJobUiDelegateExtension](kio-jobuidelegateextension.md#setDefaultJobUiDelegateExtension)()

### void setDefaultJobUiDelegateExtension(KIO::JobUiDelegateExtension \**extension*) {#setDefaultJobUiDelegateExtension}

Internal. Allows the KIO widgets library to register its widget-based job UI delegate extension automatically.

*See also* [defaultJobUiDelegateExtension](kio-jobuidelegateextension.md#defaultJobUiDelegateExtension)()
