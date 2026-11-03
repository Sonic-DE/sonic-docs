---
title: "KBugReport Class"
description: "A dialog box for sending bug reports."
---

# KBugReport Class

A dialog box for sending bug reports. [More...](#details)

- **Header:** `#include <KBugReport>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS XmlGui)`  
  `target_link_libraries(mytarget PRIVATE KF6::XmlGui)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](kbugreport-members.md)

## Public Functions

- [KBugReport(const KAboutData &aboutData, QWidget \*parent = nullptr)](#KBugReport)
- [~KBugReport()](#dtor.KBugReport)
- [void accept()](#accept)

## Protected Functions

- [bool sendBugReport()](#sendBugReport)

## Detailed Description {#details}

All the information needed by the dialog box (program name, version, bug-report address, etc.) comes from the [KAboutData](../kcoreaddons/kaboutdata.md) class. Make sure you create an instance of [KAboutData](../kcoreaddons/kaboutdata.md) and call [KAboutData::setApplicationData](../kcoreaddons/kaboutdata.md#setApplicationData)(\<aboutData\>).

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KBugReport::KBugReport(const KAboutData &*aboutData*, QWidget \**parent* = nullptr) {#KBugReport}

Creates a bug-report dialog using information derived from `aboutData` as a child of `parent`.

Note that you shouldn't have to do this manually, since [KHelpMenu](khelpmenu.md) takes care of the menu item for "Report Bug..." and of creating a [KBugReport](kbugreport.md) dialog.

### \[override virtual noexcept\] KBugReport::~KBugReport() {#dtor.KBugReport}

Destructor.

### \[override virtual\] void KBugReport::accept() {#accept}

Reimplements: [QDialog::accept()](https://doc.qt.io/qt-6/qdialog.html#accept).

OK has been clicked.

### \[protected\] bool KBugReport::sendBugReport() {#sendBugReport}

Attempt to e-mail the bug report.

Returns true on success.
