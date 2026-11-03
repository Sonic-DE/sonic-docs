---
title: "KFilePreviewGenerator Class"
description: "Generates previews for files of an item view."
---

# KFilePreviewGenerator Class

Generates previews for files of an item view. [More...](#details)

- **Header:** `#include <KFilePreviewGenerator>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOFileWidgets)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kfilepreviewgenerator-members.md)

## Public Functions

- [KFilePreviewGenerator(QAbstractItemView \*parent)](#KFilePreviewGenerator)
- [QStringList enabledPlugins() const](#enabledPlugins)
- [bool isPreviewShown() const](#isPreviewShown)
- [void setEnabledPlugins(const QStringList &list)](#setEnabledPlugins)
- [void setPreviewShown(bool show)](#setPreviewShown)

## Public Slots

- [void cancelPreviews()](#cancelPreviews)
- [void updateIcons()](#updateIcons)

## Detailed Description {#details}

Per default a preview is generated for each item. Additionally the clipboard is checked for cut items. The icon state for cut items gets dimmed automatically.

The following strategy is used when creating previews:

- The previews for currently visible items are created before the previews for invisible items.
- If the user changes the visible area by using the scrollbars, all pending previews get paused. As soon as the user stays on the same position for a short delay, the previews are resumed. Also in this case the previews for the visible items are generated first.

## Member Function Documentation {#member-function-documentation}

### KFilePreviewGenerator::KFilePreviewGenerator(QAbstractItemView \**parent*) {#KFilePreviewGenerator}

`parent` Item view containing the file items where previews should be generated. It is mandatory that the item view specifies an icon size by [QAbstractItemView::setIconSize](https://doc.qt.io/qt-6/qabstractitemview.html#iconSize-prop)() and that the model of the view (or the source model of the proxy model) is an instance of [KDirModel](../kiowidgets/kdirmodel.md). Otherwise no previews will be generated.

### \[slot\] void KFilePreviewGenerator::cancelPreviews() {#cancelPreviews}

Cancels all pending previews.

### QStringList KFilePreviewGenerator::enabledPlugins() const {#enabledPlugins}

Returns the list of enabled thumbnail plugins.

*See also* [setEnabledPlugins](kfilepreviewgenerator.md#setEnabledPlugins)

### bool KFilePreviewGenerator::isPreviewShown() const {#isPreviewShown}

### void KFilePreviewGenerator::setEnabledPlugins(const QStringList &*list*) {#setEnabledPlugins}

Sets the list of enabled thumbnail plugins. Per default all plugins enabled in the [KConfigGroup](../kconfigcore/kconfiggroup.md) "PreviewSettings" are used.

Note that this method doesn't cause already generated previews to be regenerated.

For a list of available plugins, call [KIO::PreviewJob::availableThumbnailerPlugins](../kiogui/kio-previewjob.md#availableThumbnailerPlugins)().

*See also* [enabledPlugins](kfilepreviewgenerator.md#enabledPlugins)

### void KFilePreviewGenerator::setPreviewShown(bool *show*) {#setPreviewShown}

If `show` is set to true, a preview is generated for each item. If `show` is false, the MIME type icon of the item is shown instead. Per default showing the preview is turned on. Note that it is mandatory that the item view specifies an icon size by [QAbstractItemView::setIconSize](https://doc.qt.io/qt-6/qabstractitemview.html#iconSize-prop)(), otherwise [KFilePreviewGenerator::isPreviewShown](kfilepreviewgenerator.md#isPreviewShown)() will always return false.

*See also* [isPreviewShown](kfilepreviewgenerator.md#isPreviewShown)()

### \[slot\] void KFilePreviewGenerator::updateIcons() {#updateIcons}

Updates the icons for all items. Usually it is only necessary to invoke this method when the icon size of the abstract item view has been changed by [QAbstractItemView::setIconSize](https://doc.qt.io/qt-6/qabstractitemview.html#iconSize-prop)(). Note that this method should also be invoked if previews have been turned off, as the icons for cut items must be updated when the icon size has changed.
