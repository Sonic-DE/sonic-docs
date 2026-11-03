---
title: "Sonnet::ConfigDialog Class"
description: "The sonnet ConfigDialog."
---

# Sonnet::ConfigDialog Class

The sonnet [ConfigDialog](sonnet-configdialog.md). [More...](#details)

- **Header:** `#include <Sonnet/ConfigDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Sonnet)`  
  `target_link_libraries(mytarget PRIVATE KF6::SonnetUi)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](sonnet-configdialog-members.md)

## Public Functions

- [ConfigDialog(QWidget \*parent)](#ConfigDialog)
- [QString language() const](#language)
- [void setLanguage(const QString &language)](#setLanguage)

## Public Slots

- [void slotApply()](#slotApply)
- [void slotOk()](#slotOk)

## Signals

- [void configChanged()](#configChanged)
- [void languageChanged(const QString &language)](#languageChanged)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ConfigDialog::ConfigDialog(QWidget \**parent*) {#ConfigDialog}

### \[signal\] void ConfigDialog::configChanged() {#configChanged}

This is emitted when configChanged

### QString ConfigDialog::language() const {#language}

return selected language

*See also* [setLanguage](sonnet-configdialog.md#setLanguage)()

### \[signal\] void ConfigDialog::languageChanged(const QString &*language*) {#languageChanged}

This is emitted all the time when we change config and not just language

`language` the language which the user has selected

### void ConfigDialog::setLanguage(const QString &*language*) {#setLanguage}

Sets the language/dictionary that will be selected by default in this config dialog. This overrides the setting in the config file.

`language` the language which will be selected by default.

*See also* [language](sonnet-configdialog.md#language)()

### \[virtual protected slot\] void ConfigDialog::slotApply() {#slotApply}

### \[virtual protected slot\] void ConfigDialog::slotOk() {#slotOk}
