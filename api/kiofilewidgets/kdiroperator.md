---
title: "KDirOperator Class"
description: "A widget for displaying files and browsing directories."
---

# KDirOperator Class

A widget for displaying files and browsing directories. [More...](#details)

- **Header:** `#include <KDirOperator>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOFileWidgets)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kdiroperator-members.md)  
[Deprecated members](kdiroperator-obsolete.md)

## Public Types

- [enum KDirOperator::Action](#Action-enum)
- [enum KDirOperator::ActionType](#ActionType-enum)

## Public Functions

- [KDirOperator(const QUrl &urlName = QUrl{}, QWidget \*parent = nullptr)](#KDirOperator)
- [QAction \*action(KDirOperator::Action action) const](#action)
- [QList\<QAction \*\> allActions() const](#allActions)
- [void clearFilter()](#clearFilter)
- [void clearHistory()](#clearHistory)
- [void close()](#close)
- [KCompletion \*completionObject() const](#completionObject)
- [QStyleOptionViewItem::Position decorationPosition() const](#decorationPosition)
- [KCompletion \*dirCompletionObject() const](#dirCompletionObject)
- [bool dirHighlighting() const](#dirHighlighting)
- [KDirLister \*dirLister() const](#dirLister)
- [bool dirOnlyMode() const](#dirOnlyMode)
- [bool followNewDirectories() const](#followNewDirectories)
- [bool followSelectedDirectories() const](#followSelectedDirectories)
- [int iconSize() const](#iconSize)
- [bool isInlinePreviewShown() const](#isInlinePreviewShown)
- [bool isRoot() const](#isRoot)
- [bool isSaving() const](#isSaving)
- [bool isSelected(const KFileItem &item) const](#isSelected)
- [QStringList mimeFilter() const](#mimeFilter)
- [KFile::Modes mode() const](#mode)
- [QString nameFilter() const](#nameFilter)
- [QStringList newFileMenuSupportedMimeTypes() const](#newFileMenuSupportedMimeTypes)
- [int numDirs() const](#numDirs)
- [int numFiles() const](#numFiles)
- [bool onlyDoubleClickSelectsFiles() const](#onlyDoubleClickSelectsFiles)
- [KFilePreviewGenerator \*previewGenerator() const](#previewGenerator)
- [QProgressBar \*progressBar() const](#progressBar)
- [void readConfig(const KConfigGroup &configGroup)](#readConfig)
- [KFileItemList selectedItems() const](#selectedItems)
- [void setAcceptDrops(bool b)](#setAcceptDrops)
- [void setCurrentItem(const KFileItem &item)](#setCurrentItem)
- [void setCurrentItem(const QUrl &url)](#setCurrentItem-1)
- [void setCurrentItems(const KFileItemList &items)](#setCurrentItems)
- [void setCurrentItems(const QList\<QUrl\> &urls)](#setCurrentItems-1)
- [void setDecorationPosition(QStyleOptionViewItem::Position position)](#setDecorationPosition)
- [void setDropOptions(int options)](#setDropOptions)
- [void setEnableDirHighlighting(bool enable)](#setEnableDirHighlighting)
- [void setFollowNewDirectories(bool enable)](#setFollowNewDirectories)
- [void setFollowSelectedDirectories(bool enable)](#setFollowSelectedDirectories)
- [void setInlinePreviewShown(bool show)](#setInlinePreviewShown)
- [void setIsSaving(bool isSaving)](#setIsSaving)
- [void setMimeFilter(const QStringList &mimetypes)](#setMimeFilter)
- [void setMode(KFile::Modes m)](#setMode)
- [void setNameFilter(const QString &filter)](#setNameFilter)
- [void setNewFileMenuSelectDirWhenAlreadyExist(bool selectOnDirExists)](#setNewFileMenuSelectDirWhenAlreadyExist)
- [void setNewFileMenuSupportedMimeTypes(const QStringList &mime)](#setNewFileMenuSupportedMimeTypes)
- [void setOnlyDoubleClickSelectsFiles(bool enable)](#setOnlyDoubleClickSelectsFiles)
- [void setShowHiddenFiles(bool s)](#setShowHiddenFiles)
- [void setSorting(QDir::SortFlags)](#setSorting)
- [void setUrl(const QUrl &url, bool clearforward)](#setUrl)
- [void setViewConfig(KConfigGroup &configGroup)](#setViewConfig)
- [void setViewMode(KFile::FileView viewKind)](#setViewMode)
- [void setupMenu(int whichActions)](#setupMenu-1)
- [bool showHiddenFiles() const](#showHiddenFiles)
- [void showOpenWithActions(bool enable)](#showOpenWithActions)
- [QDir::SortFlags sorting() const](#sorting)
- [QStringList supportedSchemes() const](#supportedSchemes)
- [KIO::CopyJob \*trash(const KFileItemList &items, QWidget \*parent, bool ask = true, bool showProgress = true)](#trash)
- [QUrl url() const](#url)
- [bool usingKeyNavigation()](#usingKeyNavigation) (since 6.14)
- [QAbstractItemView \*view() const](#view)
- [KConfigGroup \*viewConfigGroup() const](#viewConfigGroup)
- [KFile::FileView viewMode() const](#viewMode)
- [void writeConfig(KConfigGroup &configGroup)](#writeConfig)

## Public Slots

- [void back()](#back)
- [void cdUp()](#cdUp)
- [void deleteSelected()](#deleteSelected)
- [void forward()](#forward)
- [void highlightFile(const KFileItem &item)](#highlightFile)
- [void home()](#home)
- [QString makeCompletion(const QString &)](#makeCompletion)
- [QString makeDirCompletion(const QString &)](#makeDirCompletion)
- [void mkdir()](#mkdir)
- [void pathChanged()](#pathChanged)
- [void renameSelected()](#renameSelected)
- [void rereadDir()](#rereadDir)
- [void resetCursor()](#resetCursor)
- [void selectDir(const KFileItem &item)](#selectDir)
- [void selectFile(const KFileItem &item)](#selectFile)
- [void setIconSize(int value)](#setIconSize)
- [void setSupportedSchemes(const QStringList &schemes)](#setSupportedSchemes)
- [void slotCompletionMatch(const QString &match)](#slotCompletionMatch)
- [void sortByDate()](#sortByDate)
- [void sortByName()](#sortByName)
- [void sortBySize()](#sortBySize)
- [void sortByType()](#sortByType)
- [void sortReversed()](#sortReversed)
- [void toggleDirsFirst()](#toggleDirsFirst)
- [void toggleIgnoreCase()](#toggleIgnoreCase)
- [void trashSelected()](#trashSelected)
- [void updateDir()](#updateDir)
- [void updateSelectionDependentActions()](#updateSelectionDependentActions)

## Signals

- [void completion(const QString &)](#completion)
- [void contextMenuAboutToShow(const KFileItem &item, QMenu \*menu)](#contextMenuAboutToShow)
- [void currentIconSizeChanged(int size)](#currentIconSizeChanged)
- [void dirActivated(const KFileItem &item)](#dirActivated)
- [void dropped(const KFileItem &item, QDropEvent \*event, const QList\<QUrl\> &urls)](#dropped)
- [void fileHighlighted(const KFileItem &item)](#fileHighlighted)
- [void fileSelected(const KFileItem &item)](#fileSelected)
- [void finishedLoading()](#finishedLoading)
- [void keyEnterReturnPressed()](#keyEnterReturnPressed)
- [void renamingFinished(const QList\<QUrl\> &urls)](#renamingFinished)
- [void updateInformation(int files, int dirs)](#updateInformation)
- [void urlEntered(const QUrl &)](#urlEntered)
- [void viewChanged(QAbstractItemView \*newView)](#viewChanged)

## Protected Functions

- [void activatedMenu(const KFileItem &item, const QPoint &pos)](#activatedMenu)
- [bool checkPreviewSupport()](#checkPreviewSupport)
- [QAbstractItemView \*createView(QWidget \*parent, KFile::FileView viewKind)](#createView)
- [void prepareCompletionObjects()](#prepareCompletionObjects)
- [void setDirLister(KDirLister \*lister)](#setDirLister)
- [void setupActions()](#setupActions)
- [void setupMenu()](#setupMenu)
- [void updateSortActions()](#updateSortActions)
- [void updateViewActions()](#updateViewActions)

## Detailed Description {#details}

This widget works as a network transparent filebrowser. You specify a URL to display and this url will be loaded via [KDirLister](../kiowidgets/kdirlister.md). The user can browse through directories, highlight and select files, delete or rename files.

It supports different views, e.g. a detailed view (see KFileDetailView), a simple icon view (see KFileIconView), a combination of two views, separating directories and files ( KCombiView).

Additionally, a preview view is available (see KFilePreview), which can show either a simple or detailed view and additionally a preview widget (see setPreviewWidget()). [KImageFilePreview](kimagefilepreview.md) is one implementation of a preview widget, that displays previews for all supported filetypes utilizing [KIO::PreviewJob](../kiogui/kio-previewjob.md).

Currently, those classes don't support Drag&Drop out of the box – there you have to use your own view-classes. You can use some DnD-aware views from Björn Sahlström \<bjorn@kbear.org\> until they will be integrated into this library. See http://devel-home.kde.org/~pfeiffer/DnD-classes.tar.gz

This widget is the one used in the [KFileWidget](kfilewidget.md).

Basic usage is like this:

```cpp
KDirOperator *op = new KDirOperator(QUrl("file:///home/gis"), this);
// some signals you might be interested in
connect(op, &KDirOperator::urlEntered, this, [this](const QUrl &url) { slotUrlEntered(url); });
connect(op, &KDirOperator::fileHighlighted, this, [this](const KFileItem &item) { slotFileHighlighted(item) });
connect(op, &KDirOperator::fileSelected, this, [this](const KFileItem &item) { slotFileSelected(item) });
connect(op, &KDirOperator::finishedLoading, this, [this]() { slotLoadingFinished(); };

KConfigGroup grp(KSharedConfig::openConfig(),"Your KDiroperator ConfigGroup" );
op->readConfig( &grp);
op->setViewMode(KFile::Default);
```

This will create a childwidget of 'this' showing the directory contents of /home/gis in the default-view. The view is determined by the [readConfig](kdiroperator.md#readConfig)() call, which will read the [KDirOperator](kdiroperator.md) settings, the user left your program with (and which you saved with op-\>[writeConfig](kdiroperator.md#writeConfig)()).

## Member Type Documentation {#member-type-documentation}

### enum KDirOperator::Action {#Action-enum}

Actions provided by [KDirOperator](kdiroperator.md) that can be accessed from the outside using [action](kdiroperator.md#action)()

| Constant | Value | Description |
| --- | --- | --- |
| `KDirOperator::PopupMenu` | `0` | An ActionMenu presenting a popupmenu with all actions |
| `KDirOperator::Up` | `1` | Changes to the parent directory |
| `KDirOperator::Back` | `2` | Goes back to the previous directory |
| `KDirOperator::Forward` | `3` | Goes forward in the history |
| `KDirOperator::Home` | `4` | Changes to the user's home directory |
| `KDirOperator::Reload` | `5` | Reloads the current directory |
| `KDirOperator::New` | `6` | A [KNewFileMenu](knewfilemenu.md) |
| `KDirOperator::NewFolder` | `7` | Opens a dialog box to create a directory |
| `KDirOperator::Rename` | `8` |   |
| `KDirOperator::Trash` | `9` |   |
| `KDirOperator::Delete` | `10` | Deletes the selected files/directories |
| `KDirOperator::SortMenu` | `11` | An ActionMenu containing all sort-options |
| `KDirOperator::SortByName` | `12` | Sorts by name |
| `KDirOperator::SortBySize` | `13` | Sorts by size |
| `KDirOperator::SortByDate` | `14` | Sorts by date |
| `KDirOperator::SortByType` | `15` | Sorts by type |
| `KDirOperator::SortAscending` | `16` | Changes sort order to ascending |
| `KDirOperator::SortDescending` | `17` | Changes sort order to descending |
| `KDirOperator::SortFoldersFirst` | `18` | Sorts folders before files |
| `KDirOperator::SortHiddenFilesLast` | `19` | Sorts hidden files last |
| `KDirOperator::ViewModeMenu` | `20` | an ActionMenu containing all actions concerning the view |
| `KDirOperator::ViewIconsView` | `21` |   |
| `KDirOperator::ViewCompactView` | `22` |   |
| `KDirOperator::ViewDetailsView` | `23` |   |
| `KDirOperator::DecorationMenu` | `24` |   |
| `KDirOperator::DecorationAtTop` | `25` |   |
| `KDirOperator::DecorationAtLeft` | `26` |   |
| `KDirOperator::ShortView` | `27` | Shows a simple fileview |
| `KDirOperator::DetailedView` | `28` | Shows a detailed fileview (dates, permissions ,...) |
| `KDirOperator::TreeView` | `29` |   |
| `KDirOperator::DetailedTreeView` | `30` |   |
| `KDirOperator::AllowExpansionInDetailsView` | `31` |   |
| `KDirOperator::ShowHiddenFiles` | `32` | shows hidden files |
| `KDirOperator::ShowPreviewPanel` | `33` | shows a preview next to the fileview |
| `KDirOperator::ShowPreview` | `34` |   |
| `KDirOperator::OpenContainingFolder` | `35` |   |
| `KDirOperator::Properties` | `36` | Shows a [KPropertiesDialog](../kiowidgets/kpropertiesdialog.md) for the selected files |

### enum KDirOperator::ActionType {#ActionType-enum}

The various action types. These values can be or'd together

| Constant |   |
| --- | --- |
| `KDirOperator::SortActions` | `1` |
| `KDirOperator::ViewActions` | `2` |
| `KDirOperator::NavActions` | `4` |
| `KDirOperator::FileActions` | `8` |
| `KDirOperator::AllActions` | `15` |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KDirOperator::KDirOperator(const QUrl &*urlName* = QUrl{}, QWidget \**parent* = nullptr) {#KDirOperator}

Constructs the [KDirOperator](kdiroperator.md) with no initial view. As the views are configurable, call [readConfig](kdiroperator.md#readConfig)() to load the user's configuration and then setView to explicitly set a view.

This constructor doesn't start loading the url, setView will do it.

### QAction \*KDirOperator::action(KDirOperator::Action *action*) const {#action}

Obtain a given action from the [KDirOperator](kdiroperator.md)'s set of actions.

You can e.g. use

```cpp
dirOperator->action(KDirOperator::Up)->plug(someToolBar);
```

to add a button into a toolbar, which makes the dirOperator change to its parent directory.

### \[virtual protected\] void KDirOperator::activatedMenu(const KFileItem &*item*, const QPoint &*pos*) {#activatedMenu}

Called upon right-click to activate the popupmenu.

### QList\<QAction \*\> KDirOperator::allActions() const {#allActions}

A list of all actions for this [KDirOperator](kdiroperator.md).

See [action](kdiroperator.md#action)()

### \[virtual slot\] void KDirOperator::back() {#back}

Goes one step back in the history and opens that url.

### \[virtual slot\] void KDirOperator::cdUp() {#cdUp}

Goes one directory up from the current url.

### \[protected\] bool KDirOperator::checkPreviewSupport() {#checkPreviewSupport}

Checks if there support from [KIO::PreviewJob](../kiogui/kio-previewjob.md) for the currently shown files, taking [mimeFilter](kdiroperator.md#mimeFilter)() and [nameFilter](kdiroperator.md#nameFilter)() into account Enables/disables the preview-action accordingly.

### void KDirOperator::clearFilter() {#clearFilter}

Clears both the namefilter and MIME type filter, so that all files and directories will be shown. Call [updateDir](kdiroperator.md#updateDir)() to apply it.

*See also* [setMimeFilter](kdiroperator.md#setMimeFilter), [setNameFilter](kdiroperator.md#setNameFilter)

### void KDirOperator::clearHistory() {#clearHistory}

Clears the forward and backward history.

### void KDirOperator::close() {#close}

Stops loading immediately. You don't need to call this, usually.

### \[signal\] void KDirOperator::completion(*const QString &*) {#completion}

### KCompletion \*KDirOperator::completionObject() const {#completionObject}

Returns a [KCompletion](../kcompletion/kcompletion.md) object, containing all filenames and directories of the current directory/URL. You can use it to insert it into a [KLineEdit](../kcompletion/klineedit.md) or [KComboBox](../kcompletion/kcombobox.md) Note: it will only contain files, after [prepareCompletionObjects](kdiroperator.md#prepareCompletionObjects)() has been called. It will be implicitly called from [makeCompletion](kdiroperator.md#makeCompletion)() or [makeDirCompletion](kdiroperator.md#makeDirCompletion)()

### \[signal\] void KDirOperator::contextMenuAboutToShow(const KFileItem &*item*, QMenu \**menu*) {#contextMenuAboutToShow}

Emitted just before the context menu is shown, allows users to extend the menu with custom actions.

`item` the file on which the context menu was invoked

`menu` the context menu, pre-populated with the file-management actions

### \[virtual protected\] QAbstractItemView \*KDirOperator::createView(QWidget \**parent*, KFile::FileView *viewKind*) {#createView}

A view factory for creating predefined fileviews. Called internally by setView, but you can also call it directly. Reimplement this if you depend on self defined fileviews.

`parent` is the [QWidget](https://doc.qt.io/qt-6/qwidget.html) to be set as parent

`viewKind` is the predefined view to be set, note: this can be several ones OR:ed together

Returns the created view

*See also* [KFile::FileView](../kiowidgets/kfile.md#FileView-enum), [setViewMode](kdiroperator.md#setViewMode)

### \[signal\] void KDirOperator::currentIconSizeChanged(int *size*) {#currentIconSizeChanged}

Will notify that the icon size has changed. Since we save the icon size depending on the view type (list view or a different kind of view), a call to [setViewMode](kdiroperator.md#setViewMode)() can trigger this signal to be emitted.

### QStyleOptionViewItem::Position KDirOperator::decorationPosition() const {#decorationPosition}

Returns the position where icons are shown relative to the labels of file items in the icon view.

*See also* [setDecorationPosition](kdiroperator.md#setDecorationPosition)()

### \[virtual slot\] void KDirOperator::deleteSelected() {#deleteSelected}

Deletes the currently selected files/directories.

### \[signal\] void KDirOperator::dirActivated(const KFileItem &*item*) {#dirActivated}

### KCompletion \*KDirOperator::dirCompletionObject() const {#dirCompletionObject}

Returns a [KCompletion](../kcompletion/kcompletion.md) object, containing only all directories of the current directory/URL. You can use it to insert it into a [KLineEdit](../kcompletion/klineedit.md) or [KComboBox](../kcompletion/kcombobox.md) Note: it will only contain directories, after [prepareCompletionObjects](kdiroperator.md#prepareCompletionObjects)() has been called. It will be implicitly called from [makeCompletion](kdiroperator.md#makeCompletion)() or [makeDirCompletion](kdiroperator.md#makeDirCompletion)()

### bool KDirOperator::dirHighlighting() const {#dirHighlighting}

Returns whether the last directory will be made the current item (and hence highlighted) when going up or back in the directory hierarchy

Directories are highlighted by default.

### KDirLister \*KDirOperator::dirLister() const {#dirLister}

Returns the object listing the directory

*See also* [setDirLister](kdiroperator.md#setDirLister)()

### bool KDirOperator::dirOnlyMode() const {#dirOnlyMode}

Returns true if we are in directory-only mode, that is, no files are shown.

### \[signal\] void KDirOperator::dropped(const KFileItem &*item*, QDropEvent \**event*, const QList\<QUrl\> &*urls*) {#dropped}

Emitted when files are dropped. Dropping files is disabled by default. You need to enable it with [setAcceptDrops](kdiroperator.md#setAcceptDrops)()

`item` the item on which the drop occurred or 0.

`event` the drop event itself.

`urls` the urls that where dropped.

### \[signal\] void KDirOperator::fileHighlighted(const KFileItem &*item*) {#fileHighlighted}

Emitted when a file is highlighted or generally the selection changes in multiselection mode. In the latter case, `item` is a null [KFileItem](../kiocore/kfileitem.md). You can access the selected items with [selectedItems](kdiroperator.md#selectedItems)().

### \[signal\] void KDirOperator::fileSelected(const KFileItem &*item*) {#fileSelected}

### \[signal\] void KDirOperator::finishedLoading() {#finishedLoading}

### bool KDirOperator::followNewDirectories() const {#followNewDirectories}

Returns true if [setUrl](kdiroperator.md#setUrl) is called on newly created directories, false otherwise. Enabled by default.

*See also* [setFollowNewDirectories](kdiroperator.md#setFollowNewDirectories)

### bool KDirOperator::followSelectedDirectories() const {#followSelectedDirectories}

Returns whether [setUrl](kdiroperator.md#setUrl) is called on selected directories when a tree view is used. Enabled by default.

*See also* [setFollowSelectedDirectories](kdiroperator.md#setFollowSelectedDirectories)()

### \[virtual slot\] void KDirOperator::forward() {#forward}

Goes one step forward in the history and opens that url.

### \[protected slot\] void KDirOperator::highlightFile(const KFileItem &*item*) {#highlightFile}

Emits [fileHighlighted](kdiroperator.md#fileHighlighted)(item)

### \[virtual slot\] void KDirOperator::home() {#home}

Enters the home directory.

### int KDirOperator::iconSize() const {#iconSize}

Returns the icon size in pixels, ranged from KIconLoader::SizeSmall (16) to KIconLoader::SizeEnormous (128).

*See also* [setIconSize](kdiroperator.md#setIconSize)()

### bool KDirOperator::isInlinePreviewShown() const {#isInlinePreviewShown}

Returns whether the inline previews are shown or not.

### bool KDirOperator::isRoot() const {#isRoot}

Returns true if we are displaying the root directory of the current url

### bool KDirOperator::isSaving() const {#isSaving}

Returns whether [KDirOperator](kdiroperator.md) will force a double click to accept.

> **Note:** this is false by default

*See also* [setIsSaving](kdiroperator.md#setIsSaving)()

### bool KDirOperator::isSelected(const KFileItem &*item*) const {#isSelected}

Returns true if `item` is currently selected, or false otherwise.

### \[signal\] void KDirOperator::keyEnterReturnPressed() {#keyEnterReturnPressed}

Triggered when the user hit Enter/Return

### \[slot\] QString KDirOperator::makeCompletion(*const QString &*) {#makeCompletion}

Tries to complete the given string (only completes files).

### \[slot\] QString KDirOperator::makeDirCompletion(*const QString &*) {#makeDirCompletion}

Tries to complete the given string (only completes directories).

### QStringList KDirOperator::mimeFilter() const {#mimeFilter}

Returns the current MIME type filter.

*See also* [setMimeFilter](kdiroperator.md#setMimeFilter)()

### \[virtual slot\] void KDirOperator::mkdir() {#mkdir}

Opens a dialog to create a new directory.

### KFile::Modes KDirOperator::mode() const {#mode}

Returns the listing/selection mode.

*See also* [setMode](kdiroperator.md#setMode)()

### QString KDirOperator::nameFilter() const {#nameFilter}

Returns the current namefilter.

*See also* [setNameFilter](kdiroperator.md#setNameFilter)

### QStringList KDirOperator::newFileMenuSupportedMimeTypes() const {#newFileMenuSupportedMimeTypes}

Returns the current Supported Mimes Types.

*See also* [setNewFileMenuSupportedMimeTypes](kdiroperator.md#setNewFileMenuSupportedMimeTypes)()

### int KDirOperator::numDirs() const {#numDirs}

Returns the number of directories in the currently listed url. Returns 0 if there is no view.

### int KDirOperator::numFiles() const {#numFiles}

Returns the number of files in the currently listed url. Returns 0 if there is no view.

### bool KDirOperator::onlyDoubleClickSelectsFiles() const {#onlyDoubleClickSelectsFiles}

Returns whether files (not directories) should only be select()ed by double-clicks.

*See also* [setOnlyDoubleClickSelectsFiles](kdiroperator.md#setOnlyDoubleClickSelectsFiles)

### \[protected slot\] void KDirOperator::pathChanged() {#pathChanged}

Called after [setUrl](kdiroperator.md#setUrl)() to load the directory, update the history, etc.

### \[protected\] void KDirOperator::prepareCompletionObjects() {#prepareCompletionObjects}

Synchronizes the completion objects with the entries of the currently listed url.

Automatically called from [makeCompletion](kdiroperator.md#makeCompletion)() and [makeDirCompletion](kdiroperator.md#makeDirCompletion)()

### KFilePreviewGenerator \*KDirOperator::previewGenerator() const {#previewGenerator}

Returns the preview generator for the current view.

### QProgressBar \*KDirOperator::progressBar() const {#progressBar}

Returns the progress widget, that is shown during directory listing. You can for example reparent() it to put it into a statusbar.

### \[virtual\] void KDirOperator::readConfig(const KConfigGroup &*configGroup*) {#readConfig}

Reads the default settings for a view, i.e. the default [KFile::FileView](../kiowidgets/kfile.md#FileView-enum). Also reads the sorting and whether hidden files should be shown. Note: the default view will not be set - you have to call

```cpp
setViewMode( KFile::Default )
```

to apply it.

*See also* [setViewMode](kdiroperator.md#setViewMode), [setViewConfig](kdiroperator.md#setViewConfig), [writeConfig](kdiroperator.md#writeConfig)

### \[slot\] void KDirOperator::renameSelected() {#renameSelected}

Initiates a rename operation on the currently selected files/directories, prompting the user to choose a new name(s) for the currently selected items

*See also* [renamingFinished](kdiroperator.md#renamingFinished)

### \[signal\] void KDirOperator::renamingFinished(const QList\<QUrl\> &*urls*) {#renamingFinished}

Emitted when renaming selected files has finished.

`urls` URL list of the renamed files

### \[virtual slot\] void KDirOperator::rereadDir() {#rereadDir}

Re-reads the current url.

### \[protected slot\] void KDirOperator::resetCursor() {#resetCursor}

Restores the normal cursor after showing the busy-cursor. Also hides the progressbar.

### \[virtual protected slot\] void KDirOperator::selectDir(const KFileItem &*item*) {#selectDir}

Enters the directory specified by the given `item`.

### \[protected slot\] void KDirOperator::selectFile(const KFileItem &*item*) {#selectFile}

Emits [fileSelected](kdiroperator.md#fileSelected)( item )

### KFileItemList KDirOperator::selectedItems() const {#selectedItems}

Returns a list of all currently selected items. If there is no view, or there are no selected items, an empty list is returned.

### \[virtual\] void KDirOperator::setAcceptDrops(bool *b*) {#setAcceptDrops}

Reimplemented - allow dropping of files if `b` is true, defaults to true since 5.59

`b` true if the widget should allow dropping of files

### void KDirOperator::setCurrentItem(const KFileItem &*item*) {#setCurrentItem}

Clears the current selection and attempts to set `item` as the current item.

### void KDirOperator::setCurrentItem(const QUrl &*url*) {#setCurrentItem-1}

Clears the current selection and attempts to set `url` the current url file.

### void KDirOperator::setCurrentItems(const KFileItemList &*items*) {#setCurrentItems}

Clears the current selection and attempts to set `items` as the current items.

### void KDirOperator::setCurrentItems(const QList\<QUrl\> &*urls*) {#setCurrentItems-1}

Clears the current selection and attempts to set `urls` the current url files.

### void KDirOperator::setDecorationPosition(QStyleOptionViewItem::Position *position*) {#setDecorationPosition}

Sets the position where icons shall be shown relative to the labels of file items in the icon view.

*See also* [decorationPosition](kdiroperator.md#decorationPosition)()

### \[virtual protected\] void KDirOperator::setDirLister(KDirLister \**lister*) {#setDirLister}

Sets a custom [KDirLister](../kiowidgets/kdirlister.md) to list directories. The [KDirOperator](kdiroperator.md) takes ownership of the given [KDirLister](../kiowidgets/kdirlister.md).

*See also* [dirLister](kdiroperator.md#dirLister)()

### \[virtual\] void KDirOperator::setDropOptions(int *options*) {#setDropOptions}

Sets the options for dropping files. CURRENTLY NOT IMPLEMENTED

### \[virtual\] void KDirOperator::setEnableDirHighlighting(bool *enable*) {#setEnableDirHighlighting}

When using the up or back actions to navigate the directory hierarchy, [KDirOperator](kdiroperator.md) can highlight the directory that was just left.

For example:

- starting in /a/b/c/, going up to /a/b, "c" will be highlighted
- starting in /a/b/c, going up (twice) to /a, "b" will be highlighted; using the back action to go to /a/b/, "c" will be highlighted
- starting in /a, going to "b", then going to "c", using the back action to go to /a/b/, "c" will be highlighted; using the back action again to go to /a/, "b" will be highlighted

The default is to highlight directories when going back/up.

*See also* [dirHighlighting](kdiroperator.md#dirHighlighting)

### void KDirOperator::setFollowNewDirectories(bool *enable*) {#setFollowNewDirectories}

Toggles whether [setUrl](kdiroperator.md#setUrl) is called on newly created directories.

*See also* [followNewDirectories](kdiroperator.md#followNewDirectories)()

### void KDirOperator::setFollowSelectedDirectories(bool *enable*) {#setFollowSelectedDirectories}

Toggles whether [setUrl](kdiroperator.md#setUrl) is called on selected directories when a tree view is used.

*See also* [followSelectedDirectories](kdiroperator.md#followSelectedDirectories)()

### \[slot\] void KDirOperator::setIconSize(int *value*) {#setIconSize}

Notifies that the icons size should change. `value` is the icon size in pixels, ranged from KIconLoader::SizeSmall (16) to KIconLoader::SizeEnormous (128).

*See also* [iconSize](kdiroperator.md#iconSize)()

### void KDirOperator::setInlinePreviewShown(bool *show*) {#setInlinePreviewShown}

Forces the inline previews to be shown or hidden, depending on `show`.

`show` Whether to show inline previews or not.

*See also* [isInlinePreviewShown](kdiroperator.md#isInlinePreviewShown)()

### void KDirOperator::setIsSaving(bool *isSaving*) {#setIsSaving}

If the system is set up to trigger items on single click, if `isSaving` is true, we will force to double click to accept.

> **Note:** this is false by default

*See also* [isSaving](kdiroperator.md#isSaving)()

### void KDirOperator::setMimeFilter(const QStringList &*mimetypes*) {#setMimeFilter}

Sets a list of MIME types as filter. Only files of those MIME types will be shown.

Example:

```cpp
QStringList filter;
filter << "text/html" << "image/png" << "inode/directory";
dirOperator->setMimefilter( filter );
```

Node: Without the MIME type inode/directory, only files would be shown. Call [updateDir](kdiroperator.md#updateDir)() to apply it.

*See also* [KDirLister::setMimeFilter](../kiocore/kcoredirlister.md#setMimeFilter), [mimeFilter](kdiroperator.md#mimeFilter)

### \[virtual\] void KDirOperator::setMode(KFile::Modes *m*) {#setMode}

Sets the listing/selection mode for the views, an OR'ed combination of

- File
- Directory
- Files
- ExistingOnly
- LocalOnly

You cannot mix File and Files of course, as the former means single-selection mode, the latter multi-selection.

*See also* [mode](kdiroperator.md#mode)()

### void KDirOperator::setNameFilter(const QString &*filter*) {#setNameFilter}

Sets a filter like "\*.cpp \*.h \*.o". Only files matching that filter will be shown.

*See also* [KDirLister::setNameFilter](../kiocore/kcoredirlister.md#setNameFilter), [nameFilter](kdiroperator.md#nameFilter)

### void KDirOperator::setNewFileMenuSelectDirWhenAlreadyExist(bool *selectOnDirExists*) {#setNewFileMenuSelectDirWhenAlreadyExist}

Setting this to true will make a directory get selected when trying to create a new one that has the same name.

### void KDirOperator::setNewFileMenuSupportedMimeTypes(const QStringList &*mime*) {#setNewFileMenuSupportedMimeTypes}

Only show the files in a given set of MIME types. This is useful in specialized applications (while file managers, on the other hand, want to show all MIME types). Internally uses [KNewFileMenu::setSupportedMimeTypes](knewfilemenu.md#setSupportedMimeTypes)

Example:

```cpp
QStringList mimeTypes;
mimeTypes << "text/html" << "inode/directory";
dirOperator->setNewFileMenuSupportedMimeTypes(mimeTypes);
```

Note: If the list is empty, all options will be shown. Otherwise, without the MIME type inode/directory, only file options will be shown.

*See also* [KNewFileMenu::setSupportedMimeTypes](knewfilemenu.md#setSupportedMimeTypes), [newFileMenuSupportedMimeTypes](kdiroperator.md#newFileMenuSupportedMimeTypes)

### void KDirOperator::setOnlyDoubleClickSelectsFiles(bool *enable*) {#setOnlyDoubleClickSelectsFiles}

This toggles between double/single click file and directory selection mode. When argument is true, files and directories are highlighted with single click and selected (executed) with double click.

NOTE: this currently has no effect.

The default follows the single/double click system setting.

*See also* [onlyDoubleClickSelectsFiles](kdiroperator.md#onlyDoubleClickSelectsFiles)()

### \[virtual\] void KDirOperator::setShowHiddenFiles(bool *s*) {#setShowHiddenFiles}

Enables/disables showing hidden files.

*See also* [showHiddenFiles](kdiroperator.md#showHiddenFiles)()

### void KDirOperator::setSorting(*QDir::SortFlags*) {#setSorting}

Sets the way to sort files and directories.

*See also* [sorting](kdiroperator.md#sorting)()

### \[slot\] void KDirOperator::setSupportedSchemes(const QStringList &*schemes*) {#setSupportedSchemes}

Set the URL schemes that the file widget should allow navigating to.

If the returned list is empty, all schemes are supported. Examples for schemes are `"file"` or `"ftp"`.

*See also* [supportedSchemes](kdiroperator.md#supportedSchemes)(), [QFileDialog::setSupportedSchemes](https://doc.qt.io/qt-6/qfiledialog.html#supportedSchemes-prop)

### \[virtual\] void KDirOperator::setUrl(const QUrl &*url*, bool *clearforward*) {#setUrl}

Sets a new url to list.

`clearforward` specifies whether the "forward" history should be cleared.

`url` the URL to set

*See also* [url](kdiroperator.md#url)()

### \[virtual\] void KDirOperator::setViewConfig(KConfigGroup &*configGroup*) {#setViewConfig}

Sets the config object and the to be used group in [KDirOperator](kdiroperator.md). This will be used to store the view's configuration. If you don't set this, the views cannot save and restore their configuration.

Usually you call this right after [KDirOperator](kdiroperator.md) creation so that the view instantiation can make use of it already.

Note that [KDirOperator](kdiroperator.md) does NOT take ownership of that object (typically it's [KSharedConfig::openConfig](../kconfigcore/ksharedconfig.md#openConfig)() anyway.

You must not delete the [KConfig](../kconfigcore/kconfig.md) or [KConfigGroup](../kconfigcore/kconfiggroup.md) object (and master config object) before either deleting the [KDirOperator](kdiroperator.md) or calling setViewConfig(0); or something like that

*See also* [viewConfigGroup](kdiroperator.md#viewConfigGroup)

### void KDirOperator::setViewMode(KFile::FileView *viewKind*) {#setViewMode}

Set the view mode to one of the predefined modes.

*See also* [viewMode](kdiroperator.md#viewMode)(), [KFile::FileView](../kiowidgets/kfile.md#FileView-enum)

### \[protected\] void KDirOperator::setupActions() {#setupActions}

Sets up all the actions. Called from the constructor, you usually better not call this.

### \[protected\] void KDirOperator::setupMenu() {#setupMenu}

Sets up the context-menu with all the necessary actions. Called from the constructor, you usually don't need to call this.

### void KDirOperator::setupMenu(int *whichActions*) {#setupMenu-1}

Sets up the action menu.

`whichActions` is an value of OR'd ActionTypes that controls which actions to show in the action menu

### bool KDirOperator::showHiddenFiles() const {#showHiddenFiles}

Returns true when hidden files are shown or false otherwise.

*See also* [setShowHiddenFiles](kdiroperator.md#setShowHiddenFiles)()

### void KDirOperator::showOpenWithActions(bool *enable*) {#showOpenWithActions}

Call with `true` to add open-with actions to items in the view. This can be useful when you're attaching an image or text file to an email or uploading an image to some online service, and need to check the contents before going forward.

### \[protected slot\] void KDirOperator::slotCompletionMatch(const QString &*match*) {#slotCompletionMatch}

Tries to make the given `match` as current item in the view and emits completion( match )

### \[protected slot\] void KDirOperator::sortByDate() {#sortByDate}

Changes sorting to sort by date

### \[protected slot\] void KDirOperator::sortByName() {#sortByName}

Changes sorting to sort by name

### \[protected slot\] void KDirOperator::sortBySize() {#sortBySize}

Changes sorting to sort by size

### \[protected slot\] void KDirOperator::sortByType() {#sortByType}

Changes sorting to sort by date

### \[protected slot\] void KDirOperator::sortReversed() {#sortReversed}

Changes sorting to reverse sorting

### QDir::SortFlags KDirOperator::sorting() const {#sorting}

Returns the current way of sorting files and directories

*See also* [setSorting](kdiroperator.md#setSorting)()

### QStringList KDirOperator::supportedSchemes() const {#supportedSchemes}

Returns the URL schemes that the file widget should allow navigating to.

If the returned list is empty, all schemes are supported.

*See also* [setSupportedSchemes](kdiroperator.md#setSupportedSchemes)(), [QFileDialog::supportedSchemes](https://doc.qt.io/qt-6/qfiledialog.html#supportedSchemes-prop)

### \[protected slot\] void KDirOperator::toggleDirsFirst() {#toggleDirsFirst}

Toggles showing directories first / having them sorted like files.

### \[protected slot\] void KDirOperator::toggleIgnoreCase() {#toggleIgnoreCase}

Toggles case sensitive / case insensitive sorting

### \[virtual\] KIO::CopyJob \*KDirOperator::trash(const KFileItemList &*items*, QWidget \**parent*, bool *ask* = true, bool *showProgress* = true) {#trash}

Starts and returns a [KIO::CopyJob](../kiocore/kio-copyjob.md) to trash the given `items`.

`items` the list of items to be trashed `parent` the parent widget used for the confirmation dialog `ask` specifies whether a confirmation dialog should be shown `showProgress` passed to the CopyJob to show a progress dialog

### \[virtual slot\] void KDirOperator::trashSelected() {#trashSelected}

Trashes the currently selected files/directories.

This function used to take activation reason and keyboard modifiers, in order to call [deleteSelected](kdiroperator.md#deleteSelected)() if the user wanted to delete. Instead, call [deleteSelected](kdiroperator.md#deleteSelected)().

FIXME KAction Port: link [deleteSelected](kdiroperator.md#deleteSelected)() up correctly

### \[slot\] void KDirOperator::updateDir() {#updateDir}

to update the view after changing the settings

### \[signal\] void KDirOperator::updateInformation(int *files*, int *dirs*) {#updateInformation}

### \[slot\] void KDirOperator::updateSelectionDependentActions() {#updateSelectionDependentActions}

Enables/disables actions that are selection dependent. Call this e.g. when you are about to show a popup menu using some of KDirOperators actions.

### \[protected\] void KDirOperator::updateSortActions() {#updateSortActions}

Updates the sorting-related actions to comply with the current sorting

*See also* [sorting](kdiroperator.md#sorting)

### \[protected\] void KDirOperator::updateViewActions() {#updateViewActions}

Updates the view-related actions to comply with the current [KFile::FileView](../kiowidgets/kfile.md#FileView-enum)

### QUrl KDirOperator::url() const {#url}

Returns the current url

*See also* [setUrl](kdiroperator.md#setUrl)()

### \[signal\] void KDirOperator::urlEntered(*const QUrl &*) {#urlEntered}

### \[since 6.14\] bool KDirOperator::usingKeyNavigation() {#usingKeyNavigation}

@returns true if the user was using keys to navigate.

This function was introduced in Qt 6.14.

### QAbstractItemView \*KDirOperator::view() const {#view}

Returns the currently used view.

*See also* [setViewMode](kdiroperator.md#setViewMode)

### \[signal\] void KDirOperator::viewChanged(QAbstractItemView \**newView*) {#viewChanged}

Emitted whenever the current fileview is changed, either by an explicit call to [setViewMode](kdiroperator.md#setViewMode)() or by the user selecting a different view thru the GUI.

### KConfigGroup \*KDirOperator::viewConfigGroup() const {#viewConfigGroup}

Returns the group set by [setViewConfig](kdiroperator.md#setViewConfig) configuration.

### KFile::FileView KDirOperator::viewMode() const {#viewMode}

Returns the current view mode.

*See also* [setViewMode](kdiroperator.md#setViewMode)(), [KFile::FileView](../kiowidgets/kfile.md#FileView-enum)

### \[virtual\] void KDirOperator::writeConfig(KConfigGroup &*configGroup*) {#writeConfig}

Saves the current settings like sorting, simple or detailed view.

*See also* [readConfig](kdiroperator.md#readConfig), [setViewConfig](kdiroperator.md#setViewConfig)
