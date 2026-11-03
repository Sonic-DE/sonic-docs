---
title: "KPropertiesDialog Class"
description: "The main properties dialog class."
---

# KPropertiesDialog Class

The main properties dialog class. [More...](#details)

- **Header:** `#include <KPropertiesDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`

[List of all members, including inherited members](kpropertiesdialog-members.md)

## Public Functions

- [KPropertiesDialog(const KFileItem &item, QWidget \*parent = nullptr)](#KPropertiesDialog)
- [KPropertiesDialog(const QList\<QUrl\> &urls, QWidget \*parent = nullptr)](#KPropertiesDialog-1)
- [KPropertiesDialog(const QString &title, QWidget \*parent = nullptr)](#KPropertiesDialog-2)
- [KPropertiesDialog(const QUrl &url, QWidget \*parent = nullptr)](#KPropertiesDialog-3)
- [KPropertiesDialog(const QUrl &\_tempUrl, const QUrl &\_currentDir, const QString &\_defaultName, QWidget \*parent = nullptr)](#KPropertiesDialog-4)
- [KPropertiesDialog(const KFileItemList &\_items, QWidget \*parent = nullptr)](#KPropertiesDialog-5)
- [~KPropertiesDialog()](#dtor.KPropertiesDialog)
- [void abortApplying()](#abortApplying)
- [QUrl currentDir() const](#currentDir)
- [QString defaultName() const](#defaultName)
- [KFileItem &item()](#item)
- [KFileItemList items() const](#items)
- [void rename(const QString &\_name)](#rename)
- [void setFileNameReadOnly(bool ro)](#setFileNameReadOnly)
- [void setFileSharingPage(QWidget \*page)](#setFileSharingPage)
- [void showFileSharingPage()](#showFileSharingPage)
- [void updateUrl(const QUrl &newUrl)](#updateUrl)
- [QUrl url() const](#url)

## Public Slots

- [void accept()](#accept)
- [void reject()](#reject)

## Signals

- [void applied()](#applied)
- [void canceled()](#canceled)
- [void propertiesClosed()](#propertiesClosed)
- [void saveAs(const QUrl &oldUrl, QUrl &newUrl)](#saveAs)

## Static Public Members

- [bool canDisplay(const KFileItemList &\_items)](#canDisplay)
- [bool showDialog(const KFileItem &item, QWidget \*parent = nullptr, bool modal = true)](#showDialog)
- [bool showDialog(const KFileItemList &\_items, QWidget \*parent = nullptr, bool modal = true)](#showDialog-1)
- [bool showDialog(const QList\<QUrl\> &urls, QWidget \*parent = nullptr, bool modal = true)](#showDialog-2)
- [bool showDialog(const QUrl &\_url, QWidget \*parent = nullptr, bool modal = true)](#showDialog-3)

## Detailed Description {#details}

A Properties Dialog is a dialog which displays various information about a particular file or URL, or several files or URLs. This main class holds various related classes, which are instantiated in the form of tab entries in the tabbed dialog that this class provides. The various tabs themselves will let the user view, and sometimes change, information about the file or URL.

The best way to display the properties dialog is to use [showDialog](kpropertiesdialog.md#showDialog)(). Otherwise, you should use (void)new [KPropertiesDialog](kpropertiesdialog.md)(...) It will take care of deleting itself when closed.

If you are looking for more flexibility, see KFileMetaInfo and KFileMetaInfoWidget.

This respects the "editfiletype", "run\_desktop\_files" and "shell\_access" Kiosk action restrictions (see KAuthorized::authorize()).

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KPropertiesDialog::KPropertiesDialog(const KFileItem &*item*, QWidget \**parent* = nullptr) {#KPropertiesDialog}

Brings up a Properties dialog, as shown above. This is the normal constructor for file-manager type applications, where you have a [KFileItem](../kiocore/kfileitem.md) instance to work with. Normally you will use this method rather than the one below.

`item` file item whose properties should be displayed.

`parent` is the parent of the dialog widget.

### \[explicit\] KPropertiesDialog::KPropertiesDialog(const QList\<QUrl\> &*urls*, QWidget \**parent* = nullptr) {#KPropertiesDialog-1}

Brings up a Properties dialog. Convenience constructor for non-file-manager applications, where you have a list of QUrls rather than a [KFileItemList](../kiocore/kfileitemlist.md).

`urls` list of URLs whose properties should be displayed (must contain at least one non-empty URL)

`parent` is the parent of the dialog widget.

For local files with a known MIME type, simply create a [KFileItemList](../kiocore/kfileitemlist.md) and pass it to the other constructor.

### \[explicit\] KPropertiesDialog::KPropertiesDialog(const QString &*title*, QWidget \**parent* = nullptr) {#KPropertiesDialog-2}

Creates an empty properties dialog (for applications that want use a standard dialog, but for things not doable via the plugin-mechanism).

`title` is the string display as the "filename" in the title of the dialog.

`parent` is the parent of the dialog widget.

### \[explicit\] KPropertiesDialog::KPropertiesDialog(const QUrl &*url*, QWidget \**parent* = nullptr) {#KPropertiesDialog-3}

Brings up a Properties dialog. Convenience constructor for non-file-manager applications, where you have a [QUrl](https://doc.qt.io/qt-6/qurl.html) rather than a [KFileItem](../kiocore/kfileitem.md) or [KFileItemList](../kiocore/kfileitemlist.md).

`url` the URL whose properties should be displayed

`parent` is the parent of the dialog widget.

For local files with a known MIME type, simply create a [KFileItem](../kiocore/kfileitem.md) and pass it to the other constructor.

### KPropertiesDialog::KPropertiesDialog(const QUrl &*\_tempUrl*, const QUrl &*\_currentDir*, const QString &*\_defaultName*, QWidget \**parent* = nullptr) {#KPropertiesDialog-4}

Creates a properties dialog for a new .desktop file (whose name is not known yet), based on a template. Special constructor for "File / New" in file-manager type applications.

`_tempUrl` template used for reading only

`_currentDir` directory where the file will be written to

`_defaultName` something to put in the name field, like mimetype.desktop

`parent` is the parent of the dialog widget.

### \[explicit\] KPropertiesDialog::KPropertiesDialog(const KFileItemList &*\_items*, QWidget \**parent* = nullptr) {#KPropertiesDialog-5}

You use this constructor for cases where you have a number of items, rather than a single item. Be careful which methods you use when passing a list of files or URLs, since some of them will only work on the first item in a list.

`_items` list of file items whose properties should be displayed.

`parent` is the parent of the dialog widget.

This is an overloaded function.

### \[override virtual noexcept\] KPropertiesDialog::~KPropertiesDialog() {#dtor.KPropertiesDialog}

Cleans up the properties dialog and frees any associated resources, including the dialog itself. Note that when a properties dialog is closed it cleans up and deletes itself.

### void KPropertiesDialog::abortApplying() {#abortApplying}

To abort applying changes.

### \[override virtual slot\] void KPropertiesDialog::accept() {#accept}

Called when the user presses 'Ok'.

### \[signal\] void KPropertiesDialog::applied() {#applied}

This signal is emitted when the properties changes are applied (for example, with the OK button)

### \[static\] bool KPropertiesDialog::canDisplay(const KFileItemList &*\_items*) {#canDisplay}

Determine whether there are any property pages available for the given file items.

`_items` the list of items to check.

Returns true if there are any property pages, otherwise false.

### \[signal\] void KPropertiesDialog::canceled() {#canceled}

This signal is emitted when the properties changes are aborted (for example, with the Cancel button)

### QUrl KPropertiesDialog::currentDir() const {#currentDir}

If the dialog is being built from a template, this method returns the current directory. If no template, it returns QString(). See the template form of the constructor.

Returns the current directory or QString()

### QString KPropertiesDialog::defaultName() const {#defaultName}

If the dialog is being built from a template, this method returns the default name. If no template, it returns QString(). See the template form of the constructor. Returns the default name or QString()

### KFileItem &KPropertiesDialog::item() {#item}

Returns the file item for which the dialog is shown

> **Warning:** this method returns the first item of the list. This means that you should use this only if you are sure the dialog is used for a single item. Otherwise, you probably want [items](kpropertiesdialog.md#items)() instead.

### KFileItemList KPropertiesDialog::items() const {#items}

Returns the items for which the dialog is shown

### \[signal\] void KPropertiesDialog::propertiesClosed() {#propertiesClosed}

This signal is emitted when the Properties Dialog is closed (for example, with OK or Cancel buttons)

### \[override virtual slot\] void KPropertiesDialog::reject() {#reject}

Called when the user presses 'Cancel' or Esc.

### void KPropertiesDialog::rename(const QString &*\_name*) {#rename}

Renames the item to the specified name. This can only be called if the dialog applies to a single file or URL.

`_name` new filename, encoded.

*See also* [KPropertiesDialogPlugin::applyChanges](kpropertiesdialogplugin.md#applyChanges)()

### \[signal\] void KPropertiesDialog::saveAs(const QUrl &*oldUrl*, QUrl &*newUrl*) {#saveAs}

Emitted before changes to `oldUrl` are saved as `newUrl`.

The receiver may change `newUrl` to point to an alternative save location.

### void KPropertiesDialog::setFileNameReadOnly(bool *ro*) {#setFileNameReadOnly}

Call this to make the filename lineedit readonly, to prevent the user from renaming the file. `ro` true if the lineedit should be read only

### void KPropertiesDialog::setFileSharingPage(QWidget \**page*) {#setFileSharingPage}

Sets the file sharing page. This page is shown when calling [showFileSharingPage](kpropertiesdialog.md#showFileSharingPage)().

`page` the page to set

> **Note:** This should only be called by [KPropertiesDialog](kpropertiesdialog.md) plugins.

*See also* [showFileSharingPage](kpropertiesdialog.md#showFileSharingPage)

### \[static\] bool KPropertiesDialog::showDialog(const KFileItem &*item*, QWidget \**parent* = nullptr, bool *modal* = true) {#showDialog}

Immediately displays a Properties dialog using constructor with the same parameters.

On MS Windows, if `item` points to a local file, native (non modal) property dialog is displayed (`parent` and `modal` are ignored in this case).

Returns `true` on successful dialog displaying (can be `false` on win32).

### \[static\] bool KPropertiesDialog::showDialog(const KFileItemList &*\_items*, QWidget \**parent* = nullptr, bool *modal* = true) {#showDialog-1}

Immediately displays a Properties dialog using constructor with the same parameters.

On MS Windows, if `_items` has one element and this element points to a local file, native (non modal) property dialog is displayed (`parent` and `modal` are ignored in this case).

Returns `true` on successful dialog displaying (can be `false` on win32).

### \[static\] bool KPropertiesDialog::showDialog(const QList\<QUrl\> &*urls*, QWidget \**parent* = nullptr, bool *modal* = true) {#showDialog-2}

Immediately displays a Properties dialog using constructor with the same parameters.

On MS Windows, if `_urls` has one element and this element points to a local file, native (non modal) property dialog is displayed (`parent` and `modal` are ignored in this case).

`urls` list of URLs whose properties should be displayed (must contain at least one non-empty URL)

`parent` is the parent of the dialog widget.

`modal` tells the dialog whether it should be modal.

Returns `true` on successful dialog displaying (can be `false` on win32).

### \[static\] bool KPropertiesDialog::showDialog(const QUrl &*\_url*, QWidget \**parent* = nullptr, bool *modal* = true) {#showDialog-3}

Immediately displays a Properties dialog using constructor with the same parameters.

On MS Windows, if `_url` points to a local file, native (non modal) property dialog is displayed (`parent` and `modal` are ignored in this case).

Returns `true` on successful dialog displaying (can be `false` on win32).

### void KPropertiesDialog::showFileSharingPage() {#showFileSharingPage}

Shows the page that was previously set by [setFileSharingPage](kpropertiesdialog.md#setFileSharingPage)(), or does nothing if no page was set yet.

*See also* [setFileSharingPage](kpropertiesdialog.md#setFileSharingPage)

### void KPropertiesDialog::updateUrl(const QUrl &*newUrl*) {#updateUrl}

Updates the item URL (either called by rename or because a global apps/mimelnk desktop file is being saved) Can only be called if the dialog applies to a single file or URL.

`newUrl` the new URL

### QUrl KPropertiesDialog::url() const {#url}

The URL of the file that has its properties being displayed.

This is only valid if the [KPropertiesDialog](kpropertiesdialog.md) was created/shown for one file or URL.

Returns the single URL.
