---
title: "KIO::RestoreJob Class"
description: "RestoreJob is used to restore files from the trash."
---

# KIO::RestoreJob Class

[RestoreJob](kio-restorejob.md) is used to restore files from the trash. [More...](#details)

- **Header:** `#include <KIO/RestoreJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [KIO::Job](kio-job.md)

[List of all members, including inherited members](kio-restorejob-members.md)

## Public Functions

- [QList\<QUrl\> trashUrls() const](#trashUrls)

## Detailed Description {#details}

Don't create the job directly, but use [KIO::restoreFromTrash](kio-restorejob.md#restoreFromTrash)().

*See also* [KIO::trash()](kio-index.md), [KIO::copy()](kio-index.md)

## Member Function Documentation {#member-function-documentation}

### QList\<QUrl\> RestoreJob::trashUrls() const {#trashUrls}

Returns the list of trash URLs to restore.

## Related Non-Members {#related-non-members}

### KIO::RestoreJob \*restoreFromTrash(const QList\<QUrl\> &*urls*, KIO::JobFlags *flags* = DefaultFlags) {#restoreFromTrash}

Restore a set of trashed files or directories.

`urls` the trash:/ URLs to restore. The trash implementation will know where the files came from and will restore them to their original location.

`flags` restoreFromTrash() supports [HideProgressInfo](kio.md#JobFlag-enum).

Returns the job handling the operation
