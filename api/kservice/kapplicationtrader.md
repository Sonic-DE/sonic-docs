---
title: "KApplicationTrader Namespace"
description: "The application trader is a convenient way to find installed applications based on specific criteria (association with a MIME type, name contains Foo, etc.)."
---

# KApplicationTrader Namespace

The application trader is a convenient way to find installed applications based on specific criteria (association with a MIME type, name contains Foo, etc.). [More...](#details)

- Header: KApplicationTrader
- CMake: find\_package(KF6 REQUIRED COMPONENTS Service) target\_link\_libraries(mytarget PRIVATE KF6::Service)

## Detailed Description {#details}

Example: say that you want to get the list of all applications that can handle PNG images. The code would look like:

```cpp
KService::List lst = KApplicationTrader::queryByMimeType("image/png");
```

If you want to get the preferred application for image/png you would use:

```cpp
KService::Ptr service = KApplicationTrader::preferredService("image/png");
```

*See also* [KService](kservice-index.md)

## Type Documentation {#type-documentation}

### \[alias\] KApplicationTrader::FilterFunc {#FilterFunc-typedef}

Filter function, used for filtering results of query and [queryByMimeType](kapplicationtrader.md#queryByMimeType).

## Function Documentation {#function-documentation}

### bool KApplicationTrader::isSubsequence(const QString &*pattern*, const QString &*text*, Qt::CaseSensitivity *cs* = Qt::CaseSensitive) {#isSubsequence}

Returns true if `pattern` matches a subsequence of the string `text`. For instance the pattern "libremath" matches the text "LibreOffice Math", assuming `cs` is [Qt::CaseInsensitive](https://doc.qt.io/qt-6/qt.html#CaseSensitivity-enum).

This can be useful from your filter function, e.g. with `text` being service-\>name().

### KService::Ptr KApplicationTrader::preferredService(const QString &*mimeType*) {#preferredService}

Returns the preferred service for `mimeType`

This a convenience method for [queryByMimeType](kapplicationtrader.md#queryByMimeType)(mimeType).at(0), with a check for empty.

`mimeType` the MIME type (see [query](kapplicationtrader.md#query)())

Returns the preferred service, or `nullptr` if no service is available

*See also* [setPreferredService](kapplicationtrader.md#setPreferredService)()

### KService::List KApplicationTrader::query(KApplicationTrader::FilterFunc *filterFunc*) {#query}

This method returns a list of services (applications) that match a given filter.

`filterFunc` a callback function that returns `true` if the application should be selected and `false` if it should be skipped.

Returns a list of services that satisfy the query

### KService::List KApplicationTrader::queryByMimeType(const QString &*mimeType*, KApplicationTrader::FilterFunc *filterFunc* = {}) {#queryByMimeType}

This method returns a list of services (applications) which are associated with a given MIME type.

`mimeType` a MIME type like 'text/plain' or 'text/html'

`filterFunc` a callback function that returns `true` if the application should be selected and `false` if it should be skipped. Do not return true for all services, this would return the complete list of all installed applications (slow).

Returns a list of services that satisfy the query, sorted by preference (preferred service first)

### void KApplicationTrader::setPreferredService(const QString &*mimeType*, const KService::Ptr *service*) {#setPreferredService}

Changes the preferred service for `mimeType` to `service`

You may need to rebuild KSyCoca for the change to be reflected

`mimeType` the MIME type

`service` the service to set as the preferred one

*See also* [preferredService](kapplicationtrader.md#preferredService)()
