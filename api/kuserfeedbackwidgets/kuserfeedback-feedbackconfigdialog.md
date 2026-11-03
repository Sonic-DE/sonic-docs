---
title: "KUserFeedback::FeedbackConfigDialog Class"
description: "Configure which feedback a user wants to provide."
---

# KUserFeedback::FeedbackConfigDialog Class

Configure which feedback a user wants to provide. [More...](#details)

- **Header:** `#include <KUserFeedback/FeedbackConfigDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UserFeedbackWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::UserFeedbackWidgets)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](kuserfeedback-feedbackconfigdialog-members.md)

## Public Functions

- [FeedbackConfigDialog(QWidget \*parent = nullptr)](#FeedbackConfigDialog)
- [void accept()](#accept)
- [void setFeedbackProvider(KUserFeedback::Provider \*provider)](#setFeedbackProvider)

## Detailed Description {#details}

`FeedbackConfigWidget`

## Member Function Documentation {#member-function-documentation}

### \[explicit\] FeedbackConfigDialog::FeedbackConfigDialog(QWidget \**parent* = nullptr) {#FeedbackConfigDialog}

Create a new feedback configuration dialog.

`parent` The parent widget.

### \[override virtual\] void FeedbackConfigDialog::accept() {#accept}

Reimplements: [QDialog::accept()](https://doc.qt.io/qt-6/qdialog.html#accept).

Accepts the dialog and write changes made by the user to the feedback provider.

### void FeedbackConfigDialog::setFeedbackProvider(KUserFeedback::Provider \**provider*) {#setFeedbackProvider}

Set the feedback provider that this dialog configures.
