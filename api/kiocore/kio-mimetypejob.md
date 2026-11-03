---
title: "KIO::MimetypeJob Class"
description: "Network transparent access to files and data."
---

# KIO::MimetypeJob Class

Network transparent access to files and data. [More...](#details)

- **Header:** `#include <KIO/MimetypeJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [KIO::TransferJob](kio-transferjob.md)

[List of all members, including inherited members](kio-mimetypejob-members.md)

## Detailed Description {#details}

A [MimetypeJob](kio-mimetypejob.md) is a [TransferJob](kio-transferjob.md) that allows you to get the MIME type of a URL. Don't create directly, but use [KIO::mimetype](kio-mimetypejob.md#mimetype)() instead.

*See also* [KIO::mimetype()](kio-index.md)

## Related Non-Members {#related-non-members}

### KIO::MimetypeJob \*mimetype(const QUrl &*url*, KIO::JobFlags *flags* = DefaultFlags) {#mimetype}

Find MIME type for one file or directory.

If you are going to download the file right after determining its MIME type, then don't use this, prefer using a [KIO::get](kio-transferjob.md#get)() job instead. See the note about putting the job on hold once the MIME type is determined.

`url` the URL of the file

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.
