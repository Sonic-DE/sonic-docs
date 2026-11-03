---
title: "KJsonUtils Namespace"
description: "Additions to Qt Core."
---

# KJsonUtils Namespace

Additions to Qt Core. [More...](#details)

- Header: KJsonUtils
- CMake: find\_package(KF6 REQUIRED COMPONENTS CoreAddons) target\_link\_libraries(mytarget PRIVATE KF6::CoreAddons)

## Detailed Description {#details}

Reads a value from `jo` but unlike [QJsonObject::value](https://doc.qt.io/qt-6/qjsonobject.html#value)() it allows different entries for each locale

This is done by appending the locale identifier in brackets to the key (e.g. "\[de\_DE\]" or "\[es\]")

When looking for a key "foo" with German (Germany) locale we will first attempt to read "foo\[de\_DE\]", if that does not exist "foo\[de\]", finally falling back to "foo" if that also doesn't exist.

Returns the translated value for `key` from `jo` or `defaultValue` if `key` was not found

## Function Documentation {#function-documentation}

### QString KJsonUtils::readTranslatedString(const QJsonObject &*jo*, const QString &*key*, const QString &*defaultValue* = QString()) {#readTranslatedString}

Returns the translated value of `key` from `jo` as a string or `defaultValue` if `key` was not found or the value for `key` is not of type string
