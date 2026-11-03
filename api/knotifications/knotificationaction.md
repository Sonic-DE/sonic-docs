---
title: "KNotificationAction Class"
description: "This class represents an action in a notification. This class was introduced in Qt 6.0."
---

# KNotificationAction Class

This class represents an action in a notification. This class was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <KNotification>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Notifications)`  
  `target_link_libraries(mytarget PRIVATE KF6::Notifications)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](knotificationaction-members.md)

## Properties

- [label : QString](#label-prop)

## Public Functions

- [KNotificationAction(const QString &label)](#KNotificationAction)
- [QString label() const](#label)
- [void setLabel(const QString &label)](#setLabel)

## Signals

- [void activated()](#activated)
- [void labelChanged(const QString &label)](#labelChanged)

## Detailed Description {#details}

This can be a button on the notification popup, or triggered by clicking the notification popup itself.

## Property Documentation {#property-documentation}

### label : QString {#label-prop}

**Access functions:**

- `QString` **[label](knotificationaction.md#label)**() const
- `void` **[setLabel](knotificationaction.md#setLabel)**(const `QString` &*label*)

**Notifier signal:**

- `void` **[labelChanged](knotificationaction.md#labelChanged)**(const `QString` &*label*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KNotificationAction::KNotificationAction(const QString &*label*) {#KNotificationAction}

Creates an action with given label

`label` The label for the action

### \[signal\] void KNotificationAction::activated() {#activated}

Emitted when the user activates the action

### QString KNotificationAction::label() const {#label}

The user-facing label for the action

> **Note:** Getter function for property [label](knotificationaction.md#label-prop).

*See also* [setLabel](knotificationaction.md#setLabel)()

### \[signal\] void KNotificationAction::labelChanged(const QString &*label*) {#labelChanged}

Emitted when `label` changed.

> **Note:** Notifier signal for property [label](knotificationaction.md#label-prop).

### void KNotificationAction::setLabel(const QString &*label*) {#setLabel}

Set the user-facing label for the action

> **Note:** Setter function for property [label](knotificationaction.md#label-prop).

*See also* [label](knotificationaction.md#label)()
