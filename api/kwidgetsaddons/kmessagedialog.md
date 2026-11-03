---
title: "KMessageDialog Class"
description: "KMessageDialog creates a message box similar to the ones you get from KMessageBox, but that can be used asynchronously, i.e. you can show the dialog by using show() or open()."
---

# KMessageDialog Class

[KMessageDialog](kmessagedialog.md) creates a message box similar to the ones you get from [KMessageBox](kmessagebox.md), but that can be used asynchronously, i.e. you can show the dialog by using [show](https://doc.qt.io/qt-6/qwidget.html#show)() or [open](https://doc.qt.io/qt-6/qdialog.html#open)(). [More...](#details)

- **Header:** `#include <KMessageDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](kmessagedialog-members.md)

## Public Types

- [enum KMessageDialog::ButtonType](#ButtonType-enum)
- [enum KMessageDialog::Type](#Type-enum)

## Public Functions

- [KMessageDialog(KMessageDialog::Type type, const QString &text, QWidget \*parent = nullptr)](#KMessageDialog)
- [KMessageDialog(KMessageDialog::Type type, const QString &text, WId parent\_id)](#KMessageDialog-1)
- [~KMessageDialog()](#dtor.KMessageDialog)
- [bool isDontAskAgainChecked() const](#isDontAskAgainChecked)
- [bool isNotifyEnabled() const](#isNotifyEnabled)
- [void setButtons(const KGuiItem &primaryAction = KGuiItem(), const KGuiItem &secondaryAction = KGuiItem(), const KGuiItem &cancelAction = KGuiItem())](#setButtons)
- [void setCaption(const QString &caption)](#setCaption)
- [void setDetails(const QString &details)](#setDetails)
- [void setDontAskAgainChecked(bool isChecked)](#setDontAskAgainChecked)
- [void setDontAskAgainText(const QString &dontAskAgainText)](#setDontAskAgainText)
- [void setIcon(const QIcon &icon)](#setIcon)
- [void setListWidgetItems(const QStringList &strlist)](#setListWidgetItems)
- [void setNotifyEnabled(bool enable)](#setNotifyEnabled)
- [void setOpenExternalLinks(bool isAllowed)](#setOpenExternalLinks)

## Static Public Members

- [void beep(KMessageDialog::Type type, const QString &text = QString(), QWidget \*dialog = nullptr)](#beep) (since 6.0)

## Detailed Description {#details}

This class contructs a dialog similar to the dialogs the [KMessageBox](kmessagebox.md) convenience functions create. The main difference is that the [KMessageBox](kmessagebox.md) methods typically use [exec](https://doc.qt.io/qt-6/qdialog.html#exec)() to show the dialogs; one of the main disadvantages of using [exec](https://doc.qt.io/qt-6/qdialog.html#exec)(), is that it starts a nested eventloop, which could lead to nasty crashes.

Another difference is that the API is supposed to be slightly easier to use as it has various methods to set up the dialog, e.g. [setCaption](kmessagedialog.md#setCaption)(), [setDetails](kmessagedialog.md#setDetails)() ...etc.

By default, appropriate buttons based on the dialog type are added (since 5.85) (e.g. an "OK" button is added to an Information dialog), you can set custom buttons by using the [setButtons](kmessagedialog.md#setButtons)() method.

The [QDialog::done](https://doc.qt.io/qt-6/qdialog.html#done)() slot is called to set the result of the dialog, which will emit the [QDialog::finished](https://doc.qt.io/qt-6/qdialog.html#finished)() signal with that result. The result is one of the [KMessageDialog::ButtonType](kmessagedialog.md#ButtonType-enum) enum. This is useful as you can tell exactly which button was clicked by the user. E.g.:

- the secondary action button having been clicked, in which case you may still want to save the status of the "Do not ask again" CheckBox
- the "Cancel" button having been clicked, in which case you ideally will ignore the status of the "Do not ask again" CheckBox

For "warning" dialogs, i.e. dialogs with a potentially destructive action, the default button is set to a button with the [QDialogButtonBox::RejectRole](https://doc.qt.io/qt-6/qdialogbuttonbox.html#ButtonRole-enum). If the "Cancel" button is used, it will be the default, otherwise the secondary action button.

This class intends to be very flexible with the buttons that can be used, since you can call the [setButtons](kmessagedialog.md#setButtons)() method with a [KGuiItem](kguiitem.md) that has custom text/icon.

Since Frameworks 5.97 a notification sound is played when the dialog opens like [KMessageBox](kmessagebox.md) does, this can be controlled using the [setNotifyEnabled](kmessagedialog.md#setNotifyEnabled)() method.

Example:

```cpp
auto *dlg = new KMessageDialog(KMessageDialog::QuestionTwoActionsCancel,
                               QStringLiteral("Back or forward?"),
                               nullptr);

dlg->setCaption(QStringLiteral("Window Title"));
dlg->setButtons(KStandardGuiItem::back(), KStandardGuiItem::forward(), KStandardGuiItem::cancel());
dlg->setListWidgetItems(QStringList{QStringLiteral("file1"), QStringLiteral("file2")});
dlg->setDetails(QStringLiteral("Some more details."));
dlg->setDontAskAgainText(QStringLiteral("Do not ask again"));
dlg->setDontAskAgainChecked(false);

 // Delete the dialog when it's closed
 dlg->setAttribute(Qt::WA_DeleteOnClose);
 // Make the dialog window modal
 dlg->setWindowModality(Qt::WindowModal);

 QObject::connect(dlg, &QDialog::finished, &app, [dlg](int result) {
     auto button = static_cast<KMessageDialog::ButtonType>(result);
     switch(button) {
     case KMessageDialog::PrimaryAction:
         // The user clicked the primary action, handle the result...
         // save the "do not ask again" box status...
         break;
     case KMessageDialog::SecondaryAction:
         // The user clicked the secondary action, handle the result...
         // save the "do not ask again" box status...
         break;
     case KMessageDialog::Cancel:
         // The user clicked cancel, reject the changes...
         break;
     default:
         break;
     }
 });

 dlg->show();
```

## Member Type Documentation {#member-type-documentation}

### enum KMessageDialog::ButtonType {#ButtonType-enum}

Button types

| Constant | Value | Description |
| --- | --- | --- |
| `KMessageDialog::Ok` | `1` | Ok button |
| `KMessageDialog::Cancel` | `2` | Cancel button |
| `KMessageDialog::PrimaryAction` | `3` | Primary action button |
| `KMessageDialog::SecondaryAction` | `4` | Secondary action button |

### enum KMessageDialog::Type {#Type-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KMessageDialog::QuestionTwoActions (since Qt 5.100)` | `1` | Question dialog with two buttons |
| `KMessageDialog::QuestionTwoActionsCancel (since Qt 5.100)` | `2` | Question dialog with two buttons and Cancel |
| `KMessageDialog::WarningTwoActions (since Qt 5.100)` | `3` | Warning dialog with two buttons |
| `KMessageDialog::WarningTwoActionsCancel (since Qt 5.100)` | `4` | Warning dialog with two buttons and Cancel |
| `KMessageDialog::WarningContinueCancel` | `5` | Warning dialog with Continue and Cancel |
| `KMessageDialog::Information` | `6` | Information dialog |
| `KMessageDialog::Error` | `8` | Error dialog |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KMessageDialog::KMessageDialog(KMessageDialog::Type *type*, const QString &*text*, QWidget \**parent* = nullptr) {#KMessageDialog}

Constructs a [KMessageDialog](kmessagedialog.md).

Buttons based on the dialog type are set by default in some cases, using [KStandardGuiItem](kstandardguiitem.md) instances. For the dialog types Information and Error the button is set to [KStandardGuiItem::ok](kstandardguiitem.md#ok)(). For the type [WarningContinueCancel](kmessagedialog.md#Type-enum) the buttons are set to [KStandardGuiItem::cont](kstandardguiitem.md#cont)() & [KStandardGuiItem::cancel](kstandardguiitem.md#cancel)().

For the other Quesion\* and Warning\* types the buttons are to be set explicitly.

`type` the dialog Type, one of [KMessageDialog::Type](kmessagedialog.md#Type-enum) enum

`text` the text message that is going to be displayed in the dialog

`parent` a [QWidget](https://doc.qt.io/qt-6/qwidget.html)\* that will be set as the dialog parent

### \[explicit\] KMessageDialog::KMessageDialog(KMessageDialog::Type *type*, const QString &*text*, WId *parent\_id*) {#KMessageDialog-1}

This constructor takes the window Id of the parent window, instead of a [QWidget](https://doc.qt.io/qt-6/qwidget.html)\*.

`type` the dialog Type, one of [KMessageDialog::Type](kmessagedialog.md#Type-enum) enum

`text` the text message that is going to be displayed in the dialog

`parent_id` the native parent's window system identifier

### \[override virtual noexcept\] KMessageDialog::~KMessageDialog() {#dtor.KMessageDialog}

Destructor

### \[static, since 6.0\] void KMessageDialog::beep(KMessageDialog::Type *type*, const QString &*text* = QString(), QWidget \**dialog* = nullptr) {#beep}

Manually play the notification sound

When implementing your entirely own message box, not using [KMessageDialog](kmessagedialog.md), you can call this function to play the relevant notification sound (if enabled).

> **Note:** You don't need to call this when using [KMessageDialog](kmessagedialog.md), it plays the sound automatically.

`type` The message box type

`text` The message box contents, for accessibility purposes.

`dialog` The dialog that was displayed

This function was introduced in Qt 6.0.

*See also* [setNotifyEnabled](kmessagedialog.md#setNotifyEnabled)

### bool KMessageDialog::isDontAskAgainChecked() const {#isDontAskAgainChecked}

This can be used to query the status of the "Do not ask again" checkbox; returns `true` if the box is checked and `false` otherwise.

> **Note:** This method will return `false` if a checkbox widget isn't shown in the dialog. The dialog will not show a checkbox if [setDontAskAgainText](kmessagedialog.md#setDontAskAgainText)() was not used previously to add a checkbox to begin with.

### bool KMessageDialog::isNotifyEnabled() const {#isNotifyEnabled}

Whether a KNotification is emitted when the dialog is shown.

This typically plays a notification sound. Default is true.

*See also* [KMessageBox::Notify](kmessagebox.md#Option-enum)

### void KMessageDialog::setButtons(const KGuiItem &*primaryAction* = KGuiItem(), const KGuiItem &*secondaryAction* = KGuiItem(), const KGuiItem &*cancelAction* = KGuiItem()) {#setButtons}

Sets the buttons in the buttom box.

Using this method, you can customize the behavior based on your use-case, by using a [KGuiItem](kguiitem.md) to get a button with custom text and icon.

Since 5.85 buttons based on the dialog type are added by default (see [KMessageDialog](kmessagedialog.md)([KMessageDialog::Type](kmessagedialog.md#Type-enum), const [QString](https://doc.qt.io/qt-6/qstring.html) &, [QWidget](https://doc.qt.io/qt-6/qwidget.html) \*) for details). Before, this method had to be called explicitly to have any buttons added to the dialog.

> **Note:** For dialog types Information and Error only one button ([KStandardGuiItem::ok](kstandardguiitem.md#ok)()) is added to the dialog.

`primaryAction` the action for the primary button. Reported in the result for dialog types Information and Error as [KMessageDialog::Ok](kmessagedialog.md#ButtonType-enum) enum value, otherwise as [KMessageDialog::PrimaryAction](kmessagedialog.md#ButtonType-enum).

`secondaryAction` the action for the secondary button. Reported in the result as [KMessageDialog::SecondaryAction](kmessagedialog.md#ButtonType-enum) enum value. Ignored with all dialog types without a "secondary" action.

`cancelAction` the action for the cancel button. Reported in the result as [KMessageDialog::Cancel](kmessagedialog.md#ButtonType-enum) enum value. Ignored with all dialog types without a Cancel button.

### void KMessageDialog::setCaption(const QString &*caption*) {#setCaption}

This can be used to set the title of the dialog window. If you pass an empty QString(), a generic title will be used depending on the dialog Type. E.g. for [KMessageDialog::WarningTwoActions](kmessagedialog.md#Type-enum), "Warning" will be used.

### void KMessageDialog::setDetails(const QString &*details*) {#setDetails}

This will add a [KCollapsibleGroupBox](kcollapsiblegroupbox.md) with a title "Details", as the class name implies it is collapsible (and collapsed by default); you can use it to add a more detailed explanation of what the dialog is trying to tell the user.

If `details` is empty, the details widget will not be shown.

### void KMessageDialog::setDontAskAgainChecked(bool *isChecked*) {#setDontAskAgainChecked}

This can be used to set the initial status of the "Do not ask again" checkbox, checked or unchecked, by setting `isChecked` to `true` or `false` respectively.

You need to call [setDontAskAgainText](kmessagedialog.md#setDontAskAgainText)() first to actually show a checkbox in the dialog, otherwise calling this function will have no effect.

*See also* [isDontAskAgainChecked](kmessagedialog.md#isDontAskAgainChecked)()

### void KMessageDialog::setDontAskAgainText(const QString &*dontAskAgainText*) {#setDontAskAgainText}

This will add a "Do not ask again" checkbox to the dialog with the text from `dontAskAgainText`. You can set the initial status of the checkbox by using [setDontAskAgainChecked](kmessagedialog.md#setDontAskAgainChecked)().

If `dontAskAgainText` is empty, no checkbox will be shown.

Typical usage of this checkbox is for recurring questions, e.g. showing a dialog to confirm moving files/directories to trash, the user can then set the checkbox so as not to be asked about that again.

You can get the state of the checkbox by using [isDontAskAgainChecked](kmessagedialog.md#isDontAskAgainChecked)().

### void KMessageDialog::setIcon(const QIcon &*icon*) {#setIcon}

This can be used to set an icon that will be shown next to the main text message. If you pass a null QIcon() a generic icon based on the dialog Type will be used. E.g. for [KMessageDialog::QuestionTwoActions](kmessagedialog.md#Type-enum), [QMessageBox::Question](https://doc.qt.io/qt-6/qmessagebox.html#Icon-enum) will be used.

### void KMessageDialog::setListWidgetItems(const QStringList &*strlist*) {#setListWidgetItems}

This will add a [QListWidget](https://doc.qt.io/qt-6/qlistwidget.html) to the dialog and populate it with `strlist`. If `strlist` is empty, the list widget will not be shown.

### void KMessageDialog::setNotifyEnabled(bool *enable*) {#setNotifyEnabled}

Whether to emit a KNotification when the dialog is shown.

This typically plays a notification sound.

*See also* [isNotifyEnabled](kmessagedialog.md#isNotifyEnabled)(), [KMessageBox::Notify](kmessagebox.md#Option-enum)

### void KMessageDialog::setOpenExternalLinks(bool *isAllowed*) {#setOpenExternalLinks}

Sets the text labels in the dialog to either allow opening external links or not.
