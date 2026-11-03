---
title: "Sonnet::Speller Class"
description: "class used for actual spell checking."
---

# Sonnet::Speller Class

class used for actual spell checking. [More...](#details)

- **Header:** `#include <Sonnet/Speller>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Sonnet)`  
  `target_link_libraries(mytarget PRIVATE KF6::SonnetCore)`

[List of all members, including inherited members](sonnet-speller-members.md)

## Public Types

- [enum Speller::Attribute](#Attribute-enum)

## Public Functions

- [Speller(const QString &lang = QString())](#Speller)
- [bool addToPersonal(const QString &word)](#addToPersonal)
- [bool addToSession(const QString &word)](#addToSession)
- [QStringList availableBackends() const](#availableBackends)
- [QMap\<QString, QString\> availableDictionaries() const](#availableDictionaries)
- [QStringList availableLanguageNames() const](#availableLanguageNames)
- [QStringList availableLanguages() const](#availableLanguages)
- [bool checkAndSuggest(const QString &word, QStringList &suggestions) const](#checkAndSuggest)
- [QString defaultClient() const](#defaultClient)
- [QString defaultLanguage() const](#defaultLanguage)
- [bool isCorrect(const QString &word) const](#isCorrect)
- [bool isMisspelled(const QString &word) const](#isMisspelled)
- [bool isValid() const](#isValid)
- [QString language() const](#language)
- [QMap\<QString, QString\> preferredDictionaries() const](#preferredDictionaries)
- [void restore()](#restore)
- [void save()](#save)
- [void setAttribute(Sonnet::Speller::Attribute attr, bool b = true)](#setAttribute)
- [void setDefaultClient(const QString &client)](#setDefaultClient)
- [void setDefaultLanguage(const QString &lang)](#setDefaultLanguage)
- [void setLanguage(const QString &lang)](#setLanguage)
- [bool storeReplacement(const QString &bad, const QString &good)](#storeReplacement)
- [QStringList suggest(const QString &word) const](#suggest)
- [bool testAttribute(Sonnet::Speller::Attribute attr) const](#testAttribute)

## Detailed Description {#details}

Spell checker object.

## Member Type Documentation {#member-type-documentation}

### enum Speller::Attribute {#Attribute-enum}

| Constant |   |
| --- | --- |
| `Sonnet::Speller::CheckUppercase` | `0` |
| `Sonnet::Speller::SkipRunTogether` | `1` |
| `Sonnet::Speller::AutoDetectLanguage` | `2` |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Speller::Speller(const QString &*lang* = QString()) {#Speller}

### bool Speller::addToPersonal(const QString &*word*) {#addToPersonal}

Adds word to the list of of personal words. Returns true on success

### bool Speller::addToSession(const QString &*word*) {#addToSession}

Adds word to the words recognizable in the current session. Returns true on success

### QStringList Speller::availableBackends() const {#availableBackends}

Returns names of all supported backends (e.g. ISpell, ASpell)

### QMap\<QString, QString\> Speller::availableDictionaries() const {#availableDictionaries}

Returns a map of all available dictionaries with language descriptions and their codes. The key is the description, the code the value.

### QStringList Speller::availableLanguageNames() const {#availableLanguageNames}

Returns a localized list of names of supported languages.

> **Note:** use [availableDictionaries](sonnet-speller.md#availableDictionaries)

### QStringList Speller::availableLanguages() const {#availableLanguages}

Returns a list of supported languages.

> **Note:** use [availableDictionaries](sonnet-speller.md#availableDictionaries)

### bool Speller::checkAndSuggest(const QString &*word*, QStringList &*suggestions*) const {#checkAndSuggest}

Convenience method calling [isCorrect](sonnet-speller.md#isCorrect)() and [suggest](sonnet-speller.md#suggest)() if the word isn't correct.

### QString Speller::defaultClient() const {#defaultClient}

*See also* [setDefaultClient](sonnet-speller.md#setDefaultClient)()

### QString Speller::defaultLanguage() const {#defaultLanguage}

*See also* [setDefaultLanguage](sonnet-speller.md#setDefaultLanguage)()

### bool Speller::isCorrect(const QString &*word*) const {#isCorrect}

Checks the given word. Returns false if the word is misspelled. true otherwise

### bool Speller::isMisspelled(const QString &*word*) const {#isMisspelled}

Checks the given word. Returns true if the word is misspelled. false otherwise

### bool Speller::isValid() const {#isValid}

Returns `true` if the speller supports currently selected language.

### QString Speller::language() const {#language}

Returns language supported by this speller.

*See also* [setLanguage](sonnet-speller.md#setLanguage)()

### QMap\<QString, QString\> Speller::preferredDictionaries() const {#preferredDictionaries}

Returns a map of user preferred dictionaries with language descriptions and their codes. The key is the description, the code the value.

### void Speller::restore() {#restore}

### void Speller::save() {#save}

### void Speller::setAttribute(Sonnet::Speller::Attribute *attr*, bool *b* = true) {#setAttribute}

### void Speller::setDefaultClient(const QString &*client*) {#setDefaultClient}

*See also* [defaultClient](sonnet-speller.md#defaultClient)()

### void Speller::setDefaultLanguage(const QString &*lang*) {#setDefaultLanguage}

*See also* [defaultLanguage](sonnet-speller.md#defaultLanguage)()

### void Speller::setLanguage(const QString &*lang*) {#setLanguage}

Sets the language supported by this speller.

*See also* [language](sonnet-speller.md#language)()

### bool Speller::storeReplacement(const QString &*bad*, const QString &*good*) {#storeReplacement}

Stores user defined good replacement for the bad word.

Returns `true` on success

### QStringList Speller::suggest(const QString &*word*) const {#suggest}

Fetches suggestions for the word.

Returns list of all suggestions for the word

### bool Speller::testAttribute(Sonnet::Speller::Attribute *attr*) const {#testAttribute}
