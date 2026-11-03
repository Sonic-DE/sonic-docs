---
title: "PagePool QML Type"
description: "A pool of Page items."
---

# PagePool QML Type

A pool of Page items. [More...](#details)

- Import Statement: import org.kde.kirigami

## Detailed Description {#details}

Pages will be unique per url and the items will be kept around unless explicitly deleted.

Instances are C++ owned and can be deleted only manually using [deletePage](qml-org-kde-kirigami-pagepool.md#deletePage-method)().

Instance are unique per url: if you need 2 different instances for a page url, you should instantiate them in the traditional way or use a different [PagePool](qml-org-kde-kirigami-pagepool.md) instance.

*See also* [PagePoolAction](qml-org-kde-kirigami-pagepoolaction.md)

## Property Documentation {#property-documentation}

### cachePages : bool {#cachePages-prop}

If `true` (default) the pages will be kept around, will have C++ ownership and only one instance per page will be created. If `false` the pages will have Javascript ownership (thus deleted on pop by the page stacks) and each call to [loadPage](qml-org-kde-kirigami-pagepool.md#loadPage-method) will create a new page instance. When cachePages is false, Components get cached nevertheless.

### items : list\<Item\> {#items-prop}

All items loaded/managed by the [PagePool](qml-org-kde-kirigami-pagepool.md).

### lastLoadedItem : Item {#lastLoadedItem-prop}

The last item that was loaded with [loadPage](qml-org-kde-kirigami-pagepool.md#loadPage-method).

### lastLoadedUrl : url {#lastLoadedUrl-prop}

The last url that was loaded with [loadPage](qml-org-kde-kirigami-pagepool.md#loadPage-method). Useful if you need to have a "checked" state to buttons or list items that load the page when clicked.

### urls : list\<url\> {#urls-prop}

All page URLs loaded/managed by the [PagePool](qml-org-kde-kirigami-pagepool.md).

## Method Documentation {#method-documentation}

### void clear() {#clear-method}

Deletes all pages managed by the pool.

### bool contains(variant *page*) {#contains-method}

Return `true` if `page` is managed by the [PagePool](qml-org-kde-kirigami-pagepool.md)

### void deletePage(variant *page*) {#deletePage-method}

Deletes `page` (only if is managed by the pool).

### bool isLocalUrl(url *url*) {#isLocalUrl-method}

Returns `true` if the url identifies a local resource (local file or a file inside Qt's resource system).

`false` if the url points to a network location

### Item loadPage(string *url*, var *callback*) {#loadPage-method}

Returns the instance of the item defined in the QML file identified by url, only one instance will be made per url if cachePAges is true. If the url is remote (i.e. http) don't rely on the return value but us the async callback instead.

`url` full url of the item: it can be a well formed Url, an absolute path or a relative one to the path of the qml file the [PagePool](qml-org-kde-kirigami-pagepool.md) is instantiated from

`callback` If we are loading a remote url, we can't have the item immediately but will be passed as a parameter to the provided callback. Normally, don't set a callback, use it only in case of remote urls

Return the page instance that will have been created if necessary. If the url is remote it will return null, as well will return null if the callback has been provided

### Item loadPageWithProperties(string *url*, variantMap *properties*, var *callback*) {#loadPageWithProperties-method}

### Item pageForUrl(url *url*) {#pageForUrl-method}

Returns the page associated with a given URL, nullptr if there is no correspondence

### url resolvedUrl(string *file*) {#resolvedUrl-method}

Returns the full url from an absolute or relative path

### url urlForPage(Item *item*) {#urlForPage-method}

Returns the url of the page for the given instance, empty if there is no correspondence
