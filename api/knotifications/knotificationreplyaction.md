---
title: "KNotificationReplyAction Class"
description: "An inline reply action."
---

# KNotificationReplyAction Class

An inline reply action. [More...](#details)

- **Header:** `#include <KNotificationReplyAction>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Notifications)`  
  `target_link_libraries(mytarget PRIVATE KF6::Notifications)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](knotificationreplyaction-members.md)

## Public Types

- [enum KNotificationReplyAction::FallbackBehavior](#FallbackBehavior-enum)

## Properties

- [fallbackBehavior : FallbackBehavior](#fallbackBehavior-prop)
- [label : QString](#label-prop)
- [placeholderText : QString](#placeholderText-prop)
- [submitButtonIconName : QString](#submitButtonIconName-prop)
- [submitButtonText : QString](#submitButtonText-prop)

## Public Functions

- [KNotificationReplyAction(const QString &label)](#KNotificationReplyAction)
- [KNotificationReplyAction::FallbackBehavior fallbackBehavior() const](#fallbackBehavior)
- [QString label() const](#label)
- [QString placeholderText() const](#placeholderText)
- [void setFallbackBehavior(KNotificationReplyAction::FallbackBehavior fallbackBehavior)](#setFallbackBehavior)
- [void setLabel(const QString &label)](#setLabel)
- [void setPlaceholderText(const QString &placeholderText)](#setPlaceholderText)
- [void setSubmitButtonIconName(const QString &submitButtonIconName)](#setSubmitButtonIconName)
- [void setSubmitButtonText(const QString &submitButtonText)](#setSubmitButtonText)
- [QString submitButtonIconName() const](#submitButtonIconName)
- [QString submitButtonText() const](#submitButtonText)

## Signals

- [void activated()](#activated)
- [void fallbackBehaviorChanged()](#fallbackBehaviorChanged)
- [void labelChanged()](#labelChanged)
- [void placeholderTextChanged()](#placeholderTextChanged)
- [void replied(const QString &text)](#replied)
- [void submitButtonIconNameChanged()](#submitButtonIconNameChanged)
- [void submitButtonTextChanged()](#submitButtonTextChanged)

## Detailed Description {#details}

This class represents an inline reply action, which lets the user type a reply to a chat message or email in the notification popup.

## Member Type Documentation {#member-type-documentation}

### enum KNotificationReplyAction::FallbackBehavior {#FallbackBehavior-enum}

Behavior when the notification server does not support inline replies

| Constant | Value | Description |
| --- | --- | --- |
| `KNotificationReplyAction::FallbackBehavior::HideAction` | `0` | Don't add the reply action (default) |
| `KNotificationReplyAction::FallbackBehavior::UseRegularAction` | `1` | Add the reply action as regular button Use this if you want to provide your own reply functionality Note: The [activated](knotificationreplyaction.md#activated)() signal is emitted instead of [replied](knotificationreplyaction.md#replied)() |

## Property Documentation {#property-documentation}

### fallbackBehavior : FallbackBehavior {#fallbackBehavior-prop}

**Access functions:**

- `KNotificationReplyAction::FallbackBehavior` **[fallbackBehavior](knotificationreplyaction.md#fallbackBehavior)**() const
- `void` **[setFallbackBehavior](knotificationreplyaction.md#setFallbackBehavior)**(`KNotificationReplyAction::FallbackBehavior` *fallbackBehavior*)

**Notifier signal:**

- `void` **[fallbackBehaviorChanged](knotificationreplyaction.md#fallbackBehaviorChanged)**()

### label : QString {#label-prop}

**Access functions:**

- `QString` **[label](knotificationreplyaction.md#label)**() const
- `void` **[setLabel](knotificationreplyaction.md#setLabel)**(const `QString` &*label*)

**Notifier signal:**

- `void` **[labelChanged](knotificationreplyaction.md#labelChanged)**()

### placeholderText : QString {#placeholderText-prop}

**Access functions:**

- `QString` **[placeholderText](knotificationreplyaction.md#placeholderText)**() const
- `void` **[setPlaceholderText](knotificationreplyaction.md#setPlaceholderText)**(const `QString` &*placeholderText*)

**Notifier signal:**

- `void` **[placeholderTextChanged](knotificationreplyaction.md#placeholderTextChanged)**()

### submitButtonIconName : QString {#submitButtonIconName-prop}

**Access functions:**

- `QString` **[submitButtonIconName](knotificationreplyaction.md#submitButtonIconName)**() const
- `void` **[setSubmitButtonIconName](knotificationreplyaction.md#setSubmitButtonIconName)**(const `QString` &*submitButtonIconName*)

**Notifier signal:**

- `void` **[submitButtonIconNameChanged](knotificationreplyaction.md#submitButtonIconNameChanged)**()

### submitButtonText : QString {#submitButtonText-prop}

**Access functions:**

- `QString` **[submitButtonText](knotificationreplyaction.md#submitButtonText)**() const
- `void` **[setSubmitButtonText](knotificationreplyaction.md#setSubmitButtonText)**(const `QString` &*submitButtonText*)

**Notifier signal:**

- `void` **[submitButtonTextChanged](knotificationreplyaction.md#submitButtonTextChanged)**()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KNotificationReplyAction::KNotificationReplyAction(const QString &*label*) {#KNotificationReplyAction}

Creates a inline reply action with given label

`label` The label for the action

### \[signal\] void KNotificationReplyAction::activated() {#activated}

Emitted when the user clicks the reply fallback button

> **Note:** This is emitted when the notification server does not support inline replies and [fallbackBehavior](knotificationreplyaction.md#fallbackBehavior) is set to [UseRegularAction](knotificationreplyaction.md#FallbackBehavior-enum).

### KNotificationReplyAction::FallbackBehavior KNotificationReplyAction::fallbackBehavior() const {#fallbackBehavior}

Gets the fallback behavior when the notification server does not support inline replies

> **Note:** Getter function for property [fallbackBehavior](knotificationreplyaction.md#fallbackBehavior-prop).

*See also* [setFallbackBehavior](knotificationreplyaction.md#setFallbackBehavior)()

### \[signal\] void KNotificationReplyAction::fallbackBehaviorChanged() {#fallbackBehaviorChanged}

Emitted when [fallbackBehavior](knotificationreplyaction.md#fallbackBehavior) changed.

> **Note:** Notifier signal for property [fallbackBehavior](knotificationreplyaction.md#fallbackBehavior-prop).

### QString KNotificationReplyAction::label() const {#label}

The label for the action button

> **Note:** Getter function for property [label](knotificationreplyaction.md#label-prop).

*See also* [setLabel](knotificationreplyaction.md#setLabel)()

### \[signal\] void KNotificationReplyAction::labelChanged() {#labelChanged}

Emitted when label changed.

> **Note:** Notifier signal for property [label](knotificationreplyaction.md#label-prop).

### QString KNotificationReplyAction::placeholderText() const {#placeholderText}

The placeholder text for the inline reply text field

> **Note:** Getter function for property [placeholderText](knotificationreplyaction.md#placeholderText-prop).

*See also* [setPlaceholderText](knotificationreplyaction.md#setPlaceholderText)()

### \[signal\] void KNotificationReplyAction::placeholderTextChanged() {#placeholderTextChanged}

Emitted when [placeholderText](knotificationreplyaction.md#placeholderText) changed.

> **Note:** Notifier signal for property [placeholderText](knotificationreplyaction.md#placeholderText-prop).

### \[signal\] void KNotificationReplyAction::replied(const QString &*text*) {#replied}

Emitted when the user has submitted a reply

> **Note:** This is never emitted when the notification server does not support inline replies

`text` The text the user entered

### void KNotificationReplyAction::setFallbackBehavior(KNotificationReplyAction::FallbackBehavior *fallbackBehavior*) {#setFallbackBehavior}

Set the fallback behavior for when the notification server does not support inline replies

> **Note:** Setter function for property [fallbackBehavior](knotificationreplyaction.md#fallbackBehavior-prop).

*See also* [fallbackBehavior](knotificationreplyaction.md#fallbackBehavior)()

### void KNotificationReplyAction::setLabel(const QString &*label*) {#setLabel}

Set the label for the action button

> **Note:** Setter function for property [label](knotificationreplyaction.md#label-prop).

*See also* [label](knotificationreplyaction.md#label)()

### void KNotificationReplyAction::setPlaceholderText(const QString &*placeholderText*) {#setPlaceholderText}

Set the placeholder text for the inline reply text field, for example "Reply to Konqi..."

> **Note:** Setter function for property [placeholderText](knotificationreplyaction.md#placeholderText-prop).

*See also* [placeholderText](knotificationreplyaction.md#placeholderText)()

### void KNotificationReplyAction::setSubmitButtonIconName(const QString &*submitButtonIconName*) {#setSubmitButtonIconName}

Set the icon name for the button to send the typed reply

> **Note:** Setter function for property [submitButtonIconName](knotificationreplyaction.md#submitButtonIconName-prop).

*See also* [submitButtonIconName](knotificationreplyaction.md#submitButtonIconName)()

### void KNotificationReplyAction::setSubmitButtonText(const QString &*submitButtonText*) {#setSubmitButtonText}

Set the label for the button to send the typed reply

> **Note:** Setter function for property [submitButtonText](knotificationreplyaction.md#submitButtonText-prop).

*See also* [submitButtonText](knotificationreplyaction.md#submitButtonText)()

### QString KNotificationReplyAction::submitButtonIconName() const {#submitButtonIconName}

The icon name for the button to send the typed reply

> **Note:** Getter function for property [submitButtonIconName](knotificationreplyaction.md#submitButtonIconName-prop).

*See also* [setSubmitButtonIconName](knotificationreplyaction.md#setSubmitButtonIconName)()

### \[signal\] void KNotificationReplyAction::submitButtonIconNameChanged() {#submitButtonIconNameChanged}

Emitted when [submitButtonIconName](knotificationreplyaction.md#submitButtonIconName) changed.

> **Note:** Notifier signal for property [submitButtonIconName](knotificationreplyaction.md#submitButtonIconName-prop).

### QString KNotificationReplyAction::submitButtonText() const {#submitButtonText}

The label for the button to send the typed reply

> **Note:** Getter function for property [submitButtonText](knotificationreplyaction.md#submitButtonText-prop).

*See also* [setSubmitButtonText](knotificationreplyaction.md#setSubmitButtonText)()

### \[signal\] void KNotificationReplyAction::submitButtonTextChanged() {#submitButtonTextChanged}

Emitted when [submitButtonText](knotificationreplyaction.md#submitButtonText) changed.

> **Note:** Notifier signal for property [submitButtonText](knotificationreplyaction.md#submitButtonText-prop).
