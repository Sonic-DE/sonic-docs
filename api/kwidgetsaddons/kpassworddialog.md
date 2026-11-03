---
title: "KPasswordDialog Class"
description: "A dialog for requesting a password and optionally a login from the end user."
---

# KPasswordDialog Class

A dialog for requesting a password and optionally a login from the end user. [More...](#details)

- **Header:** `#include <KPasswordDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](kpassworddialog-members.md)  
[Deprecated members](kpassworddialog-obsolete.md)

## Public Types

- [enum KPasswordDialog::ErrorType](#ErrorType-enum)
- [enum KPasswordDialog::KPasswordDialogFlag](#KPasswordDialogFlag-enum)

## Public Functions

- [KPasswordDialog(QWidget \*parent = nullptr, const KPasswordDialog::KPasswordDialogFlags &flags = KPasswordDialog::NoFlags)](#KPasswordDialog)
- [void addCommentLine(const QString &label, const QString &comment)](#addCommentLine)
- [bool anonymousMode() const](#anonymousMode)
- [QDialogButtonBox \*buttonBox() const](#buttonBox)
- [QString domain() const](#domain)
- [QIcon icon() const](#icon)
- [bool keepPassword() const](#keepPassword)
- [QString password() const](#password)
- [QString prompt() const](#prompt)
- [KPassword::RevealMode revealPasswordMode() const](#revealPasswordMode) (since 6.0)
- [void setAnonymousMode(bool anonymous)](#setAnonymousMode)
- [void setDomain(const QString &)](#setDomain)
- [void setIcon(const QIcon &icon)](#setIcon)
- [void setKeepPassword(bool b)](#setKeepPassword)
- [void setKnownLogins(const QMap\<QString, QString\> &knownLogins)](#setKnownLogins)
- [void setPassword(const QString &password)](#setPassword)
- [void setPrompt(const QString &prompt)](#setPrompt)
- [void setRevealPasswordMode(KPassword::RevealMode revealPasswordMode)](#setRevealPasswordMode) (since 6.0)
- [void setUsername(const QString &)](#setUsername)
- [void setUsernameContextHelp(const QString &help)](#setUsernameContextHelp)
- [void setUsernameReadOnly(bool readOnly)](#setUsernameReadOnly)
- [void showErrorMessage(const QString &message, const KPasswordDialog::ErrorType type = PasswordError)](#showErrorMessage)
- [QString username() const](#username)

## Signals

- [void gotPassword(const QString &password, bool keep)](#gotPassword)
- [void gotUsernameAndPassword(const QString &username, const QString &password, bool keep)](#gotUsernameAndPassword)

## Protected Functions

- [bool checkPassword()](#checkPassword)

## Detailed Description {#details}

### Usage Example {#usage-example}

Requesting a simple password, asynchronous

```cpp
KPasswordDialog *dlg = new KPasswordDialog(parent);
dlg->setPrompt(i18n("Enter a password"));
connect(dlg, &KPasswordDialog::gotPassword,
        this, [this](const QString &password) { setPassword(password); });
connect(dlg, &QDialog::rejected, this, [this]() { slotCancel(); });
dlg->show();
```

Requesting a login and a password, synchronous

```cpp
KPasswordDialog dlg(parent, KPasswordDialog::ShowUsernameLine);
dlg.setPrompt(i18n("Enter a login and a password"));
if(!dlg.exec()) {
    return; //the user canceled
}
use(dlg.username(), dlg.password());
```

## Member Type Documentation {#member-type-documentation}

### enum KPasswordDialog::ErrorType {#ErrorType-enum}

| Constant | Value |   |
| --- | --- | --- |
| `KPasswordDialog::UnknownError` | `0` |   |
| `KPasswordDialog::UsernameError` | `1` | A problem with the user name as entered |
| `KPasswordDialog::PasswordError` | `2` | Incorrect password |
| `KPasswordDialog::FatalError` | `3` | Error preventing further attempts, will result in disabling most of the interface |
| `KPasswordDialog::DomainError (since Qt 4.1)` | `4` | A problem with the domain as entered |

### enum KPasswordDialog::KPasswordDialogFlag {#KPasswordDialogFlag-enum}

**flags KPasswordDialog::KPasswordDialogFlags**

| Constant | Value |   |
| --- | --- | --- |
| `KPasswordDialog::NoFlags` | `0x00` |   |
| `KPasswordDialog::ShowKeepPassword` | `0x01` | If this flag is set, the "keep this password" checkbox will been shown, otherwise, it will not be shown and [keepPassword](kpassworddialog.md#keepPassword) will have no effect. |
| `KPasswordDialog::ShowUsernameLine` | `0x02` | If this flag is set, there will be an additional line to let the user enter his login, otherwise, only the password line will be shown. |
| `KPasswordDialog::UsernameReadOnly` | `0x04` | If this flag is set, the login lineedit will be in read only mode. |
| `KPasswordDialog::ShowAnonymousLoginCheckBox (since Qt 4.1)` | `0x08` | If this flag is set, the Anonymous Login checkbox will be displayed |
| `KPasswordDialog::ShowDomainLine (since Qt 4.1)` | `0x10` | If this flag is set, there will be an additional line to let the user enter the domain. |
| `KPasswordDialog::DomainReadOnly (since Qt 4.1)` | `0x20` | If this flag is set, the domain lineedit will be in read only mode. |

The `KPasswordDialogFlags` type is a typedef for `QFlags<KPasswordDialogFlag>. `It stores an OR combination of `KPasswordDialogFlag` values.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KPasswordDialog::KPasswordDialog(QWidget \**parent* = nullptr, const KPasswordDialog::KPasswordDialogFlags &*flags* = KPasswordDialog::NoFlags) {#KPasswordDialog}

create a password dialog

`parent` the parent widget

`flags` a set of [KPasswordDialogFlag](kpassworddialog.md#KPasswordDialogFlag-enum) flags

### void KPasswordDialog::addCommentLine(const QString &*label*, const QString &*comment*) {#addCommentLine}

Adds a comment line to the dialog.

This function allows you to add one additional comment line to this widget. Calling this function after a comment has already been added will not have any effect.

`label` label for comment (ex:"Command:")

`comment` the actual comment text.

### bool KPasswordDialog::anonymousMode() const {#anonymousMode}

Returns whether anonymous mode has been selected.

*See also* [setAnonymousMode](kpassworddialog.md#setAnonymousMode)()

### QDialogButtonBox \*KPasswordDialog::buttonBox() const {#buttonBox}

Returns the button box used in the dialog. This can be used to add new buttons.

### \[virtual protected\] bool KPasswordDialog::checkPassword() {#checkPassword}

Virtual function that can be overridden to provide password checking in derived classes. It should return `true` if the password is valid, `false` otherwise.

### QString KPasswordDialog::domain() const {#domain}

Returns the domain entered by the user.

*See also* [setDomain](kpassworddialog.md#setDomain)()

### \[signal\] void KPasswordDialog::gotPassword(const QString &*password*, bool *keep*) {#gotPassword}

emitted when the dialog has been accepted

`password` the entered password

`keep` true if the "remember password" checkbox was checked, false otherwise. false if [ShowKeepPassword](kpassworddialog.md#KPasswordDialogFlag-enum) was not set in the constructor

### \[signal\] void KPasswordDialog::gotUsernameAndPassword(const QString &*username*, const QString &*password*, bool *keep*) {#gotUsernameAndPassword}

emitted when the dialog has been accepted, and [ShowUsernameLine](kpassworddialog.md#KPasswordDialogFlag-enum) was set on the constructor

`username` the entered username

`password` the entered password

`keep` true if the "remember password" checkbox was checked, false otherwise. false if [ShowKeepPassword](kpassworddialog.md#KPasswordDialogFlag-enum) was not set in the constructor

### QIcon KPasswordDialog::icon() const {#icon}

Returns the icon that appears next to the prompt.

*See also* [setIcon](kpassworddialog.md#setIcon)()

### bool KPasswordDialog::keepPassword() const {#keepPassword}

Determines whether supplied authorization should persist even after the application has been closed.

this is set with the check password checkbox is the ShowKeepCheckBox flag is set in the constructor, if it is not set, this function return false

Returns whether to keep the password

*See also* [setKeepPassword](kpassworddialog.md#setKeepPassword)()

### QString KPasswordDialog::password() const {#password}

Returns the password entered by the user.

*See also* [setPassword](kpassworddialog.md#setPassword)()

### QString KPasswordDialog::prompt() const {#prompt}

Returns the prompt

*See also* [setPrompt](kpassworddialog.md#setPrompt)()

### \[since 6.0\] KPassword::RevealMode KPasswordDialog::revealPasswordMode() const {#revealPasswordMode}

Return when the reveal password button is visible.

This function was introduced in Qt 6.0.

*See also* [setRevealPasswordMode](kpassworddialog.md#setRevealPasswordMode)()

### void KPasswordDialog::setAnonymousMode(bool *anonymous*) {#setAnonymousMode}

set anonymous mode (all other fields will be grayed out)

*See also* [anonymousMode](kpassworddialog.md#anonymousMode)()

### void KPasswordDialog::setDomain(*const QString &*) {#setDomain}

set the default domain.

*See also* [domain](kpassworddialog.md#domain)()

### void KPasswordDialog::setIcon(const QIcon &*icon*) {#setIcon}

Set the icon that appears next to the prompt.

*See also* [icon](kpassworddialog.md#icon)()

### void KPasswordDialog::setKeepPassword(bool *b*) {#setKeepPassword}

Check or uncheck the "keep password" checkbox. This can be used to check it before showing the dialog, to tell the user that the password is stored already (e.g. in the wallet). enableKeep must have been set to true in the constructor.

has only effect if ShowKeepCheckBox is set in the constructor

*See also* [keepPassword](kpassworddialog.md#keepPassword)()

### void KPasswordDialog::setKnownLogins(const QMap\<QString, QString\> &*knownLogins*) {#setKnownLogins}

Presets a number of login+password pairs that the user can choose from.

The passwords can be empty if you simply want to offer usernames to choose from.

This require the flag [ShowUsernameLine](kpassworddialog.md#KPasswordDialogFlag-enum) to be set in the constructoe, and not the flag [UsernameReadOnly](kpassworddialog.md#KPasswordDialogFlag-enum)

`knownLogins` map of known logins: the keys are usernames, the values are passwords.

### void KPasswordDialog::setPassword(const QString &*password*) {#setPassword}

Presets the password.

If the password is not empty, the ability to show the password will not be available.

`password` the password to set

*See also* [password](kpassworddialog.md#password)()

### void KPasswordDialog::setPrompt(const QString &*prompt*) {#setPrompt}

Sets the prompt to show to the user.

`prompt` instructional text to be shown.

*See also* [prompt](kpassworddialog.md#prompt)()

### \[since 6.0\] void KPasswordDialog::setRevealPasswordMode(KPassword::RevealMode *revealPasswordMode*) {#setRevealPasswordMode}

Set when the reveal password button will be visible.

The default is RevealMode::OnlyNew and the reveal password button will only be visible when entering a new password.

This can be used to honor the lineedit\_reveal\_password kiosk key, for example:

```cpp
if (KAuthorized::authorize(QStringLiteral("lineedit_reveal_password"))) {
    passwordDialog.setRevealPasswordMode(KPassword::RevealMode::OnlyNew);
} else {
    passwordDialog.setRevealPasswordMode(KPassword::RevealMode::Never);
}
```

This function was introduced in Qt 6.0.

*See also* [revealPasswordMode](kpassworddialog.md#revealPasswordMode)()

### void KPasswordDialog::setUsername(*const QString &*) {#setUsername}

set the default username.

*See also* [username](kpassworddialog.md#username)()

### void KPasswordDialog::setUsernameContextHelp(const QString &*help*) {#setUsernameContextHelp}

Sets contextual help for the username input field. This displays a somewhat visual hint in the UI giving very visible access to a whats-this style input description for the user name line. This is particularly useful when the user name may require or support special input syntax. For example windows-like auth dialogs supports multiple different logon name syntax.

### void KPasswordDialog::setUsernameReadOnly(bool *readOnly*) {#setUsernameReadOnly}

Sets the username field read-only and sets the focus to the password field.

this can also be set by passing [UsernameReadOnly](kpassworddialog.md#KPasswordDialogFlag-enum) as flag in the constructor

`readOnly` true to set the user field to read-only

### void KPasswordDialog::showErrorMessage(const QString &*message*, const KPasswordDialog::ErrorType *type* = PasswordError) {#showErrorMessage}

Shows an error message in the dialog box. Prevents having to show a dialog-on-a-dialog.

`message` the error message to show

### QString KPasswordDialog::username() const {#username}

Returns the username entered by the user.

*See also* [setUsername](kpassworddialog.md#setUsername)()
