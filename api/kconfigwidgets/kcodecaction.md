---
title: "KCodecAction Class"
description: "Action for selecting one of several text codecs."
---

# KCodecAction Class

Action for selecting one of several text codecs. [More...](#details)

- **Header:** `#include <KCodecAction>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ConfigWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigWidgets)`
- **Inherits:** [KSelectAction](../kwidgetsaddons/kselectaction.md)

[List of all members, including inherited members](kcodecaction-members.md)

## Properties

- [codecName : QString](#codecName-prop)

## Public Functions

- [KCodecAction(QObject \*parent, bool showAutoOptions = false)](#KCodecAction)
- [KCodecAction(const QString &text, QObject \*parent, bool showAutoOptions = false)](#KCodecAction-1)
- [KCodecAction(const QIcon &icon, const QString &text, QObject \*parent, bool showAutoOptions = false)](#KCodecAction-2)
- [QString currentCodecName() const](#currentCodecName)
- [bool setCurrentCodec(const QString &codecName)](#setCurrentCodec)

## Public Slots

- [void slotActionTriggered(QAction \*)](#slotActionTriggered)

## Signals

- [void codecNameTriggered(const QByteArray &name)](#codecNameTriggered)
- [void defaultItemTriggered()](#defaultItemTriggered)

## Detailed Description {#details}

This action shows up a submenu with a list of the available codecs on the system.

## Property Documentation {#property-documentation}

### codecName : QString {#codecName-prop}

**Access functions:**

- `QString` **[currentCodecName](kcodecaction.md#currentCodecName)**() const
- `bool` **[setCurrentCodec](kcodecaction.md#setCurrentCodec)**(const `QString` &*codecName*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KCodecAction::KCodecAction(QObject \**parent*, bool *showAutoOptions* = false) {#KCodecAction}

### KCodecAction::KCodecAction(const QString &*text*, QObject \**parent*, bool *showAutoOptions* = false) {#KCodecAction-1}

### KCodecAction::KCodecAction(const QIcon &*icon*, const QString &*text*, QObject \**parent*, bool *showAutoOptions* = false) {#KCodecAction-2}

### \[signal\] void KCodecAction::codecNameTriggered(const QByteArray &*name*) {#codecNameTriggered}

Emitted when a codec was selected

`name` the name of the selected encoding.

Note that textTriggered(const [QString](https://doc.qt.io/qt-6/qstring.html) &) is emitted too (as defined in [KSelectAction](../kwidgetsaddons/kselectaction.md)).

### QString KCodecAction::currentCodecName() const {#currentCodecName}

> **Note:** Getter function for property [codecName](kcodecaction.md#codecName-prop).

### \[signal\] void KCodecAction::defaultItemTriggered() {#defaultItemTriggered}

Emitted when the 'Default' codec action is triggered.

### bool KCodecAction::setCurrentCodec(const QString &*codecName*) {#setCurrentCodec}

> **Note:** Setter function for property [codecName](kcodecaction.md#codecName-prop).

### \[override virtual protected slot\] void KCodecAction::slotActionTriggered(*QAction \**) {#slotActionTriggered}

Reimplements: [KSelectAction::slotActionTriggered(QAction \*action)](../kwidgetsaddons/kselectaction.md#slotActionTriggered).
