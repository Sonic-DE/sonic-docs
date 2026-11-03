---
title: "KAssistantDialog Class"
description: "This class provides a framework for assistant dialogs."
---

# KAssistantDialog Class

This class provides a framework for assistant dialogs. [More...](#details)

- **Header:** `#include <KAssistantDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [KPageDialog](kpagedialog.md)

[List of all members, including inherited members](kassistantdialog-members.md)  
[Deprecated members](kassistantdialog-obsolete.md)

## Public Functions

- [KAssistantDialog(QWidget \*parent = nullptr, Qt::WindowFlags flags = WindowFlags())](#KAssistantDialog)
- [bool isAppropriate(KPageWidgetItem \*page) const](#isAppropriate)
- [bool isValid(KPageWidgetItem \*page) const](#isValid)
- [bool onLastPage() const](#onLastPage) (since 6.29)
- [void setAppropriate(KPageWidgetItem \*page, bool appropriate)](#setAppropriate)
- [void setValid(KPageWidgetItem \*page, bool enable)](#setValid)

## Public Slots

- [void back()](#back)
- [void next()](#next)

## Protected Functions

- [KAssistantDialog(KPageWidget \*widget, QWidget \*parent = nullptr, Qt::WindowFlags flags = WindowFlags())](#KAssistantDialog-1)

## Detailed Description {#details}

An assistant dialog consists of a sequence of pages. Its purpose is to guide the user (assist) through a process step by step. Assistant dialogs are useful for complex or infrequently occurring tasks that people may find difficult to learn or do. Sometimes a task requires too many input fields to fit them on a single dialog.

Create and populate dialog pages that inherit from [QWidget](https://doc.qt.io/qt-6/qwidget.html) and add them to the assistant dialog using [addPage](kpagedialog.md#addPage)().

The functions [next](kassistantdialog.md#next)() and [back](kassistantdialog.md#back)() are virtual and may be reimplemented to override the default actions of the next and back buttons.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KAssistantDialog::KAssistantDialog(QWidget \**parent* = nullptr, Qt::WindowFlags *flags* = Qt::WindowFlags()) {#KAssistantDialog}

Construct a new assistant dialog with `parent` as parent.

`parent` is the parent of the widget.

`flags` the window flags to give to the assistant dialog. The default of zero is usually what you want.

### \[explicit protected\] KAssistantDialog::KAssistantDialog(KPageWidget \**widget*, QWidget \**parent* = nullptr, Qt::WindowFlags *flags* = Qt::WindowFlags()) {#KAssistantDialog-1}

Construct an assistant dialog from a single widget.

`widget` the widget to construct the dialog with

`parent` the parent of the assistant dialog

`flags` the window flags to use when creating the widget. The default of zero is usually fine.

Calls the [KPageDialog](kpagedialog.md)([KPageWidget](kpagewidget.md) \*widget, [QWidget](https://doc.qt.io/qt-6/qwidget.html) \*parent, [Qt::WindowFlags](https://doc.qt.io/qt-6/qt.html#WindowType-enum) flags) constructor

### \[virtual slot\] void KAssistantDialog::back() {#back}

Called when the user clicks the Back button.

This function will show the preceding relevant page in the sequence. Do nothing if the current page is the first page in the sequence.

### bool KAssistantDialog::isAppropriate(KPageWidgetItem \**page*) const {#isAppropriate}

Check if a page is appropriate for use in the assistant dialog.

`page` is the page to check the appropriateness of.

Returns `true` if `page` is appropriate, false if it is not

### bool KAssistantDialog::isValid(KPageWidgetItem \**page*) const {#isValid}

return if a page is valid

`page` the page to check the validity of

*See also* [setValid](kassistantdialog.md#setValid)()

### \[virtual slot\] void KAssistantDialog::next() {#next}

Called when the user clicks the Next/Finish button.

This function will show the next relevant page in the sequence. If the current page is the last page, it will call [accept](https://doc.qt.io/qt-6/qdialog.html#accept)()

### \[since 6.29\] bool KAssistantDialog::onLastPage() const {#onLastPage}

Returns true if the dialog is currently showing the last visible page, i.e. the last page for which [isAppropriate](kassistantdialog.md#isAppropriate)() returns true.

This function was introduced in Qt 6.29.

### void KAssistantDialog::setAppropriate(KPageWidgetItem \**page*, bool *appropriate*) {#setAppropriate}

Specify whether a page is appropriate.

A page is considered inappropriate if it should not be shown due to the contents of other pages making it inappropriate.

A page which is inappropriate will not be shown.

The last page in an assistant dialog should always be appropriate

`page` the page to set as appropriate

`appropriate` flag indicating the appropriateness of the page.

If `appropriate` is true, then `page` is appropriate and will be shown in the assistant dialog. If false, `page` will not be shown.

*See also* [isAppropriate](kassistantdialog.md#isAppropriate)()

### void KAssistantDialog::setValid(KPageWidgetItem \**page*, bool *enable*) {#setValid}

Specify if the content of the page is valid, and if the next button may be enabled on this page. By default all pages are valid.

This will disable or enable the next button on the specified page

`page` the page on which the next button will be enabled/disable

`enable` if true the next button will be enabled, if false it will be disabled

*See also* [isValid](kassistantdialog.md#isValid)()
