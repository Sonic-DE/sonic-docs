---
title: Introduction to KConfig
description: An overview of the KConfig classes and how to use them in your application code.
source_url: https://develop.kde.org/docs/features/configuration/introduction/
source_authors: [Alexander Lohnau, Andrey Butirsky, Carl Schwan, Chris Holland, Mikhail Zolotukhin, Nicolas Fella, Thiago Sueto, Tobias Fella]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-frameworks-settings (KConfigCore source and API reference), sonic-interface-libraries (Plasma::Applet::immutability)
---

# Introduction to KConfig

This page looks at SonicDE's configuration system from an application developer's point of view: first its design, then the classes an application uses one by one, and finally Kiosk (lockdown and user and group profiles).

KConfig is part of `sonic-frameworks-settings`, which provides the `KF6Config` CMake package. Its API reference is in [KConfigCore](/docs/api/kconfigcore/kconfigcore-module).

## Design essentials

KConfig hides how settings are stored and read behind an API for getting and setting them. Where and in what format the data is stored doesn't matter to an application using KConfig. All SonicDE applications handle their configuration the same way, and no application author has to build such a system, which is easy to get wrong.

A KConfig object represents one configuration. Each is referenced by a unique name and may actually be read from several files or other sources. Each application has a default configuration object, and there is also a global one.

A configuration has two levels: groups and keys. It can have any number of groups, and each group has one or more keys with their values.

Values can be of many data types, and you store and read them as the objects themselves. To store a color, for example, you pass a QColor, and reading it gives you a QColor back. So applications generally don't serialize and deserialize values themselves.

### The KConfig class

A [KConfig](/docs/api/kconfigcore/kconfig) object gives access to one configuration. There are several ways to create one:

```cpp
// a plain old read/write config object
KConfig config("myapprc");

// a specific file in the filesystem
// currently must be an INI style file
KConfig fullPath("/etc/kderc");

// not merged with the user's global values
KConfig globalFree("localsrc", KConfig::NoGlobals);

// not merged with globals or the system-wide configuration
KConfig simpleConfig("simplerc", KConfig::SimpleConfig);

// outside the standard config resource
KConfig dataResource("data", KConfig::SimpleConfig, QStandardPaths::AppDataLocation);
```

