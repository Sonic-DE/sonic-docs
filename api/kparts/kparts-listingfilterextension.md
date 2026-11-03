---
title: "KParts::ListingFilterExtension Class"
description: "An extension for filtering listings."
---

# KParts::ListingFilterExtension Class

An extension for filtering listings. [More...](#details)

- **Header:** `#include <KParts/ListingFilterExtension>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Parts)`  
  `target_link_libraries(mytarget PRIVATE KF6::Parts)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kparts-listingfilterextension-members.md)

## Public Types

- [enum ListingFilterExtension::FilterMode](#FilterMode-enum)

## Public Functions

- [ListingFilterExtension(KParts::ReadOnlyPart \*parent)](#ListingFilterExtension)
- [QVariant filter(KParts::ListingFilterExtension::FilterMode mode) const](#filter)
- [void setFilter(KParts::ListingFilterExtension::FilterMode mode, const QVariant &filter)](#setFilter)
- [KParts::ListingFilterExtension::FilterModes supportedFilterModes() const](#supportedFilterModes)
- [bool supportsMultipleFilters(KParts::ListingFilterExtension::FilterMode mode) const](#supportsMultipleFilters)

## Static Public Members

- [KParts::ListingFilterExtension \*childObject(QObject \*obj)](#childObject)

## Detailed Description {#details}

This extension is intended to be implemented by parts that provide listing services, e.g. file management parts and is intended to provide a generic API for filtering any listing through keywords, wildcard characters and/or content-type.

Examples:

To show items that only match the term "kde"

```cpp
KParts::ListingFilterExtension* ext = KParts::ListingFilterExtension::childObject(part);
if (ext && (ext->supportedFilterModes() & KParts::ListingFilterExtension::SubString)) {
   ext->setFilter(KParts::ListingFilterExtension::SubString, QLatin1String("kde"));
}
```

To show items that only match "text/html"

```cpp
KParts::ListingFilterExtension* ext = KParts::ListingFilterExtension::childObject(part);
if (ext && (ext->supportedFilterModes() & KParts::ListingFilterExtension::MimeType)) {
    ext->setFilter(KParts::ListingFilterExtension::MimeType, QLatin1String("text/html"));
}
```

To show items that only match the wildcard string "\*.txt"

```cpp
KParts::ListingFilterExtension* ext = KParts::ListingFilterExtension::childObject(part);
if (ext && (ext->supportedFilterModes() & KParts::ListingFilterExtension::WildCard)) {
    ext->setFilter(KParts::ListingFilterExtension::WildCard, QLatin1String("*.txt"));
}
```

To show items that match multiple mime types, e.g. text/html & application/xml:

```cpp
KParts::ListingFilterExtension* ext = KParts::ListingFilterExtension::childObject(part);
if (ext &&
    (ext->supportedFilterModes() & KParts::ListingFilterExtension::MimeType) &&
    ext->supportsMultipleFilters(KParts::ListingFilterExtension::MimeType)) {
    QStringList mimeTypes = ext->filter(KParts::ListingFilterExtension::MimeType).toStringList();
    mimeTypes << QLatin1String("text/html") << QLatin1String("application/xml");
    ext->setFilter(KParts::ListingFilterExtension::MimeType, mimeTypes);
}
```

## Member Type Documentation {#member-type-documentation}

### enum ListingFilterExtension::FilterMode {#FilterMode-enum}

**flags ListingFilterExtension::FilterModes**

Supported file filtering modes modes.

| Constant | Value |   |
| --- | --- | --- |
| `KParts::ListingFilterExtension::None` | `0x00` |   |
| `KParts::ListingFilterExtension::MimeType` | `0x01` | Filter by mime type, e.g. "text/plain" |
| `KParts::ListingFilterExtension::SubString` | `0x02` | Filter by matching any part of a file or directory name, e.g. "Documents" |
| `KParts::ListingFilterExtension::WildCard` | `0x04` | Filter by using wildcard matches, e.g. "\*.txt" |

The `FilterModes` type is a typedef for `QFlags<FilterMode>. `It stores an OR combination of `FilterMode` values.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ListingFilterExtension::ListingFilterExtension(KParts::ReadOnlyPart \**parent*) {#ListingFilterExtension}

Constructor

### \[static\] KParts::ListingFilterExtension \*ListingFilterExtension::childObject(QObject \**obj*) {#childObject}

Queries `obj` for a child object which inherits from this class.

### \[pure virtual\] QVariant ListingFilterExtension::filter(KParts::ListingFilterExtension::FilterMode *mode*) const {#filter}

Returns the currently set filters for the given `mode`.

`mode` the desired filter mode as specified in [FilterMode](kparts-listingfilterextension.md#FilterMode-enum).

*See also* [setFilter](kparts-listingfilterextension.md#setFilter)()

### \[pure virtual\] void ListingFilterExtension::setFilter(KParts::ListingFilterExtension::FilterMode *mode*, const QVariant &*filter*) {#setFilter}

Sets the file `filter` that should be applied by the part that implements this extension for the given filtering `mode`.

To remove a filter for a given filter mode, simply call this function with the desired mode and the `filter` parameter set to a NULL variant.

The second parameter can be

`mode` the desired filter mode as specified in [FilterMode](kparts-listingfilterextension.md#FilterMode-enum).

`filter` a list of filter texts based on the selected mode.

*See also* [filter](kparts-listingfilterextension.md#filter)()

### \[virtual\] KParts::ListingFilterExtension::FilterModes ListingFilterExtension::supportedFilterModes() const {#supportedFilterModes}

Returns the OR'ed value of the file filter modes supported by the part that implements this extension.

By default this function returns None.

### \[virtual\] bool ListingFilterExtension::supportsMultipleFilters(KParts::ListingFilterExtension::FilterMode *mode*) const {#supportsMultipleFilters}

Returns true if the part that implements this extension allows the use of multiple filters for the given filtering `mode`.

By default this function returns `false`.
