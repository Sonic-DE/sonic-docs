---
title: "KFontSizeAction Class"
description: "An action to allow changing of the font size."
---

# KFontSizeAction Class

An action to allow changing of the font size. [More...](#details)

- **Header:** `#include <KFontSizeAction>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [KSelectAction](kselectaction.md)

[List of all members, including inherited members](kfontsizeaction-members.md)

## Properties

- [fontSize : int](#fontSize-prop)

## Public Functions

- [KFontSizeAction(QObject \*parent)](#KFontSizeAction)
- [KFontSizeAction(const QString &text, QObject \*parent)](#KFontSizeAction-1)
- [KFontSizeAction(const QIcon &icon, const QString &text, QObject \*parent)](#KFontSizeAction-2)
- [int fontSize() const](#fontSize)
- [void setFontSize(int size)](#setFontSize)

## Public Slots

- [void slotActionTriggered(QAction \*action)](#slotActionTriggered)

## Signals

- [void fontSizeChanged(int)](#fontSizeChanged)

## Detailed Description {#details}

This action will be shown as a combobox on a toolbar with a proper set of font sizes.

## Property Documentation {#property-documentation}

### fontSize : int {#fontSize-prop}

**Access functions:**

- `int` **[fontSize](kfontsizeaction.md#fontSize)**() const
- `void` **[setFontSize](kfontsizeaction.md#setFontSize)**(`int` *size*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KFontSizeAction::KFontSizeAction(QObject \**parent*) {#KFontSizeAction}

### KFontSizeAction::KFontSizeAction(const QString &*text*, QObject \**parent*) {#KFontSizeAction-1}

### KFontSizeAction::KFontSizeAction(const QIcon &*icon*, const QString &*text*, QObject \**parent*) {#KFontSizeAction-2}

### int KFontSizeAction::fontSize() const {#fontSize}

> **Note:** Getter function for property [fontSize](kfontsizeaction.md#fontSize-prop).

*See also* [setFontSize](kfontsizeaction.md#setFontSize)()

### \[signal\] void KFontSizeAction::fontSizeChanged(*int*) {#fontSizeChanged}

### void KFontSizeAction::setFontSize(int *size*) {#setFontSize}

> **Note:** Setter function for property [fontSize](kfontsizeaction.md#fontSize-prop).

*See also* [fontSize](kfontsizeaction.md#fontSize)()

### \[override virtual protected slot\] void KFontSizeAction::slotActionTriggered(QAction \**action*) {#slotActionTriggered}

Reimplements: [KSelectAction::slotActionTriggered(QAction \*action)](kselectaction.md#slotActionTriggered).

This function is called whenever an action from the selections is triggered.
