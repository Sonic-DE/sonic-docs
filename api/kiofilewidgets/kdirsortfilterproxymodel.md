---
title: "KDirSortFilterProxyModel Class"
description: "Acts as proxy model for KDirModel to sort and filter KFileItems."
---

# KDirSortFilterProxyModel Class

Acts as proxy model for [KDirModel](../kiowidgets/kdirmodel.md) to sort and filter KFileItems. [More...](#details)

- **Header:** `#include <KDirSortFilterProxyModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOFileWidgets)`

[List of all members, including inherited members](kdirsortfilterproxymodel-members.md)

## Public Functions

- [bool canFetchMore(const QModelIndex &parent) const](#canFetchMore)
- [bool hasChildren(const QModelIndex &parent = QModelIndex()) const](#hasChildren)
- [void setSortFoldersFirst(bool foldersFirst)](#setSortFoldersFirst)
- [void setSortHiddenFilesLast(bool hiddenFilesLast)](#setSortHiddenFilesLast)
- [bool sortFoldersFirst() const](#sortFoldersFirst)
- [bool sortHiddenFilesLast() const](#sortHiddenFilesLast)
- [Qt::DropActions supportedDragOptions() const](#supportedDragOptions)

## Static Public Members

- [int pointsForPermissions(const QFileInfo &info)](#pointsForPermissions)

## Detailed Description {#details}

A natural sorting is done. This means that items like:

- item\_10.png
- item\_1.png
- item\_2.png

are sorted like

- item\_1.png
- item\_2.png
- item\_10.png

Don't use it with non-[KDirModel](../kiowidgets/kdirmodel.md) derivatives.

## Member Function Documentation {#member-function-documentation}

### \[override virtual\] bool KDirSortFilterProxyModel::canFetchMore(const QModelIndex &*parent*) const {#canFetchMore}

Returns true for 'empty' directories so they can be populated later.

### \[override virtual\] bool KDirSortFilterProxyModel::hasChildren(const QModelIndex &*parent* = QModelIndex()) const {#hasChildren}

Returns true for directories.

### \[static\] int KDirSortFilterProxyModel::pointsForPermissions(const QFileInfo &*info*) {#pointsForPermissions}

Returns the permissions in "points". This is useful for sorting by permissions.

### void KDirSortFilterProxyModel::setSortFoldersFirst(bool *foldersFirst*) {#setSortFoldersFirst}

Choose if files and folders are sorted separately (with folders first) or not.

*See also* [sortFoldersFirst](kdirsortfilterproxymodel.md#sortFoldersFirst)()

### void KDirSortFilterProxyModel::setSortHiddenFilesLast(bool *hiddenFilesLast*) {#setSortHiddenFilesLast}

Sets a separate sorting with hidden files and folders last (true) or not (false).

*See also* [sortHiddenFilesLast](kdirsortfilterproxymodel.md#sortHiddenFilesLast)()

### bool KDirSortFilterProxyModel::sortFoldersFirst() const {#sortFoldersFirst}

Returns if files and folders are sorted separately (with folders first) or not.

*See also* [setSortFoldersFirst](kdirsortfilterproxymodel.md#setSortFoldersFirst)()

### bool KDirSortFilterProxyModel::sortHiddenFilesLast() const {#sortHiddenFilesLast}

*See also* [setSortHiddenFilesLast](kdirsortfilterproxymodel.md#setSortHiddenFilesLast)()

### Qt::DropActions KDirSortFilterProxyModel::supportedDragOptions() const {#supportedDragOptions}
