---
title: "KLanguageName Namespace"
description: "KLanguageName is a helper namespace that returns the name of a given language code."
---

# KLanguageName Namespace

[KLanguageName](klanguagename.md) is a helper namespace that returns the name of a given language code. [More...](#details)

- Header: KLanguageName
- CMake: find\_package(KF6 REQUIRED COMPONENTS ConfigWidgets) target\_link\_libraries(mytarget PRIVATE KF6::ConfigWidgets)

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### QStringList KLanguageName::allLanguageCodes() {#allLanguageCodes}

Returns the list of language codes found on the system.

### QString KLanguageName::nameForCode(const QString &*code*) {#nameForCode}

Returns the name of the given language code in the current locale.

If it can't be found in the current locale it returns the name in English.

It it can't be found in English either it returns an empty [QString](https://doc.qt.io/qt-6/qstring.html).

`code` code (ISO 639-1) of the language whose name is wanted.

### QString KLanguageName::nameForCodeInLocale(const QString &*code*, const QString &*outputLocale*) {#nameForCodeInLocale}

Returns the name of the given language code in the other given locale code.

If it can't be found in the given locale it returns the name in English.

It it can't be found in English either it returns an empty [QString](https://doc.qt.io/qt-6/qstring.html).

`code` code (ISO 639-1) of the language whose name is wanted.

`outputLocale` code (ISO 639-1) of the language in which we want the name in.
