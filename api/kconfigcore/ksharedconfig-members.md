---
title: "List of All Members for KSharedConfig"
description: "Every member of KSharedConfig, including inherited members."
parent: "kconfigcore/ksharedconfig"
---

# List of All Members for KSharedConfig

This is the complete list of members for [KSharedConfig](ksharedconfig.md), including inherited members.

- [accessMode() const : KConfigBase::AccessMode](kconfigbase.md#accessMode)
- [addConfigSources(const QStringList &)](kconfig.md#addConfigSources)
- [additionalConfigSources() const : QStringList](kconfig.md#additionalConfigSources)
- [checkUpdate(const QString &, const QString &)](kconfig.md#checkUpdate)
- [copyFrom(const KConfig &) const](kconfig.md#copyFrom)
- [copyTo(const QString &, KConfig \*) const : KConfig \*](kconfig.md#copyTo)
- [deleteGroup(const QString &, KConfigBase::WriteConfigFlags)](kconfigbase.md#deleteGroup)
- [entryMap(const QString &) const : QMap\<QString, QString\>](kconfig.md#entryMap)
- [group(const QString &) : KConfigGroup](kconfigbase.md#group)
- [group(const QString &) const : const KConfigGroup](kconfigbase.md#group-1)
- [groupList() const : QStringList](kconfigbase.md#groupList)
- [hasGroup(const QString &) const : bool](kconfigbase.md#hasGroup)
- [isConfigWritable(bool) : bool](kconfig.md#isConfigWritable)
- [isDirty() const : bool](kconfig.md#isDirty)
- [isGroupImmutable(const QString &) const : bool](kconfigbase.md#isGroupImmutable)
- [isImmutable() const : bool](kconfigbase.md#isImmutable)
- [locale() const : QString](kconfig.md#locale)
- [locationType() const : QStandardPaths::StandardLocation](kconfig.md#locationType)
- [mainConfigName() : QString](kconfig.md#mainConfigName)
- [markAsClean()](kconfigbase.md#markAsClean)
- [name() const : QString](kconfig.md#name)
- [openConfig(const QString &, KConfig::OpenFlags, QStandardPaths::StandardLocation) : KSharedConfig::Ptr](ksharedconfig.md#openConfig)
- [openFlags() const : KConfig::OpenFlags](kconfig.md#openFlags)
- [openStateConfig(const QString &) : KSharedConfig::Ptr](ksharedconfig.md#openStateConfig)
- [readDefaults() const : bool](kconfig.md#readDefaults)
- [reparseConfiguration()](kconfig.md#reparseConfiguration)
- [setLocale(const QString &) : bool](kconfig.md#setLocale)
- [setMainConfigName(const QString &)](kconfig.md#setMainConfigName)
- [setReadDefaults(bool)](kconfig.md#setReadDefaults)
- [sync() : bool](kconfigbase.md#sync)

KSharedConfig also inherits the members of [QSharedData](https://doc.qt.io/qt-6/qshareddata-members.html).
