---
title: "KPluralHandlingSpinBox Class"
description: "A QSpinBox with plural handling for the suffix. This class is deprecated since 6.6. We strongly advise against using it in new code."
---

# KPluralHandlingSpinBox Class

A [QSpinBox](https://doc.qt.io/qt-6/qspinbox.html) with plural handling for the suffix. **This class is deprecated since 6.6. We strongly advise against using it in new code.** [More...](#details)

- **Header:** `#include <KPluralHandlingSpinBox>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextWidgets)`
- **Inherits:** [QSpinBox](https://doc.qt.io/qt-6/qspinbox.html)
- **Status:** Deprecated since 6.6

[List of all members, including inherited members](kpluralhandlingspinbox-members.md)

## Public Functions

- [KPluralHandlingSpinBox(QWidget \*parent = nullptr)](#KPluralHandlingSpinBox)
- [void setSuffix(const KLocalizedString &suffix)](#setSuffix)

**This class is deprecated since 6.6. We strongly advise against using it in new code.**

## Detailed Description {#details}

Use KLocalization::setupSpinBoxFormatString() from KF6::I18n instead, which is more powerful and does not require inheriting from a specific [QSpinBox](https://doc.qt.io/qt-6/qspinbox.html) subclass.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KPluralHandlingSpinBox::KPluralHandlingSpinBox(QWidget \**parent* = nullptr) {#KPluralHandlingSpinBox}

Default constructor

### void KPluralHandlingSpinBox::setSuffix(const KLocalizedString &*suffix*) {#setSuffix}

Sets the suffix to `suffix`. Use this to add a plural-aware suffix, e.g. by using ki18np("singular", "plural").
