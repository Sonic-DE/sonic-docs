---
title: "KPasswordLineEdit Class"
description: "A lineedit which allows to display password."
---

# KPasswordLineEdit Class

A lineedit which allows to display password. [More...](#details)

- **Header:** `#include <KPasswordLineEdit>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kpasswordlineedit-members.md)  
[Deprecated members](kpasswordlineedit-obsolete.md)

## Properties

- [clearButtonEnabled : bool](#clearButtonEnabled-prop)
- [echoMode : QLineEdit::EchoMode](#echoMode-prop)
- [password : QString](#password-prop)

## Public Functions

- [KPasswordLineEdit(QWidget \*parent = nullptr)](#KPasswordLineEdit)
- [void clear()](#clear)
- [QLineEdit::EchoMode echoMode() const](#echoMode)
- [bool isClearButtonEnabled() const](#isClearButtonEnabled)
- [bool isReadOnly() const](#isReadOnly) (since 6.0)
- [QLineEdit \*lineEdit() const](#lineEdit)
- [QString password() const](#password)
- [KPassword::RevealMode revealPasswordMode() const](#revealPasswordMode) (since 6.0)
- [void setClearButtonEnabled(bool clear)](#setClearButtonEnabled)
- [void setEchoMode(QLineEdit::EchoMode mode)](#setEchoMode)
- [void setPassword(const QString &password)](#setPassword)
- [void setReadOnly(bool readOnly)](#setReadOnly) (since 6.0)
- [void setRevealPasswordMode(KPassword::RevealMode revealPasswordMode)](#setRevealPasswordMode) (since 6.0)

## Signals

- [void echoModeChanged(QLineEdit::EchoMode echoMode)](#echoModeChanged)
- [void passwordChanged(const QString &password)](#passwordChanged)

## Detailed Description {#details}

Usage Example:

Get password

```cpp
KPasswordLineEdit *passwordLineEdit = new KPasswordLineEdit(parent);
QString password = passwordLineEdit->password();
```

## Property Documentation {#property-documentation}

### clearButtonEnabled : bool {#clearButtonEnabled-prop}

**Access functions:**

- `bool` **[isClearButtonEnabled](kpasswordlineedit.md#isClearButtonEnabled)**() const
- `void` **[setClearButtonEnabled](kpasswordlineedit.md#setClearButtonEnabled)**(`bool` *clear*)

### echoMode : QLineEdit::EchoMode {#echoMode-prop}

**Access functions:**

- `QLineEdit::EchoMode` **[echoMode](kpasswordlineedit.md#echoMode)**() const
- `void` **[setEchoMode](kpasswordlineedit.md#setEchoMode)**(`QLineEdit::EchoMode` *mode*)

**Notifier signal:**

- `void` **[echoModeChanged](kpasswordlineedit.md#echoModeChanged)**(`QLineEdit::EchoMode` *echoMode*)

### password : QString {#password-prop}

**Access functions:**

- `QString` **[password](kpasswordlineedit.md#password)**() const
- `void` **[setPassword](kpasswordlineedit.md#setPassword)**(const `QString` &*password*)

**Notifier signal:**

- `void` **[passwordChanged](kpasswordlineedit.md#passwordChanged)**(const `QString` &*password*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KPasswordLineEdit::KPasswordLineEdit(QWidget \**parent* = nullptr) {#KPasswordLineEdit}

Constructs a lineedit password widget.

`parent` Passed to lower level constructor.

### void KPasswordLineEdit::clear() {#clear}

Clear text

### QLineEdit::EchoMode KPasswordLineEdit::echoMode() const {#echoMode}

Return echo mode

> **Note:** Getter function for property [echoMode](kpasswordlineedit.md#echoMode-prop).

*See also* [setEchoMode](kpasswordlineedit.md#setEchoMode)()

### \[signal\] void KPasswordLineEdit::echoModeChanged(QLineEdit::EchoMode *echoMode*) {#echoModeChanged}

When we click on visibility icon echo mode is switched between Normal echo mode and Password echo mode

> **Note:** Notifier signal for property [echoMode](kpasswordlineedit.md#echoMode-prop).

### bool KPasswordLineEdit::isClearButtonEnabled() const {#isClearButtonEnabled}

Inform if we show or not clear button

> **Note:** Getter function for property [clearButtonEnabled](kpasswordlineedit.md#clearButtonEnabled-prop).

### \[since 6.0\] bool KPasswordLineEdit::isReadOnly() const {#isReadOnly}

Return whether the line edit is read only.

This function was introduced in Qt 6.0.

### QLineEdit \*KPasswordLineEdit::lineEdit() const {#lineEdit}

Returns the lineedit widget.

### QString KPasswordLineEdit::password() const {#password}

Returns the password entered.

> **Note:** Getter function for property [password](kpasswordlineedit.md#password-prop).

*See also* [setPassword](kpasswordlineedit.md#setPassword)()

### \[signal\] void KPasswordLineEdit::passwordChanged(const QString &*password*) {#passwordChanged}

> **Note:** Notifier signal for property [password](kpasswordlineedit.md#password-prop).

### \[since 6.0\] KPassword::RevealMode KPasswordLineEdit::revealPasswordMode() const {#revealPasswordMode}

Return when the reveal password button is visible.

This function was introduced in Qt 6.0.

*See also* [setRevealPasswordMode](kpasswordlineedit.md#setRevealPasswordMode)()

### void KPasswordLineEdit::setClearButtonEnabled(bool *clear*) {#setClearButtonEnabled}

Show/hide clear button (false by default)

> **Note:** Setter function for property [clearButtonEnabled](kpasswordlineedit.md#clearButtonEnabled-prop).

*See also* [isClearButtonEnabled](kpasswordlineedit.md#isClearButtonEnabled)()

### void KPasswordLineEdit::setEchoMode(QLineEdit::EchoMode *mode*) {#setEchoMode}

Change echo mode ([QLineEdit::Password](https://doc.qt.io/qt-6/qlineedit.html#EchoMode-enum) by default)

> **Note:** Setter function for property [echoMode](kpasswordlineedit.md#echoMode-prop).

*See also* [echoMode](kpasswordlineedit.md#echoMode)()

### void KPasswordLineEdit::setPassword(const QString &*password*) {#setPassword}

Assign password

> **Note:** Setter function for property [password](kpasswordlineedit.md#password-prop).

*See also* [password](kpasswordlineedit.md#password)()

### \[since 6.0\] void KPasswordLineEdit::setReadOnly(bool *readOnly*) {#setReadOnly}

Set whether the line edit is read only.

This function was introduced in Qt 6.0.

*See also* [isReadOnly](kpasswordlineedit.md#isReadOnly)()

### \[since 6.0\] void KPasswordLineEdit::setRevealPasswordMode(KPassword::RevealMode *revealPasswordMode*) {#setRevealPasswordMode}

Set when the reveal password button will be visible.

The default is RevealPasswordMode::OnlyNew and the reveal password button will only be visible when entering a new password.

This can be used to honor the lineedit\_reveal\_password kiosk key, for example:

```cpp
if (KAuthorized::authorize(QStringLiteral("lineedit_reveal_password"))) {
    passwordLineEdit.setRevealPasswordMode(KPasswordLineEdit::RevealPasswordMode::OnlyNew);
} else {
    passwordLineEdit.setRevealPasswordMode(KPasswordLineEdit::RevealPasswordMode::Never);
}
```

This function was introduced in Qt 6.0.

*See also* [revealPasswordMode](kpasswordlineedit.md#revealPasswordMode)()
