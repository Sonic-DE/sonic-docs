---
title: "KUriFilterData Class"
description: "A class for exchanging filtering information."
---

# KUriFilterData Class

A class for exchanging filtering information. [More...](#details)

- **Header:** `#include <KUriFilter>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KIOGui)`

[List of all members, including inherited members](kurifilterdata-members.md)

## Public Types

- [enum KUriFilterData::SearchFilterOption](#SearchFilterOption-enum)
- [enum KUriFilterData::UriTypes](#UriTypes-enum)

## Public Functions

- [KUriFilterData()](#KUriFilterData)
- [KUriFilterData(const QString &url)](#KUriFilterData-2)
- [KUriFilterData(const QUrl &url)](#KUriFilterData-3)
- [KUriFilterData(const KUriFilterData &other)](#KUriFilterData-1)
- [QString absolutePath() const](#absolutePath)
- [QStringList allQueriesForSearchProvider(const QString &provider) const](#allQueriesForSearchProvider)
- [QString alternateDefaultSearchProvider() const](#alternateDefaultSearchProvider)
- [QStringList alternateSearchProviders() const](#alternateSearchProviders)
- [QString argsAndOptions() const](#argsAndOptions)
- [bool checkForExecutables() const](#checkForExecutables)
- [QString defaultUrlScheme() const](#defaultUrlScheme)
- [QString errorMsg() const](#errorMsg)
- [bool hasAbsolutePath() const](#hasAbsolutePath)
- [bool hasArgsAndOptions() const](#hasArgsAndOptions)
- [QString iconName()](#iconName)
- [QString iconNameForPreferredSearchProvider(const QString &provider) const](#iconNameForPreferredSearchProvider)
- [QStringList preferredSearchProviders() const](#preferredSearchProviders)
- [QString queryForPreferredSearchProvider(const QString &provider) const](#queryForPreferredSearchProvider)
- [KUriFilterSearchProvider queryForSearchProvider(const QString &provider) const](#queryForSearchProvider)
- [KUriFilterData::SearchFilterOptions searchFilteringOptions() const](#searchFilteringOptions)
- [QString searchProvider() const](#searchProvider)
- [QString searchTerm() const](#searchTerm)
- [QChar searchTermSeparator() const](#searchTermSeparator)
- [bool setAbsolutePath(const QString &abs\_path)](#setAbsolutePath)
- [void setAlternateDefaultSearchProvider(const QString &provider)](#setAlternateDefaultSearchProvider)
- [void setAlternateSearchProviders(const QStringList &providers)](#setAlternateSearchProviders)
- [void setCheckForExecutables(bool check)](#setCheckForExecutables)
- [void setData(const QString &url)](#setData)
- [void setData(const QUrl &url)](#setData-1)
- [void setDefaultUrlScheme(const QString &)](#setDefaultUrlScheme)
- [void setSearchFilteringOptions(KUriFilterData::SearchFilterOptions options)](#setSearchFilteringOptions)
- [QString typedString() const](#typedString)
- [QUrl uri() const](#uri)
- [KUriFilterData::UriTypes uriType() const](#uriType)

## Detailed Description {#details}

This class is a basic messaging class used to exchange filtering information between the filter plugins and the application requesting the filtering service.

Use this object if you require a more detailed information about the URI you want to filter. Any application can create an instance of this class and send it to [KUriFilter](kurifilter.md) to have the plugins fill out all possible information about the URI.

On successful filtering you can use [uriType](kurifilterdata.md#uriType)() to determine what type of resource the request was filtered into. See KUriFilter::UriTypes for details. If an error is encountered, then KUriFilter::Error is returned. You can use [errorMsg](kurifilterdata.md#errorMsg) to obtain the error information.

The functions in this class are not reentrant.

Example:

Here is a basic example of how this class is used with [KUriFilter](kurifilter.md):

```cpp
KUriFilterData filterData (QLatin1String("kde.org"));
bool filtered = KUriFilter::self()->filterUri(filterData);
```

If you are only interested in getting the list of preferred search providers, then you can do the following:

```cpp
KUriFilterData data;
data.setData("<text-to-search-for>");
data.setSearchFilteringOptions(KUriFilterData::RetrievePreferredSearchProvidersOnly);
bool filtered = KUriFilter::self()->filterSearchUri(data, KUriFilter::NormalTextFilter);
```

## Member Type Documentation {#member-type-documentation}

### enum KUriFilterData::SearchFilterOption {#SearchFilterOption-enum}

**flags KUriFilterData::SearchFilterOptions**

This enum describes the search filtering options to be used.

| Constant | Value | Description |
| --- | --- | --- |
| `KUriFilterData::SearchFilterOptionNone` | `0x0` | No search filter options are set and normal filtering is performed on the input data. |
| `KUriFilterData::RetrieveSearchProvidersOnly` | `0x01` | If set, the list of all available search providers are returned without any input filtering. This flag only applies when used in conjunction with the [KUriFilter::NormalTextFilter](kurifilter.md#SearchFilterType-enum) flag. |
| `KUriFilterData::RetrievePreferredSearchProvidersOnly` | `0x02` | If set, the list of preferred search providers are returned without any input filtering. This flag only applies when used in conjunction with the [KUriFilter::NormalTextFilter](kurifilter.md#SearchFilterType-enum) flag. |
| `KUriFilterData::RetrieveAvailableSearchProvidersOnly` | `(RetrievePreferredSearchProvidersOnly | RetrieveSearchProvidersOnly)` | Same as doing RetrievePreferredSearchProvidersOnly \| RetrieveSearchProvidersOnly, where all available search providers are returned if no preferred ones are available. No input filtering will be performed. |

The `SearchFilterOptions` type is a typedef for `QFlags<SearchFilterOption>. `It stores an OR combination of `SearchFilterOption` values.

*See also* [setSearchFilteringOptions](kurifilterdata.md#setSearchFilteringOptions), [KUriFilter::filterSearchUri](kurifilter.md#filterSearchUri)

### enum KUriFilterData::UriTypes {#UriTypes-enum}

Describes the type of the URI that was filtered.

| Constant | Value | Description |
| --- | --- | --- |
| `KUriFilterData::NetProtocol` | `0` | Any network protocol: http, ftp, nttp, pop3, etc... |
| `KUriFilterData::LocalFile` | `1` | A local file whose executable flag is not set |
| `KUriFilterData::LocalDir` | `2` | A local directory |
| `KUriFilterData::Executable` | `3` | A local file whose executable flag is set |
| `KUriFilterData::Help` | `4` | A man or info page |
| `KUriFilterData::Shell` | `5` | A shell executable (ex: echo "Test..." \>\> ~/testfile) |
| `KUriFilterData::Blocked` | `6` | A URI that should be blocked/filtered (ex: ad filtering) |
| `KUriFilterData::Error` | `7` | An incorrect URI (ex: "~johndoe" when user johndoe does not exist in that system) |
| `KUriFilterData::Unknown` | `8` | A URI that is not identified. Default value when a [KUriFilterData](kurifilterdata.md) is first created. |

## Member Function Documentation {#member-function-documentation}

### KUriFilterData::KUriFilterData() {#KUriFilterData}

Default constructor.

Creates a UriFilterData object.

### \[explicit\] KUriFilterData::KUriFilterData(const QString &*url*) {#KUriFilterData-2}

Creates a [KUriFilterData](kurifilterdata.md) object from the given string.

`url` is the string to be filtered.

### \[explicit\] KUriFilterData::KUriFilterData(const QUrl &*url*) {#KUriFilterData-3}

Creates a [KUriFilterData](kurifilterdata.md) object from the given URL.

`url` is the URL to be filtered.

### KUriFilterData::KUriFilterData(const KUriFilterData &*other*) {#KUriFilterData-1}

Copy constructor.

Creates a [KUriFilterData](kurifilterdata.md) object from another KURIFilterData object.

`other` the uri filter data to be copied.

### QString KUriFilterData::absolutePath() const {#absolutePath}

Returns the absolute path if one has already been set.

Returns the absolute path, or QString()

*See also* [setAbsolutePath](kurifilterdata.md#setAbsolutePath)(), [hasAbsolutePath](kurifilterdata.md#hasAbsolutePath)()

### QStringList KUriFilterData::allQueriesForSearchProvider(const QString &*provider*) const {#allQueriesForSearchProvider}

Returns all the query urls for the given search provider.

Use this function to obtain all the different queries that can be used for the given provider. For example, if a search engine provider named "foobar" has web shortcuts named "foobar", "foo" and "bar", then this function, unlike [queryForPreferredSearchProvider](kurifilterdata.md#queryForPreferredSearchProvider), will return a a query for each and every web shortcut.

*See also* [queryForPreferredSearchProvider](kurifilterdata.md#queryForPreferredSearchProvider)

### QString KUriFilterData::alternateDefaultSearchProvider() const {#alternateDefaultSearchProvider}

Returns the search provider to use when a default provider is not available.

This function returns an empty string if [setAlternateDefaultSearchProvider](kurifilterdata.md#setAlternateDefaultSearchProvider) was not called to set the default search provider to be used when none has been chosen by the user through the search configuration module.

*See also* [setAlternateDefaultSearchProvider](kurifilterdata.md#setAlternateDefaultSearchProvider)

### QStringList KUriFilterData::alternateSearchProviders() const {#alternateSearchProviders}

Returns the list of alternate search providers.

This function returns an empty list if [setAlternateSearchProviders](kurifilterdata.md#setAlternateSearchProviders) was not called to set the alternate search providers to be when no preferred providers have been chosen by the user through the search configuration module.

*See also* [setAlternateSearchProviders](kurifilterdata.md#setAlternateSearchProviders), [preferredSearchProviders](kurifilterdata.md#preferredSearchProviders)

### QString KUriFilterData::argsAndOptions() const {#argsAndOptions}

Returns the command line options and arguments for a local resource when present.

Returns options and arguments when present, otherwise QString()

### bool KUriFilterData::checkForExecutables() const {#checkForExecutables}

Returns true if the filters should attempt to check whether the supplied uri is an executable. False otherwise.

*See also* [setCheckForExecutables](kurifilterdata.md#setCheckForExecutables)()

### QString KUriFilterData::defaultUrlScheme() const {#defaultUrlScheme}

Returns the default protocol to use when filtering potentially valid url inputs.

By default this function will return an empty string.

*See also* [setDefaultUrlScheme](kurifilterdata.md#setDefaultUrlScheme)

### QString KUriFilterData::errorMsg() const {#errorMsg}

Returns an error message.

This functions returns the error message set by the plugin whenever the uri type is set to KUriFilterData::ERROR. Otherwise, it returns a nullptr string.

Returns the error message or a nullptr when there is none.

### bool KUriFilterData::hasAbsolutePath() const {#hasAbsolutePath}

Checks whether the supplied data had an absolute path.

Returns true if the supplied data has an absolute path

*See also* [absolutePath](kurifilterdata.md#absolutePath)()

### bool KUriFilterData::hasArgsAndOptions() const {#hasArgsAndOptions}

Checks whether the current data is a local resource with command line options and arguments.

Returns true if the current data has command line options and arguments

### QString KUriFilterData::iconName() {#iconName}

The name of the icon that matches the current filtered URL.

This function returns a null string by default and when no icon is found for the filtered URL.

### QString KUriFilterData::iconNameForPreferredSearchProvider(const QString &*provider*) const {#iconNameForPreferredSearchProvider}

Returns the icon associated with the given preferred search provider.

You can use this function to obtain the icon names associated with the preferred search providers returned by [preferredSearchProviders](kurifilterdata.md#preferredSearchProviders).

*See also* [preferredSearchProviders](kurifilterdata.md#preferredSearchProviders)

### QStringList KUriFilterData::preferredSearchProviders() const {#preferredSearchProviders}

Returns a list of the names of preferred or available search providers.

This function returns the list of providers marked as preferred whenever the input data, i.e. [typedString](kurifilterdata.md#typedString), is successfully filtered.

If no default search provider has been selected prior to a filter request, this function will return an empty list. To avoid this problem you must either set an alternate default search provider using [setAlternateDefaultSearchProvider](kurifilterdata.md#setAlternateDefaultSearchProvider) or set one of the [SearchFilterOption](kurifilterdata.md#SearchFilterOption-enum) flags if you are only interested in getting the list of providers and not filtering the input.

Additionally, you can also provide alternate search providers in case there are no preferred ones already selected.

You can use queryForPreferredServiceProvider to obtain the query associated with the list of search providers returned by this function.

*See also* [setAlternateSearchProviders](kurifilterdata.md#setAlternateSearchProviders)(), [setAlternateDefaultSearchProvider](kurifilterdata.md#setAlternateDefaultSearchProvider)(), [setSearchFilteringOptions](kurifilterdata.md#setSearchFilteringOptions)(), [queryForPreferredSearchProvider](kurifilterdata.md#queryForPreferredSearchProvider)()

### QString KUriFilterData::queryForPreferredSearchProvider(const QString &*provider*) const {#queryForPreferredSearchProvider}

Returns the web shortcut url for the given preferred search provider.

You can use this function to obtain the query for the preferred search providers returned by [preferredSearchProviders](kurifilterdata.md#preferredSearchProviders).

The query returned by this function is in web shortcut format, i.e. "gg:foo bar", and must be re-filtered through [KUriFilter](kurifilter.md) to obtain a valid url.

*See also* [preferredSearchProviders](kurifilterdata.md#preferredSearchProviders)

### KUriFilterSearchProvider KUriFilterData::queryForSearchProvider(const QString &*provider*) const {#queryForSearchProvider}

Returns information about `provider`.

You can use this function to obtain the more information about the search providers returned by [preferredSearchProviders](kurifilterdata.md#preferredSearchProviders).

*See also* [preferredSearchProviders](kurifilterdata.md#preferredSearchProviders)()

### KUriFilterData::SearchFilterOptions KUriFilterData::searchFilteringOptions() const {#searchFilteringOptions}

Returns the specified search filter options.

By default this function returns [SearchFilterOptionNone](kurifilterdata.md#SearchFilterOption-enum).

*See also* [setSearchFilteringOptions](kurifilterdata.md#setSearchFilteringOptions)

### QString KUriFilterData::searchProvider() const {#searchProvider}

Returns the name of the search service provider, e.g. Google.

If [typedString](kurifilterdata.md#typedString) was not filtered by a search filter plugin, this function returns an empty string.

*See also* [typedString](kurifilterdata.md#typedString)

### QString KUriFilterData::searchTerm() const {#searchTerm}

Returns the search term portion of the typed string.

If the [typedString](kurifilterdata.md#typedString) was not filtered by a search filter plugin, this function returns an empty string.

*See also* [typedString](kurifilterdata.md#typedString)

### QChar KUriFilterData::searchTermSeparator() const {#searchTermSeparator}

Returns the character that is used to separate the search term from the keyword.

If [typedString](kurifilterdata.md#typedString) was not filtered by a search filter plugin, this function returns a null character.

*See also* [typedString](kurifilterdata.md#typedString)

### bool KUriFilterData::setAbsolutePath(const QString &*abs\_path*) {#setAbsolutePath}

Sets the absolute path to be used whenever the supplied data is a relative local URL.

> **Note:** This function should only be used for local resources, i.e. the "file:/" protocol. It is useful for specifying the absolute path in cases where the actual URL might be relative. If deriving the path from a [QUrl](https://doc.qt.io/qt-6/qurl.html), make sure you set the argument for this function to the result of calling path () instead of url ().

`abs_path` the absolute path to the local resource.

Returns true if absolute path is successfully set. Otherwise, false.

*See also* [absolutePath](kurifilterdata.md#absolutePath)()

### void KUriFilterData::setAlternateDefaultSearchProvider(const QString &*provider*) {#setAlternateDefaultSearchProvider}

Sets the search provider to use in case no default provider is available.

The default search provider set using this function will only be used if the default and favorite search providers have not yet been selected by the user. Otherwise, the default provider specified by through function will be ignored.

*See also* [alternateDefaultSearchProvider](kurifilterdata.md#alternateDefaultSearchProvider), [preferredSearchProviders](kurifilterdata.md#preferredSearchProviders)

### void KUriFilterData::setAlternateSearchProviders(const QStringList &*providers*) {#setAlternateSearchProviders}

Sets a list of search providers to use in case no preferred search providers are available.

The list of preferred search providers set using this function will only be used if the default and favorite search providers have not yet been selected by the user. Otherwise, the providers specified through this function will be ignored.

*See also* [alternateSearchProviders](kurifilterdata.md#alternateSearchProviders), [preferredSearchProviders](kurifilterdata.md#preferredSearchProviders)

### void KUriFilterData::setCheckForExecutables(bool *check*) {#setCheckForExecutables}

Check whether the provided uri is executable or not.

Setting this to false ensures that typing the name of an executable does not start that application. This is useful in the location bar of a browser. The default value is true.

*See also* [checkForExecutables](kurifilterdata.md#checkForExecutables)()

### void KUriFilterData::setData(const QString &*url*) {#setData}

Sets the URL to be filtered.

Use this function to set the string to be filtered when you construct an empty filter object.

`url` the string to be filtered.

### void KUriFilterData::setData(const QUrl &*url*) {#setData-1}

Same as above except the argument is a URL.

Use this function to set the string to be filtered when you construct an empty filter object.

`url` the URL to be filtered.

### void KUriFilterData::setDefaultUrlScheme(*const QString &*) {#setDefaultUrlScheme}

Sets the default scheme used when filtering potentially valid url inputs.

Use this function to change the default protocol used when filtering potentially valid url inputs. The default protocol is http.

If the scheme is specified without a separator, then "://" will be used as the separator by default. For example, if the default url scheme was simply set to "ftp", then a potentially valid url input such as "kde.org" will be filtered to "ftp://kde.org".

*See also* [defaultUrlScheme](kurifilterdata.md#defaultUrlScheme)

### void KUriFilterData::setSearchFilteringOptions(KUriFilterData::SearchFilterOptions *options*) {#setSearchFilteringOptions}

Sets the options used by search filter plugins to filter requests.

The default search filter option is [SearchFilterOptionNone](kurifilterdata.md#SearchFilterOption-enum). See [SearchFilterOption](kurifilterdata.md#SearchFilterOption-enum) for the description of the other flags.

It is important to note that the options set through this function can prevent any filtering from being performed by search filter plugins. As such, uriTypes can return [KUriFilterData::Unknown](kurifilterdata.md#UriTypes-enum) and uri can return an invalid url even though the filtering request returned a successful response.

*See also* [searchFilteringOptions](kurifilterdata.md#searchFilteringOptions)

### QString KUriFilterData::typedString() const {#typedString}

The string as typed by the user, before any URL processing is done.

### QUrl KUriFilterData::uri() const {#uri}

Returns the filtered or the original URL.

If one of the plugins successfully filtered the original input, this function returns it. Otherwise, it will return the input itself.

Returns the filtered or original url.

### KUriFilterData::UriTypes KUriFilterData::uriType() const {#uriType}

Returns the URI type.

This method always returns KUriFilterData::UNKNOWN if the given URL was not filtered.

Returns the type of the URI
