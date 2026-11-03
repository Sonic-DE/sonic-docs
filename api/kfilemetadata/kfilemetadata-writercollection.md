---
title: "KFileMetaData::WriterCollection Class"
description: "The WriterCollection is a helper class which internally loads all the writer plugins."
---

# KFileMetaData::WriterCollection Class

The [WriterCollection](kfilemetadata-writercollection.md) is a helper class which internally loads all the writer plugins. [More...](#details)

- **Header:** `#include <KFileMetaData/WriterCollection>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS FileMetaData)`  
  `target_link_libraries(mytarget PRIVATE KF6::FileMetaData)`

[List of all members, including inherited members](kfilemetadata-writercollection-members.md)

## Public Functions

- [WriterCollection()](#WriterCollection)
- [QList\<KFileMetaData::Writer \*\> fetchWriters(const QString &mimetype) const](#fetchWriters)

## Detailed Description {#details}

It can be used to fetch a certain subset of writer plugins based on a given MIME type.

Once the appropriate plugins have been fetched, a [WriteData](kfilemetadata-writedata.md) should be created and passed to the plugin's write function.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] WriterCollection::WriterCollection() {#WriterCollection}

### QList\<KFileMetaData::Writer \*\> WriterCollection::fetchWriters(const QString &*mimetype*) const {#fetchWriters}
