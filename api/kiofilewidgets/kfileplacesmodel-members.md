---
title: "List of All Members for KFilePlacesModel"
description: "Every member of KFilePlacesModel, including inherited members."
parent: "kiofilewidgets/kfileplacesmodel"
---

# List of All Members for KFilePlacesModel

This is the complete list of members for [KFilePlacesModel](kfileplacesmodel.md), including inherited members.

- [KFilePlacesModel(QObject \*)](kfileplacesmodel.md#KFilePlacesModel)
- [addPlace(const QString &, const QUrl &, const QString &, const QString &)](kfileplacesmodel.md#addPlace)
- [addPlace(const QString &, const QUrl &, const QString &, const QString &, const QModelIndex &)](kfileplacesmodel.md#addPlace-1)
- [bookmarkForIndex(const QModelIndex &) const : KBookmark](kfileplacesmodel.md#bookmarkForIndex)
- [bookmarkForUrl(const QUrl &) const : KBookmark](kfileplacesmodel.md#bookmarkForUrl)
- [closestItem(const QUrl &) const : QModelIndex](kfileplacesmodel.md#closestItem)
- [convertedUrl(const QUrl &) : QUrl](kfileplacesmodel.md#convertedUrl)
- [deviceAccessibility(const QModelIndex &) const : KFilePlacesModel::DeviceAccessibility](kfileplacesmodel.md#deviceAccessibility)
- [deviceForIndex(const QModelIndex &) const : Solid::Device](kfileplacesmodel.md#deviceForIndex)
- [editPlace(const QModelIndex &, const QString &, const QUrl &, const QString &, const QString &)](kfileplacesmodel.md#editPlace)
- [ejectActionForIndex(const QModelIndex &) const : QAction \*](kfileplacesmodel.md#ejectActionForIndex)
- [errorMessage(const QString &)](kfileplacesmodel.md#errorMessage)
- [groupHiddenChanged(KFilePlacesModel::GroupType, bool)](kfileplacesmodel.md#groupHiddenChanged)
- [groupIndexes(const KFilePlacesModel::GroupType) const : QModelIndexList](kfileplacesmodel.md#groupIndexes)
- [groupType(const QModelIndex &) const : KFilePlacesModel::GroupType](kfileplacesmodel.md#groupType)
- [hiddenCount() const : int](kfileplacesmodel.md#hiddenCount)
- [icon(const QModelIndex &) const : QIcon](kfileplacesmodel.md#icon)
- [isDevice(const QModelIndex &) const : bool](kfileplacesmodel.md#isDevice)
- [isEjectAllowed(const QModelIndex &) const : bool](kfileplacesmodel.md#isEjectAllowed)
- [isGroupHidden(const KFilePlacesModel::GroupType) const : bool](kfileplacesmodel.md#isGroupHidden)
- [isGroupHidden(const QModelIndex &) const : bool](kfileplacesmodel.md#isGroupHidden-1)
- [isHidden(const QModelIndex &) const : bool](kfileplacesmodel.md#isHidden)
- [isTeardownAllowed(const QModelIndex &) const : bool](kfileplacesmodel.md#isTeardownAllowed)
- [isTeardownOverlayRecommended(const QModelIndex &) const : bool](kfileplacesmodel.md#isTeardownOverlayRecommended)
- [movePlace(int, int) : bool](kfileplacesmodel.md#movePlace)
- [openRecentOption(const QModelIndex &) const : QAction \*](kfileplacesmodel.md#openRecentOption)
- [partitionActionForIndex(const QModelIndex &) const : QAction \*](kfileplacesmodel.md#partitionActionForIndex)
- [placeCollapsedUrl(const QUrl &) const : QString](kfileplacesmodel.md#placeCollapsedUrl)
- [refresh() const](kfileplacesmodel.md#refresh)
- [reloaded()](kfileplacesmodel.md#reloaded)
- [removePlace(const QModelIndex &) const](kfileplacesmodel.md#removePlace)
- [requestEject(const QModelIndex &)](kfileplacesmodel.md#requestEject)
- [requestSetup(const QModelIndex &)](kfileplacesmodel.md#requestSetup)
- [requestTeardown(const QModelIndex &)](kfileplacesmodel.md#requestTeardown)
- [setGroupHidden(const KFilePlacesModel::GroupType, bool)](kfileplacesmodel.md#setGroupHidden)
- [setPlaceHidden(const QModelIndex &, bool)](kfileplacesmodel.md#setPlaceHidden)
- [setSupportedSchemes(const QStringList &)](kfileplacesmodel.md#setSupportedSchemes)
- [setupDone(const QModelIndex &, bool)](kfileplacesmodel.md#setupDone)
- [setupNeeded(const QModelIndex &) const : bool](kfileplacesmodel.md#setupNeeded)
- [supportedSchemes : QStringList](kfileplacesmodel.md#supportedSchemes-prop)
- [supportedSchemes() const : QStringList](kfileplacesmodel.md#supportedSchemes)
- [supportedSchemesChanged()](kfileplacesmodel.md#supportedSchemesChanged)
- [teardownActionForIndex(const QModelIndex &) const : QAction \*](kfileplacesmodel.md#teardownActionForIndex)
- [teardownDone(const QModelIndex &, Solid::ErrorType, const QVariant &)](kfileplacesmodel.md#teardownDone)
- [text(const QModelIndex &) const : QString](kfileplacesmodel.md#text)
- [url(const QModelIndex &) const : QUrl](kfileplacesmodel.md#url)

KFilePlacesModel also inherits the members of [QAbstractItemModel](https://doc.qt.io/qt-6/qabstractitemmodel-members.html).
