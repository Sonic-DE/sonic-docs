---
title: "KTextEditor::ConfigPage Class"
description: "Config page interface for the Editor and Plugin%s."
---

# KTextEditor::ConfigPage Class

Config page interface for the Editor and Plugin%s. [More...](#details)

- **Header:** `#include <KTextEditor/ConfigPage>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextEditor)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextEditor)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](ktexteditor-configpage-members.md)

## Public Functions

- [ConfigPage(QWidget \*parent)](#ConfigPage)
- [QString fullName() const](#fullName)
- [QIcon icon() const](#icon)
- [QString name() const](#name)

## Public Slots

- [void apply()](#apply)
- [void defaults()](#defaults)
- [void reset()](#reset)

## Signals

- [void changed()](#changed)

## Detailed Description {#details}

Introduction

The class [ConfigPage](ktexteditor-configpage.md) represents a config page. The config pages are usually embedded into a dialog that shows buttons like `Defaults`, `Reset` and `Apply`. If one of the buttons is clicked and the config page sent the signal [changed](ktexteditor-configpage.md#changed)() beforehand the Editor will call the corresponding slot, either [defaults](ktexteditor-configpage.md#defaults)(), [reset](ktexteditor-configpage.md#reset)() or [apply](ktexteditor-configpage.md#apply)().

To obtain a useful navigation information for displaying to a user see [name](ktexteditor-configpage.md#name)(), [fullName](ktexteditor-configpage.md#fullName)() and [icon](ktexteditor-configpage.md#icon)() functions.

Saving and Loading Config Data

Saving and loading the configuration data can either be achieved by using the host application's [KSharedConfig::openConfig](../kconfigcore/ksharedconfig.md#openConfig)() object, or by using an own configuration file.

*See also* [KTextEditor::Editor](ktexteditor-index.md), [KTextEditor::Plugin](ktexteditor-index.md)

## Member Function Documentation {#member-function-documentation}

### ConfigPage::ConfigPage(QWidget \**parent*) {#ConfigPage}

Constructor.

Create a new config page with the specified parent.

`parent` is the parent widget

### \[pure virtual slot\] void ConfigPage::apply() {#apply}

This slot is called whenever the button `Apply` or `OK` was clicked. Apply the changed settings made in the config page now.

### \[signal\] void ConfigPage::changed() {#changed}

Emit this signal whenever a config option changed.

### \[pure virtual slot\] void ConfigPage::defaults() {#defaults}

Sets default options This slot is called whenever the button `Defaults` was clicked. Set the config page settings to the default values.

### \[virtual\] QString ConfigPage::fullName() const {#fullName}

Get a readable full name for the config page. The name should be translated.

Example: If the name is "Filetypes", the full name could be "Filetype Specific Settings". For "Shortcuts" the full name would be something like "Shortcut Configuration". Returns full name of given page index, default implementation returns [name](ktexteditor-configpage.md#name)()

*See also* [name](ktexteditor-configpage.md#name)(), [icon](ktexteditor-configpage.md#icon)()

### \[virtual\] QIcon ConfigPage::icon() const {#icon}

Get an icon for the config page. Returns icon for the given page index

*See also* [name](ktexteditor-configpage.md#name)(), [fullName](ktexteditor-configpage.md#fullName)()

### \[pure virtual\] QString ConfigPage::name() const {#name}

Get a readable name for the config page. The name should be translated. Returns name of given page index

*See also* [fullName](ktexteditor-configpage.md#fullName)(), [icon](ktexteditor-configpage.md#icon)()

### \[pure virtual slot\] void ConfigPage::reset() {#reset}

This slot is called whenever the button `Reset` was clicked. Reset the config page settings to the initial state.
