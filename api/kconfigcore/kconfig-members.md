---
title: "List of All Members for KConfig"
description: "Every member of KConfig, including inherited members."
parent: "kconfigcore/kconfig"
---

# List of All Members for KConfig

This is the complete list of members for [KConfig](kconfig.md), including inherited members.

- [KConfig(const QString &, KConfig::OpenFlags, QStandardPaths::StandardLocation)](kconfig.md#KConfig-1)
- [KConfig(const std::shared\_ptr\<QIODevice\> &, KConfig::OpenFlags)](kconfig.md#KConfig)
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
- [openFlags() const : KConfig::OpenFlags](kconfig.md#openFlags)
- [readDefaults() const : bool](kconfig.md#readDefaults)
- [reparseConfiguration()](kconfig.md#reparseConfiguration)
- [setLocale(const QString &) : bool](kconfig.md#setLocale)
- [setMainConfigName(const QString &)](kconfig.md#setMainConfigName)
- [setReadDefaults(bool)](kconfig.md#setReadDefaults)
- [sync() : bool](kconfigbase.md#sync)
