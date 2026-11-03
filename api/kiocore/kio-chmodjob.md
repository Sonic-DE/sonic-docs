---
title: "KIO::ChmodJob Class"
description: "This job changes permissions on a list of files or directories, optionally in a recursive manner."
---

# KIO::ChmodJob Class

This job changes permissions on a list of files or directories, optionally in a recursive manner. [More...](#details)

- **Header:** `#include <KIO/ChmodJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [KIO::Job](kio-job.md)

[List of all members, including inherited members](kio-chmodjob-members.md)

## Detailed Description {#details}

*See also* [KIO::chmod()](kio-index.md)

## Related Non-Members {#related-non-members}

### KIO::ChmodJob \*chmod(const KFileItemList &*lstItems*, int *permissions*, int *mask*, const QString &*newOwner*, const QString &*newGroup*, bool *recursive*, KIO::JobFlags *flags* = DefaultFlags) {#chmod}

Creates a job that changes permissions/ownership on several files or directories, optionally recursively. This version of chmod uses a [KFileItemList](kfileitemlist.md) so that it directly knows what to do with the items. TODO: a version that takes a [QList](https://doc.qt.io/qt-6/qlist.html)\<[QUrl](https://doc.qt.io/qt-6/qurl.html)\>, and a general job that stats each url and returns a [KFileItemList](kfileitemlist.md).

Note that change of ownership is only supported for local files.

Inside directories, the "x" bits will only be changed for files that had at least one "x" bit before, and for directories. This emulates the behavior of chmod +X.

`lstItems` The file items representing several files or directories.

`permissions` the permissions we want to set

`mask` the bits we are allowed to change. For instance, if mask is 0077, we don't change the "user" bits, only "group" and "others".

`newOwner` If non-empty, the new owner for the files

`newGroup` If non-empty, the new group for the files

`recursive` whether to open directories recursively

`flags` We support [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.
