---
title: "Sonnet::ConfigWidget Class"
description: "The sonnet ConfigWidget."
---

# Sonnet::ConfigWidget Class

The sonnet [ConfigWidget](sonnet-configwidget.md). [More...](#details)

- **Header:** `#include <Sonnet/ConfigWidget>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Sonnet)`  
  `target_link_libraries(mytarget PRIVATE KF6::SonnetUi)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](sonnet-configwidget-members.md)

## Public Functions

- [ConfigWidget(QWidget \*parent)](#ConfigWidget)
- [bool backgroundCheckingButtonShown() const](#backgroundCheckingButtonShown)
- [QString language() const](#language)
- [void setLanguage(const QString &language)](#setLanguage)

## Public Slots

- [void save()](#save)
- [void setBackgroundCheckingButtonShown(bool)](#setBackgroundCheckingButtonShown)
- [void slotDefault()](#slotDefault)
- [void slotIgnoreWordAdded()](#slotIgnoreWordAdded)
- [void slotIgnoreWordRemoved()](#slotIgnoreWordRemoved)

## Signals

- [void configChanged()](#configChanged)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ConfigWidget::ConfigWidget(QWidget \**parent*) {#ConfigWidget}

### bool ConfigWidget::backgroundCheckingButtonShown() const {#backgroundCheckingButtonShown}

*See also* [setBackgroundCheckingButtonShown](sonnet-configwidget.md#setBackgroundCheckingButtonShown)()

### \[signal\] void ConfigWidget::configChanged() {#configChanged}

Signal sends when config was changed

### QString ConfigWidget::language() const {#language}

Get the currently selected language for spell checking. Returns an empty string if Sonnet was built without any spellchecking plugins.

Returns the language currently selected in the language combobox

*See also* [setLanguage](sonnet-configwidget.md#setLanguage)()

### \[slot\] void ConfigWidget::save() {#save}

### \[slot\] void ConfigWidget::setBackgroundCheckingButtonShown(*bool*) {#setBackgroundCheckingButtonShown}

*See also* [backgroundCheckingButtonShown](sonnet-configwidget.md#backgroundCheckingButtonShown)()

### void ConfigWidget::setLanguage(const QString &*language*) {#setLanguage}

Sets the language/dictionary that will be selected by default in this config widget. This overrides the setting in the config file.

`language` the language which will be selected by default.

*See also* [language](sonnet-configwidget.md#language)()

### \[slot\] void ConfigWidget::slotDefault() {#slotDefault}

### \[protected slot\] void ConfigWidget::slotIgnoreWordAdded() {#slotIgnoreWordAdded}

### \[protected slot\] void ConfigWidget::slotIgnoreWordRemoved() {#slotIgnoreWordRemoved}
