---
title: "KCharsets Class"
description: "Charset font and encoder/decoder handling."
---

# KCharsets Class

Charset font and encoder/decoder handling. [More...](#details)

- **Header:** `#include <KCharsets>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Codecs)`  
  `target_link_libraries(mytarget PRIVATE KF6::Codecs)`

[List of all members, including inherited members](kcharsets-members.md)

## Public Functions

- [QStringList availableEncodingNames() const](#availableEncodingNames)
- [QString descriptionForEncoding(QStringView encoding) const](#descriptionForEncoding)
- [QStringList descriptiveEncodingNames() const](#descriptiveEncodingNames)
- [QString encodingForName(const QString &descriptiveName) const](#encodingForName)
- [QList\<QStringList\> encodingsByScript() const](#encodingsByScript)

## Static Public Members

- [KCharsets \*charsets()](#charsets)
- [QChar fromEntity(QStringView str)](#fromEntity)
- [QChar fromEntity(QStringView str, int &len)](#fromEntity-1)
- [QString resolveEntities(const QString &text)](#resolveEntities)
- [QString toEntity(const QChar &ch)](#toEntity)

## Detailed Description {#details}

This is needed, because Qt's encoding name matching in [QTextCodec::codecForName](https://doc.qt.io/qt-6/qtextcodec.html#codecForName)() matches only closely-related encoded names but not alternate names, e.g. found in the reality of the Internet.

## Member Function Documentation {#member-function-documentation}

### QStringList KCharsets::availableEncodingNames() const {#availableEncodingNames}

Lists all available encodings as names

### \[static\] KCharsets \*KCharsets::charsets() {#charsets}

The global charset manager.

### QString KCharsets::descriptionForEncoding(QStringView *encoding*) const {#descriptionForEncoding}

Returns a long description for an encoding name.

`encoding` the encoding for the language

### QStringList KCharsets::descriptiveEncodingNames() const {#descriptiveEncodingNames}

Lists the available encoding names together with a more descriptive language

### QString KCharsets::encodingForName(const QString &*descriptiveName*) const {#encodingForName}

Returns the encoding for a string obtained with [descriptiveEncodingNames](kcharsets.md#descriptiveEncodingNames)().

`descriptiveName` the descriptive name for the encoding

### QList\<QStringList\> KCharsets::encodingsByScript() const {#encodingsByScript}

Lists the available encoding names grouped by script (or language that uses them).

Returns the list of lists consisting of description followed by encoding names (i.e. encodingsByScript().at(i).at(0) is a description for encodingsByScript().at(i).at(k), k\>0)

### \[static\] QChar KCharsets::fromEntity(QStringView *str*) {#fromEntity}

Converts an entity to a character.

The string must contain only the entity *without* the trailing ';'. For numeric character references, the leading '&' *may* be included.

`str` the entity

Returns [QChar::Null](https://doc.qt.io/qt-6/qchar.html#SpecialCharacter-enum) if the entity could not be decoded.

### \[static\] QChar KCharsets::fromEntity(QStringView *str*, int &*len*) {#fromEntity-1}

Tries to find an entity in the [QString](https://doc.qt.io/qt-6/qstring.html) str.

`str` the string containing entified

`len` is a return value, that gives the length of the decoded entity.

Returns a decoded entity if one could be found, QChar::null otherwise

This function overloads [KCharsets::fromEntity(QStringView)](kcharsets.md#fromEntity).

### \[static\] QString KCharsets::resolveEntities(const QString &*text*) {#resolveEntities}

Scans the given string for entities (like &amp;amp;) and resolves them using [fromEntity](kcharsets.md#fromEntity).

`text` the string containing the entities

Returns the clean string

### \[static\] QString KCharsets::toEntity(const QChar &*ch*) {#toEntity}

Converts a [QChar](https://doc.qt.io/qt-6/qchar.html) to an entity. The returned string does already contain the leading '&' and the trailing ';'.

`ch` the char to convert

Returns the entity
