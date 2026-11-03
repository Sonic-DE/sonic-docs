---
title: "KBookmarkOwner Class"
description: "Bookmarks management library."
---

# KBookmarkOwner Class

Bookmarks management library. [More...](#details)

- **Header:** `#include <KBookmarkOwner>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Bookmarks)`  
  `target_link_libraries(mytarget PRIVATE KF6::Bookmarks)`

[List of all members, including inherited members](kbookmarkowner-members.md)

## Public Types

- [enum KBookmarkOwner::BookmarkOption](#BookmarkOption-enum)

## Public Functions

- [KBookmarkOwner()](#KBookmarkOwner)
- [QList\<KBookmarkOwner::FutureBookmark\> currentBookmarkList() const](#currentBookmarkList)
- [QString currentIcon() const](#currentIcon)
- [QString currentTitle() const](#currentTitle)
- [QUrl currentUrl() const](#currentUrl)
- [bool enableOption(KBookmarkOwner::BookmarkOption option) const](#enableOption)
- [void openBookmark(const KBookmark &bm, Qt::MouseButtons mb, Qt::KeyboardModifiers km)](#openBookmark)
- [void openFolderinTabs(const KBookmarkGroup &bm)](#openFolderinTabs)
- [void openInNewTab(const KBookmark &bm)](#openInNewTab)
- [void openInNewWindow(const KBookmark &bm)](#openInNewWindow)
- [bool supportsTabs() const](#supportsTabs)

## Detailed Description {#details}

The [KBookmarkMenu](../kbookmarkswidgets/kbookmarkmenu.md) and KBookmarkBar classes gives the user the ability to either edit bookmarks or add their own. In the first case, the app may want to open the bookmark in a special way. In the second case, the app must supply the name and the URL for the bookmark.

This class gives the app this callback-like ability.

If your app does not give the user the ability to add bookmarks and you don't mind using the default bookmark editor to edit your bookmarks, then you don't need to overload this class at all. Rather, just use something like:

```cpp
bookmarks = new KBookmarkMenu(manager, nullptr, menu);
```

If you wish to use your own editor or allow the user to add bookmarks, you must overload this class.

## Member Type Documentation {#member-type-documentation}

### enum KBookmarkOwner::BookmarkOption {#BookmarkOption-enum}

| Constant |   |
| --- | --- |
| `KBookmarkOwner::ShowAddBookmark` | `0` |
| `KBookmarkOwner::ShowEditBookmark` | `1` |

## Member Function Documentation {#member-function-documentation}

### KBookmarkOwner::KBookmarkOwner() {#KBookmarkOwner}

### \[virtual\] QList\<KBookmarkOwner::FutureBookmark\> KBookmarkOwner::currentBookmarkList() const {#currentBookmarkList}

Returns a list of bookmark data for the open tabs. The default returns an empty list.

### \[virtual\] QString KBookmarkOwner::currentIcon() const {#currentIcon}

This function is called whenever the user wants to add the current page to the bookmarks list. The icon will become the icon of the bookmark. You must overload this function if you wish to give your users the ability to add bookmarks. The default returns an empty string.

A very common implementation for this method is return KIO::iconNameForUrl([currentUrl](kbookmarkowner.md#currentUrl)());

Returns the icon name of the current page.

### \[virtual\] QString KBookmarkOwner::currentTitle() const {#currentTitle}

This function is called whenever the user wants to add the current page to the bookmarks list. The title will become the "name" of the bookmark. You must overload this function if you wish to give your users the ability to add bookmarks. The default returns an empty string.

Returns the title of the current page.

### \[virtual\] QUrl KBookmarkOwner::currentUrl() const {#currentUrl}

This function is called whenever the user wants to add the current page to the bookmarks list. The URL will become the URL of the bookmark. You must overload this function if you wish to give your users the ability to add bookmarks. The default returns an empty string.

Returns the URL of the current page.

Since 5.0 this method returns a [QUrl](https://doc.qt.io/qt-6/qurl.html). While porting it, remember to implement [currentIcon](kbookmarkowner.md#currentIcon) too.

### \[virtual\] bool KBookmarkOwner::enableOption(KBookmarkOwner::BookmarkOption *option*) const {#enableOption}

Returns true if `action` should be shown in the menu The default is to show both a add and editBookmark Entry

### \[pure virtual\] void KBookmarkOwner::openBookmark(const KBookmark &*bm*, Qt::MouseButtons *mb*, Qt::KeyboardModifiers *km*) {#openBookmark}

Called if a bookmark is selected. You need to override this.

### \[virtual\] void KBookmarkOwner::openFolderinTabs(const KBookmarkGroup &*bm*) {#openFolderinTabs}

Called if the user wants to open every bookmark in this folder in a new tab. The default implementation does nothing. This is only called if [supportsTabs](kbookmarkowner.md#supportsTabs)() returns true

### \[virtual\] void KBookmarkOwner::openInNewTab(const KBookmark &*bm*) {#openInNewTab}

Called when a bookmark should be opened in a new tab. The default implementation calls [openBookmark](kbookmarkowner.md#openBookmark).

### \[virtual\] void KBookmarkOwner::openInNewWindow(const KBookmark &*bm*) {#openInNewWindow}

Called when a bookmark should be opened in a new window. The default implementation calls [openBookmark](kbookmarkowner.md#openBookmark).

### \[virtual\] bool KBookmarkOwner::supportsTabs() const {#supportsTabs}

This function returns whether the owner supports tabs. The default returns `false`.
