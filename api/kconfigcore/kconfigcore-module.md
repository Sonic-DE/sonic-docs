---
title: "KConfigCore C++ Classes"
description: "Persistent platform-independent application settings."
---

# KConfigCore C++ Classes

Persistent platform-independent application settings. [More...](#details)

## Classes {#classes}

- [KAuthorized](kauthorized.md): Used for checking whether actions are allowed for a user.
- [KConfig](kconfig.md): The central class of the KDE configuration data system.
- [KConfigBase](kconfigbase.md): Interface to interact with configuration.
- [KConfigGroup](kconfiggroup.md): A class for one specific group in a KConfig object.
- [KConfigSkeletonGenericItem](kconfigskeletongenericitem.md): Base class for storing a preferences setting of type T.
- [KConfigSkeletonItem](kconfigskeletonitem.md): Class for storing a preferences setting.
- [KConfigWatcher](kconfigwatcher.md): Watches for configuration changes.
- [KCoreConfigSkeleton](kcoreconfigskeleton.md): Class for handling preferences settings for an application.
- [KCoreConfigSkeleton::ItemBool](kcoreconfigskeleton-itembool.md): Class for handling a bool preferences item.
- [KCoreConfigSkeleton::ItemDateTime](kcoreconfigskeleton-itemdatetime.md): Class for handling a QDateTime preferences item.
- [KCoreConfigSkeleton::ItemDouble](kcoreconfigskeleton-itemdouble.md): Class for handling a floating point preference item.
- [KCoreConfigSkeleton::ItemEnum](kcoreconfigskeleton-itemenum.md): Class for handling enums.
- [KCoreConfigSkeleton::ItemEnum::Choice](kcoreconfigskeleton-itemenum-choice.md): Provides strongly typed enum options for use with KConfigXT.
- [KCoreConfigSkeleton::ItemInt](kcoreconfigskeleton-itemint.md): Class for handling a 32-bit integer preferences item.
- [KCoreConfigSkeleton::ItemIntList](kcoreconfigskeleton-itemintlist.md): Class for handling an integer list preferences item.
- [KCoreConfigSkeleton::ItemLongLong](kcoreconfigskeleton-itemlonglong.md): Class for handling a 64-bit integer preferences item.
- [KCoreConfigSkeleton::ItemPassword](kcoreconfigskeleton-itempassword.md): Class for handling a password preferences item.
- [KCoreConfigSkeleton::ItemPath](kcoreconfigskeleton-itempath.md): Class for handling a path preferences item.
- [KCoreConfigSkeleton::ItemPathList](kcoreconfigskeleton-itempathlist.md): Class for handling a path list preferences item.
- [KCoreConfigSkeleton::ItemPoint](kcoreconfigskeleton-itempoint.md): Class for handling a QPoint preferences item.
- [KCoreConfigSkeleton::ItemPointF](kcoreconfigskeleton-itempointf.md): Class for handling a QPointF preferences item.
- [KCoreConfigSkeleton::ItemProperty](kcoreconfigskeleton-itemproperty.md): Class for handling a QVariant preferences item.
- [KCoreConfigSkeleton::ItemRect](kcoreconfigskeleton-itemrect.md): Class for handling a QRect preferences item.
- [KCoreConfigSkeleton::ItemRectF](kcoreconfigskeleton-itemrectf.md): Class for handling a QRectF preferences item.
- [KCoreConfigSkeleton::ItemSize](kcoreconfigskeleton-itemsize.md): Class for handling a QSize preferences item.
- [KCoreConfigSkeleton::ItemSizeF](kcoreconfigskeleton-itemsizef.md): Class for handling a QSizeF preferences item.
- [KCoreConfigSkeleton::ItemString](kcoreconfigskeleton-itemstring.md): Class for handling a string preferences item.
- [KCoreConfigSkeleton::ItemStringList](kcoreconfigskeleton-itemstringlist.md): Class for handling a string list preferences item.
- [KCoreConfigSkeleton::ItemTime](kcoreconfigskeleton-itemtime.md): Class for handling a QTime preferences item.
- [KCoreConfigSkeleton::ItemUInt](kcoreconfigskeleton-itemuint.md): Class for handling an unsigned 32-bit integer preferences item.
- [KCoreConfigSkeleton::ItemULongLong](kcoreconfigskeleton-itemulonglong.md): Class for handling unsigned 64-bit integer preferences item.
- [KCoreConfigSkeleton::ItemUrl](kcoreconfigskeleton-itemurl.md): Class for handling a url preferences item.
- [KCoreConfigSkeleton::ItemUrlList](kcoreconfigskeleton-itemurllist.md): Class for handling a url list preferences item.
- [KDesktopFile](kdesktopfile.md)
- [KDesktopFileAction](kdesktopfileaction.md): Class for representing an Action of a desktop file.
- [KEMailSettings](kemailsettings.md): Access to e-mail settings.
- [KPropertySkeletonItem](kpropertyskeletonitem.md): Class for proxying a QObject property as a preferences setting.
- [KSharedConfig](ksharedconfig.md): KConfig variant using shared memory.

## Detailed Description {#details}

[KConfigCore](kconfigcore-module.md) provides access to the configuration files themselves. It features:

- Code generation: describe your configuration in an XML file, and use kconfig\_compiler to generate classes that read and write configuration entries.
- Cascading configuration files (global settings overridden by local settings).
- Optional shell expansion support.
- The ability to lock down configuration options.
