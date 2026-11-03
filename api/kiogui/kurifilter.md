---
title: "KUriFilter Class"
description: "Filters the given input into a valid url whenever possible."
---

# KUriFilter Class

Filters the given input into a valid url whenever possible. [More...](#details)

- **Header:** `#include <KUriFilter>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KIOGui)`

[List of all members, including inherited members](kurifilter-members.md)

## Public Types

- [enum KUriFilter::SearchFilterType](#SearchFilterType-enum)

## Public Functions

- [bool filterSearchUri(KUriFilterData &data, KUriFilter::SearchFilterTypes types)](#filterSearchUri)
- [bool filterUri(KUriFilterData &data, const QStringList &filters = QStringList())](#filterUri)
- [bool filterUri(QString &uri, const QStringList &filters = QStringList())](#filterUri-1)
- [bool filterUri(QUrl &uri, const QStringList &filters = QStringList())](#filterUri-2)
- [QString filteredUri(const QString &uri, const QStringList &filters = QStringList())](#filteredUri)
- [QUrl filteredUri(const QUrl &uri, const QStringList &filters = QStringList())](#filteredUri-1)
- [QStringList pluginNames() const](#pluginNames)

## Static Public Members

- [KUriFilter \*self()](#self)

## Protected Functions

- [KUriFilter()](#KUriFilter)

## Detailed Description {#details}

[KUriFilter](kurifilter.md) applies a number of filters to a URI and returns a filtered version if any filter matches. A simple example is "kde.org" to "http://www.kde.org", which is commonplace in web browsers.

The filters are implemented as plugins in KUriFilterPlugin subclasses.

[KUriFilter](kurifilter.md) is a singleton object: obtain the instance by calling [KUriFilter::self](kurifilter.md#self)() and use the public member functions to perform the filtering.

Example:

To simply filter a given string:

```cpp
QString url("kde.org");
bool filtered = KUriFilter::self()->filteredUri( url );
```

You can alternatively use a [QUrl](https://doc.qt.io/qt-6/qurl.html):

```cpp
QUrl url("kde.org");
bool filtered = KUriFilter::self()->filterUri( url );
```

If you have a constant string or a constant URL, simply invoke the corresponding function to obtain the filtered string or URL instead of a boolean flag:

```cpp
QString filteredText = KUriFilter::self()->filteredUri( "kde.org" );
```

All of the above examples should result in "kde.org" being filtered into "http://kde.org".

You can also restrict the filters to be used by supplying the name of the filters you want to use. By default all available filters are used.

To use specific filters, add the names of the filters you want to use to a [QStringList](https://doc.qt.io/qt-6/qstringlist.html) and invoke the appropriate filtering function.

The examples below show the use of specific filters. KDE ships with the following filter plugins by default:

kshorturifilter: This is used for filtering potentially valid url inputs such as "kde.org" Additionally it filters shell variables and shortcuts such as $HOME and ~ as well as man and info page shortcuts, \# and \#\# respectively.

kuriikwsfilter: This is used for filtering normal input text into a web search url using the configured fallback search engine selected by the user.

kurisearchfilter: This is used for filtering KDE webshortcuts. For example "gg:KDE" will be converted to a url for searching the work "KDE" using the Google search engine.

localdomainfilter: This is used for doing a DNS lookup to determine whether the input is a valid local address.

fixuphosturifilter: This is used to append "www." to the host name of a pre filtered http url if the original url cannot be resolved.

```cpp
QString text ("kde.org");
bool filtered = KUriFilter::self()->filterUri(text, QLatin1String("kshorturifilter"));
```

The above code should result in "kde.org" being filtered into "http://kde.org".

```cpp
QStringList list;
list << QLatin1String("kshorturifilter") << QLatin1String("localdomainfilter");
bool filtered = KUriFilter::self()->filterUri( text, list );
```

Additionally if you only want to do search related filtering, you can use the search specific function, [filterSearchUri](kurifilter.md#filterSearchUri), that is available in KDE 4.5 and higher. For example, to search for a given input on the web you can do the following:

[KUriFilterData](kurifilterdata.md) filterData ("foo"); bool filtered = [KUriFilter::self](kurifilter.md#self)()-\>[filterSearchUri](kurifilter.md#filterSearchUri)(filterData, KUriFilterData::NormalTextFilter);

[KUriFilter](kurifilter.md) converts all filtering requests to use [KUriFilterData](kurifilterdata.md) internally. The use of this bi-directional class allows you to send specific instructions to the filter plugins as well as receive detailed information about the filtered request from them. See the documentation of [KUriFilterData](kurifilterdata.md) class for more examples and details.

All functions in this class are thread safe and reentrant.

## Member Type Documentation {#member-type-documentation}

### enum KUriFilter::SearchFilterType {#SearchFilterType-enum}

**flags KUriFilter::SearchFilterTypes**

This enum describes the types of search plugin filters available.

| Constant | Value | Description |
| --- | --- | --- |
| `KUriFilter::NormalTextFilter` | `0x01` | The plugin used to filter normal text, e.g. "some term to search". |
| `KUriFilter::WebShortcutFilter` | `0x02` | The plugin used to filter web shortcuts, e.g. gg:KDE. |

The `SearchFilterTypes` type is a typedef for `QFlags<SearchFilterType>. `It stores an OR combination of `SearchFilterType` values.

## Member Function Documentation {#member-function-documentation}

### \[protected\] KUriFilter::KUriFilter() {#KUriFilter}

Constructor.

Creates a [KUriFilter](kurifilter.md) object and calls loads all available URI filter plugins.

### bool KUriFilter::filterSearchUri(KUriFilterData &*data*, KUriFilter::SearchFilterTypes *types*) {#filterSearchUri}

Filter `data` using the criteria specified by `types`.

The search filter type can be individual value of [SearchFilterTypes](kurifilter.md#SearchFilterType-enum) or a combination of those types using the bitwise OR operator.

You can also use the flags from [KUriFilterData::SearchFilterOption](kurifilterdata.md#SearchFilterOption-enum) to alter the filtering mechanisms of the search filter providers.

`data` object that contains the URI to be filtered.

`types` the search filters used to filter the request.

Returns `true` if the specified `data` was successfully filtered.

*See also* [KUriFilterData::setSearchFilteringOptions](kurifilterdata.md#setSearchFilteringOptions)

### bool KUriFilter::filterUri(KUriFilterData &*data*, const QStringList &*filters* = QStringList()) {#filterUri}

Filters `data` using the specified `filters`.

If no named filters are specified, the default, then all the URI filter plugins found will be used.

`data` object that contains the URI to be filtered.

`filters` specify the list of filters to be used.

Returns a boolean indicating whether the URI has been changed

### bool KUriFilter::filterUri(QString &*uri*, const QStringList &*filters* = QStringList()) {#filterUri-1}

Filters a string representing a URI.

The given URL is filtered based on the specified list of filters. If the list is empty all available filters would be used.

`uri` The URI to filter.

`filters` specify the list of filters to be used.

Returns a boolean indicating whether the URI has been changed

### bool KUriFilter::filterUri(QUrl &*uri*, const QStringList &*filters* = QStringList()) {#filterUri-2}

Filters the URI given by the URL.

The given URL is filtered based on the specified list of filters. If the list is empty all available filters would be used.

`uri` the URI to filter.

`filters` specify the list of filters to be used.

Returns a boolean indicating whether the URI has been changed

### QString KUriFilter::filteredUri(const QString &*uri*, const QStringList &*filters* = QStringList()) {#filteredUri}

Return a filtered string representation of a URI.

The given URL is filtered based on the specified list of filters. If the list is empty all available filters would be used.

`uri` the URI to filter.

`filters` specify the list of filters to be used.

Returns the filtered URI or null if it cannot be filtered

### QUrl KUriFilter::filteredUri(const QUrl &*uri*, const QStringList &*filters* = QStringList()) {#filteredUri-1}

Returns the filtered URI.

The given URL is filtered based on the specified list of filters. If the list is empty all available filters would be used.

`uri` The URI to filter.

`filters` specify the list of filters to be used.

Returns the filtered URI or null if it cannot be filtered

### QStringList KUriFilter::pluginNames() const {#pluginNames}

Return a list of the names of all loaded plugins.

### \[static\] KUriFilter \*KUriFilter::self() {#self}

Returns an instance of [KUriFilter](kurifilter.md).
