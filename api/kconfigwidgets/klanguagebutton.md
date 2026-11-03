---
title: "KLanguageButton Class"
description: "KLanguageButton is a pushbutton which allows a language to be selected from a popup list."
---

# KLanguageButton Class

[KLanguageButton](klanguagebutton.md) is a pushbutton which allows a language to be selected from a popup list. [More...](#details)

- **Header:** `#include <KLanguageButton>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ConfigWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigWidgets)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](klanguagebutton-members.md)

## Public Functions

- [KLanguageButton(QWidget \*parent = nullptr)](#KLanguageButton)
- [KLanguageButton(const QString &text, QWidget \*parent = nullptr)](#KLanguageButton-1)
- [void clear()](#clear)
- [bool contains(const QString &languageCode) const](#contains)
- [int count() const](#count)
- [QString current() const](#current)
- [void insertLanguage(const QString &languageCode, const QString &name = QString(), int index = -1)](#insertLanguage)
- [void insertSeparator(int index = -1)](#insertSeparator)
- [void loadAllLanguages()](#loadAllLanguages)
- [void setCurrentItem(const QString &languageCode)](#setCurrentItem)
- [void setLocale(const QString &locale)](#setLocale)
- [void setText(const QString &text)](#setText)
- [void showLanguageCodes(bool show)](#showLanguageCodes)

## Signals

- [void activated(const QString &languageCode)](#activated)
- [void highlighted(const QString &languageCode)](#highlighted)

## Detailed Description {#details}

Languages are identified by their ISO 639-1 codes, e.g. en, pt\_BR.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KLanguageButton::KLanguageButton(QWidget \**parent* = nullptr) {#KLanguageButton}

Constructs a button whose text is determined by the current language in the popup list.

`parent` the parent of the button

### \[explicit\] KLanguageButton::KLanguageButton(const QString &*text*, QWidget \**parent* = nullptr) {#KLanguageButton-1}

Constructs a button with static text.

`text` the text of the button

`parent` the parent of the button

### \[signal\] void KLanguageButton::activated(const QString &*languageCode*) {#activated}

This signal is emitted when a new item is activated.

`languageCode` code of the activated language

### void KLanguageButton::clear() {#clear}

Removes all combobox items.

### bool KLanguageButton::contains(const QString &*languageCode*) const {#contains}

Checks whether the specified language is in the popup list.

`languageCode` the language's code

### int KLanguageButton::count() const {#count}

Returns the number of items in the combo box.

### QString KLanguageButton::current() const {#current}

Returns the language code of the combobox's current item.

### \[signal\] void KLanguageButton::highlighted(const QString &*languageCode*) {#highlighted}

This signal is emitted when a new item is highlighted.

`languageCode` code of the highlighted language

### void KLanguageButton::insertLanguage(const QString &*languageCode*, const QString &*name* = QString(), int *index* = -1) {#insertLanguage}

Inserts a language into the combo box.

Normally the display name of the language is obtained automatically, but if either the language code does not exist, or there are special display requirements, the name of the language can be specified in `name`.

`languageCode` the code for the language

`name` language name. If empty, the name is obtained automatically

`index` the insertion position, or -1 to insert in alphabetical order

### void KLanguageButton::insertSeparator(int *index* = -1) {#insertSeparator}

Inserts a separator item into the combo box. A negative index will append the item.

`index` the insertion position

### void KLanguageButton::loadAllLanguages() {#loadAllLanguages}

Load all known languages into the popup list.

The current language in the list is set to the default language for the current locale (as modified by [setLocale](klanguagebutton.md#setLocale)()).

### void KLanguageButton::setCurrentItem(const QString &*languageCode*) {#setCurrentItem}

Sets a given language to be the current item.

`languageCode` the language's code

### void KLanguageButton::setLocale(const QString &*locale*) {#setLocale}

Sets the locale to display language names. By default, [QLocale::system](https://doc.qt.io/qt-6/qlocale.html#system)().name() is used.

`locale` locale to use

### void KLanguageButton::setText(const QString &*text*) {#setText}

Sets a static button text.

`text` button text

### void KLanguageButton::showLanguageCodes(bool *show*) {#showLanguageCodes}

Specifies whether language codes should be shown alongside language names in the popup. Calling this method does not affect any previously inserted language texts, so it should normally be called before populating the list.

`show` `true` to show codes, `false` to hide codes
