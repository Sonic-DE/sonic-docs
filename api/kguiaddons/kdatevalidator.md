---
title: "KDateValidator Class"
description: "Validates user-entered dates."
---

# KDateValidator Class

Validates user-entered dates. [More...](#details)

- **Header:** `#include <KDateValidator>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS GuiAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::GuiAddons)`
- **Inherits:** [QValidator](https://doc.qt.io/qt-6/qvalidator.html)

[List of all members, including inherited members](kdatevalidator-members.md)

## Public Functions

- [void fixup(QString &input) const](#fixup)
- [QValidator::State validate(QString &text, int &e) const](#validate)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[override virtual\] void KDateValidator::fixup(QString &*input*) const {#fixup}

Reimplements: [QValidator::fixup(QString &input) const](https://doc.qt.io/qt-6/qvalidator.html#fixup).

### \[override virtual\] QValidator::State KDateValidator::validate(QString &*text*, int &*e*) const {#validate}

Reimplements: [QValidator::validate(QString &input, int &pos) const](https://doc.qt.io/qt-6/qvalidator.html#validate).
