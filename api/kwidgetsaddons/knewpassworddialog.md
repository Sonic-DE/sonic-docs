---
title: "KNewPasswordDialog Class"
description: "A password input dialog."
---

# KNewPasswordDialog Class

A password input dialog. [More...](#details)

- **Header:** `#include <KNewPasswordDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](knewpassworddialog-members.md)  
[Deprecated members](knewpassworddialog-obsolete.md)

## Properties

- [\[since 6.0\] revealPasswordMode : KPassword::RevealMode](#revealPasswordMode-prop)

## Public Functions

- [KNewPasswordDialog(QWidget \*parent = nullptr)](#KNewPasswordDialog)
- [bool allowEmptyPasswords() const](#allowEmptyPasswords)
- [QColor backgroundWarningColor() const](#backgroundWarningColor)
- [QIcon icon() const](#icon)
- [int maximumPasswordLength() const](#maximumPasswordLength)
- [int minimumPasswordLength() const](#minimumPasswordLength)
- [QString password() const](#password)
- [int passwordStrengthWarningLevel() const](#passwordStrengthWarningLevel)
- [QString prompt() const](#prompt)
- [int reasonablePasswordLength() const](#reasonablePasswordLength)
- [KPassword::RevealMode revealPasswordMode() const](#revealPasswordMode) (since 6.0)
- [void setAllowEmptyPasswords(bool allowed)](#setAllowEmptyPasswords)
- [void setBackgroundWarningColor(const QColor &color)](#setBackgroundWarningColor)
- [void setIcon(const QIcon &icon)](#setIcon)
- [void setMaximumPasswordLength(int maxLength)](#setMaximumPasswordLength)
- [void setMinimumPasswordLength(int minLength)](#setMinimumPasswordLength)
- [void setPasswordStrengthWarningLevel(int warningLevel)](#setPasswordStrengthWarningLevel)
- [void setPrompt(const QString &prompt)](#setPrompt)
- [void setReasonablePasswordLength(int reasonableLength)](#setReasonablePasswordLength)
- [void setRevealPasswordMode(KPassword::RevealMode revealPasswordMode)](#setRevealPasswordMode) (since 6.0)

## Signals

- [void newPassword(const QString &password)](#newPassword)

## Protected Functions

- [bool checkAndGetPassword(QString \*pwd)](#checkAndGetPassword)
- [bool checkPassword(const QString &)](#checkPassword)

## Detailed Description {#details}

This dialog asks the user to enter a new password.

The password has to be entered twice to check if the passwords match. A hint about the strength of the entered password is also shown.

### Usage Example {#usage-example}

#### Asynchronous {#asynchronous}

```cpp
KNewPasswordDialog *dlg = new KNewPasswordDialog( parent );
dlg->setPrompt(i18n("Enter a password"));
connect(dlg, &KNewPasswordDialog::newPassword, this, [this](const QString &pass) { setPassword(pass); });
connect(dlg, &QDialog::rejected, this, [this]() { slotCancel(); });
dlg->show();
```

#### Synchronous {#synchronous}

```cpp
KNewPasswordDialog dlg(parent);
dlg.setPrompt(i18n("Enter a password"));
if(dlg.exec()) {
    setPassword(dlg.password());
}
```

## Property Documentation {#property-documentation}

### \[since 6.0\] revealPasswordMode : KPassword::RevealMode {#revealPasswordMode-prop}

This property was introduced in Qt 6.0.

**Access functions:**

- `KPassword::RevealMode` **[revealPasswordMode](knewpassworddialog.md#revealPasswordMode)**() const
- `void` **[setRevealPasswordMode](knewpassworddialog.md#setRevealPasswordMode)**(`KPassword::RevealMode` *revealPasswordMode*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KNewPasswordDialog::KNewPasswordDialog(QWidget \**parent* = nullptr) {#KNewPasswordDialog}

Constructs a password dialog.

`parent` Passed to lower level constructor.

### bool KNewPasswordDialog::allowEmptyPasswords() const {#allowEmptyPasswords}

Allow empty passwords?

Returns `true` if [minimumPasswordLength](knewpassworddialog.md#minimumPasswordLength)() == 0

*See also* [setAllowEmptyPasswords](knewpassworddialog.md#setAllowEmptyPasswords)()

### QColor KNewPasswordDialog::backgroundWarningColor() const {#backgroundWarningColor}

The color used as warning for the verification password field's background.

*See also* [setBackgroundWarningColor](knewpassworddialog.md#setBackgroundWarningColor)()

### \[protected\] bool KNewPasswordDialog::checkAndGetPassword(QString \**pwd*) {#checkAndGetPassword}

Checks input password. If the password is right, returns true and fills pwd with the password. Otherwise returns false and pwd will be null.

### \[virtual protected\] bool KNewPasswordDialog::checkPassword(*const QString &*) {#checkPassword}

Virtual function that can be overridden to provide password checking in derived classes. It should return `true` if the password is valid, `false` otherwise.

### QIcon KNewPasswordDialog::icon() const {#icon}

Returns the icon that appears next to the prompt in the dialog. The default icon represents a simple key.

*See also* [setIcon](knewpassworddialog.md#setIcon)()

### int KNewPasswordDialog::maximumPasswordLength() const {#maximumPasswordLength}

Maximum acceptable password length.

*See also* [setMaximumPasswordLength](knewpassworddialog.md#setMaximumPasswordLength)()

### int KNewPasswordDialog::minimumPasswordLength() const {#minimumPasswordLength}

Minimum acceptable password length.

*See also* [setMinimumPasswordLength](knewpassworddialog.md#setMinimumPasswordLength)()

### \[signal\] void KNewPasswordDialog::newPassword(const QString &*password*) {#newPassword}

The dialog has been accepted, and the new password is `password`

### QString KNewPasswordDialog::password() const {#password}

Returns the password entered.

> **Note:** Only has meaningful data after accept has been called if you want to access the password from a subclass use [checkAndGetPassword](knewpassworddialog.md#checkAndGetPassword)()

### int KNewPasswordDialog::passwordStrengthWarningLevel() const {#passwordStrengthWarningLevel}

Password strength level below which a warning is given

*See also* [setPasswordStrengthWarningLevel](knewpassworddialog.md#setPasswordStrengthWarningLevel)()

### QString KNewPasswordDialog::prompt() const {#prompt}

Returns the password prompt.

*See also* [setPrompt](knewpassworddialog.md#setPrompt)()

### int KNewPasswordDialog::reasonablePasswordLength() const {#reasonablePasswordLength}

Password length that is expected to be reasonably safe.

*See also* [setReasonablePasswordLength](knewpassworddialog.md#setReasonablePasswordLength)()

### \[since 6.0\] KPassword::RevealMode KNewPasswordDialog::revealPasswordMode() const {#revealPasswordMode}

Whether the visibility trailing action in the line edit is visible.

> **Note:** Getter function for property [revealPasswordMode](knewpassworddialog.md#revealPasswordMode-prop).

This function was introduced in Qt 6.0.

*See also* [setRevealPasswordMode](knewpassworddialog.md#setRevealPasswordMode)()

### void KNewPasswordDialog::setAllowEmptyPasswords(bool *allowed*) {#setAllowEmptyPasswords}

Allow empty passwords? - Default: true

same as [setMinimumPasswordLength](knewpassworddialog.md#setMinimumPasswordLength)( allowed ? 0 : 1 )

*See also* [allowEmptyPasswords](knewpassworddialog.md#allowEmptyPasswords)()

### void KNewPasswordDialog::setBackgroundWarningColor(const QColor &*color*) {#setBackgroundWarningColor}

When the verification password does not match, the background color of the verification field is set to `color`. As soon as the passwords match, the original color of the verification field is restored.

Default: the background color from the current theme.

*See also* [backgroundWarningColor](knewpassworddialog.md#backgroundWarningColor)()

### void KNewPasswordDialog::setIcon(const QIcon &*icon*) {#setIcon}

Sets the icon that appears next to the prompt in the dialog. The default icon represents a simple key.

*See also* [icon](knewpassworddialog.md#icon)()

### void KNewPasswordDialog::setMaximumPasswordLength(int *maxLength*) {#setMaximumPasswordLength}

Maximum acceptable password length.

`maxLength` The new maximum password length.

*See also* [maximumPasswordLength](knewpassworddialog.md#maximumPasswordLength)()

### void KNewPasswordDialog::setMinimumPasswordLength(int *minLength*) {#setMinimumPasswordLength}

Minimum acceptable password length.

Default: 0

`minLength` The new minimum password length

*See also* [minimumPasswordLength](knewpassworddialog.md#minimumPasswordLength)()

### void KNewPasswordDialog::setPasswordStrengthWarningLevel(int *warningLevel*) {#setPasswordStrengthWarningLevel}

Set the password strength level below which a warning is given Value is in the range 0 to 99. Empty passwords score 0; non-empty passwords score up to 100, depending on their length and whether they contain numbers, mixed case letters and punctuation.

Default: 1 - warn if the password has no discernible strength whatsoever

`warningLevel` The level below which a warning should be given.

*See also* [passwordStrengthWarningLevel](knewpassworddialog.md#passwordStrengthWarningLevel)()

### void KNewPasswordDialog::setPrompt(const QString &*prompt*) {#setPrompt}

Sets the password prompt.

*See also* [prompt](knewpassworddialog.md#prompt)()

### void KNewPasswordDialog::setReasonablePasswordLength(int *reasonableLength*) {#setReasonablePasswordLength}

Password length that is expected to be reasonably safe.

Used to compute the strength level

Default: 8 - the standard UNIX password length

`reasonableLength` The new reasonable password length.

*See also* [reasonablePasswordLength](knewpassworddialog.md#reasonablePasswordLength)()

### \[since 6.0\] void KNewPasswordDialog::setRevealPasswordMode(KPassword::RevealMode *revealPasswordMode*) {#setRevealPasswordMode}

Set when the reveal password button will be visible.

The default is RevealPasswordMode::OnlyNew and the reveal password button will only be visible when entering a new password.

This can be used to honor the lineedit\_reveal\_password kiosk key, for example:

```cpp
if (KAuthorized::authorize(QStringLiteral("lineedit_reveal_password"))) {
    newPasswordDialog.setRevealPasswordMode(KPassword::RevealMode::OnlyNew);
} else {
    newPasswordDialog.setRevealPasswordMode(KPassword::RevealMode::Never);
}
```

> **Note:** Setter function for property [revealPasswordMode](knewpassworddialog.md#revealPasswordMode-prop).

This function was introduced in Qt 6.0.

*See also* [revealPasswordMode](knewpassworddialog.md#revealPasswordMode)()
