---
title: "Sonnet::Dialog Class"
description: "Spellcheck dialog."
---

# Sonnet::Dialog Class

Spellcheck dialog. [More...](#details)

- **Header:** `#include <Sonnet/Dialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Sonnet)`  
  `target_link_libraries(mytarget PRIVATE KF6::SonnetUi)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](sonnet-dialog-members.md)

## Public Functions

- [Dialog(Sonnet::BackgroundChecker \*checker, QWidget \*parent)](#Dialog)
- [void activeAutoCorrect(bool \_active)](#activeAutoCorrect)
- [QString buffer() const](#buffer)
- [QString originalBuffer() const](#originalBuffer)
- [void setSpellCheckContinuedAfterReplacement(bool b)](#setSpellCheckContinuedAfterReplacement)
- [void show()](#show)
- [void showProgressDialog(int timeout = 500)](#showProgressDialog)
- [void showSpellCheckCompletionMessage(bool b = true)](#showSpellCheckCompletionMessage)

## Public Slots

- [void setBuffer(const QString &)](#setBuffer)

## Signals

- [void autoCorrect(const QString &currentWord, const QString &replaceWord)](#autoCorrect)
- [void cancel()](#cancel)
- [void languageChanged(const QString &language)](#languageChanged)
- [void misspelling(const QString &word, int start)](#misspelling)
- [void replace(const QString &oldWord, int start, const QString &newWord)](#replace)
- [void spellCheckDone(const QString &newBuffer)](#spellCheckDone)
- [void spellCheckStatus(const QString &)](#spellCheckStatus)
- [void stop()](#stop)

## Detailed Description {#details}

```cpp
Sonnet::Dialog dlg = new Sonnet::Dialog(
      new Sonnet::BackgroundChecker(this), this);
//connect signals
...
dlg->setBuffer( someText );
dlg->show();
```

You can change buffer inside a slot connected to [done](https://doc.qt.io/qt-6/qdialog.html#done)() signal and spellcheck will continue with new data automatically.

## Member Function Documentation {#member-function-documentation}

### Dialog::Dialog(Sonnet::BackgroundChecker \**checker*, QWidget \**parent*) {#Dialog}

### void Dialog::activeAutoCorrect(bool *\_active*) {#activeAutoCorrect}

### \[signal\] void Dialog::autoCorrect(const QString &*currentWord*, const QString &*replaceWord*) {#autoCorrect}

### QString Dialog::buffer() const {#buffer}

*See also* [setBuffer](sonnet-dialog.md#setBuffer)()

### \[signal\] void Dialog::cancel() {#cancel}

### \[signal\] void Dialog::languageChanged(const QString &*language*) {#languageChanged}

Emitted when the user changes the language used for spellchecking, which is shown in a combobox of this dialog.

`dictionary` the new language the user selected

### \[signal\] void Dialog::misspelling(const QString &*word*, int *start*) {#misspelling}

### QString Dialog::originalBuffer() const {#originalBuffer}

### \[signal\] void Dialog::replace(const QString &*oldWord*, int *start*, const QString &*newWord*) {#replace}

### \[slot\] void Dialog::setBuffer(*const QString &*) {#setBuffer}

*See also* [buffer](sonnet-dialog.md#buffer)()

### void Dialog::setSpellCheckContinuedAfterReplacement(bool *b*) {#setSpellCheckContinuedAfterReplacement}

Controls whether the spell checking is continued after the replacement of a misspelled word has been performed. By default it is continued.

### void Dialog::show() {#show}

### void Dialog::showProgressDialog(int *timeout* = 500) {#showProgressDialog}

Controls whether an (indefinite) progress dialog is shown when the spell checking takes longer than the given time to complete. By default no progress dialog is shown. If the progress dialog is set to be shown, no time consuming operation (for example, showing a notification message) should be performed in a slot connected to the 'done' signal as this might trigger the progress dialog unnecessarily.

`timeout` time after which the progress dialog should appear; a negative value can be used to hide it

### void Dialog::showSpellCheckCompletionMessage(bool *b* = true) {#showSpellCheckCompletionMessage}

Controls whether a message box indicating the completion of the spell checking is shown or not. By default it is not shown.

### \[signal\] void Dialog::spellCheckDone(const QString &*newBuffer*) {#spellCheckDone}

The dialog won't be closed if you [setBuffer](sonnet-dialog.md#setBuffer)() in slot connected to this signal Also emitted after [stop](sonnet-dialog.md#stop)() signal

### \[signal\] void Dialog::spellCheckStatus(*const QString &*) {#spellCheckStatus}

Signal sends when spell checking is finished/stopped/completed

### \[signal\] void Dialog::stop() {#stop}
