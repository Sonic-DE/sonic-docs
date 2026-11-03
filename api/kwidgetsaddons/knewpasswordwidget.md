---
title: "KNewPasswordWidget Class"
description: "A password input widget."
---

# KNewPasswordWidget Class

A password input widget. [More...](#details)

- **Header:** `#include <KNewPasswordWidget>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](knewpasswordwidget-members.md)  
[Deprecated members](knewpasswordwidget-obsolete.md)

## Public Types

- [enum KNewPasswordWidget::PasswordStatus](#PasswordStatus-enum)
- [\[since 6.0\] enum KNewPasswordWidget::RevealPasswordMode](#RevealPasswordMode-enum)

## Properties

- [allowEmptyPasswords : bool](#allowEmptyPasswords-prop)
- [backgroundWarningColor : QColor](#backgroundWarningColor-prop)
- [maximumPasswordLength : int](#maximumPasswordLength-prop)
- [minimumPasswordLength : int](#minimumPasswordLength-prop)
- [\[read-only\] passwordStatus : PasswordStatus](#passwordStatus-prop)
- [passwordStrengthMeterVisible : bool](#passwordStrengthMeterVisible-prop)
- [passwordStrengthWarningLevel : int](#passwordStrengthWarningLevel-prop)
- [reasonablePasswordLength : int](#reasonablePasswordLength-prop)
- [revealPasswordMode : KPassword::RevealMode](#revealPasswordMode-prop)

## Public Functions

- [KNewPasswordWidget(QWidget \*parent = nullptr)](#KNewPasswordWidget)
- [bool allowEmptyPasswords() const](#allowEmptyPasswords)
- [QColor backgroundWarningColor() const](#backgroundWarningColor)
- [bool isPasswordStrengthMeterVisible() const](#isPasswordStrengthMeterVisible)
- [int maximumPasswordLength() const](#maximumPasswordLength)
- [int minimumPasswordLength() const](#minimumPasswordLength)
- [QString password() const](#password)
- [KNewPasswordWidget::PasswordStatus passwordStatus() const](#passwordStatus)
- [int passwordStrengthWarningLevel() const](#passwordStrengthWarningLevel)
- [int reasonablePasswordLength() const](#reasonablePasswordLength)
- [KPassword::RevealMode revealPasswordMode() const](#revealPasswordMode) (since 6.0)

## Public Slots

- [void setAllowEmptyPasswords(bool allowed)](#setAllowEmptyPasswords)
- [void setBackgroundWarningColor(const QColor &color)](#setBackgroundWarningColor)
- [void setMaximumPasswordLength(int maxLength)](#setMaximumPasswordLength)
- [void setMinimumPasswordLength(int minLength)](#setMinimumPasswordLength)
- [void setPasswordStrengthMeterVisible(bool visible)](#setPasswordStrengthMeterVisible)
- [void setPasswordStrengthWarningLevel(int warningLevel)](#setPasswordStrengthWarningLevel)
- [void setReasonablePasswordLength(int reasonableLength)](#setReasonablePasswordLength)
- [void setRevealPasswordMode(KPassword::RevealMode revealPasswordMode)](#setRevealPasswordMode) (since 6.0)

## Signals

- [void passwordStatusChanged()](#passwordStatusChanged)

## Detailed Description {#details}

This widget allows the user to enter a new password.

The password has to be entered twice to check if the passwords match. A hint about the strength of the entered password is also shown.

In order to embed this widget in your custom password dialog, you may want to connect to the [passwordStatus](knewpasswordwidget.md#passwordStatus)() signal. This way you can e.g. disable the OK button if the passwords don't match, warn the user if the password is too weak, and so on.

### Usage Example {#usage-example}

#### Setup {#setup}

```cpp
KNewPasswordWidget *m_passwordWidget = new KNewPasswordWidget(this);
// set a background warning color (taken from the current color scheme)
KColorScheme colorScheme(QPalette::Active, KColorScheme::View);
m_passwordWidget->setBackgroundWarningColor(colorScheme.background(KColorScheme::NegativeBackground).color());
// listen to password status updates
connect(m_passwordWidget, &KNewPasswordWidget::passwordStatusChanged, this, &MyCustomDialog::slotPasswordStatusChanged);
...
```

#### Update your custom dialog {#update-your-custom-dialog}

TODO qdoc @snippet knewpasswordwidget\_test.cpp update\_custom\_dialog

#### Accept your custom dialog {#accept-your-custom-dialog}

TODO qdoc @snippet knewpasswordwidget\_test.cpp accept\_custom\_dialog

## Member Type Documentation {#member-type-documentation}

### enum KNewPasswordWidget::PasswordStatus {#PasswordStatus-enum}

Status of the password being typed in the widget.

| Constant | Value | Description |
| --- | --- | --- |
| `KNewPasswordWidget::EmptyPasswordNotAllowed` | `0` | Both passwords fields empty, but minimum length \> 0. |
| `KNewPasswordWidget::PasswordTooShort` | `1` | Password length is too low. |
| `KNewPasswordWidget::PasswordNotVerified` | `2` | Password and verification password don't match. |
| `KNewPasswordWidget::WeakPassword` | `3` | Passwords match but the strength level is not enough. |
| `KNewPasswordWidget::StrongPassword` | `4` | Passwords match and the strength level is good. |

### \[since 6.0\] enum KNewPasswordWidget::RevealPasswordMode {#RevealPasswordMode-enum}

This enum describe when the reveal password button is visible.

| Constant | Value | Description |
| --- | --- | --- |
| `KNewPasswordWidget::RevealPasswordMode::OnlyNew` | `0` | Display the button when entering a new password, but doesn't let you see a previously entered password. This is the default. |
| `KNewPasswordWidget::RevealPasswordMode::Never` | `1` | Never display the reveal button. |
| `KNewPasswordWidget::RevealPasswordMode::Always` | `2` | Always display the reveal button. Usefull in a password manager for example. |

This enum was introduced in Qt 6.0.

## Property Documentation {#property-documentation}

### allowEmptyPasswords : bool {#allowEmptyPasswords-prop}

**Access functions:**

- `bool` **[allowEmptyPasswords](knewpasswordwidget.md#allowEmptyPasswords)**() const
- `void` **[setAllowEmptyPasswords](knewpasswordwidget.md#setAllowEmptyPasswords)**(`bool` *allowed*)

### backgroundWarningColor : QColor {#backgroundWarningColor-prop}

**Access functions:**

- `QColor` **[backgroundWarningColor](knewpasswordwidget.md#backgroundWarningColor)**() const
- `void` **[setBackgroundWarningColor](knewpasswordwidget.md#setBackgroundWarningColor)**(const `QColor` &*color*)

### maximumPasswordLength : int {#maximumPasswordLength-prop}

**Access functions:**

- `int` **[maximumPasswordLength](knewpasswordwidget.md#maximumPasswordLength)**() const
- `void` **[setMaximumPasswordLength](knewpasswordwidget.md#setMaximumPasswordLength)**(`int` *maxLength*)

### minimumPasswordLength : int {#minimumPasswordLength-prop}

**Access functions:**

- `int` **[minimumPasswordLength](knewpasswordwidget.md#minimumPasswordLength)**() const
- `void` **[setMinimumPasswordLength](knewpasswordwidget.md#setMinimumPasswordLength)**(`int` *minLength*)

### \[read-only\] passwordStatus : PasswordStatus {#passwordStatus-prop}

**Access functions:**

- `KNewPasswordWidget::PasswordStatus` **[passwordStatus](knewpasswordwidget.md#passwordStatus)**() const

### passwordStrengthMeterVisible : bool {#passwordStrengthMeterVisible-prop}

**Access functions:**

- `bool` **[isPasswordStrengthMeterVisible](knewpasswordwidget.md#isPasswordStrengthMeterVisible)**() const
- `void` **[setPasswordStrengthMeterVisible](knewpasswordwidget.md#setPasswordStrengthMeterVisible)**(`bool` *visible*)

### passwordStrengthWarningLevel : int {#passwordStrengthWarningLevel-prop}

**Access functions:**

- `int` **[passwordStrengthWarningLevel](knewpasswordwidget.md#passwordStrengthWarningLevel)**() const
- `void` **[setPasswordStrengthWarningLevel](knewpasswordwidget.md#setPasswordStrengthWarningLevel)**(`int` *warningLevel*)

### reasonablePasswordLength : int {#reasonablePasswordLength-prop}

**Access functions:**

- `int` **[reasonablePasswordLength](knewpasswordwidget.md#reasonablePasswordLength)**() const
- `void` **[setReasonablePasswordLength](knewpasswordwidget.md#setReasonablePasswordLength)**(`int` *reasonableLength*)

### revealPasswordMode : KPassword::RevealMode {#revealPasswordMode-prop}

**Access functions:**

- `KPassword::RevealMode` **[revealPasswordMode](knewpasswordwidget.md#revealPasswordMode)**() const
- `void` **[setRevealPasswordMode](knewpasswordwidget.md#setRevealPasswordMode)**(`KPassword::RevealMode` *revealPasswordMode*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KNewPasswordWidget::KNewPasswordWidget(QWidget \**parent* = nullptr) {#KNewPasswordWidget}

Constructs a password widget.

`parent` Passed to lower level constructor.

### bool KNewPasswordWidget::allowEmptyPasswords() const {#allowEmptyPasswords}

Allow empty passwords?

Returns `true` if [minimumPasswordLength](knewpasswordwidget.md#minimumPasswordLength)() == 0

> **Note:** Getter function for property [allowEmptyPasswords](knewpasswordwidget.md#allowEmptyPasswords-prop).

*See also* [setAllowEmptyPasswords](knewpasswordwidget.md#setAllowEmptyPasswords)()

### QColor KNewPasswordWidget::backgroundWarningColor() const {#backgroundWarningColor}

The color used as warning for the verification password field's background.

> **Note:** Getter function for property [backgroundWarningColor](knewpasswordwidget.md#backgroundWarningColor-prop).

*See also* [setBackgroundWarningColor](knewpasswordwidget.md#setBackgroundWarningColor)()

### bool KNewPasswordWidget::isPasswordStrengthMeterVisible() const {#isPasswordStrengthMeterVisible}

Whether the password strength meter is visible.

> **Note:** Getter function for property [passwordStrengthMeterVisible](knewpasswordwidget.md#passwordStrengthMeterVisible-prop).

### int KNewPasswordWidget::maximumPasswordLength() const {#maximumPasswordLength}

Maximum acceptable password length.

> **Note:** Getter function for property [maximumPasswordLength](knewpasswordwidget.md#maximumPasswordLength-prop).

*See also* [setMaximumPasswordLength](knewpasswordwidget.md#setMaximumPasswordLength)()

### int KNewPasswordWidget::minimumPasswordLength() const {#minimumPasswordLength}

Minimum acceptable password length.

> **Note:** Getter function for property [minimumPasswordLength](knewpasswordwidget.md#minimumPasswordLength-prop).

*See also* [setMinimumPasswordLength](knewpasswordwidget.md#setMinimumPasswordLength)()

### QString KNewPasswordWidget::password() const {#password}

Returns the password entered.

> **Note:** Only returns meaningful data when [passwordStatus](knewpasswordwidget.md#passwordStatus) is either [WeakPassword](knewpasswordwidget.md#PasswordStatus-enum) or [StrongPassword](knewpasswordwidget.md#PasswordStatus-enum).

### KNewPasswordWidget::PasswordStatus KNewPasswordWidget::passwordStatus() const {#passwordStatus}

The current status of the password in the widget.

> **Note:** Getter function for property [passwordStatus](knewpasswordwidget.md#passwordStatus-prop).

### \[signal\] void KNewPasswordWidget::passwordStatusChanged() {#passwordStatusChanged}

Notify about the current status of the password being typed.

### int KNewPasswordWidget::passwordStrengthWarningLevel() const {#passwordStrengthWarningLevel}

Password strength level below which a warning is given

> **Note:** Getter function for property [passwordStrengthWarningLevel](knewpasswordwidget.md#passwordStrengthWarningLevel-prop).

*See also* [setPasswordStrengthWarningLevel](knewpasswordwidget.md#setPasswordStrengthWarningLevel)()

### int KNewPasswordWidget::reasonablePasswordLength() const {#reasonablePasswordLength}

Password length that is expected to be reasonably safe.

> **Note:** Getter function for property [reasonablePasswordLength](knewpasswordwidget.md#reasonablePasswordLength-prop).

*See also* [setReasonablePasswordLength](knewpasswordwidget.md#setReasonablePasswordLength)()

### \[since 6.0\] KPassword::RevealMode KNewPasswordWidget::revealPasswordMode() const {#revealPasswordMode}

Whether the visibility trailing action in the line edit is visible.

> **Note:** Getter function for property [revealPasswordMode](knewpasswordwidget.md#revealPasswordMode-prop).

This function was introduced in Qt 6.0.

*See also* [setRevealPasswordMode](knewpasswordwidget.md#setRevealPasswordMode)()

### \[slot\] void KNewPasswordWidget::setAllowEmptyPasswords(bool *allowed*) {#setAllowEmptyPasswords}

Allow empty passwords? - Default: true

same as [setMinimumPasswordLength](knewpasswordwidget.md#setMinimumPasswordLength)( allowed ? 0 : 1 )

> **Note:** Setter function for property [allowEmptyPasswords](knewpasswordwidget.md#allowEmptyPasswords-prop).

*See also* [allowEmptyPasswords](knewpasswordwidget.md#allowEmptyPasswords)()

### \[slot\] void KNewPasswordWidget::setBackgroundWarningColor(const QColor &*color*) {#setBackgroundWarningColor}

When the verification password does not match, the background color of the verification field is set to @p color. As soon as the passwords match, the original color of the verification field is restored.

> **Note:** Setter function for property [backgroundWarningColor](knewpasswordwidget.md#backgroundWarningColor-prop).

*See also* [backgroundWarningColor](knewpasswordwidget.md#backgroundWarningColor)()

### \[slot\] void KNewPasswordWidget::setMaximumPasswordLength(int *maxLength*) {#setMaximumPasswordLength}

Maximum acceptable password length.

`maxLength` The new maximum password length.

> **Note:** Setter function for property [maximumPasswordLength](knewpasswordwidget.md#maximumPasswordLength-prop).

*See also* [maximumPasswordLength](knewpasswordwidget.md#maximumPasswordLength)()

### \[slot\] void KNewPasswordWidget::setMinimumPasswordLength(int *minLength*) {#setMinimumPasswordLength}

Minimum acceptable password length.

Default: 0

`minLength` The new minimum password length

> **Note:** Setter function for property [minimumPasswordLength](knewpasswordwidget.md#minimumPasswordLength-prop).

*See also* [minimumPasswordLength](knewpasswordwidget.md#minimumPasswordLength)()

### \[slot\] void KNewPasswordWidget::setPasswordStrengthMeterVisible(bool *visible*) {#setPasswordStrengthMeterVisible}

Whether to show the password strength meter (label and progress bar). Default is true.

> **Note:** Setter function for property [passwordStrengthMeterVisible](knewpasswordwidget.md#passwordStrengthMeterVisible-prop).

*See also* [isPasswordStrengthMeterVisible](knewpasswordwidget.md#isPasswordStrengthMeterVisible)()

### \[slot\] void KNewPasswordWidget::setPasswordStrengthWarningLevel(int *warningLevel*) {#setPasswordStrengthWarningLevel}

Set the password strength level below which a warning is given The value is guaranteed to be in the range from 0 to 99. Empty passwords score 0; non-empty passwords score up to 100, depending on their length and whether they contain numbers, mixed case letters and punctuation.

Default: 1 - warn if the password has no discernible strength whatsoever

`warningLevel` The level below which a warning should be given.

> **Note:** Setter function for property [passwordStrengthWarningLevel](knewpasswordwidget.md#passwordStrengthWarningLevel-prop).

*See also* [passwordStrengthWarningLevel](knewpasswordwidget.md#passwordStrengthWarningLevel)()

### \[slot\] void KNewPasswordWidget::setReasonablePasswordLength(int *reasonableLength*) {#setReasonablePasswordLength}

Password length that is expected to be reasonably safe. The value is guaranteed to be in the range from 1 to [maximumPasswordLength](knewpasswordwidget.md#maximumPasswordLength)().

Used to compute the strength level

Default: 8 - the standard UNIX password length

`reasonableLength` The new reasonable password length.

> **Note:** Setter function for property [reasonablePasswordLength](knewpasswordwidget.md#reasonablePasswordLength-prop).

*See also* [reasonablePasswordLength](knewpasswordwidget.md#reasonablePasswordLength)()

### \[slot, since 6.0\] void KNewPasswordWidget::setRevealPasswordMode(KPassword::RevealMode *revealPasswordMode*) {#setRevealPasswordMode}

Set when the reveal password button will be visible.

The default is [RevealPasswordMode::OnlyNew](knewpasswordwidget.md#RevealPasswordMode-enum) and the reveal password button will only be visible when entering a new password.

This can be used to honor the lineedit\_reveal\_password kiosk key, for example:

```cpp
if (KAuthorized::authorize(QStringLiteral("lineedit_reveal_password"))) {
    newPasswordWidget.setRevealPasswordMode(KPassword::RevealMode::OnlyNew);
} else {
    newPasswordWidget.setRevealPasswordMode(KPassword::RevealMode::Never);
}
```

> **Note:** Setter function for property [revealPasswordMode](knewpasswordwidget.md#revealPasswordMode-prop).

This function was introduced in Qt 6.0.

*See also* [revealPasswordMode](knewpasswordwidget.md#revealPasswordMode)()
