---
title: "KMessageBox Namespace"
description: "Easy message dialog box."
---

# KMessageBox Namespace

Easy message dialog box. [More...](#details)

- **Header:** `#include <KMessageBox>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`

## Detailed Description {#details}

Provides convenience functions for some i18n'ed standard dialogs, as well as audible notification via KNotification

The text in message boxes is wrapped automatically. The text may either be plaintext or richtext. If the text is plaintext, a newline-character may be used to indicate the end of a paragraph.

## Type Documentation {#type-documentation}

### enum KMessageBox::ButtonCode {#ButtonCode-enum}

Button types.

| Constant | Value | Description |
| --- | --- | --- |
| `KMessageBox::Ok` | `1` | Ok button |
| `KMessageBox::Cancel` | `2` | Cancel button |
| `KMessageBox::PrimaryAction (since Qt 5.100)` | `3` | Primary action button |
| `KMessageBox::SecondaryAction (since Qt 5.100)` | `4` | Secondary action button |
| `KMessageBox::Continue` | `5` | Continue button |

### enum KMessageBox::DialogType {#DialogType-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KMessageBox::QuestionTwoActions (since Qt 5.100)` | `1` | Question dialog with two buttons |
| `KMessageBox::WarningTwoActions (since Qt 5.100)` | `2` | Warning dialog with two buttons |
| `KMessageBox::WarningContinueCancel` | `3` | Warning dialog with Continue and Cancel |
| `KMessageBox::WarningTwoActionsCancel (since Qt 5.100)` | `4` | Warning dialog with two buttons and Cancel |
| `KMessageBox::Information` | `5` | Information dialog |
| `KMessageBox::Error` | `8` | Error dialog |
| `KMessageBox::QuestionTwoActionsCancel (since Qt 5.100)` | `9` | Question dialog with two buttons and Cancel |

### enum KMessageBox::Option {#Option-enum}

**flags KMessageBox::Options**

| Constant | Value | Description |
| --- | --- | --- |
| `KMessageBox::Notify` | `1` | Emit a KNotify event |
| `KMessageBox::AllowLink` | `2` | The message may contain links. |
| `KMessageBox::Dangerous` | `4` | The action to be confirmed by the dialog is a potentially destructive one. The default button will be set to Cancel or [SecondaryAction](kmessagebox.md#ButtonCode-enum), depending on which is available. |
| `KMessageBox::NoExec` | `16` | Do not call exec() in [createKMessageBox](kmessagebox.md#createKMessageBox)() |
| `KMessageBox::WindowModal` | `32` | The window is to be modal relative to its parent. By default, it is application modal. |
| `KMessageBox::PlainText (since Qt 6.9)` | `64` | The label content should be considered as plain text. This should be used when the text comes from untrusted user input. |

The `Options` type is a typedef for `QFlags<Option>. `It stores an OR combination of `Option` values.

## Function Documentation {#function-documentation}

### QDialogButtonBox::StandardButton KMessageBox::createKMessageBox(QDialog \**dialog*, QDialogButtonBox \**buttons*, QMessageBox::Icon *icon*, const QString &*text*, const QStringList &*strlist*, const QString &*ask*, bool \**checkboxReturn*, KMessageBox::Options *options*, const QString &*details* = QString()) {#createKMessageBox}

Create content and layout of a standard dialog

`dialog` The parent dialog base

`buttons` a [QDialogButtonBox](https://doc.qt.io/qt-6/qdialogbuttonbox.html) instance. This function will take care of connecting to it.

`icon` Which predefined icon the message box shall show.

`text` Message string.

`strlist` List of strings to be written in the listbox. If the list is empty, it doesn't show any listbox

`ask` The text of the checkbox. If empty none will be shown.

`checkboxReturn` The result of the checkbox. If it's initially true then the checkbox will be checked by default. May be a null pointer. Incompatible with [NoExec](kmessagebox.md#Option-enum).

`options` see Options

`details` Detailed message string.

Returns a [QDialogButtonBox::StandardButton](https://doc.qt.io/qt-6/qdialogbuttonbox.html#StandardButton-enum) button code, not a [KMessageBox](kmessagebox.md) button code, based on the buttonmask given to the constructor of the `dialog` (ie. will return [QDialogButtonBox::Yes](https://doc.qt.io/qt-6/qdialogbuttonbox.html#StandardButton-enum) instead of [KMessageBox::PrimaryAction](kmessagebox.md#ButtonCode-enum)). Will return [QDialogButtonBox::NoButton](https://doc.qt.io/qt-6/qdialogbuttonbox.html#StandardButton-enum) if the message box is queued for display instead of exec()ed immediately or if the option [NoExec](kmessagebox.md#Option-enum) is set.

> **Note:** Unless [NoExec](kmessagebox.md#Option-enum) is used, the `dialog` that is passed in is deleted by this function. Do not delete it yourself.

### QDialogButtonBox::StandardButton KMessageBox::createKMessageBox(QDialog \**dialog*, QDialogButtonBox \**buttons*, const QIcon &*icon*, const QString &*text*, const QStringList &*strlist*, const QString &*ask*, bool \**checkboxReturn*, KMessageBox::Options *options*, const QString &*details* = QString(), QMessageBox::Icon *notifyType* = QMessageBox::Information) {#createKMessageBox-1}

Create content and layout of a standard dialog

`dialog` The parent dialog base

`buttons` a [QDialogButtonBox](https://doc.qt.io/qt-6/qdialogbuttonbox.html) instance. This function will take care of connecting to it.

`icon` A [QPixmap](https://doc.qt.io/qt-6/qpixmap.html) containing the icon to be displayed in the dialog next to the text.

`text` Message string.

`strlist` List of strings to be written in the listbox. If the list is empty, it doesn't show any listbox

`ask` The text of the checkbox. If empty none will be shown.

`checkboxReturn` The result of the checkbox. If it's initially true then the checkbox will be checked by default. May be a null pointer. Incompatible with [NoExec](kmessagebox.md#Option-enum).

`options` see Options

`details` Detailed message string.

`notifyType` The type of notification to send when this message is presentend.

Returns a [QDialogButtonBox::StandardButton](https://doc.qt.io/qt-6/qdialogbuttonbox.html#StandardButton-enum) button code, not a [KMessageBox](kmessagebox.md) button code, based on the buttonmask given to the constructor of the `dialog` (ie. will return [QDialogButtonBox::Yes](https://doc.qt.io/qt-6/qdialogbuttonbox.html#StandardButton-enum) instead of [KMessageBox::PrimaryAction](kmessagebox.md#ButtonCode-enum)). Will return [QDialogButtonBox::NoButton](https://doc.qt.io/qt-6/qdialogbuttonbox.html#StandardButton-enum) if the message box is queued for display instead of exec()ed immediately or if the option [NoExec](kmessagebox.md#Option-enum) is set.

> **Note:** Unless [NoExec](kmessagebox.md#Option-enum) is used, the `dialog` that is passed in is deleted by this function. Do not delete it yourself.

### void KMessageBox::detailedError(QWidget \**parent*, const QString &*text*, const QString &*details*, const QString &*title* = QString(), KMessageBox::Options *options* = Notify) {#detailedError}

Displays an "Error" dialog with a "Details \>\>" button.

`parent` Parent widget.

`text` Message string.

`details` Detailed message string.

`title` Message box title. The application name is added to the title. The default title is i18n("Error").

`options` see Options

Your program messed up and now it's time to inform the user. To be used for important things like "Sorry, I deleted your hard disk."

The `details` message can contain additional information about the problem and can be shown on request to advanced/interested users.

The default button is "&OK". Pressing "Esc" selects the OK-button.

> **Note:** The OK button will always have the i18n'ed text '&OK'.

### void KMessageBox::detailedError(QWidget \**parent*, const QString &*text*, const QString &*details*, const QString &*title*, const KGuiItem &*buttonOk*, KMessageBox::Options *options* = Notify) {#detailedError-1}

Displays an "Error" dialog with a "Details \>\>" button.

`parent` Parent widget.

`text` Message string.

`details` Detailed message string.

`title` Message box title. The application name is added to the title. The default title is i18n("Error").

`buttonOk` The text for the only button. The default is [KStandardGuiItem::ok](kstandardguiitem.md#ok)().

`options` see Options

Your program messed up and now it's time to inform the user. To be used for important things like "Sorry, I deleted your hard disk."

The `details` message can contain additional information about the problem and can be shown on request to advanced/interested users.

There is only one button, therefore it's the default button, and pressing "Esc" selects it as well.

### void KMessageBox::detailedErrorWId(WId *parent\_id*, const QString &*text*, const QString &*details*, const QString &*title* = QString(), KMessageBox::Options *options* = Notify) {#detailedErrorWId}

This function accepts the window id of the parent window, instead of [QWidget](https://doc.qt.io/qt-6/qwidget.html)\*. It should be used only when necessary.

### void KMessageBox::detailedErrorWId(WId *parent\_id*, const QString &*text*, const QString &*details*, const QString &*title*, const KGuiItem &*buttonOk*, KMessageBox::Options *options* = Notify) {#detailedErrorWId-1}

This function accepts the window id of the parent window, instead of [QWidget](https://doc.qt.io/qt-6/qwidget.html)\*. It should be used only when necessary.

### void KMessageBox::enableAllMessages() {#enableAllMessages}

Enable all messages which have been turned off with the

`dontShowAgainName` feature.

### void KMessageBox::enableMessage(const QString &*dontShowAgainName*) {#enableMessage}

Re-enable a specific `dontShowAgainName` messages that had previously been turned off.

*See also* [saveDontShowAgainTwoActions](kmessagebox.md#saveDontShowAgainTwoActions)(), [saveDontShowAgainContinue](kmessagebox.md#saveDontShowAgainContinue)()

### void KMessageBox::error(QWidget \**parent*, const QString &*text*, const QString &*title* = QString(), KMessageBox::Options *options* = Notify) {#error}

Display an "Error" dialog.

`parent` Parent widget.

`text` Message string.

`title` Message box title. The application name is added to the title. The default title is i18n("Error").

`options` see Options

Your program messed up and now it's time to inform the user. To be used for important things like "Sorry, I deleted your hard disk."

The default button is "&OK". Pressing "Esc" selects the OK-button.

> **Note:** The OK button will always have the i18n'ed text '&OK'.

### void KMessageBox::error(QWidget \**parent*, const QString &*text*, const QString &*title*, const KGuiItem &*buttonOk*, KMessageBox::Options *options* = Notify) {#error-1}

Display an "Error" dialog.

`parent` Parent widget.

`text` Message string.

`title` Message box title. The application name is added to the title. The default title is i18n("Error").

`buttonOk` The text for the only button. The default is [KStandardGuiItem::ok](kstandardguiitem.md#ok)().

`options` see Options

There is only one button, therefore it's the default button, and pressing "Esc" selects it as well.

### void KMessageBox::errorList(QWidget \**parent*, const QString &*text*, const QStringList &*strlist*, const QString &*title* = QString(), KMessageBox::Options *options* = Notify) {#errorList}

Display an "Error" dialog with a listbox.

`parent` Parent widget.

`text` Message string.

`strlist` List of strings to be written in the listbox. If the list is empty, it doesn't show any listbox, working as [error](kmessagebox.md#error)().

`title` Message box title. The application name is added to the title. The default title is i18n("Error").

`options` see Options

Your program messed up and now it's time to inform the user. To be used for important things like "Sorry, I deleted your hard disk."

The default button is "&OK". Pressing "Esc" selects the OK-button.

> **Note:** The OK button will always have the i18n'ed text '&OK'.

### void KMessageBox::errorListWId(WId *parent\_id*, const QString &*text*, const QStringList &*strlist*, const QString &*title* = QString(), KMessageBox::Options *options* = Notify) {#errorListWId}

This function accepts the window id of the parent window, instead of [QWidget](https://doc.qt.io/qt-6/qwidget.html)\*. It should be used only when necessary.

### void KMessageBox::errorWId(WId *parent\_id*, const QString &*text*, const QString &*title* = QString(), KMessageBox::Options *options* = Notify) {#errorWId}

This function accepts the window id of the parent window, instead of [QWidget](https://doc.qt.io/qt-6/qwidget.html)\*. It should be used only when necessary.

### void KMessageBox::information(QWidget \**parent*, const QString &*text*, const QString &*title* = QString(), const QString &*dontShowAgainName* = QString(), KMessageBox::Options *options* = Notify) {#information}

Display an "Information" dialog.

`parent` Parent widget.

`text` Message string.

`title` Message box title. The application name is added to the title. The default title is i18n("Information").

`dontShowAgainName` If provided, a checkbox is added with which further notifications can be turned off. The string is used to lookup and store the setting in the applications config file. The setting is stored in the "Notification Messages" group.

`options` see Options

Your program wants to tell the user something. To be used for things like: "Your bookmarks have been rearranged."

The default button is "&OK". Pressing "Esc" selects the OK-button.

> **Note:** The OK button will always have the i18n'ed text '&OK'.

### void KMessageBox::informationList(QWidget \**parent*, const QString &*text*, const QStringList &*strlist*, const QString &*title* = QString(), const QString &*dontShowAgainName* = QString(), KMessageBox::Options *options* = Notify) {#informationList}

Display an "Information" dialog with a listbox.

`parent` Parent widget.

`text` Message string.

`strlist` List of strings to be written in the listbox. If the list is empty, it doesn't show any listbox, working as information.

`title` Message box title. The application name is added to the title. The default title is i18n("Information").

`dontShowAgainName` If provided, a checkbox is added with which further notifications can be turned off. The string is used to lookup and store the setting in the applications config file. The setting is stored in the "Notification Messages" group.

`options` see Options

Your program wants to tell the user something. To be used for things like: "The following bookmarks have been rearranged:"

The default button is "&OK". Pressing "Esc" selects the OK-button.

> **Note:** The OK button will always have the i18n'ed text '&OK'.

### void KMessageBox::informationListWId(WId *parent\_id*, const QString &*text*, const QStringList &*strlist*, const QString &*title* = QString(), const QString &*dontShowAgainName* = QString(), KMessageBox::Options *options* = Notify) {#informationListWId}

This function accepts the window id of the parent window, instead of [QWidget](https://doc.qt.io/qt-6/qwidget.html)\*. It should be used only when necessary.

### void KMessageBox::informationWId(WId *parent\_id*, const QString &*text*, const QString &*title* = QString(), const QString &*dontShowAgainName* = QString(), KMessageBox::Options *options* = Notify) {#informationWId}

This function accepts the window id of the parent window, instead of [QWidget](https://doc.qt.io/qt-6/qwidget.html)\*. It should be used only when necessary.

### KMessageBox::ButtonCode KMessageBox::messageBox(QWidget \**parent*, KMessageBox::DialogType *type*, const QString &*text*, const QString &*title*, const KGuiItem &*primaryAction*, const KGuiItem &*secondaryAction*, const KGuiItem &*cancelAction* = KStandardGuiItem::cancel(), const QString &*dontShowAskAgainName* = QString(), KMessageBox::Options *options* = Notify) {#messageBox}

Alternate method to show a messagebox:

`parent` Parent widget.

`type` type of message box: [QuestionTwoActions](kmessagebox.md#DialogType-enum), [WarningTwoActions](kmessagebox.md#DialogType-enum), [WarningContinueCancel](kmessagebox.md#DialogType-enum)...

`text` Message string.

`title` Message box title.

`primaryAction` The [KGuiItem](kguiitem.md) for the first button.

`secondaryAction` The [KGuiItem](kguiitem.md) for the second button.

`cancelAction` The text for the third button. The default is [KStandardGuiItem::cancel](kstandardguiitem.md#cancel)().

`dontShowAskAgainName` If provided, a checkbox is added with which further questions/information can be turned off. If turned off all questions will be automatically answered with the last answer (either [PrimaryAction](kmessagebox.md#ButtonCode-enum) or [SecondaryAction](kmessagebox.md#ButtonCode-enum)), if the message box needs an answer. The string is used to lookup and store the setting in the applications config file.

`options` see Options

Note: for ContinueCancel, primaryAction is the continue button and secondaryAction is unused. and for Information, none is used.

Returns a button code, as defined in [KMessageBox](kmessagebox.md).

### KMessageBox::ButtonCode KMessageBox::messageBoxWId(WId *parent\_id*, KMessageBox::DialogType *type*, const QString &*text*, const QString &*title*, const KGuiItem &*primaryAction*, const KGuiItem &*secondaryAction*, const KGuiItem &*cancelAction* = KStandardGuiItem::cancel(), const QString &*dontShowAskAgainName* = QString(), KMessageBox::Options *options* = Notify) {#messageBoxWId}

This function accepts the window id of the parent window, instead of [QWidget](https://doc.qt.io/qt-6/qwidget.html)\*. It should be used only when necessary.

### KMessageBox::ButtonCode KMessageBox::questionTwoActions(QWidget \**parent*, const QString &*text*, const QString &*title*, const KGuiItem &*primaryAction*, const KGuiItem &*secondaryAction*, const QString &*dontAskAgainName* = QString(), KMessageBox::Options *options* = Notify) {#questionTwoActions}

Display a "question" dialog with two action buttons.

To be used for questions like "Do you want to save the message for later or discard it?".

The default button is the primary button. Pressing "Esc" triggers the secondary button.

`parent` the parent widget

`text` the message string

`title` the message box title. If an empty string, defaults to i18n("Question").

`primaryAction` the action for the primary button

`secondaryAction` the action for the secondary button

`dontAskAgainName` If not an empty string, a checkbox is added with which further confirmation can be turned off. The string is used to lookup and store the setting in the applications config file. The setting is stored in the "Notification Messages" group. If `dontAskAgainName` starts with a ':' then the setting is stored in the global config file.

`options` see Option

Returns [PrimaryAction](kmessagebox.md#ButtonCode-enum) if the primary button is triggered, [SecondaryAction](kmessagebox.md#ButtonCode-enum) if the secondary button is triggered.

### KMessageBox::ButtonCode KMessageBox::questionTwoActionsCancel(QWidget \**parent*, const QString &*text*, const QString &*title*, const KGuiItem &*primaryAction*, const KGuiItem &*secondaryAction*, const KGuiItem &*cancelAction* = KStandardGuiItem::cancel(), const QString &*dontAskAgainName* = QString(), KMessageBox::Options *options* = Notify) {#questionTwoActionsCancel}

Display a "question" dialog with two action buttons and a cancel button.

To be used for questions like "Do you want to save the message for later or discard it?".

The default button is the primary button. Pressing "Esc" triggers the cancel button.

`parent` the parent widget

`text` the message string

`title` the message box title. If an empty string, defaults to i18n("Question").

`primaryAction` the action for the primary button

`secondaryAction` the action for the secondary button

`cancelAction` the action for the cancel button

`dontAskAgainName` If not an empty string, a checkbox is added with which further confirmation can be turned off. The string is used to lookup and store the setting in the applications config file. The setting is stored in the "Notification Messages" group. If `dontAskAgainName` starts with a ':' then the setting is stored in the global config file.

`options` see Option

Returns [PrimaryAction](kmessagebox.md#ButtonCode-enum) if the primary button is triggered, [SecondaryAction](kmessagebox.md#ButtonCode-enum) if the secondary button is triggered. Cancel if the cancel button is triggered.

### KMessageBox::ButtonCode KMessageBox::questionTwoActionsCancelWId(WId *parent\_id*, const QString &*text*, const QString &*title*, const KGuiItem &*primaryAction*, const KGuiItem &*secondaryAction*, const KGuiItem &*cancelAction* = KStandardGuiItem::cancel(), const QString &*dontAskAgainName* = QString(), KMessageBox::Options *options* = Notify) {#questionTwoActionsCancelWId}

This function accepts the window id of the parent window, instead of [QWidget](https://doc.qt.io/qt-6/qwidget.html)\*. It should be used only when necessary.

*See also* [questionTwoActionsCancel](kmessagebox.md#questionTwoActionsCancel)()

### KMessageBox::ButtonCode KMessageBox::questionTwoActionsList(QWidget \**parent*, const QString &*text*, const QStringList &*strlist*, const QString &*title*, const KGuiItem &*primaryAction*, const KGuiItem &*secondaryAction*, const QString &*dontAskAgainName* = QString(), KMessageBox::Options *options* = Notify) {#questionTwoActionsList}

Display a "question" dialog with a listbox to show information to the user and two action buttons.

To be used for questions like "Do you really want to delete these files?" and show the user exactly which files are going to be deleted in case.

The default button is the primary button. Pressing "Esc" triggers the secondary button.

`parent` the parent widget

`text` the message string

`strlist` List of strings to be written in the listbox. If the list is empty, it doesn't show any listbox, working as [questionTwoActions](kmessagebox.md#questionTwoActions)().

`title` the message box title. If an empty string, defaults to i18n("Question").

`primaryAction` the action for the primary button

`secondaryAction` the action for the secondary button

`dontAskAgainName` If not an empty string, a checkbox is added with which further confirmation can be turned off. The string is used to lookup and store the setting in the applications config file. The setting is stored in the "Notification Messages" group. If `dontAskAgainName` starts with a ':' then the setting is stored in the global config file. `options` see Option

Returns [PrimaryAction](kmessagebox.md#ButtonCode-enum) if the primary button is triggered, [SecondaryAction](kmessagebox.md#ButtonCode-enum) if the secondary button is triggered.

### KMessageBox::ButtonCode KMessageBox::questionTwoActionsListWId(WId *parent\_id*, const QString &*text*, const QStringList &*strlist*, const QString &*title*, const KGuiItem &*primaryAction*, const KGuiItem &*secondaryAction*, const QString &*dontAskAgainName* = QString(), KMessageBox::Options *options* = Notify) {#questionTwoActionsListWId}

This function accepts the window id of the parent window, instead of [QWidget](https://doc.qt.io/qt-6/qwidget.html)\*. It should be used only when necessary.

*See also* [questionTwoActionsList](kmessagebox.md#questionTwoActionsList)()

### KMessageBox::ButtonCode KMessageBox::questionTwoActionsWId(WId *parent\_id*, const QString &*text*, const QString &*title*, const KGuiItem &*primaryAction*, const KGuiItem &*secondaryAction*, const QString &*dontAskAgainName* = QString(), KMessageBox::Options *options* = Notify) {#questionTwoActionsWId}

This function accepts the window id of the parent window, instead of [QWidget](https://doc.qt.io/qt-6/qwidget.html)\*. It should be used only when necessary.

*See also* [questionTwoActions](kmessagebox.md#questionTwoActions)()

### void KMessageBox::saveDontShowAgainContinue(const QString &*dontShowAgainName*) {#saveDontShowAgainContinue}

Save the fact that the continue/cancel message box should not be shown again.

`dontShowAgainName` the name that identify the message box. If empty, this method does nothing.

### void KMessageBox::saveDontShowAgainTwoActions(const QString &*dontShowAgainName*, KMessageBox::ButtonCode *result*) {#saveDontShowAgainTwoActions}

Save the fact that a two actions message box should not be shown again.

`dontShowAgainName` the name that identifies the message box. If empty, this method does nothing.

`result` the value (`PrimaryAction` or `SecondaryAction`) that should be used as the result for the message box.

### void KMessageBox::setDontShowAgainConfig(KConfig \**cfg*) {#setDontShowAgainConfig}

Use `cfg` for all settings related to the dontShowAgainName feature.

If `cfg` is 0 (default) KGlobal::config() will be used.

### void KMessageBox::setDontShowAgainInterface(KMessageBoxDontAskAgainInterface \**dontAskAgainInterface*) {#setDontShowAgainInterface}

Use `dontAskAgainInterface` for all settings related to the dontShowAgain feature.

This method does not take ownership of `dontAskAgainInterface`.

### void KMessageBox::setNotifyInterface(KMessageBoxNotifyInterface \**notifyInterface*) {#setNotifyInterface}

Use `notifyInterface` to send notifications.

This method does not take ownership of `notifyInterface`.

### bool KMessageBox::shouldBeShownContinue(const QString &*dontShowAgainName*) {#shouldBeShownContinue}

Returns `true` if the corresponding continue/cancel message box should be shown.

`dontShowAgainName` the name that identify the message box. If empty, true is always returned.

### bool KMessageBox::shouldBeShownTwoActions(const QString &*dontShowAgainName*, KMessageBox::ButtonCode &*result*) {#shouldBeShownTwoActions}

`dontShowAgainName` the name that identifies the message box. If empty, `true` is always returned.

`result` reference to a variable to be set to the choice (`PrimaryAction` or `SecondaryAction`) that was chosen the last time the message box was shown. Only meaningful if the message box should not be shown.

Returns `true` if the corresponding two actions message box should be shown, `false` otherwise.

### KMessageBox::ButtonCode KMessageBox::warningContinueCancel(QWidget \**parent*, const QString &*text*, const QString &*title* = QString(), const KGuiItem &*buttonContinue* = KStandardGuiItem::cont(), const KGuiItem &*buttonCancel* = KStandardGuiItem::cancel(), const QString &*dontAskAgainName* = QString(), KMessageBox::Options *options* = Notify) {#warningContinueCancel}

Display a "warning" dialog.

`parent` Parent widget.

`text` Message string.

`title` Message box title. The application name is added to the title. The default title is i18n("Warning").

`buttonContinue` The text for the first button. The default is [KStandardGuiItem::cont](kstandardguiitem.md#cont)().

`buttonCancel` The text for the second button. The default is [KStandardGuiItem::cancel](kstandardguiitem.md#cancel)().

`dontAskAgainName` If provided, a checkbox is added with which further confirmation can be turned off. The string is used to lookup and store the setting in the applications config file. The setting is stored in the "Notification Messages" group. If `dontAskAgainName` starts with a ':' then the setting is stored in the global config file.

`options` see Options

Continue is returned if the Continue-button is pressed.

Cancel is returned if the Cancel-button is pressed.

To be used for questions like "You are about to Print. Are you sure?" the continueButton should then be labeled "Print".

The default button is buttonContinue. Pressing "Esc" selects "Cancel".

### KMessageBox::ButtonCode KMessageBox::warningContinueCancelDetailed(QWidget \**parent*, const QString &*text*, const QString &*title* = QString(), const KGuiItem &*buttonContinue* = KStandardGuiItem::cont(), const KGuiItem &*buttonCancel* = KStandardGuiItem::cancel(), const QString &*dontAskAgainName* = QString(), KMessageBox::Options *options* = Notify, const QString &*details* = QString()) {#warningContinueCancelDetailed}

Display a "warning" dialog with a collapsible "Details" section.

### KMessageBox::ButtonCode KMessageBox::warningContinueCancelList(QWidget \**parent*, const QString &*text*, const QStringList &*strlist*, const QString &*title* = QString(), const KGuiItem &*buttonContinue* = KStandardGuiItem::cont(), const KGuiItem &*buttonCancel* = KStandardGuiItem::cancel(), const QString &*dontAskAgainName* = QString(), KMessageBox::Options *options* = Notify) {#warningContinueCancelList}

Display a "warning" dialog with a listbox to show information to the user.

`parent` Parent widget.

`text` Message string.

`strlist` List of strings to be written in the listbox. If the list is empty, it doesn't show any listbox, working as [warningContinueCancel](kmessagebox.md#warningContinueCancel).

`title` Message box title. The application name is added to the title. The default title is i18n("Warning").

`buttonContinue` The text for the first button. The default is [KStandardGuiItem::cont](kstandardguiitem.md#cont)().

`buttonCancel` The text for the second button. The default is [KStandardGuiItem::cancel](kstandardguiitem.md#cancel)().

`dontAskAgainName` If provided, a checkbox is added with which further confirmation can be turned off. The string is used to lookup and store the setting in the applications config file. The setting is stored in the "Notification Messages" group. If `dontAskAgainName` starts with a ':' then the setting is stored in the global config file.

`options` see Options

Continue is returned if the Continue-button is pressed.

Cancel is returned if the Cancel-button is pressed.

To be used for questions like "You are about to Print. Are you sure?" the continueButton should then be labeled "Print".

The default button is buttonContinue. Pressing "Esc" selects "Cancel".

### KMessageBox::ButtonCode KMessageBox::warningContinueCancelListWId(WId *parent\_id*, const QString &*text*, const QStringList &*strlist*, const QString &*title* = QString(), const KGuiItem &*buttonContinue* = KStandardGuiItem::cont(), const KGuiItem &*buttonCancel* = KStandardGuiItem::cancel(), const QString &*dontAskAgainName* = QString(), KMessageBox::Options *options* = Notify) {#warningContinueCancelListWId}

This function accepts the window id of the parent window, instead of [QWidget](https://doc.qt.io/qt-6/qwidget.html)\*. It should be used only when necessary.

### KMessageBox::ButtonCode KMessageBox::warningContinueCancelWId(WId *parent\_id*, const QString &*text*, const QString &*title* = QString(), const KGuiItem &*buttonContinue* = KStandardGuiItem::cont(), const KGuiItem &*buttonCancel* = KStandardGuiItem::cancel(), const QString &*dontAskAgainName* = QString(), KMessageBox::Options *options* = Notify) {#warningContinueCancelWId}

This function accepts the window id of the parent window, instead of [QWidget](https://doc.qt.io/qt-6/qwidget.html)\*. It should be used only when necessary.

### KMessageBox::ButtonCode KMessageBox::warningTwoActions(QWidget \**parent*, const QString &*text*, const QString &*title*, const KGuiItem &*primaryAction*, const KGuiItem &*secondaryAction*, const QString &*dontAskAgainName* = QString(), KMessageBox::Options *options* = Options(Notify \| Dangerous)) {#warningTwoActions}

Display a "warning" dialog with two action buttons.

To be used for questions like "Shall I update your configuration?". The text should explain the implication of both actions.

The default button is the secondary button. Pressing "Esc" triggers the secondary button.

`parent` the parent widget

`text` the message string

`title` the message box title. If an empty string, defaults to i18n("Warning").

`primaryAction` the action for the primary button

`secondaryAction` the action for the secondary button

`dontAskAgainName` If not an empty string, a checkbox is added with which further confirmation can be turned off. The string is used to lookup and store the setting in the applications config file. The setting is stored in the "Notification Messages" group. If `dontAskAgainName` starts with a ':' then the setting is stored in the global config file.

`options` see Options

Returns `PrimaryAction` if the primary button is triggered, `SecondaryAction` if the secondary button is triggered.

### KMessageBox::ButtonCode KMessageBox::warningTwoActionsCancel(QWidget \**parent*, const QString &*text*, const QString &*title*, const KGuiItem &*primaryAction*, const KGuiItem &*secondaryAction*, const KGuiItem &*cancelAction* = KStandardGuiItem::cancel(), const QString &*dontAskAgainName* = QString(), KMessageBox::Options *options* = Options(Notify \| Dangerous)) {#warningTwoActionsCancel}

Display a "warning" dialog with two action buttons and a cancel button.

To be used for questions like "Shall I update your configuration?". The text should explain the implication of both actions.

The default button is the cancel button. Pressing "Esc" triggers the cancel button.

`parent` the parent widget

`text` the message string

`title` the message box title. If an empty string, defaults to i18n("Warning").

`primaryAction` the action for the primary button

`secondaryAction` the action for the secondary button

`cancelAction` the action for the cancel button

`dontAskAgainName` If not an empty string, a checkbox is added with which further confirmation can be turned off. The string is used to lookup and store the setting in the applications config file. The setting is stored in the "Notification Messages" group. If `dontAskAgainName` starts with a ':' then the setting is stored in the global config file.

`options` see Options

Returns [PrimaryAction](kmessagebox.md#ButtonCode-enum) if the primary button is triggered, [SecondaryAction](kmessagebox.md#ButtonCode-enum) if the secondary button is triggered. Cancel if the cancel button is triggered.

### KMessageBox::ButtonCode KMessageBox::warningTwoActionsCancelList(QWidget \**parent*, const QString &*text*, const QStringList &*strlist*, const QString &*title*, const KGuiItem &*primaryAction*, const KGuiItem &*secondaryAction*, const KGuiItem &*cancelAction* = KStandardGuiItem::cancel(), const QString &*dontAskAgainName* = QString(), KMessageBox::Options *options* = Options(Notify \| Dangerous)) {#warningTwoActionsCancelList}

Display a "warning" dialog with a listbox to show information to the user, two action buttons and a cancel button.

To be used for questions like "Shall I update your configuration?". The text should explain the implication of both actions.

The default button is the cancel button. Pressing "Esc" triggers the cancel button.

`parent` the parent widget

`text` the message string

`strlist` a List of strings to be written in the listbox. If the list is empty, it doesn't show any listbox, working as [warningTwoActionsCancel](kmessagebox.md#warningTwoActionsCancel)().

`title` the message box title. If an empty string, defaults to i18n("Warning").

`primaryAction` the action for the primary button

`secondaryAction` the action for the secondary button

`cancelAction` the action for the cancel button

`dontAskAgainName` If not an empty string, a checkbox is added with which further confirmation can be turned off. The string is used to lookup and store the setting in the applications config file. The setting is stored in the "Notification Messages" group. If `dontAskAgainName` starts with a ':' then the setting is stored in the global config file.

`options` see Options

Returns [PrimaryAction](kmessagebox.md#ButtonCode-enum) if the primary button is triggered, [SecondaryAction](kmessagebox.md#ButtonCode-enum) if the secondary button is triggered. Cancel if the cancel button is triggered.

### KMessageBox::ButtonCode KMessageBox::warningTwoActionsCancelListWId(WId *parent\_id*, const QString &*text*, const QStringList &*strlist*, const QString &*title*, const KGuiItem &*primaryAction*, const KGuiItem &*secondaryAction*, const KGuiItem &*cancelAction* = KStandardGuiItem::cancel(), const QString &*dontAskAgainName* = QString(), KMessageBox::Options *options* = Options(Notify \| Dangerous)) {#warningTwoActionsCancelListWId}

This function accepts the window id of the parent window, instead of [QWidget](https://doc.qt.io/qt-6/qwidget.html)\*. It should be used only when necessary.

*See also* [warningTwoActionsCancelList](kmessagebox.md#warningTwoActionsCancelList)()

### KMessageBox::ButtonCode KMessageBox::warningTwoActionsCancelWId(WId *parent\_id*, const QString &*text*, const QString &*title*, const KGuiItem &*primaryAction*, const KGuiItem &*secondaryAction*, const KGuiItem &*cancelAction* = KStandardGuiItem::cancel(), const QString &*dontAskAgainName* = QString(), KMessageBox::Options *options* = Options(Notify \| Dangerous)) {#warningTwoActionsCancelWId}

This function accepts the window id of the parent window, instead of [QWidget](https://doc.qt.io/qt-6/qwidget.html)\*. It should be used only when necessary.

*See also* [warningTwoActionsCancel](kmessagebox.md#warningTwoActionsCancel)()

### KMessageBox::ButtonCode KMessageBox::warningTwoActionsList(QWidget \**parent*, const QString &*text*, const QStringList &*strlist*, const QString &*title*, const KGuiItem &*primaryAction*, const KGuiItem &*secondaryAction*, const QString &*dontAskAgainName* = QString(), KMessageBox::Options *options* = Options(Notify \| Dangerous)) {#warningTwoActionsList}

Display a "warning" dialog with a listbox to show information to the user and two action buttons.

To be used for questions like "Shall I update your configuration?". The text should explain the implication of both actions.

The default button is the secondary button. Pressing "Esc" triggers the secondary button.

`parent` the parent widget

`text` the message string

`strlist` List of strings to be written in the listbox. If the list is empty, it doesn't show any listbox, working as [warningTwoActions](kmessagebox.md#warningTwoActions).

`title` the message box title. If an empty string, defaults to i18n("Warning").

`primaryAction` the action for the primary button

`secondaryAction` the action for the secondary button

`dontAskAgainName` If not an empty string, a checkbox is added with which further confirmation can be turned off. The string is used to lookup and store the setting in the applications config file. The setting is stored in the "Notification Messages" group. If `dontAskAgainName` starts with a ':' then the setting is stored in the global config file.

`options` see Options

Returns [PrimaryAction](kmessagebox.md#ButtonCode-enum) if the primary button is triggered, [SecondaryAction](kmessagebox.md#ButtonCode-enum) if the secondary button is triggered.

### KMessageBox::ButtonCode KMessageBox::warningTwoActionsListWId(WId *parent\_id*, const QString &*text*, const QStringList &*strlist*, const QString &*title*, const KGuiItem &*primaryAction*, const KGuiItem &*secondaryAction*, const QString &*dontAskAgainName* = QString(), KMessageBox::Options *options* = Options(Notify \| Dangerous)) {#warningTwoActionsListWId}

This function accepts the window id of the parent window, instead of [QWidget](https://doc.qt.io/qt-6/qwidget.html)\*. It should be used only when necessary.

*See also* [warningTwoActionsList](kmessagebox.md#warningTwoActionsList)()

### KMessageBox::ButtonCode KMessageBox::warningTwoActionsWId(WId *parent\_id*, const QString &*text*, const QString &*title*, const KGuiItem &*primaryAction*, const KGuiItem &*secondaryAction*, const QString &*dontAskAgainName* = QString(), KMessageBox::Options *options* = Options(Notify \| Dangerous)) {#warningTwoActionsWId}

This function accepts the window id of the parent window, instead of [QWidget](https://doc.qt.io/qt-6/qwidget.html)\*. It should be used only when necessary.

*See also* [warningTwoActions](kmessagebox.md#warningTwoActions)()
