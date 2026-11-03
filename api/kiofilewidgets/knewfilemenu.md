---
title: "KNewFileMenu Class"
description: "The 'Create New' submenu, for creating files using templates (e.g. \"new HTML file\") and directories."
---

# KNewFileMenu Class

The 'Create New' submenu, for creating files using templates (e.g. "new HTML file") and directories. [More...](#details)

- **Header:** `#include <KNewFileMenu>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOFileWidgets)`

[List of all members, including inherited members](knewfilemenu-members.md)

## Public Functions

- [KNewFileMenu(QObject \*parent)](#KNewFileMenu)
- [~KNewFileMenu()](#dtor.KNewFileMenu)
- [bool isCreateDirectoryRunning()](#isCreateDirectoryRunning) (since 6.2)
- [bool isCreateFileRunning()](#isCreateFileRunning) (since 6.2)
- [bool isModal() const](#isModal)
- [void setModal(bool modality)](#setModal)
- [void setNewFileShortcutAction(QAction \*action)](#setNewFileShortcutAction)
- [void setNewFolderShortcutAction(QAction \*action)](#setNewFolderShortcutAction)
- [void setParentWidget(QWidget \*parentWidget)](#setParentWidget)
- [void setSelectDirWhenAlreadyExist(bool b)](#setSelectDirWhenAlreadyExist)
- [void setSupportedMimeTypes(const QStringList &mime)](#setSupportedMimeTypes)
- [void setWindowTitle(const QString &title)](#setWindowTitle) (since 6.11)
- [void setWorkingDirectory(const QUrl &directory)](#setWorkingDirectory)
- [QStringList supportedMimeTypes() const](#supportedMimeTypes)
- [QUrl workingDirectory() const](#workingDirectory)

## Public Slots

- [void checkUpToDate()](#checkUpToDate)
- [void createDirectory()](#createDirectory)
- [void createFile()](#createFile)
- [void slotResult(KJob \*job)](#slotResult)

## Signals

- [void directoryCreated(const QUrl &url)](#directoryCreated)
- [void directoryCreationRejected(const QUrl &url)](#directoryCreationRejected) (since 6.2)
- [void directoryCreationStarted(const QUrl &url)](#directoryCreationStarted) (since 6.2)
- [void fileCreated(const QUrl &url)](#fileCreated)
- [void fileCreationRejected(const QUrl &url)](#fileCreationRejected) (since 6.2)
- [void fileCreationStarted(const QUrl &url)](#fileCreationStarted) (since 6.2)
- [void selectExistingDir(const QUrl &url)](#selectExistingDir)

## Detailed Description {#details}

The same instance can be used by both for the File menu and the RMB popup menu, in a file manager. This is also used in the file dialog's RMB menu.

To use this class, you need to connect aboutToShow() of the File menu with slotCheckUpToDate() and to call slotCheckUpToDate() before showing the RMB popupmenu.

[KNewFileMenu](knewfilemenu.md) automatically updates the list of templates shown if installed templates are added/updated/deleted.

## Member Function Documentation {#member-function-documentation}

### KNewFileMenu::KNewFileMenu(QObject \**parent*) {#KNewFileMenu}

Constructor.

`parent` the parent object, for ownership. If the parent object is a widget, it will also be used as the parent widget for any dialogs that this class might show. Otherwise, call [setParentWidget](knewfilemenu.md#setParentWidget).

### \[override virtual noexcept\] KNewFileMenu::~KNewFileMenu() {#dtor.KNewFileMenu}

Destructor. KNewMenu uses internally a globally shared cache, so that multiple instances of it don't need to parse the installed templates multiple times. Therefore you can safely create and delete KNewMenu instances without a performance issue.

### \[slot\] void KNewFileMenu::checkUpToDate() {#checkUpToDate}

Checks if updating the list is necessary IMPORTANT : Call this in the slot for aboutToShow.

### \[slot\] void KNewFileMenu::createDirectory() {#createDirectory}

Call this to create a new directory as if the user had done it using a popupmenu. This is useful to make sure that creating a directory with a key shortcut (e.g. F10) triggers the exact same code as when using the New menu. Requirements: since 5.97 call [setWorkingDirectory](knewfilemenu.md#setWorkingDirectory) first (for older releases call setPopupFiles first), and keep this [KNewFileMenu](knewfilemenu.md) instance alive (the mkdir is async).

### \[slot\] void KNewFileMenu::createFile() {#createFile}

Call this to create a new file as if the user had done it using a popupmenu. This is useful to make sure that creating a directory with a key shortcut (e.g. Shift-F10) triggers the exact same code as when using the New menu. Requirements: since 5.97 call [setWorkingDirectory](knewfilemenu.md#setWorkingDirectory) first (for older releases call setPopupFiles first), and keep this [KNewFileMenu](knewfilemenu.md) instance alive (the copy is async).

### \[signal\] void KNewFileMenu::directoryCreated(const QUrl &*url*) {#directoryCreated}

Emitted once the directory @p url has been successfully created

### \[signal, since 6.2\] void KNewFileMenu::directoryCreationRejected(const QUrl &*url*) {#directoryCreationRejected}

Emitted once the creation for directory @p url has been rejected

This function was introduced in Qt 6.2.

### \[signal, since 6.2\] void KNewFileMenu::directoryCreationStarted(const QUrl &*url*) {#directoryCreationStarted}

Emitted once the creation job for directory @p url has been started

This function was introduced in Qt 6.2.

### \[signal\] void KNewFileMenu::fileCreated(const QUrl &*url*) {#fileCreated}

Emitted once the file (or symlink) @p url has been successfully created

### \[signal, since 6.2\] void KNewFileMenu::fileCreationRejected(const QUrl &*url*) {#fileCreationRejected}

Emitted once the creation for file @p url has been rejected

This function was introduced in Qt 6.2.

### \[signal, since 6.2\] void KNewFileMenu::fileCreationStarted(const QUrl &*url*) {#fileCreationStarted}

Emitted once the creation job for file @p url has been started

This function was introduced in Qt 6.2.

### \[since 6.2\] bool KNewFileMenu::isCreateDirectoryRunning() {#isCreateDirectoryRunning}

Use this to check if namejob for new directory creation still running. Namejob is what spawns the new directory dialog, which can be slow in, for example, network folders.

This function was introduced in Qt 6.2.

### \[since 6.2\] bool KNewFileMenu::isCreateFileRunning() {#isCreateFileRunning}

Use this to check if the file creation process is still running.

This function was introduced in Qt 6.2.

### bool KNewFileMenu::isModal() const {#isModal}

Returns the modality of dialogs

### \[signal\] void KNewFileMenu::selectExistingDir(const QUrl &*url*) {#selectExistingDir}

Emitted when trying to create a new directory that has the same name as an existing one, so that [KDirOperator](kdiroperator.md) can select the existing item in the view (in case the user wants to use that directory instead of creating a new one).

### void KNewFileMenu::setModal(bool *modality*) {#setModal}

Sets the modality of dialogs created by KNewFile. Set to false if you do not want to block your application window when entering a new directory name i.e.

*See also* [isModal](knewfilemenu.md#isModal)()

### void KNewFileMenu::setNewFileShortcutAction(QAction \**action*) {#setNewFileShortcutAction}

Use this to set a shortcut for the new file action.

The shortcut is copied from `action`.

### void KNewFileMenu::setNewFolderShortcutAction(QAction \**action*) {#setNewFolderShortcutAction}

Use this to set a shortcut for the "New Folder" action.

The shortcut is copied from `action`.

### void KNewFileMenu::setParentWidget(QWidget \**parentWidget*) {#setParentWidget}

Sets a parent widget for the dialogs shown by [KNewFileMenu](knewfilemenu.md). This is strongly recommended, for apps with a main window.

### void KNewFileMenu::setSelectDirWhenAlreadyExist(bool *b*) {#setSelectDirWhenAlreadyExist}

Whether on not the dialog should emit \`[selectExistingDir](knewfilemenu.md#selectExistingDir)\` when trying to create an exist directory

default: false

### void KNewFileMenu::setSupportedMimeTypes(const QStringList &*mime*) {#setSupportedMimeTypes}

Only show the files in a given set of MIME types. This is useful in specialized applications (while file managers, on the other hand, want to show all MIME types).

*See also* [supportedMimeTypes](knewfilemenu.md#supportedMimeTypes)()

### \[since 6.11\] void KNewFileMenu::setWindowTitle(const QString &*title*) {#setWindowTitle}

Allow to change the popup

This function was introduced in Qt 6.11.

### void KNewFileMenu::setWorkingDirectory(const QUrl &*directory*) {#setWorkingDirectory}

Set the working directory. Files will be created relative to this directory.

*See also* [workingDirectory](knewfilemenu.md#workingDirectory)()

### \[virtual protected slot\] void KNewFileMenu::slotResult(KJob \**job*) {#slotResult}

Called when the job that copied the template has finished. This method is virtual so that error handling can be reimplemented. Make sure to call the base class slotResult when !job-\>error() though.

### QStringList KNewFileMenu::supportedMimeTypes() const {#supportedMimeTypes}

Returns the MIME types set in supportedMimeTypes()

*See also* [setSupportedMimeTypes](knewfilemenu.md#setSupportedMimeTypes)()

### QUrl KNewFileMenu::workingDirectory() const {#workingDirectory}

Returns the working directory. Files will be created relative to this directory.

*See also* [setWorkingDirectory](knewfilemenu.md#setWorkingDirectory)()
