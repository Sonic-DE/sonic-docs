---
title: "KCollapsibleGroupBox Class"
description: "A groupbox featuring a clickable header and arrow indicator that can be expanded and collapsed to reveal the contents."
---

# KCollapsibleGroupBox Class

A groupbox featuring a clickable header and arrow indicator that can be expanded and collapsed to reveal the contents. [More...](#details)

- **Header:** `#include <KCollapsibleGroupBox>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kcollapsiblegroupbox-members.md)

## Properties

- [title : QString](#title-prop)

## Public Functions

- [KCollapsibleGroupBox(QWidget \*parent = nullptr)](#KCollapsibleGroupBox)
- [bool isExpanded() const](#isExpanded)
- [void setExpanded(bool expanded)](#setExpanded)
- [void setTitle(const QString &title)](#setTitle)
- [QString title() const](#title)

## Public Slots

- [void collapse()](#collapse)
- [void expand()](#expand)
- [void toggle()](#toggle)

## Signals

- [void expandedChanged()](#expandedChanged)
- [void titleChanged()](#titleChanged)

## Detailed Description {#details}

When expanded, the widget will resize to fit the sizeHint of child items.

## Property Documentation {#property-documentation}

### title : QString {#title-prop}

**Access functions:**

- `QString` **[title](kcollapsiblegroupbox.md#title)**() const
- `void` **[setTitle](kcollapsiblegroupbox.md#setTitle)**(const `QString` &*title*)

**Notifier signal:**

- `void` **[titleChanged](kcollapsiblegroupbox.md#titleChanged)**()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KCollapsibleGroupBox::KCollapsibleGroupBox(QWidget \**parent* = nullptr) {#KCollapsibleGroupBox}

### \[slot\] void KCollapsibleGroupBox::collapse() {#collapse}

Equivalent to [setExpanded](kcollapsiblegroupbox.md#setExpanded)(false)

### \[slot\] void KCollapsibleGroupBox::expand() {#expand}

Equivalent to [setExpanded](kcollapsiblegroupbox.md#setExpanded)(true)

### \[signal\] void KCollapsibleGroupBox::expandedChanged() {#expandedChanged}

Emitted when the widget expands or collapsed

> **Note:** Notifier signal for property expanded.

### bool KCollapsibleGroupBox::isExpanded() const {#isExpanded}

Whether contents are shown During animations, this will reflect the target state at the end of the animation

> **Note:** Getter function for property expanded.

### void KCollapsibleGroupBox::setExpanded(bool *expanded*) {#setExpanded}

Set whether contents are shown

The default is false until the user clicks

> **Note:** Setter function for property expanded.

*See also* [isExpanded](kcollapsiblegroupbox.md#isExpanded)()

### void KCollapsibleGroupBox::setTitle(const QString &*title*) {#setTitle}

Set the title that will be permanently shown at the top of the collapsing box Mnemonics are supported

> **Note:** Setter function for property [title](kcollapsiblegroupbox.md#title-prop).

*See also* [title](kcollapsiblegroupbox.md#title)()

### QString KCollapsibleGroupBox::title() const {#title}

The title

> **Note:** Getter function for property [title](kcollapsiblegroupbox.md#title-prop).

*See also* [setTitle](kcollapsiblegroupbox.md#setTitle)()

### \[signal\] void KCollapsibleGroupBox::titleChanged() {#titleChanged}

Emitted when the title is changed

> **Note:** Notifier signal for property [title](kcollapsiblegroupbox.md#title-prop).

### \[slot\] void KCollapsibleGroupBox::toggle() {#toggle}

Expands if collapsed and vice versa