The first object is a regular configuration: you can read values, write new entries and ask for its properties. It is found through [QStandardPaths](https://doc.qt.io/qt-6/qstandardpaths.html): every `myapprc` in the configuration directories is merged into the values this object shows. That is how system-wide settings and user and group profiles work, without the application noticing.

The configuration directories searched are `$XDG_CONFIG_HOME` and then `$XDG_CONFIG_DIRS`, as defined in the [XDG Base Directory Specification](https://specifications.freedesktop.org/basedir-spec/latest/). Qt implements the specification in `QStandardPaths`.

The second object opens a specific file, here `/etc/kderc`. Nothing is merged into it, and it must be an INI-style file.

The third object isn't merged with the user's global configuration, `kdeglobals` (`KConfig::NoGlobals`), and the fourth also isn't merged with system-wide configuration files (`KConfig::SimpleConfig`, a single file). This can noticeably speed up reading a simple configuration for which global values make no sense.

The last object isn't in the configuration resource at all, but in the application's data directory. You can use any `QStandardPaths::StandardLocation`.

The flags are:

| Flag | Meaning |
| --- | --- |
| `KConfig::FullConfig` (default) | Merge `kdeglobals` and the system-wide configuration files. |
| `KConfig::NoGlobals` | Merge the system-wide files, but not `kdeglobals`. |
| `KConfig::NoCascade` | Merge the user's `kdeglobals`, but no system-wide files. |
| `KConfig::SimpleConfig` | Just the one file. |

### Special configuration objects

Each application has its own configuration object, named after the application with `rc` appended: an application named `myapp` (the component name given to [KAboutData](/docs/api/kcoreaddons/kaboutdata), or `QCoreApplication::applicationName()`) has the default configuration `myapprc`, in `~/.config/`. You get it like this:

```cpp
#include <KSharedConfig>

MyClass::MyClass()
{
    KSharedConfigPtr config = KSharedConfig::openConfig();
}
```

Creating a `KConfig` without a name also opens the application's default configuration. So you could also write this, but it is slower, because the file is parsed again:

```cpp
#include <KConfig>

MyClass::MyClass()
{
    KConfig config;
}
```

Finally there is a global configuration, `kdeglobals`, shared by all applications. It holds, for example, the default shortcuts for common actions. It is merged into a configuration object when the `KConfig::IncludeGlobals` flag is set, which it is by default.

### Commonly useful functions

`sync()` saves the configuration object's current state. A KConfig with unsaved changes also saves them when it is destroyed. If nothing changed, or the file can't be written (for example because the user has no write permission), nothing is written. `sync()` first reads the file again and merges in changes other processes made meanwhile; your own changes take priority.

To make sure you have the latest values from disk, call `reparseConfiguration()`. If the object has unsaved changes, it calls `sync()` first, then reloads the data.

To keep changes you have already made from being saved, call `markAsClean()`. For example, to roll the configuration back to what is on disk, call `markAsClean()` and then `reparseConfiguration()`.

`groupList()` lists all groups of a configuration object:

```cpp
KSharedConfigPtr config = KSharedConfig::openConfig();

const auto groupList = config->groupList();
for (const QString& group : groupList) {
    qDebug() << "next group:" << group;
}
```

## KSharedConfig

[KSharedConfig](/docs/api/kconfigcore/ksharedconfig) is a reference-counted [KConfig](/docs/api/kconfigcore/kconfig) (`KSharedConfigPtr` is a `QExplicitlySharedDataPointer<KSharedConfig>`). With it you can use the same configuration object from several places in your application, without the cost of separate objects and without worrying about writes from different code paths.

Getting a [KSharedConfig](/docs/api/kconfigcore/ksharedconfig) object is as easy as:

```cpp
KSharedConfigPtr config = KSharedConfig::openConfig("ksomefilerc");
```

`openConfig()` takes the same parameters as the `KConfig` constructor: the file to open, the flags that control merging, and the resource type.

`KSharedConfig` is generally recommended over `KConfig` itself. `openConfig()` is thread-safe: each thread gets its own set of shared objects, so if several threads use the same file, keep them in step with `reparseConfiguration()` as you would between processes.

## KConfigGroup

With a configuration object, the next step is to choose the group of keys and values you want to use, by creating a [KConfigGroup](/docs/api/kconfigcore/kconfiggroup):

```cpp
KConfig config;
KConfigGroup generalGroup(&config, "General");
KConfigGroup colorsGroup = config.group("Colors"); // ... or a bit differently ...
```

You can pass [KConfig](/docs/api/kconfigcore/kconfig) or [KSharedConfig](/docs/api/kconfigcore/ksharedconfig) objects to [KConfigGroup](/docs/api/kconfigcore/kconfiggroup).

Groups can be nested:

```cpp
KConfigGroup subGroup1(&generalGroup, "LessGeneral");
KConfigGroup subGroup2 = colorsGroup.group("Dialogs");
```

## Reading entries

With a [KConfigGroup](/docs/api/kconfigcore/kconfiggroup), reading entries is straightforward:

```cpp
QString accountName = generalGroup.readEntry("Account", QString());
QColor color = colorsGroup.readEntry("background", QColor(Qt::white));
QStringList list = generalGroup.readEntry("List", QStringList());
QString path = generalGroup.readPathEntry("SaveTo", defaultPath);
```

As the example shows, you can mix reads from different groups of the same configuration. The read functions take the key (case-sensitive) and a default value. The default decides what kind of data is expected and what type is returned, such as the color above.

There are some special read functions, among them `readPathEntry()`, which returns a file system path. Always use it for paths: it expands variables such as `$HOME`, and `writePathEntry()` stores the home directory as `$HOME`, so profiles work across users and machines.

If the key doesn't exist, the default is returned. If the key has a localized (translated) value for the current locale, that value is returned.

## Writing entries

Setting new values is just as easy:

```cpp
generalGroup.writeEntry("Account", accountName);
generalGroup.writePathEntry("SaveTo", savePath);
colorsGroup.writeEntry("background", color);
generalGroup.config()->sync();
```

Note `writePathEntry()`, and that the type of the value, such as the QColor, decides how it is stored. When you are done writing, call `sync()` on the configuration to save it, or let the object be destroyed, which saves unsaved changes.

## KDesktopFile: a special case

When is a configuration file not a configuration file? When it is a [desktop file](https://specifications.freedesktop.org/desktop-entry-spec/latest/). These files are configuration files at heart; they describe application menu entries, MIME types, plugins and services.

For `.desktop` files use [KDesktopFile](/docs/api/kconfigcore/kdesktopfile). It is a [KConfig](/docs/api/kconfigcore/kconfig) with everything described above, plus functions for reading the standard keys of these files consistently and reliably.

## Kiosk: lockdown and user and group profiles

KConfig has powerful lockdown features, together called Kiosk, which many system administrators and integrators rely on. Most of it works without the application doing anything, but sometimes an application needs to check whether a configuration can be written.

Entries locked down with Kiosk are *immutable*. An application can check whether a whole configuration, a group or a key is immutable:

```cpp
KSharedConfigPtr config = KSharedConfig::openConfig();

if (config->isImmutable()) {
    qDebug() << "configuration object is immutable";
}

KConfigGroup group(config, "General");
if (group.isImmutable()) {
    qDebug() << "group General is immutable";
}

if (group.isEntryImmutable("URL")) {
    qDebug() << "URL entry in group General is immutable";
}
```

This is useful when an application should behave differently for immutable settings. For example, SonicDE's panels and widgets are locked when their configuration is immutable: they are then system-immutable, and the user can't change or rearrange them.

## KConfig XT

KConfig XT makes some uses of KConfig easier, faster and more reliable, in particular an application's or plugin's main configuration and keeping settings dialogs and other interfaces in step with the values. It also documents the available settings, which system administrators and integrators appreciate. See [Using KConfig XT](kconfig-xt.md).
