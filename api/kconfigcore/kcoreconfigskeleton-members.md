---
title: "List of All Members for KCoreConfigSkeleton"
description: "Every member of KCoreConfigSkeleton, including inherited members."
parent: "kconfigcore/kcoreconfigskeleton"
---

# List of All Members for KCoreConfigSkeleton

This is the complete list of members for [KCoreConfigSkeleton](kcoreconfigskeleton.md), including inherited members.

- [KCoreConfigSkeleton(KSharedConfig::Ptr, QObject \*)](kcoreconfigskeleton.md#KCoreConfigSkeleton)
- [KCoreConfigSkeleton(const QString &, QObject \*)](kcoreconfigskeleton.md#KCoreConfigSkeleton-1)
- [KCoreConfigSkeleton(std::unique\_ptr\<KConfig\>, KCoreConfigSkeleton::DisambiguateConstructor, QObject \*)](kcoreconfigskeleton.md#KCoreConfigSkeleton-2)
- [addItem(KConfigSkeletonItem \*, const QString &)](kcoreconfigskeleton.md#addItem)
- [addItemBool(const QString &, bool &, bool, const QString &) : KCoreConfigSkeleton::ItemBool \*](kcoreconfigskeleton.md#addItemBool)
- [addItemDateTime(const QString &, QDateTime &, const QDateTime &, const QString &) : KCoreConfigSkeleton::ItemDateTime \*](kcoreconfigskeleton.md#addItemDateTime)
- [addItemDouble(const QString &, double &, double, const QString &) : KCoreConfigSkeleton::ItemDouble \*](kcoreconfigskeleton.md#addItemDouble)
- [addItemInt(const QString &, qint32 &, qint32, const QString &) : KCoreConfigSkeleton::ItemInt \*](kcoreconfigskeleton.md#addItemInt)
- [addItemIntList(const QString &, QList\<int\> &, const QList\<int\> &, const QString &) : KCoreConfigSkeleton::ItemIntList \*](kcoreconfigskeleton.md#addItemIntList)
- [addItemLongLong(const QString &, qint64 &, qint64, const QString &) : KCoreConfigSkeleton::ItemLongLong \*](kcoreconfigskeleton.md#addItemLongLong)
- [addItemPassword(const QString &, QString &, const QString &, const QString &) : KCoreConfigSkeleton::ItemPassword \*](kcoreconfigskeleton.md#addItemPassword)
- [addItemPath(const QString &, QString &, const QString &, const QString &) : KCoreConfigSkeleton::ItemPath \*](kcoreconfigskeleton.md#addItemPath)
- [addItemPathList(const QString &, QList\<QString\> &, const QList\<QString\> &, const QString &) : KCoreConfigSkeleton::ItemPathList \*](kcoreconfigskeleton.md#addItemPathList)
- [addItemPoint(const QString &, QPoint &, const QPoint &, const QString &) : KCoreConfigSkeleton::ItemPoint \*](kcoreconfigskeleton.md#addItemPoint)
- [addItemPointF(const QString &, QPointF &, const QPointF &, const QString &) : KCoreConfigSkeleton::ItemPointF \*](kcoreconfigskeleton.md#addItemPointF)
- [addItemProperty(const QString &, QVariant &, const QVariant &, const QString &) : KCoreConfigSkeleton::ItemProperty \*](kcoreconfigskeleton.md#addItemProperty)
- [addItemRect(const QString &, QRect &, const QRect &, const QString &) : KCoreConfigSkeleton::ItemRect \*](kcoreconfigskeleton.md#addItemRect)
- [addItemRectF(const QString &, QRectF &, const QRectF &, const QString &) : KCoreConfigSkeleton::ItemRectF \*](kcoreconfigskeleton.md#addItemRectF)
- [addItemSize(const QString &, QSize &, const QSize &, const QString &) : KCoreConfigSkeleton::ItemSize \*](kcoreconfigskeleton.md#addItemSize)
- [addItemSizeF(const QString &, QSizeF &, const QSizeF &, const QString &) : KCoreConfigSkeleton::ItemSizeF \*](kcoreconfigskeleton.md#addItemSizeF)
- [addItemString(const QString &, QString &, const QString &, const QString &) : KCoreConfigSkeleton::ItemString \*](kcoreconfigskeleton.md#addItemString)
- [addItemStringList(const QString &, QStringList &, const QStringList &, const QString &) : KCoreConfigSkeleton::ItemStringList \*](kcoreconfigskeleton.md#addItemStringList)
- [addItemTime(const QString &, QTime &, QTime, const QString &) : KCoreConfigSkeleton::ItemTime \*](kcoreconfigskeleton.md#addItemTime)
- [addItemUInt(const QString &, quint32 &, quint32, const QString &) : KCoreConfigSkeleton::ItemUInt \*](kcoreconfigskeleton.md#addItemUInt)
- [addItemULongLong(const QString &, quint64 &, quint64, const QString &) : KCoreConfigSkeleton::ItemULongLong \*](kcoreconfigskeleton.md#addItemULongLong)
- [addItemUrlList(const QString &, QList\<QUrl\> &, const QList\<QUrl\> &, const QString &) : KCoreConfigSkeleton::ItemUrlList \*](kcoreconfigskeleton.md#addItemUrlList)
- [clearItems()](kcoreconfigskeleton.md#clearItems)
- [config() : KConfig \*](kcoreconfigskeleton.md#config)
- [config() const : const KConfig \*](kcoreconfigskeleton.md#config-1)
- [configChanged()](kcoreconfigskeleton.md#configChanged)
- [currentGroup() const : QString](kcoreconfigskeleton.md#currentGroup)
- [findItem(const QString &) const : KConfigSkeletonItem \*](kcoreconfigskeleton.md#findItem)
- [isDefaults() const : bool](kcoreconfigskeleton.md#isDefaults)
- [isImmutable(const QString &) const : bool](kcoreconfigskeleton.md#isImmutable)
- [isSaveNeeded() const : bool](kcoreconfigskeleton.md#isSaveNeeded)
- [items() const : KConfigSkeletonItem::List](kcoreconfigskeleton.md#items)
- [load()](kcoreconfigskeleton.md#load)
- [read()](kcoreconfigskeleton.md#read)
- [removeItem(const QString &)](kcoreconfigskeleton.md#removeItem)
- [save() : bool](kcoreconfigskeleton.md#save)
- [setConfig(std::unique\_ptr\<KConfig\>)](kcoreconfigskeleton.md#setConfig)
- [setCurrentGroup(const QString &)](kcoreconfigskeleton.md#setCurrentGroup)
- [setDefaults()](kcoreconfigskeleton.md#setDefaults)
- [setSharedConfig(KSharedConfig::Ptr)](kcoreconfigskeleton.md#setSharedConfig)
- [sharedConfig() const : KSharedConfig::Ptr](kcoreconfigskeleton.md#sharedConfig)
- [useDefaults(bool) : bool](kcoreconfigskeleton.md#useDefaults)
- [usrRead()](kcoreconfigskeleton.md#usrRead)
- [usrSave() : bool](kcoreconfigskeleton.md#usrSave)
- [usrSetDefaults()](kcoreconfigskeleton.md#usrSetDefaults)
- [usrUseDefaults(bool) : bool](kcoreconfigskeleton.md#usrUseDefaults)

KCoreConfigSkeleton also inherits the members of [QObject](https://doc.qt.io/qt-6/qobject-members.html).
