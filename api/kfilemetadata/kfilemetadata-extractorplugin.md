---
title: "KFileMetaData::ExtractorPlugin Class"
description: "The ExtractorPlugin is the base class for all file metadata extractors."
---

# KFileMetaData::ExtractorPlugin Class

The [ExtractorPlugin](kfilemetadata-extractorplugin.md) is the base class for all file metadata extractors. [More...](#details)

- **Header:** `#include <KFileMetaData/ExtractorPlugin>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS FileMetaData)`  
  `target_link_libraries(mytarget PRIVATE KF6::FileMetaData)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kfilemetadata-extractorplugin-members.md)  
[Deprecated members](kfilemetadata-extractorplugin-obsolete.md)

## Public Functions

- [ExtractorPlugin(QObject \*parent)](#ExtractorPlugin)
- [void extract(KFileMetaData::ExtractionResult \*result)](#extract)
- [QStringList mimetypes() const](#mimetypes)

## Protected Functions

- [QString getSupportedMimeType(const QString &mimetype) const](#getSupportedMimeType)

## Detailed Description {#details}

It is responsible for extracting the metadata in a file.

Plugins should derive from this class and implement the [mimetypes](kfilemetadata-extractorplugin.md#mimetypes)() and [extract](kfilemetadata-extractorplugin.md#extract)() method.

The plugin must also specify the implemented interface and provide sufficient metadata:

```cpp
class FooExtractor : public ExtractorPlugin
{
    Q_OBJECT
    Q_PLUGIN_METADATA(IID kfilemetadata_extractor_iid
                      FILE "fooextractor.json")
    Q_INTERFACES(KFileMetaData::ExtractorPlugin)
...
};
```

```cpp
{
    "Name" : "FooExtractor",
    "Id" :   "org.kde.fooextractor",
    "MimeTypes" : { "application/x-foo" : { "Version" : "0.0" } }
}
```

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ExtractorPlugin::ExtractorPlugin(QObject \**parent*) {#ExtractorPlugin}

### \[pure virtual\] void ExtractorPlugin::extract(KFileMetaData::ExtractionResult \**result*) {#extract}

The main function of the plugin that is responsible for extracting the data and filling up the [ExtractionResult](kfilemetadata-extractionresult.md)

The `result` provides the input URL and MIME type which can be used to identify the file.

This function is synchronous and must be reentrant as it can be called by multiple threads.

### \[protected\] QString ExtractorPlugin::getSupportedMimeType(const QString &*mimetype*) const {#getSupportedMimeType}

Return the inherited MIME type which the extractor directly supports.

The returned type is one of the types from [mimetypes](kfilemetadata-extractorplugin.md#mimetypes)(), and is one of the ancestors of the input `mimetype` (including `mimetype` itself).

In case the MIME type is not a subtype of the supported types, an empty QString() is returned.

*See also* [ExtractorCollection::fetchExtractors](kfilemetadata-extractorcollection.md#fetchExtractors), [QMimeType::allAncestors](https://doc.qt.io/qt-6/qmimetype.html#allAncestors-prop)

### \[pure virtual\] QStringList ExtractorPlugin::mimetypes() const {#mimetypes}

Provide a list of MIME types which are supported by this plugin. Only files with those MIME types will be provided to the plugin via the extract function.

This can also contains partial MIME types like "text/", in that case this plugin will be chosen only if a better plugin does not exist.

Returns a [QStringList](https://doc.qt.io/qt-6/qstringlist.html) containing the MIME types.

*See also* [extract](kfilemetadata-extractorplugin.md#extract)
