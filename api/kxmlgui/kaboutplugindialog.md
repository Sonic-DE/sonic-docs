---
title: "KAboutPluginDialog Class"
description: "This class provides a standard \"About Plugin\" dialog box."
---

# KAboutPluginDialog Class

This class provides a standard "About Plugin" dialog box. [More...](#details)

- **Header:** `#include <KAboutPluginDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS XmlGui)`  
  `target_link_libraries(mytarget PRIVATE KF6::XmlGui)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](kaboutplugindialog-members.md)

## Public Types

- [enum KAboutPluginDialog::Option](#Option-enum)

## Public Functions

- [KAboutPluginDialog(const KPluginMetaData &pluginMetaData, QWidget \*parent = nullptr)](#KAboutPluginDialog)
- [KAboutPluginDialog(const KPluginMetaData &pluginMetaData, KAboutPluginDialog::Options options, QWidget \*parent = nullptr)](#KAboutPluginDialog-1)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum KAboutPluginDialog::Option {#Option-enum}

**flags KAboutPluginDialog::Options**

Defines some options which can be applied to the about dialog.

| Constant | Value | Description |
| --- | --- | --- |
| `KAboutPluginDialog::NoOptions` | `0x0` | Show the standard about dialog. |
| `KAboutPluginDialog::HideTranslators` | `0x1` | Don't show the translators tab. |

The `Options` type is a typedef for `QFlags<Option>. `It stores an OR combination of `Option` values.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KAboutPluginDialog::KAboutPluginDialog(const KPluginMetaData &*pluginMetaData*, QWidget \**parent* = nullptr) {#KAboutPluginDialog}

Constructs a default "About Plugin" dialog box using the provided `pluginMetaData`.

`pluginMetaData` The data about the plugin to show in the dialog.

`parent` The parent of the dialog box. Use the toplevel window so that the dialog becomes centered.

### \[explicit\] KAboutPluginDialog::KAboutPluginDialog(const KPluginMetaData &*pluginMetaData*, KAboutPluginDialog::Options *options*, QWidget \**parent* = nullptr) {#KAboutPluginDialog-1}

Constructs a fully featured "About Plugin" dialog box using the provided `pluginMetaData` and extra `options`.

`pluginMetaData` The data about the plugin to show in the dialog.

`options` Options to apply, such as hiding the translators tab.

`parent` The parent of the dialog box. Use the toplevel window so that the dialog becomes centered.
