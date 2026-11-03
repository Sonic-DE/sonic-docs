---
title: "KFileCopyToMenu Class"
description: "This class adds \"Copy To\" and \"Move To\" submenus to a popupmenu."
---

# KFileCopyToMenu Class

This class adds "Copy To" and "Move To" submenus to a popupmenu. [More...](#details)

- **Header:** `#include <KFileCopyToMenu>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOFileWidgets)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kfilecopytomenu-members.md)

## Public Functions

- [KFileCopyToMenu(QWidget \*parentWidget)](#KFileCopyToMenu)
- [void addActionsTo(QMenu \*menu) const](#addActionsTo)
- [void setAutoErrorHandlingEnabled(bool b)](#setAutoErrorHandlingEnabled)
- [void setReadOnly(bool ro)](#setReadOnly)
- [void setUrls(const QList\<QUrl\> &urls)](#setUrls)

## Signals

- [void error(int errorCode, const QString &message)](#error)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KFileCopyToMenu::KFileCopyToMenu(QWidget \**parentWidget*) {#KFileCopyToMenu}

Creates a [KFileCopyToMenu](kfilecopytomenu.md) instance Note that this instance (and the widget) must stay alive for at least as long as the popupmenu; it has the slots for the actions created by [addActionsTo](kfilecopytomenu.md#addActionsTo).

`parentWidget` parent widget for the file dialog and message boxes. The parentWidget also serves as a parent for this object.

### void KFileCopyToMenu::addActionsTo(QMenu \**menu*) const {#addActionsTo}

Generate the actions and submenus, and adds them to the `menu`. All actions are created as children of the menu.

### \[signal\] void KFileCopyToMenu::error(int *errorCode*, const QString &*message*) {#error}

Emitted when the copy or move job fails.

`errorCode` the KIO job error code

`message` the error message to show the user

### void KFileCopyToMenu::setAutoErrorHandlingEnabled(bool *b*) {#setAutoErrorHandlingEnabled}

Enables or disables automatic error handling with message boxes. When called with true, a messagebox is shown in case of an error during a copy or move. When called with false, the application should connect to the error signal instead. Auto error handling is disabled by default.

### void KFileCopyToMenu::setReadOnly(bool *ro*) {#setReadOnly}

If setReadOnly(true) is called, the "Move To" submenu will not appear.

### void KFileCopyToMenu::setUrls(const QList\<QUrl\> &*urls*) {#setUrls}

Sets the URLs which the actions apply to.
