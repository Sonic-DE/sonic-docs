---
title: "KStringHandler Namespace"
description: "This namespace contains utility functions for handling strings."
---

# KStringHandler Namespace

This namespace contains utility functions for handling strings. [More...](#details)

- **Header:** `#include <KStringHandler>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`

## Detailed Description {#details}

The functions here are intended to provide an easy way to cut/slice/splice words inside sentences in whatever order desired. While the main focus of [KStringHandler](kstringhandler.md) is words (ie characters separated by spaces/tabs), the two core functions here (split() and join()) will allow you to use any character as a separator This will make it easy to redefine what a 'word' means in the future if needed.

The function names and calling styles are based on python and mIRC's scripting support.

The ranges are a fairly powerful way of getting/stripping words from a string. These ranges function, for the large part, as they would in python. See the word(const [QString](https://doc.qt.io/qt-6/qstring.html)&, int) and remword(const [QString](https://doc.qt.io/qt-6/qstring.html)&, int) functions for more detail.

The methods here are completely stateless. All strings are cut on the fly and returned as new qstrings/qstringlists.

*See also* [KShell](kshell.md)

## Function Documentation {#function-documentation}

### QString KStringHandler::capwords(const QString &*text*) {#capwords}

Capitalizes each word in the string "hello there" becomes "Hello There" (string)

`text` the text to capitalize

Returns the resulting string

### QStringList KStringHandler::capwords(const QStringList &*list*) {#capwords-1}

Capitalizes each word in the list \[hello, there\] becomes \[Hello, There\] (list)

`list` the list to capitalize

Returns the resulting list

### QString KStringHandler::csqueeze(const QString &*str*, int *maxlen* = 40) {#csqueeze}

Substitute characters at the middle of a string by "...".

`str` is the string to modify

`maxlen` is the maximum length the modified string will have

If the original string is shorter than "maxlen", it is returned verbatim

Returns the modified string

### int KStringHandler::logicalLength(const QString &*text*) {#logicalLength}

Returns the length that reflects the density of information in the text. In general the character from CJK languages are assigned with weight 2, while other Latin characters are assigned with 1.

### QString KStringHandler::lsqueeze(const QString &*str*, int *maxlen* = 40) {#lsqueeze}

Substitute characters at the beginning of a string by "...".

`str` is the string to modify

`maxlen` is the maximum length the modified string will have

If the original string is shorter than "maxlen", it is returned verbatim

Returns the modified string

### QString KStringHandler::obscure(const QString &*str*) {#obscure}

Obscure string by using a simple symmetric encryption. Applying the function to a string obscured by this function will result in the original string.

The function can be used to obscure passwords stored to configuration files. Note that this won't give you any more security than preventing that the password is directly copied and pasted.

`str` string to be obscured

Returns obscured string

### QStringList KStringHandler::perlSplit(const QChar &*sep*, const QString &*s*, int *max* = 0) {#perlSplit}

Split a [QString](https://doc.qt.io/qt-6/qstring.html) into a [QStringList](https://doc.qt.io/qt-6/qstringlist.html) in a similar fashion to the static [QStringList](https://doc.qt.io/qt-6/qstringlist.html) function in Qt, except you can specify a maximum number of tokens. If max is specified (!= 0) then only that number of tokens will be extracted. The final token will be the remainder of the string.

Example:

```cpp
perlSplit(' ', "kparts reaches the parts other parts can't", 3)
QStringList contains: "kparts", "reaches", "the parts other parts can't"
```

`sep` is the character to use to delimit s.

`s` is the input string

`max` is the maximum number of extractions to perform, or 0.

Returns a [QStringList](https://doc.qt.io/qt-6/qstringlist.html) containing tokens extracted from s.

### QStringList KStringHandler::perlSplit(const QRegularExpression &*sep*, const QString &*s*, int *max* = 0) {#perlSplit-1}

Split a [QString](https://doc.qt.io/qt-6/qstring.html) into a [QStringList](https://doc.qt.io/qt-6/qstringlist.html) in a similar fashion to the static [QStringList](https://doc.qt.io/qt-6/qstringlist.html) function in Qt, except you can specify a maximum number of tokens. If max is specified (!= 0) then only that number of tokens will be extracted. The final token will be the remainder of the string.

Example:

```cpp
perlSplit(QRegularExpression("[! ]"), "Split me up ! I'm bored ! OK ?", 3)
QStringList contains: "Split", "me", "up ! I'm bored ! OK ?"
```

`sep` is the regular expression to use to delimit s.

`s` is the input string

`max` is the maximum number of extractions to perform, or 0.

Returns a [QStringList](https://doc.qt.io/qt-6/qstringlist.html) containing tokens extracted from s.

### QStringList KStringHandler::perlSplit(const QString &*sep*, const QString &*s*, int *max* = 0) {#perlSplit-2}

Split a [QString](https://doc.qt.io/qt-6/qstring.html) into a [QStringList](https://doc.qt.io/qt-6/qstringlist.html) in a similar fashion to the static [QStringList](https://doc.qt.io/qt-6/qstringlist.html) function in Qt, except you can specify a maximum number of tokens. If max is specified (!= 0) then only that number of tokens will be extracted. The final token will be the remainder of the string.

Example:

```cpp
perlSplit("__", "some__string__for__you__here", 4)
QStringList contains: "some", "string", "for", "you__here"
```

`sep` is the string to use to delimit s.

`s` is the input string

`max` is the maximum number of extractions to perform, or 0.

Returns A [QStringList](https://doc.qt.io/qt-6/qstringlist.html) containing tokens extracted from s.

### QStringList KStringHandler::perlSplit(const QStringView *sep*, const QStringView *str*, int *max*) {#perlSplit-3}

Split a string into a [QStringList](https://doc.qt.io/qt-6/qstringlist.html) in a similar fashion to the static [QStringList](https://doc.qt.io/qt-6/qstringlist.html) function in Qt, except you can specify a maximum number of tokens. If max is specified (!= 0) then only that number of tokens will be extracted. The final token will be the remainder of the string.

Example:

```cpp
perlSplit("__", "some__string__for__you__here", 4)
QStringList contains: "some", "string", "for", "you__here"
```

`sep` is the string to use to delimit `str`

`str` the string to split

`max` the maximum number of extractions to perform, or 0

Returns a [QStringList](https://doc.qt.io/qt-6/qstringlist.html) containing tokens extracted from `str`

### QString KStringHandler::preProcessWrap(const QString &*text*) {#preProcessWrap}

Preprocesses the given string in order to provide additional line breaking opportunities for QTextLayout.

This is done by inserting ZWSP (Zero-width space) characters in the string at points that wouldn't normally be considered word boundaries by QTextLayout, but where wrapping the text will produce good results.

Examples of such points includes after punctuation signs, underscores and dashes, that aren't followed by spaces.

### QString KStringHandler::rsqueeze(const QString &*str*, int *maxlen* = 40) {#rsqueeze}

Substitute characters at the end of a string by "...".

`str` is the string to modify

`maxlen` is the maximum length the modified string will have

If the original string is shorter than "maxlen", it is returned verbatim

Returns the modified string

### QString KStringHandler::tagUrls(const QString &*text*) {#tagUrls}

This method auto-detects URLs in strings, and adds HTML markup to them so that richtext or HTML-enabled widgets will display the URL correctly.

`text` the string which may contain URLs

Returns the resulting text
