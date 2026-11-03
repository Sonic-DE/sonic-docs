---
title: "KAboutApplicationDialog Class"
description: "Standard \"About Application\" dialog box."
---

# KAboutApplicationDialog Class

Standard "About Application" dialog box. [More...](#details)

- **Header:** `#include <KAboutApplicationDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS XmlGui)`  
  `target_link_libraries(mytarget PRIVATE KF6::XmlGui)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](kaboutapplicationdialog-members.md)

## Public Types

- [enum KAboutApplicationDialog::Option](#Option-enum)

## Public Functions

- [KAboutApplicationDialog(const KAboutData &aboutData, QWidget \*parent = nullptr)](#KAboutApplicationDialog)
- [KAboutApplicationDialog(const KAboutData &aboutData, KAboutApplicationDialog::Options opts, QWidget \*parent = nullptr)](#KAboutApplicationDialog-1)

## Detailed Description {#details}

This class provides the standard "About Application" dialog box that is used by [KHelpMenu](khelpmenu.md). It uses the information of the global [KAboutData](../kcoreaddons/kaboutdata.md) that is specified at the start of your program in main(). Normally you should not use this class directly but rather the [KHelpMenu](khelpmenu.md) class or even better just subclass your toplevel window from [KMainWindow](kmainwindow.md). If you do the latter, the help menu and thereby this dialog box is available through the KMainWindow::helpMenu() function.

## Member Type Documentation {#member-type-documentation}

### enum KAboutApplicationDialog::Option {#Option-enum}

**flags KAboutApplicationDialog::Options**

Defines some options that can be applied to the about dialog.

| Constant | Value | Description |
| --- | --- | --- |
| `KAboutApplicationDialog::NoOptions` | `0x0` | Shows the standard about dialog. |
| `KAboutApplicationDialog::HideTranslators` | `0x1` | Hides the translators tab. |
| `KAboutApplicationDialog::HideLibraries` | `0x2` | Since 5.77, hides the libraries tab. Since 5.87, hides the components tab (which replaces the libraries tab). |

The `Options` type is a typedef for `QFlags<Option>. `It stores an OR combination of `Option` values.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KAboutApplicationDialog::KAboutApplicationDialog(const KAboutData &*aboutData*, QWidget \**parent* = nullptr) {#KAboutApplicationDialog}

Constructs a fully featured "About Application" dialog box using existing `aboutData`.

You should set the toplevel window as the `parent` so that the dialog becomes centered.

### \[explicit\] KAboutApplicationDialog::KAboutApplicationDialog(const KAboutData &*aboutData*, KAboutApplicationDialog::Options *opts*, QWidget \**parent* = nullptr) {#KAboutApplicationDialog-1}

Constructs a fully featured "About Application" dialog box using existing `aboutData` and the specified `opts`.

You should set the toplevel window as the parent so that the dialog becomes centered.

*See also* [Options](kaboutapplicationdialog.md#Option-enum)
