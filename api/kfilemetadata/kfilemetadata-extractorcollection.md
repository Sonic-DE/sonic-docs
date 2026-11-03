---
title: "KFileMetaData::ExtractorCollection Class"
description: "The ExtractorCollection is a helper class which internally loads all the extractor plugins."
---

# KFileMetaData::ExtractorCollection Class

The [ExtractorCollection](kfilemetadata-extractorcollection.md) is a helper class which internally loads all the extractor plugins. [More...](#details)

- **Header:** `#include <KFileMetaData/ExtractorCollection>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS FileMetaData)`  
  `target_link_libraries(mytarget PRIVATE KF6::FileMetaData)`

[List of all members, including inherited members](kfilemetadata-extractorcollection-members.md)

## Public Functions

- [ExtractorCollection()](#ExtractorCollection)
- [QList\<KFileMetaData::Extractor \*\> fetchExtractors(const QString &mimetype) const](#fetchExtractors)

## Detailed Description {#details}

It can be used to fetch a certain subset of these plugins based on a given mimetype.

Once the appropriate plugins have been fetched, an [ExtractionResult](kfilemetadata-extractionresult.md) should be created and passed to the plugin's extract function.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ExtractorCollection::ExtractorCollection() {#ExtractorCollection}

### QList\<KFileMetaData::Extractor \*\> ExtractorCollection::fetchExtractors(const QString &*mimetype*) const {#fetchExtractors}

Fetch the extractors which can be used to extract data for the respective file with the given MIME type.

If no match is found then the best matching plugins are returned, determined by MIME type inheritance.

*See also* [QMimeType::allAncestors](https://doc.qt.io/qt-6/qmimetype.html#allAncestors-prop)
