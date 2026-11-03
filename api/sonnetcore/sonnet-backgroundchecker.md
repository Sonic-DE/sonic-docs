---
title: "Sonnet::BackgroundChecker Class"
description: "class used for spell checking in the background."
---

# Sonnet::BackgroundChecker Class

class used for spell checking in the background. [More...](#details)

- **Header:** `#include <Sonnet/BackgroundChecker>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Sonnet)`  
  `target_link_libraries(mytarget PRIVATE KF6::SonnetCore)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](sonnet-backgroundchecker-members.md)

## Public Functions

- [BackgroundChecker(QObject \*parent = nullptr)](#BackgroundChecker)
- [BackgroundChecker(const Sonnet::Speller &speller, QObject \*parent = nullptr)](#BackgroundChecker-1)
- [bool addWordToPersonal(const QString &word)](#addWordToPersonal)
- [bool addWordToSession(const QString &word)](#addWordToSession)
- [bool autoDetectLanguageDisabled() const](#autoDetectLanguageDisabled)
- [bool checkWord(const QString &word)](#checkWord)
- [QString currentContext() const](#currentContext)
- [void setAutoDetectLanguageDisabled(bool autoDetectDisabled)](#setAutoDetectLanguageDisabled)
- [void setSpeller(const Sonnet::Speller &speller)](#setSpeller)
- [void setText(const QString &text)](#setText)
- [Sonnet::Speller speller() const](#speller)
- [QStringList suggest(const QString &word) const](#suggest)
- [QString text() const](#text)

## Public Slots

- [void changeLanguage(const QString &lang)](#changeLanguage)
- [void continueChecking()](#continueChecking)
- [void replace(int start, const QString &oldText, const QString &newText)](#replace)
- [void slotEngineDone()](#slotEngineDone)
- [void start()](#start)
- [void stop()](#stop)

## Signals

- [void done()](#done)
- [void misspelling(const QString &word, int start)](#misspelling)

## Protected Functions

- [QString fetchMoreText()](#fetchMoreText)
- [void finishedCurrentFeed()](#finishedCurrentFeed)

## Detailed Description {#details}

[BackgroundChecker](sonnet-backgroundchecker.md) is used to perform spell checking without blocking the application. You can use it as is by calling the checkText function or subclass it and reimplement getMoreText function.

The misspelling signal is emitted whenever a misspelled word is found. The background checker stops right before emitting the signal. So the parent has to call [continueChecking](sonnet-backgroundchecker.md#continueChecking) function to resume the checking.

The [done](sonnet-backgroundchecker.md#done)() signal is emitted when whole text is spell checked.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] BackgroundChecker::BackgroundChecker(QObject \**parent* = nullptr) {#BackgroundChecker}

### \[explicit\] BackgroundChecker::BackgroundChecker(const Sonnet::Speller &*speller*, QObject \**parent* = nullptr) {#BackgroundChecker-1}

### bool BackgroundChecker::addWordToPersonal(const QString &*word*) {#addWordToPersonal}

### bool BackgroundChecker::addWordToSession(const QString &*word*) {#addWordToSession}

This method is used to add a word to the session of the speller currently set in [BackgroundChecker](sonnet-backgroundchecker.md).

### bool BackgroundChecker::autoDetectLanguageDisabled() const {#autoDetectLanguageDisabled}

Returns whether the automatic language detection is disabled, overriding the Sonnet settings.

Returns true if the automatic language detection is disabled

*See also* [setAutoDetectLanguageDisabled](sonnet-backgroundchecker.md#setAutoDetectLanguageDisabled)()

### \[slot\] void BackgroundChecker::changeLanguage(const QString &*lang*) {#changeLanguage}

### bool BackgroundChecker::checkWord(const QString &*word*) {#checkWord}

### \[virtual slot\] void BackgroundChecker::continueChecking() {#continueChecking}

After emitting misspelling signal the background checker stops. The catcher is responsible for calling continueChecking function to resume checking.

### QString BackgroundChecker::currentContext() const {#currentContext}

### \[signal\] void BackgroundChecker::done() {#done}

Emitted after the whole text has been spell checked.

### \[virtual protected\] QString BackgroundChecker::fetchMoreText() {#fetchMoreText}

This function is called to get the text to spell check. It will be called continuesly until it returns QString() in which case the [done](sonnet-backgroundchecker.md#done)() signal is emitted.

> **Note:** the start parameter in [misspelling](sonnet-backgroundchecker.md#misspelling)() is not a combined position but a position in the last string returned by fetchMoreText. You need to store the state in the derivatives.

### \[virtual protected\] void BackgroundChecker::finishedCurrentFeed() {#finishedCurrentFeed}

This function will be called whenever the background checker will be finished text which it got from [fetchMoreText](sonnet-backgroundchecker.md#fetchMoreText).

### \[signal\] void BackgroundChecker::misspelling(const QString &*word*, int *start*) {#misspelling}

Emitted whenever a misspelled word is found

### \[slot\] void BackgroundChecker::replace(int *start*, const QString &*oldText*, const QString &*newText*) {#replace}

### void BackgroundChecker::setAutoDetectLanguageDisabled(bool *autoDetectDisabled*) {#setAutoDetectLanguageDisabled}

Sets whether to disable the automatic language detection.

`autoDetectDisabled` if true, the language will not be detected automatically by the spell checker, even if the option is enabled in the Sonnet settings.

*See also* [autoDetectLanguageDisabled](sonnet-backgroundchecker.md#autoDetectLanguageDisabled)()

### void BackgroundChecker::setSpeller(const Sonnet::Speller &*speller*) {#setSpeller}

*See also* [speller](sonnet-backgroundchecker.md#speller)()

### void BackgroundChecker::setText(const QString &*text*) {#setText}

This method is used to spell check static text. It automatically invokes [start](sonnet-backgroundchecker.md#start)().

Use [fetchMoreText](sonnet-backgroundchecker.md#fetchMoreText)() with [start](sonnet-backgroundchecker.md#start)() to spell check a stream.

*See also* [text](sonnet-backgroundchecker.md#text)()

### \[protected slot\] void BackgroundChecker::slotEngineDone() {#slotEngineDone}

### Sonnet::Speller BackgroundChecker::speller() const {#speller}

*See also* [setSpeller](sonnet-backgroundchecker.md#setSpeller)()

### \[virtual slot\] void BackgroundChecker::start() {#start}

### \[virtual slot\] void BackgroundChecker::stop() {#stop}

### QStringList BackgroundChecker::suggest(const QString &*word*) const {#suggest}

### QString BackgroundChecker::text() const {#text}

*See also* [setText](sonnet-backgroundchecker.md#setText)()
