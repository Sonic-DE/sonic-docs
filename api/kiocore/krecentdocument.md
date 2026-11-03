---
title: "KRecentDocument Class"
description: "Manage the \"Recent Document Menu\" entries displayed by applications such as Kicker and Konqueror."
---

# KRecentDocument Class

Manage the "Recent Document Menu" entries displayed by applications such as Kicker and Konqueror. [More...](#details)

- **Header:** `#include <KRecentDocument>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`

[List of all members, including inherited members](krecentdocument-members.md)

## Public Types

- [enum KRecentDocument::RecentDocumentGroup](#RecentDocumentGroup-enum)

## Static Public Members

- [void add(const QUrl &url)](#add)
- [void add(const QUrl &url, KRecentDocument::RecentDocumentGroups groups)](#add-1)
- [void add(const QUrl &url, const QString &desktopEntryName)](#add-2)
- [void add(const QUrl &url, const QString &desktopEntryName, KRecentDocument::RecentDocumentGroups groups)](#add-3)
- [void clear()](#clear)
- [bool clearEntriesOldestEntries(int maxEntries)](#clearEntriesOldestEntries)
- [int maximumItems()](#maximumItems)
- [QList\<QUrl\> recentUrls()](#recentUrls)
- [void removeApplication(const QString &desktopEntryName)](#removeApplication) (since 6.6)
- [void removeBookmarksModifiedSince(const QDateTime &since)](#removeBookmarksModifiedSince) (since 6.6)
- [void removeFile(const QUrl &url)](#removeFile) (since 6.6)

## Detailed Description {#details}

These entries are automatically generated .desktop files pointing to the current application and document. You should call the static [add](krecentdocument.md#add)() method whenever the user opens or saves a new document if you want it to show up in the menu.

It also stores history following xdg specification. Ref: https://www.freedesktop.org/wiki/Specifications/desktop-bookmark-spec This allows cross-framework file history sharing. I.e Gtk Apps can access files recently opened by KDE Apps.

You don't have to worry about this if you are using QFileDialog to open and save documents, as the KDE implementation ([KFileWidget](../kiofilewidgets/kfilewidget.md)) already calls this class. User defined limits on the maximum number of documents to save, etc... are all automatically handled.

## Member Type Documentation {#member-type-documentation}

### enum KRecentDocument::RecentDocumentGroup {#RecentDocumentGroup-enum}

Usage group for a file to bookmark in recently-used.xbel file

From spec https://www.freedesktop.org/wiki/Specifications/desktop-bookmark-spec/#appendixb:registeredgroupnames

| Constant | Value | Description |
| --- | --- | --- |
| `KRecentDocument::Development` | `0` | A bookmark related to a development environment |
| `KRecentDocument::Office` | `1` | A bookmark related to an office type document or folder |
| `KRecentDocument::Database` | `2` | A bookmark related to a database application; Office; relates to Development |
| `KRecentDocument::Email` | `3` | A bookmark related to an email application relates to Office |
| `KRecentDocument::Presentation` | `4` | A bookmark related to a presentation application relates to Office |
| `KRecentDocument::Spreadsheet` | `5` | A bookmark related to a spreadsheet application relates to Office |
| `KRecentDocument::WordProcessor` | `6` | A bookmark related to a word processing application relates to Office |
| `KRecentDocument::Graphics` | `7` | A bookmark related to a graphical application |
| `KRecentDocument::TextEditor` | `8` | A bookmark related to a text editor |
| `KRecentDocument::Viewer` | `9` | A bookmark related to any kind of file viewer |
| `KRecentDocument::Archive` | `10` | A bookmark related to an archive file |
| `KRecentDocument::Multimedia` | `11` | A bookmark related to a multimedia file or application |
| `KRecentDocument::Audio` | `12` | A bookmark related to an audio file or application relates to Multimedia |
| `KRecentDocument::Video` | `13` | A bookmark related to a video file or application relates to Multimedia |
| `KRecentDocument::Photo` | `14` | A bookmark related to a digital photography file or application relates to Multimedia; Graphics; Viewer |
| `KRecentDocument::Application` | `15` | Special bookmark for application launchers |

## Member Function Documentation {#member-function-documentation}

### \[static\] void KRecentDocument::add(const QUrl &*url*) {#add}

Add a new item to the Recent Document menu.

`url` The url to add.

### \[static\] void KRecentDocument::add(const QUrl &*url*, KRecentDocument::RecentDocumentGroups *groups*) {#add-1}

### \[static\] void KRecentDocument::add(const QUrl &*url*, const QString &*desktopEntryName*) {#add-2}

Add a new item to the Recent Document menu, specifying the application to open it with. The above [add](krecentdocument.md#add)() method uses [QCoreApplication::applicationName](https://doc.qt.io/qt-6/qcoreapplication.html#applicationName-prop)() for the app name, which isn't always flexible enough. This method is used when an application launches another one to open a document.

`url` The url to add.

`desktopEntryName` The desktopEntryName of the service to use for opening this document.

### \[static\] void KRecentDocument::add(const QUrl &*url*, const QString &*desktopEntryName*, KRecentDocument::RecentDocumentGroups *groups*) {#add-3}

### \[static\] void KRecentDocument::clear() {#clear}

Clear the recent document menu of all entries.

### \[static\] bool KRecentDocument::clearEntriesOldestEntries(int *maxEntries*) {#clearEntriesOldestEntries}

### \[static\] int KRecentDocument::maximumItems() {#maximumItems}

Returns the maximum amount of recent document entries allowed.

### \[static\] QList\<QUrl\> KRecentDocument::recentUrls() {#recentUrls}

Returns a list of recent URLs. This includes all the URLs from recentDocuments() as well as URLs from other applications conforming to the XDG desktop-bookmark-spec (e. g. the GTK file dialog).

### \[static, since 6.6\] void KRecentDocument::removeApplication(const QString &*desktopEntryName*) {#removeApplication}

This function was introduced in Qt 6.6.

### \[static, since 6.6\] void KRecentDocument::removeBookmarksModifiedSince(const QDateTime &*since*) {#removeBookmarksModifiedSince}

Remove bookmarks whose modification date is after `since` parameter.

This function was introduced in Qt 6.6.

### \[static, since 6.6\] void KRecentDocument::removeFile(const QUrl &*url*) {#removeFile}

This function was introduced in Qt 6.6.
