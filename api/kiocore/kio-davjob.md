---
title: "KIO::DavJob Class"
description: "Network transparent access to files and data."
---

# KIO::DavJob Class

Network transparent access to files and data. [More...](#details)

- **Header:** `#include <KIO/DavJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [KIO::TransferJob](kio-transferjob.md)

[List of all members, including inherited members](kio-davjob-members.md)

## Public Functions

- [QByteArray responseData() const](#responseData)

## Detailed Description {#details}

The transfer job pumps data into and/or out of a KIO worker. Data is sent to the worker on request of the worker ( dataReq). If data coming from the worker can not be handled, the reading of data from the worker should be suspended.

*See also* [KIO::davPropFind()](kio-index.md), [KIO::davPropPatch()](kio-index.md), [KIO::davSearch()](kio-index.md)

## Member Function Documentation {#member-function-documentation}

### QByteArray DavJob::responseData() const {#responseData}

Returns the response data.

## Related Non-Members {#related-non-members}

### \[since 6.27.0\] KIO::DavJob \*davMkCol(const QUrl &*url*, const QString &*properties*, KIO::JobFlags *flags* = DefaultFlags) {#davMkCol}

Creates a new [DavJob](kio-davjob.md) that issues a MKCOL command.

`url` the URL of the resource

`properties` a MKCOL document that describes the request to make

`flags` We support [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the new [DavJob](kio-davjob.md)

This function was introduced in Qt 6.27.0.

### KIO::DavJob \*davPropFind(const QUrl &*url*, const QString &*properties*, const QString &*depth*, KIO::JobFlags *flags* = DefaultFlags) {#davPropFind}

Creates a new [DavJob](kio-davjob.md) that issues a PROPFIND command. PROPFIND retrieves the properties of the resource identified by the given `url`.

`url` the URL of the resource

`properties` a propfind document that describes the properties that should be retrieved

`depth` the depth of the request. Can be "0", "1" or "infinity"

`flags` We support [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the new [DavJob](kio-davjob.md)

### KIO::DavJob \*davPropPatch(const QUrl &*url*, const QString &*properties*, KIO::JobFlags *flags* = DefaultFlags) {#davPropPatch}

Creates a new [DavJob](kio-davjob.md) that issues a PROPPATCH command. PROPPATCH sets the properties of the resource identified by the given `url`.

`url` the URL of the resource

`properties` a PROPPACTCH document that describes the properties that should be modified and its new values

`flags` We support [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the new [DavJob](kio-davjob.md)

### KIO::DavJob \*davReport(const QUrl &*url*, const QString &*report*, const QString &*depth*, KIO::JobFlags *flags* = DefaultFlags) {#davReport}

Creates a new [DavJob](kio-davjob.md) that issues a REPORT command.

`url` the URL of the resource

`report` a REPORT document that describes the request to make

`depth` the depth of the request. Can be "0", "1" or "infinity"

`flags` We support [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the new [DavJob](kio-davjob.md)

### KIO::DavJob \*davSearch(const QUrl &*url*, const QString &*nsURI*, const QString &*qName*, const QString &*query*, KIO::JobFlags *flags* = DefaultFlags) {#davSearch}

Creates a new [DavJob](kio-davjob.md) that issues a SEARCH command.

`url` the URL of the resource

`nsURI` the URI of the search method's qualified name

`qName` the local part of the search method's qualified name

`query` the search string

`flags` We support [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the new [DavJob](kio-davjob.md)
