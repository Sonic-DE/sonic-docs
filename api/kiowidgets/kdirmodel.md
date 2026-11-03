---
title: "KDirModel Class"
description: "A model for a KIO-based directory tree."
---

# KDirModel Class

A model for a KIO-based directory tree. [More...](#details)

- **Header:** `#include <KDirModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [QAbstractItemModel](https://doc.qt.io/qt-6/qabstractitemmodel.html)

[List of all members, including inherited members](kdirmodel-members.md)

## Public Types

- [enum KDirModel::AdditionalRoles](#AdditionalRoles-enum)
- [enum KDirModel::DropsAllowedFlag](#DropsAllowedFlag-enum)
- [enum KDirModel::ModelColumns](#ModelColumns-enum)
- [enum KDirModel::OpenUrlFlag](#OpenUrlFlag-enum)
- [\[anonymous\] enum](#anonymous-kdirmodel-h-168-enum)

## Public Functions

- [KDirModel(QObject \*parent = nullptr)](#KDirModel)
- [bool canFetchMore(const QModelIndex &parent) const](#canFetchMore)
- [void clearAllPreviews()](#clearAllPreviews)
- [KDirLister \*dirLister() const](#dirLister)
- [void expandToUrl(const QUrl &url)](#expandToUrl)
- [void fetchMore(const QModelIndex &parent)](#fetchMore)
- [bool hasChildren(const QModelIndex &parent = QModelIndex()) const](#hasChildren)
- [QVariant headerData(int section, Qt::Orientation orientation, int role = Qt::DisplayRole) const](#headerData)
- [QModelIndex indexForItem(const KFileItem &) const](#indexForItem)
- [QModelIndex indexForUrl(const QUrl &url) const](#indexForUrl)
- [void itemChanged(const QModelIndex &index)](#itemChanged)
- [KFileItem itemForIndex(const QModelIndex &index) const](#itemForIndex)
- [bool jobTransfersVisible() const](#jobTransfersVisible)
- [void openUrl(const QUrl &url, KDirModel::OpenUrlFlags flags = NoFlags)](#openUrl)
- [void requestSequenceIcon(const QModelIndex &index, int sequenceIndex)](#requestSequenceIcon)
- [bool setData(const QModelIndex &index, const QVariant &value, int role = Qt::EditRole)](#setData)
- [void setDirLister(KDirLister \*dirLister)](#setDirLister)
- [void setDropsAllowed(KDirModel::DropsAllowed dropsAllowed)](#setDropsAllowed)
- [void setJobTransfersVisible(bool show)](#setJobTransfersVisible)
- [void sort(int column, Qt::SortOrder order = Qt::AscendingOrder)](#sort)

## Signals

- [void expand(const QModelIndex &index)](#expand)
- [void needSequenceIcon(const QModelIndex &index, int sequenceIndex)](#needSequenceIcon)

## Static Public Members

- [QList\<QUrl\> simplifiedUrlList(const QList\<QUrl\> &urls)](#simplifiedUrlList)

## Detailed Description {#details}

[KDirModel](kdirmodel.md) implements the [QAbstractItemModel](https://doc.qt.io/qt-6/qabstractitemmodel.html) interface (for use with Qt's model/view widgets) around the directory listing for one directory or a tree of directories.

Note that there are some cases when using QPersistentModelIndexes from this model will not give expected results. QPersistentIndexes will remain valid and updated if its siblings are added or removed. However, if the QPersistentIndex or one of its ancestors is moved, the QPersistentIndex will become invalid. For example, if a file or directory is renamed after storing a [QPersistentModelIndex](https://doc.qt.io/qt-6/qpersistentmodelindex.html) for it, the index (along with any stored children) will become invalid even though it is still in the model. The reason for this is that moves of files and directories are treated as separate insert and remove actions.

*See also* [KDirSortFilterProxyModel](../kiofilewidgets/kdirsortfilterproxymodel.md)

## Member Type Documentation {#member-type-documentation}

### enum KDirModel::AdditionalRoles {#AdditionalRoles-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KDirModel::FileItemRole` | `0x07A263FF` | Returns the [KFileItem](../kiocore/kfileitem.md) for a given index. roleName is "fileItem". |
| `KDirModel::ChildCountRole` | `0x2C4D0A40` | Returns the number of items in a directory, or [ChildCountUnknown](kdirmodel.md#anonymous-kdirmodel-h-168-enum). roleName is "childCount". |
| `KDirModel::HasJobRole` | `0x01E555A5` | Returns whether or not there is a job on an item (file/directory). roleName is "hasJob". |
| `KDirModel::HandleSequencesRole` | `0x1E642272` |   |

### enum KDirModel::DropsAllowedFlag {#DropsAllowedFlag-enum}

**flags KDirModel::DropsAllowed**

| Constant | Value |   |
| --- | --- | --- |
| `KDirModel::NoDrops` | `0` |   |
| `KDirModel::DropOnDirectory` | `1` | Allow drops on any directory |
| `KDirModel::DropOnAnyFile` | `2` | Allow drops on any file |
| `KDirModel::DropOnLocalExecutable` | `4` | Allow drops on local executables, shell scripts and desktop files. Can be used with DropOnDirectory. |

The `DropsAllowed` type is a typedef for `QFlags<DropsAllowedFlag>. `It stores an OR combination of `DropsAllowedFlag` values.

### enum KDirModel::ModelColumns {#ModelColumns-enum}

Useful "default" columns. Views can use a proxy to have more control over this.

| Constant |   |
| --- | --- |
| `KDirModel::Name` | `0` |
| `KDirModel::Size` | `1` |
| `KDirModel::ModifiedTime` | `2` |
| `KDirModel::Permissions` | `3` |
| `KDirModel::Owner` | `4` |
| `KDirModel::Group` | `5` |
| `KDirModel::Type` | `6` |
| `KDirModel::ColumnCount` | `7` |

### enum KDirModel::OpenUrlFlag {#OpenUrlFlag-enum}

**flags KDirModel::OpenUrlFlags**

Flags for the [openUrl](kdirmodel.md#openUrl)() method

| Constant | Value | Description |
| --- | --- | --- |
| `KDirModel::NoFlags` | `0x0` | No additional flags specified. |
| `KDirModel::Reload` | `0x1` | Indicates whether to use the cache or to reread the directory from the disk. Use only when opening a dir not yet listed by our [dirLister](kdirmodel.md#dirLister)() without using the cache. Otherwise use [dirLister](kdirmodel.md#dirLister)()-\>updateDirectory(). |
| `KDirModel::ShowRoot` | `0x2` | Display a root node for the URL being opened. |

The `OpenUrlFlags` type is a typedef for `QFlags<OpenUrlFlag>. `It stores an OR combination of `OpenUrlFlag` values.

### \[anonymous\] enum {#anonymous-kdirmodel-h-168-enum}

Possible return value for data([ChildCountRole](kdirmodel.md#AdditionalRoles-enum)), meaning the item isn't a directory, or we haven't calculated its child count yet

| Constant |   |
| --- | --- |
| `KDirModel::ChildCountUnknown` | `-1` |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KDirModel::KDirModel(QObject \**parent* = nullptr) {#KDirModel}

`parent` parent qobject

### \[override virtual\] bool KDirModel::canFetchMore(const QModelIndex &*parent*) const {#canFetchMore}

Reimplements: [QAbstractItemModel::canFetchMore(const QModelIndex &parent) const](https://doc.qt.io/qt-6/qabstractitemmodel.html#canFetchMore).

Returns `true` for empty directories.

### \[invokable\] void KDirModel::clearAllPreviews() {#clearAllPreviews}

Forget all previews (optimization for turning previews off). The items will again have their default appearance (not controlled by the model).

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### KDirLister \*KDirModel::dirLister() const {#dirLister}

Return the directory lister used by this model.

*See also* [setDirLister](kdirmodel.md#setDirLister)()

### \[signal\] void KDirModel::expand(const QModelIndex &*index*) {#expand}

Emitted for each subdirectory that is a parent of a url passed to [expandToUrl](kdirmodel.md#expandToUrl) This allows to asynchronously open a tree view down to a given directory. Also emitted for the final file, if [expandToUrl](kdirmodel.md#expandToUrl) is called with a file (for instance so that it can be selected).

### \[invokable\] void KDirModel::expandToUrl(const QUrl &*url*) {#expandToUrl}

Lists subdirectories using [fetchMore](kdirmodel.md#fetchMore)() as needed until the given url exists in the model.

When the model is used by a treeview, call KDirLister::openUrl with the base url of the tree, then the treeview will take care of calling [fetchMore](kdirmodel.md#fetchMore)() when the user opens directories. However if you want the tree to show a given URL (i.e. open the tree recursively until that URL), call expandToUrl(). Note that this is asynchronous; the necessary listing of subdirectories will take time so the model will not immediately have this url available. The model emits the signal [expand](kdirmodel.md#expand)() when an index has become available; this can be connected to the treeview in order to let it open that index.

`url` the url of a subdirectory of the directory model (or a file in a subdirectory)

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[override virtual\] void KDirModel::fetchMore(const QModelIndex &*parent*) {#fetchMore}

Reimplements: [QAbstractItemModel::fetchMore(const QModelIndex &parent)](https://doc.qt.io/qt-6/qabstractitemmodel.html#fetchMore).

### \[override virtual\] bool KDirModel::hasChildren(const QModelIndex &*parent* = QModelIndex()) const {#hasChildren}

Reimplements: [QAbstractItemModel::hasChildren(const QModelIndex &parent) const](https://doc.qt.io/qt-6/qabstractitemmodel.html#hasChildren).

Returns `true` for directories

### \[override virtual\] QVariant KDirModel::headerData(int *section*, Qt::Orientation *orientation*, int *role* = Qt::DisplayRole) const {#headerData}

Reimplements: [QAbstractItemModel::headerData(int section, Qt::Orientation orientation, int role) const](https://doc.qt.io/qt-6/qabstractitemmodel.html#headerData).

Returns the column titles.

### \[invokable\] QModelIndex KDirModel::indexForItem(*const KFileItem &*) const {#indexForItem}

Return the index for a given kfileitem. This can be slow.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] QModelIndex KDirModel::indexForUrl(const QUrl &*url*) const {#indexForUrl}

Return the index for a given url. This can be slow.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void KDirModel::itemChanged(const QModelIndex &*index*) {#itemChanged}

Notify the model that the item at this index has changed. For instance because its mimetype was resolved. This makes the model emit its dataChanged signal at this index, so that views repaint. Note that for most things (renaming, changing size etc.), [KDirLister](kdirlister.md)'s signals tell the model already.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### KFileItem KDirModel::itemForIndex(const QModelIndex &*index*) const {#itemForIndex}

Return the fileitem for a given index. This is O(1), i.e. fast.

### bool KDirModel::jobTransfersVisible() const {#jobTransfersVisible}

Returns whether or not displaying job transfers has been enabled.

*See also* [setJobTransfersVisible](kdirmodel.md#setJobTransfersVisible)()

### \[signal\] void KDirModel::needSequenceIcon(const QModelIndex &*index*, int *sequenceIndex*) {#needSequenceIcon}

Emitted when another icon sequence index is requested

`index` Index of the item that should get another icon

`sequenceIndex` Index in the sequence. If it is zero, the standard icon should be assigned. For higher indices, arbitrary different meaningful icons should be generated. This is usually slowly counted up while the user hovers the icon. If no meaningful alternative icons can be generated, this should be ignored.

### \[invokable\] void KDirModel::openUrl(const QUrl &*url*, KDirModel::OpenUrlFlags *flags* = NoFlags) {#openUrl}

Display the contents of `url` in the model.

Apart from the support for the [ShowRoot](kdirmodel.md#OpenUrlFlag-enum) flag, this is equivalent to [dirLister](kdirmodel.md#dirLister)()-\>openUrl(url, flags)

`url` the URL of the directory whose contents should be listed. Unless [ShowRoot](kdirmodel.md#OpenUrlFlag-enum) is set, the item for this directory will NOT be shown, the model starts at its children.

`flags` see [OpenUrlFlag](kdirmodel.md#OpenUrlFlag-enum)

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### void KDirModel::requestSequenceIcon(const QModelIndex &*index*, int *sequenceIndex*) {#requestSequenceIcon}

This emits the [needSequenceIcon](kdirmodel.md#needSequenceIcon) signal, requesting another sequence icon

If there is a [KFilePreviewGenerator](../kiofilewidgets/kfilepreviewgenerator.md) attached to this model, that generator will care about creating another preview.

`index` Index of the item that should get another icon

`sequenceIndex` Index in the sequence. If it is zero, the standard icon will be assigned. For higher indices, arbitrary different meaningful icons will be generated.

### \[override virtual\] bool KDirModel::setData(const QModelIndex &*index*, const QVariant &*value*, int *role* = Qt::EditRole) {#setData}

Reimplements: [QAbstractItemModel::setData(const QModelIndex &index, const QVariant &value, int role)](https://doc.qt.io/qt-6/qabstractitemmodel.html#setData).

Call this to set a new icon, e.g. a preview

### void KDirModel::setDirLister(KDirLister \**dirLister*) {#setDirLister}

Set the directory lister to use by this model, instead of the default [KDirLister](kdirlister.md) created internally. The model takes ownership.

*See also* [dirLister](kdirmodel.md#dirLister)()

### \[invokable\] void KDirModel::setDropsAllowed(KDirModel::DropsAllowed *dropsAllowed*) {#setDropsAllowed}

Set whether dropping onto items should be allowed, and for which kind of item Drops are disabled by default.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### void KDirModel::setJobTransfersVisible(bool *show*) {#setJobTransfersVisible}

Enable/Disable the displaying of an animated overlay that is shown for any destination urls (in the view). When enabled, the animations (if any) will be drawn automatically.

Only the files/folders that are visible and have jobs associated with them will display the animation. You would likely not want this enabled if you perform some kind of custom painting that takes up a whole item, and will just make this(and what you paint) look funky.

Default is disabled.

Note: [KFileItemDelegate](kfileitemdelegate.md) needs to have it's method called with the same value, when you make the call to this method.

*See also* [jobTransfersVisible](kdirmodel.md#jobTransfersVisible)()

### \[static\] QList\<QUrl\> KDirModel::simplifiedUrlList(const QList\<QUrl\> &*urls*) {#simplifiedUrlList}

Remove urls from the list if an ancestor is present on the list. This can be used to delete only the ancestor url and skip a potential error of a non-existent url.

For example, for a list of "/home/foo/a", "/home/foo/a/a.txt", "/home/foo/a/a/a.txt", "/home/foo/a/b/b.txt", "home/foo/b/b.txt", this method will return the list "/home/foo/a", "/home/foo/b/b.txt".

Returns the list `urls` without parented urls inside.

### \[override virtual\] void KDirModel::sort(int *column*, Qt::SortOrder *order* = Qt::AscendingOrder) {#sort}

Reimplements: [QAbstractItemModel::sort(int column, Qt::SortOrder order)](https://doc.qt.io/qt-6/qabstractitemmodel.html#sort).

Not implemented.

*See also* [KDirSortFilterProxyModel](../kiofilewidgets/kdirsortfilterproxymodel.md)
