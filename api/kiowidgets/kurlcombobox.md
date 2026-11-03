---
title: "KUrlComboBox Class"
description: "This combobox shows a number of recent URLs/directories, as well as some default directories."
---

# KUrlComboBox Class

This combobox shows a number of recent URLs/directories, as well as some default directories. [More...](#details)

- **Header:** `#include <KUrlComboBox>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`

[List of all members, including inherited members](kurlcombobox-members.md)

## Public Types

- [enum KUrlComboBox::Mode](#Mode-enum)
- [enum KUrlComboBox::OverLoadResolving](#OverLoadResolving-enum)

## Properties

- [maxItems : int](#maxItems-prop)
- [urls : QStringList](#urls-prop)

## Public Functions

- [KUrlComboBox(KUrlComboBox::Mode mode, QWidget \*parent = nullptr)](#KUrlComboBox)
- [KUrlComboBox(KUrlComboBox::Mode mode, bool rw, QWidget \*parent = nullptr)](#KUrlComboBox-1)
- [void addDefaultUrl(const QUrl &url, const QString &text = QString())](#addDefaultUrl)
- [void addDefaultUrl(const QUrl &url, const QIcon &icon, const QString &text = QString())](#addDefaultUrl-1)
- [int maxItems() const](#maxItems)
- [void removeUrl(const QUrl &url, bool checkDefaultURLs = true)](#removeUrl)
- [void setDefaults()](#setDefaults)
- [void setMaxItems(int)](#setMaxItems)
- [void setUrl(const QUrl &url)](#setUrl)
- [void setUrls(const QStringList &urls)](#setUrls)
- [void setUrls(const QStringList &urls, KUrlComboBox::OverLoadResolving remove)](#setUrls-1)
- [QStringList urls() const](#urls)

## Signals

- [void onFocusOut()](#onFocusOut) (since 6.23)
- [void urlActivated(const QUrl &url)](#urlActivated)

## Detailed Description {#details}

It will manage the default dirs root-directory, home-directory and Desktop-directory, as well as a number of URLs set via [setUrls](kurlcombobox.md#setUrls)() and one additional entry to be set via [setUrl](kurlcombobox.md#setUrl)().

This widget forces the layout direction to be [Qt::LeftToRight](https://doc.qt.io/qt-6/qt.html#LayoutDirection-enum) instead of inheriting the layout direction like a normal widget. This means that even in RTL desktops the widget will be displayed in LTR mode, as generally URLs are LTR by nature.

## Member Type Documentation {#member-type-documentation}

### enum KUrlComboBox::Mode {#Mode-enum}

This enum describes which kind of items is shown in the combo box.

| Constant |   |
| --- | --- |
| `KUrlComboBox::Files` | `-1` |
| `KUrlComboBox::Directories` | `1` |
| `KUrlComboBox::Both` | `0` |

### enum KUrlComboBox::OverLoadResolving {#OverLoadResolving-enum}

This Enumeration is used in [setUrl](kurlcombobox.md#setUrl)() to determine which items will be removed when the given list is larger than [maxItems](kurlcombobox.md#maxItems)().

| Constant | Value | Description |
| --- | --- | --- |
| `KUrlComboBox::RemoveTop` | `0` | means that items will be removed from top |
| `KUrlComboBox::RemoveBottom` | `1` | means, that items will be removed from the bottom |

## Property Documentation {#property-documentation}

### maxItems : int {#maxItems-prop}

**Access functions:**

- `int` **[maxItems](kurlcombobox.md#maxItems)**() const
- `void` **[setMaxItems](kurlcombobox.md#setMaxItems)**(*int*)

### urls : QStringList {#urls-prop}

**Access functions:**

- `QStringList` **[urls](kurlcombobox.md#urls)**() const
- `void` **[setUrls](kurlcombobox.md#setUrls)**(const `QStringList` &*urls*)
- `void` **[setUrls](kurlcombobox.md#setUrls-1)**(const `QStringList` &*urls*, `KUrlComboBox::OverLoadResolving` *remove*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KUrlComboBox::KUrlComboBox(KUrlComboBox::Mode *mode*, QWidget \**parent* = nullptr) {#KUrlComboBox}

Constructs a [KUrlComboBox](kurlcombobox.md).

`mode` is either Files, Directories or Both and controls the following behavior:

- Files all inserted URLs will be treated as files, therefore the url shown in the combo will never show a trailing / the icon will be the one associated with the file's MIME type.
- Directories all inserted URLs will be treated as directories, will have a trailing slash in the combobox. The current directory will show the "open folder" icon, other directories the "folder" icon.
- Both Don't mess with anything, just show the url as given.

`parent` The parent object of this widget.

### KUrlComboBox::KUrlComboBox(KUrlComboBox::Mode *mode*, bool *rw*, QWidget \**parent* = nullptr) {#KUrlComboBox-1}

### void KUrlComboBox::addDefaultUrl(const QUrl &*url*, const QString &*text* = QString()) {#addDefaultUrl}

Adds a url that will always be shown in the combobox, it can't be "rotated away". Default urls won't be returned in [urls](kurlcombobox.md#urls)() and don't have to be set via [setUrls](kurlcombobox.md#setUrls)().

If you want to specify a special pixmap, use the overloaded method with the pixmap parameter.

Default URLs will be inserted into the combobox by [setDefaults](kurlcombobox.md#setDefaults)()

### void KUrlComboBox::addDefaultUrl(const QUrl &*url*, const QIcon &*icon*, const QString &*text* = QString()) {#addDefaultUrl-1}

Adds a url that will always be shown in the combobox, it can't be "rotated away". Default urls won't be returned in [urls](kurlcombobox.md#urls)() and don't have to be set via [setUrls](kurlcombobox.md#setUrls)().

If you don't need to specify a pixmap, use the overloaded method without the pixmap parameter.

Default URLs will be inserted into the combobox by [setDefaults](kurlcombobox.md#setDefaults)()

### int KUrlComboBox::maxItems() const {#maxItems}

Returns the maximum of items the combobox handles.

> **Note:** Getter function for property [maxItems](kurlcombobox.md#maxItems-prop).

*See also* [setMaxItems](kurlcombobox.md#setMaxItems)

### \[signal, since 6.23\] void KUrlComboBox::onFocusOut() {#onFocusOut}

Emitted when combobox loses focus.

This function was introduced in Qt 6.23.

### void KUrlComboBox::removeUrl(const QUrl &*url*, bool *checkDefaultURLs* = true) {#removeUrl}

Removes any occurrence of `url`. If `checkDefaultUrls` is false default-urls won't be removed.

### void KUrlComboBox::setDefaults() {#setDefaults}

Clears all items and inserts the default urls into the combo. Will be called implicitly upon the first call to [setUrls](kurlcombobox.md#setUrls)() or [setUrl](kurlcombobox.md#setUrl)()

*See also* [addDefaultUrl](kurlcombobox.md#addDefaultUrl)

### void KUrlComboBox::setMaxItems(*int*) {#setMaxItems}

Sets how many items should be handled and displayed by the combobox.

> **Note:** Setter function for property [maxItems](kurlcombobox.md#maxItems-prop).

*See also* [maxItems](kurlcombobox.md#maxItems)

### void KUrlComboBox::setUrl(const QUrl &*url*) {#setUrl}

Sets the current url. This combo handles exactly one url additionally to the default items and those set via [setUrls](kurlcombobox.md#setUrls)(). So you can call setUrl() as often as you want, it will always replace the previous one set via setUrl().

If `url` is already in the combo, the last item will stay there and the existing item becomes the current item.

The current item will always have the open-directory-pixmap as icon.

Note that you won't receive any signals, e.g. textChanged(), returnPressed() or activated() upon calling this method.

### void KUrlComboBox::setUrls(const QStringList &*urls*) {#setUrls}

Inserts `urls` into the combobox below the "default urls" (see [addDefaultUrl](kurlcombobox.md#addDefaultUrl)).

If the list of urls contains more items than [maxItems](kurlcombobox.md#maxItems), the first items will be stripped.

> **Note:** Setter function for property [urls](kurlcombobox.md#urls-prop).

*See also* [urls](kurlcombobox.md#urls)()

### void KUrlComboBox::setUrls(const QStringList &*urls*, KUrlComboBox::OverLoadResolving *remove*) {#setUrls-1}

Inserts `urls` into the combobox below the "default urls" (see [addDefaultUrl](kurlcombobox.md#addDefaultUrl)).

If the list of urls contains more items than [maxItems](kurlcombobox.md#maxItems), the `remove` parameter determines whether the first or last items will be stripped.

> **Note:** Setter function for property [urls](kurlcombobox.md#urls-prop).

### \[signal\] void KUrlComboBox::urlActivated(const QUrl &*url*) {#urlActivated}

Emitted when an item was clicked at.

`url` is the url of the now current item.

### QStringList KUrlComboBox::urls() const {#urls}

Returns a list of all urls currently handled. The list contains at most [maxItems](kurlcombobox.md#maxItems)() items.

Use this to save the list of urls in a config-file and reinsert them via [setUrls](kurlcombobox.md#setUrls)() next time.

Note that all default urls set via [addDefaultUrl](kurlcombobox.md#addDefaultUrl)() are not returned, they will automatically be set via [setUrls](kurlcombobox.md#setUrls)() or [setUrl](kurlcombobox.md#setUrl)().

You will always get fully qualified urls, i.e. with protocol like file:/

> **Note:** Getter function for property [urls](kurlcombobox.md#urls-prop).

*See also* [setUrls](kurlcombobox.md#setUrls)()
