---
title: "Sonnet::DictionaryComboBox Class"
description: "A combo box for selecting the dictionary used for spell checking."
---

# Sonnet::DictionaryComboBox Class

A combo box for selecting the dictionary used for spell checking. [More...](#details)

- **Header:** `#include <Sonnet/DictionaryComboBox>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Sonnet)`  
  `target_link_libraries(mytarget PRIVATE KF6::SonnetUi)`
- **Inherits:** [QComboBox](https://doc.qt.io/qt-6/qcombobox.html)

[List of all members, including inherited members](sonnet-dictionarycombobox-members.md)

## Public Functions

- [DictionaryComboBox(QWidget \*parent = nullptr)](#DictionaryComboBox)
- [bool assignByDictionnary(const QString &dictionary)](#assignByDictionnary)
- [bool assignDictionnaryName(const QString &name)](#assignDictionnaryName)
- [QString currentDictionary() const](#currentDictionary)
- [QString currentDictionaryName() const](#currentDictionaryName)
- [void reloadCombo()](#reloadCombo)
- [void setCurrentByDictionary(const QString &dictionary)](#setCurrentByDictionary)
- [void setCurrentByDictionaryName(const QString &dictionaryName)](#setCurrentByDictionaryName)

## Signals

- [void dictionaryChanged(const QString &dictionary)](#dictionaryChanged)
- [void dictionaryNameChanged(const QString &dictionaryName)](#dictionaryNameChanged)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] DictionaryComboBox::DictionaryComboBox(QWidget \**parent* = nullptr) {#DictionaryComboBox}

Constructor

### bool DictionaryComboBox::assignByDictionnary(const QString &*dictionary*) {#assignByDictionnary}

Sets the current dictionary to the given dictionary Return true if dictionary was found.

### bool DictionaryComboBox::assignDictionnaryName(const QString &*name*) {#assignDictionnaryName}

Sets the current dictionaryName to the given dictionaryName Return true if dictionary was found.

### QString DictionaryComboBox::currentDictionary() const {#currentDictionary}

Returns the current dictionary, for example "de\_CH"

### QString DictionaryComboBox::currentDictionaryName() const {#currentDictionaryName}

Returns the current dictionary name, for example "German (Switzerland)"

### \[signal\] void DictionaryComboBox::dictionaryChanged(const QString &*dictionary*) {#dictionaryChanged}

Emitted whenever the current dictionary changes. Either by user intervention or on [setCurrentByDictionaryName](sonnet-dictionarycombobox.md#setCurrentByDictionaryName)() or on [setCurrentByDictionary](sonnet-dictionarycombobox.md#setCurrentByDictionary)(). For example "de\_CH".

### \[signal\] void DictionaryComboBox::dictionaryNameChanged(const QString &*dictionaryName*) {#dictionaryNameChanged}

Emitted whenever the current dictionary changes. Either by user intervention or on [setCurrentByDictionaryName](sonnet-dictionarycombobox.md#setCurrentByDictionaryName)() or on [setCurrentByDictionary](sonnet-dictionarycombobox.md#setCurrentByDictionary)(). For example "German (Switzerland)".

### void DictionaryComboBox::reloadCombo() {#reloadCombo}

Clears the widget and reloads the dictionaries from Sonnet. Remember to set the dictionary you want selected after calling this function.

### void DictionaryComboBox::setCurrentByDictionary(const QString &*dictionary*) {#setCurrentByDictionary}

Sets the current dictionary to the given dictionary.

### void DictionaryComboBox::setCurrentByDictionaryName(const QString &*dictionaryName*) {#setCurrentByDictionaryName}

Sets the current dictionaryName to the given dictionaryName
