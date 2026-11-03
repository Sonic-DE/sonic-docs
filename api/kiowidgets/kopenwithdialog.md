---
title: "KOpenWithDialog Class"
description: "\"Open With\" dialog box."
---

# KOpenWithDialog Class

"Open With" dialog box. [More...](#details)

- **Header:** `#include <KOpenWithDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](kopenwithdialog-members.md)

## Public Functions

- [KOpenWithDialog(QWidget \*parent = nullptr)](#KOpenWithDialog)
- [KOpenWithDialog(const QList\<QUrl\> &urls, QWidget \*parent = nullptr)](#KOpenWithDialog-1)
- [KOpenWithDialog(const QString &mimeType, const QString &value, QWidget \*parent = nullptr)](#KOpenWithDialog-2)
- [KOpenWithDialog(const QList\<QUrl\> &urls, const QString &text, const QString &value, QWidget \*parent = nullptr)](#KOpenWithDialog-3)
- [KOpenWithDialog(const QList\<QUrl\> &urls, const QString &mimeType, const QString &text, const QString &value, QWidget \*parent = nullptr)](#KOpenWithDialog-4)
- [void hideNoCloseOnExit()](#hideNoCloseOnExit)
- [void hideRunInTerminal()](#hideRunInTerminal)
- [KService::Ptr service() const](#service)
- [void setSaveNewApplications(bool b)](#setSaveNewApplications)
- [QString text() const](#text)

## Detailed Description {#details}

> **Note:** To let the user choose an application and run it immediately, use simpler KRun::displayOpenWithDialog().

If the Kiosk "shell\_access" action is not authorized (see KAuthorized::authorize()), arbitrary commands are not allowed; instead, the user must browse to and choose an executable.

## Member Function Documentation {#member-function-documentation}

### KOpenWithDialog::KOpenWithDialog(QWidget \**parent* = nullptr) {#KOpenWithDialog}

Create a dialog to select an application Note that this dialog doesn't apply to URLs.

`parent` parent widget

### \[explicit\] KOpenWithDialog::KOpenWithDialog(const QList\<QUrl\> &*urls*, QWidget \**parent* = nullptr) {#KOpenWithDialog-1}

Create a dialog that asks for a application to open a given URL(s) with.

`urls` the URLs that should be opened. The list can be empty, if the dialog is used to choose an application but not for some particular URLs.

`parent` parent widget

### KOpenWithDialog::KOpenWithDialog(const QString &*mimeType*, const QString &*value*, QWidget \**parent* = nullptr) {#KOpenWithDialog-2}

Create a dialog to select a service for a given MIME type. Note that this dialog doesn't apply to URLs.

`mimeType` the MIME type we want to choose an application for.

`value` is the initial value of the line

`parent` parent widget

### KOpenWithDialog::KOpenWithDialog(const QList\<QUrl\> &*urls*, const QString &*text*, const QString &*value*, QWidget \**parent* = nullptr) {#KOpenWithDialog-3}

Create a dialog that asks for a application to open a given URL(s) with.

`urls` is the URL that should be opened

`text` appears as a label on top of the entry box. Leave empty for default text (since 5.20).

`value` is the initial value of the line

`parent` parent widget

### KOpenWithDialog::KOpenWithDialog(const QList\<QUrl\> &*urls*, const QString &*mimeType*, const QString &*text*, const QString &*value*, QWidget \**parent* = nullptr) {#KOpenWithDialog-4}

Create a dialog that asks for a application for opening a given URL (or more than one), when we already know the MIME type of the URL(s).

`urls` is the URLs that should be opened

`mimeType` the MIME type of the URL

`text` appears as a label on top of the entry box.

`value` is the initial value of the line

`parent` parent widget

### void KOpenWithDialog::hideNoCloseOnExit() {#hideNoCloseOnExit}

Hide the "Do not &close when command exits" Checkbox

### void KOpenWithDialog::hideRunInTerminal() {#hideRunInTerminal}

Hide the "Run in &terminal" Checkbox

### KService::Ptr KOpenWithDialog::service() const {#service}

Returns the chosen service in the application tree Can be null, if the user typed some text and didn't select a service.

### void KOpenWithDialog::setSaveNewApplications(bool *b*) {#setSaveNewApplications}

Set whether a new .desktop file should be created if the user selects an application for which no corresponding .desktop file can be found.

Regardless of this setting a new .desktop file may still be created if the user has chosen to remember the file association.

The default is false: no .desktop files are created.

### QString KOpenWithDialog::text() const {#text}

Returns the text the user entered
