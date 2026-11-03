---
title: "KFontAction Class"
description: "An action to select a font family."
---

# KFontAction Class

An action to select a font family. [More...](#details)

- **Header:** `#include <KFontAction>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [KSelectAction](kselectaction.md)

[List of all members, including inherited members](kfontaction-members.md)

## Properties

- [font : QString](#font-prop)

## Public Functions

- [KFontAction(QObject \*parent)](#KFontAction)
- [KFontAction(uint fontListCriteria, QObject \*parent)](#KFontAction-1)
- [QWidget \*createWidget(QWidget \*parent)](#createWidget)
- [QString font() const](#font)
- [void setFont(const QString &family)](#setFont)

## Detailed Description {#details}

On a toolbar this will show a combobox with all the fonts on the system.

## Property Documentation {#property-documentation}

### font : QString {#font-prop}

**Access functions:**

- `QString` **[font](kfontaction.md#font)**() const
- `void` **[setFont](kfontaction.md#setFont)**(const `QString` &*family*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KFontAction::KFontAction(QObject \**parent*) {#KFontAction}

### KFontAction::KFontAction(uint *fontListCriteria*, QObject \**parent*) {#KFontAction-1}

### \[override virtual\] QWidget \*KFontAction::createWidget(QWidget \**parent*) {#createWidget}

Reimplements: [QWidgetAction::createWidget(QWidget \*parent)](https://doc.qt.io/qt-6/qwidgetaction.html#createWidget).

### QString KFontAction::font() const {#font}

> **Note:** Getter function for property [font](kfontaction.md#font-prop).

*See also* [setFont](kfontaction.md#setFont)()

### void KFontAction::setFont(const QString &*family*) {#setFont}

> **Note:** Setter function for property [font](kfontaction.md#font-prop).

*See also* [font](kfontaction.md#font)()
