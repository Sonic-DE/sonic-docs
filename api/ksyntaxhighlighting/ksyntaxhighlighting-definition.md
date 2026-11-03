---
title: "KSyntaxHighlighting::Definition Class"
description: "Stand-alone implementation of the Kate syntax highlighting engine."
---

# KSyntaxHighlighting::Definition Class

Stand-alone implementation of the Kate syntax highlighting engine. [More...](#details)

- **Header:** `#include <KSyntaxHighlighting/Definition>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KSyntaxHighlighting)`  
  `target_link_libraries(mytarget PRIVATE KF6::KSyntaxHighlighting)`

[List of all members, including inherited members](ksyntaxhighlighting-definition-members.md)

## Properties

- [\[read-only\] author : QString](#author-prop)
- [\[read-only\] license : QString](#license-prop)
- [\[read-only\] name : QString](#name-prop)
- [\[read-only\] section : QString](#section-prop)
- [\[read-only\] translatedName : QString](#translatedName-prop)
- [\[read-only\] translatedSection : QString](#translatedSection-prop)

## Public Functions

- [Definition()](#Definition)
- [Definition(const KSyntaxHighlighting::Definition &other)](#Definition-2)
- [Definition(KSyntaxHighlighting::Definition &&other)](#Definition-1)
- [QStringList alternativeNames() const](#alternativeNames) (since 6.1)
- [QString author() const](#author)
- [QList\<QPair\<QChar, QString\>\> characterEncodings() const](#characterEncodings)
- [QList\<QString\> extensions() const](#extensions)
- [QString filePath() const](#filePath)
- [bool foldingEnabled() const](#foldingEnabled)
- [QStringList foldingIgnoreList() const](#foldingIgnoreList)
- [QList\<KSyntaxHighlighting::Format\> formats() const](#formats)
- [QList\<KSyntaxHighlighting::Definition\> includedDefinitions() const](#includedDefinitions)
- [bool indentationBasedFoldingEnabled() const](#indentationBasedFoldingEnabled)
- [QString indenter() const](#indenter)
- [bool isHidden() const](#isHidden)
- [bool isValid() const](#isValid)
- [bool isWordDelimiter(QChar c) const](#isWordDelimiter)
- [bool isWordWrapDelimiter(QChar c) const](#isWordWrapDelimiter)
- [QStringList keywordList(const QString &name) const](#keywordList)
- [QStringList keywordLists() const](#keywordLists)
- [QString license() const](#license)
- [QList\<QString\> mimeTypes() const](#mimeTypes)
- [QPair\<QString, QString\> multiLineCommentMarker() const](#multiLineCommentMarker)
- [QString name() const](#name)
- [int priority() const](#priority)
- [QString section() const](#section)
- [bool setKeywordList(const QString &name, const QStringList &content)](#setKeywordList)
- [QString singleLineCommentMarker() const](#singleLineCommentMarker)
- [KSyntaxHighlighting::CommentPosition singleLineCommentPosition() const](#singleLineCommentPosition)
- [QString style() const](#style)
- [QString translatedName() const](#translatedName)
- [QString translatedSection() const](#translatedSection)
- [int version() const](#version)
- [bool Definition::operator!=(const KSyntaxHighlighting::Definition &other) const](#operator-not-eq)
- [KSyntaxHighlighting::Definition &Definition::operator=(KSyntaxHighlighting::Definition &&other)](#operator-eq)
- [KSyntaxHighlighting::Definition &Definition::operator=(const KSyntaxHighlighting::Definition &rhs)](#operator-eq-1)
- [bool Definition::operator==(const KSyntaxHighlighting::Definition &other) const](#operator-eq-eq)

## Detailed Description {#details}

Represents a syntax definition.

A Definition is the short term for a syntax highlighting definition. It typically is defined in terms of an XML syntax highlighting file, containing all information about a particular syntax highlighting. This includes the highlighting of keywords, information about code folding regions, and indentation preferences.

Each Definition contains a non-translated unique [name](ksyntaxhighlighting-definition.md#name)() and a [section](ksyntaxhighlighting-definition.md#section)(). In addition, for putting this information e.g. into menus, the functions [translatedName](ksyntaxhighlighting-definition.md#translatedName)() and [translatedSection](ksyntaxhighlighting-definition.md#translatedSection)() are provided. However, if [isHidden](ksyntaxhighlighting-definition.md#isHidden)() returns `true`, the Definition should not be visible in the UI. The location of the Definition can be obtained through [filePath](ksyntaxhighlighting-definition.md#filePath)(), which either is the location on disk or a path to a compiled-in Qt resource.

The supported files of a Definition are defined by the list of [extensions](ksyntaxhighlighting-definition.md#extensions)(), and additionally by the list of [mimeTypes](ksyntaxhighlighting-definition.md#mimeTypes)(). Note, that [extensions](ksyntaxhighlighting-definition.md#extensions)() returns wildcards that need to be matched against the filename of the file that requires highlighting. If multiple Definition%s match the file, then the one with higher [priority](ksyntaxhighlighting-definition.md#priority)() wins.

Advanced text editors such as Kate require additional information from a Definition. For instance, [foldingEnabled](ksyntaxhighlighting-definition.md#foldingEnabled)() defines whether a Definition has code folding regions that can be shown in a code folding pane. Or [singleLineCommentMarker](ksyntaxhighlighting-definition.md#singleLineCommentMarker)() and [multiLineCommentMarker](ksyntaxhighlighting-definition.md#multiLineCommentMarker)() provide comment markers that can be used for commenting/uncommenting code. Similarly, [formats](ksyntaxhighlighting-definition.md#formats)() returns a list of Format items defined by this Definition (which equal the itemDatas of a highlighting definition file). [includedDefinitions](ksyntaxhighlighting-definition.md#includedDefinitions)() returns a list of all included Definition%s referenced by this Definition via the rule IncludeRules, which is useful for displaying all Format items for color configuration in the user interface.

*See also* [Repository](ksyntaxhighlighting-repository.md)

## Property Documentation {#property-documentation}

### \[read-only\] author : QString {#author-prop}

**Access functions:**

- `QString` **[author](ksyntaxhighlighting-definition.md#author)**() const

### \[read-only\] license : QString {#license-prop}

**Access functions:**

- `QString` **[license](ksyntaxhighlighting-definition.md#license)**() const

### \[read-only\] name : QString {#name-prop}

**Access functions:**

- `QString` **[name](ksyntaxhighlighting-definition.md#name)**() const

### \[read-only\] section : QString {#section-prop}

**Access functions:**

- `QString` **[section](ksyntaxhighlighting-definition.md#section)**() const

### \[read-only\] translatedName : QString {#translatedName-prop}

**Access functions:**

- `QString` **[translatedName](ksyntaxhighlighting-definition.md#translatedName)**() const

### \[read-only\] translatedSection : QString {#translatedSection-prop}

**Access functions:**

- `QString` **[translatedSection](ksyntaxhighlighting-definition.md#translatedSection)**() const

## Member Function Documentation {#member-function-documentation}

### Definition::Definition() {#Definition}

Default constructor, creating an empty (invalid) Definition instance. [isValid](ksyntaxhighlighting-definition.md#isValid)() for this instance returns `false`.

Use the Repository instead to obtain valid instances.

### Definition::Definition(const KSyntaxHighlighting::Definition &*other*) {#Definition-2}

Copy constructor.

Both this definition as well as `other` share the Definition data.

### \[noexcept\] Definition::Definition(KSyntaxHighlighting::Definition &&*other*) {#Definition-1}

Move constructor. This definition takes the Definition data from `other`.

> **Note:** `other` may only be assigned to or destroyed afterwards.

### \[since 6.1\] QStringList Definition::alternativeNames() const {#alternativeNames}

Alternate names the syntax can be referred to by.

This function was introduced in Qt 6.1.

### QString Definition::author() const {#author}

Name and email of the author of this syntax definition.

> **Note:** Getter function for property [author](ksyntaxhighlighting-definition.md#author-prop).

### QList\<QPair\<QChar, QString\>\> Definition::characterEncodings() const {#characterEncodings}

Returns a list of character/string mapping that can be used for spell checking. This is useful for instance when spell checking LaTeX, where the string "{A} represents the character Ä.

If a mapping is done to the null character, one should ignore this encoding for spell checking.

### QList\<QString\> Definition::extensions() const {#extensions}

File extensions associated with this syntax definition. The returned list contains wildcards.

### QString Definition::filePath() const {#filePath}

Returns the full path to the definition XML file containing the syntax definition. Note that this can be a path to QRC content.

### bool Definition::foldingEnabled() const {#foldingEnabled}

Returns whether the highlighting supports code folding. Code folding is supported either if the highlighting defines code folding regions or if [indentationBasedFoldingEnabled](ksyntaxhighlighting-definition.md#indentationBasedFoldingEnabled)() returns `true`.

*See also* [indentationBasedFoldingEnabled](ksyntaxhighlighting-definition.md#indentationBasedFoldingEnabled)()

### QStringList Definition::foldingIgnoreList() const {#foldingIgnoreList}

If [indentationBasedFoldingEnabled](ksyntaxhighlighting-definition.md#indentationBasedFoldingEnabled)() returns `true`, this function returns a list of regular expressions that represent empty lines. That is, all lines matching entirely one of the regular expressions should be treated as empty lines when calculating the indentation-based folding ranges.

> **Note:** This list is only of relevance, if [indentationBasedFoldingEnabled](ksyntaxhighlighting-definition.md#indentationBasedFoldingEnabled)() returns `true`.

*See also* [indentationBasedFoldingEnabled](ksyntaxhighlighting-definition.md#indentationBasedFoldingEnabled)()

### QList\<KSyntaxHighlighting::Format\> Definition::formats() const {#formats}

Returns a list of all Format items used by this definition. The order of the Format items equals the order of the itemDatas in the xml file.

### QList\<KSyntaxHighlighting::Definition\> Definition::includedDefinitions() const {#includedDefinitions}

Returns a list of Definitions that are referenced with the IncludeRules rule. The returned list does not include this Definition. In case no other Definitions are referenced via IncludeRules, the returned list is empty.

### bool Definition::indentationBasedFoldingEnabled() const {#indentationBasedFoldingEnabled}

Returns whether indentation-based folding is enabled. An example for indentation-based folding is Python. When indentation-based folding is enabled, make sure to also check [foldingIgnoreList](ksyntaxhighlighting-definition.md#foldingIgnoreList)() for lines that should be treated as empty.

*See also* [foldingIgnoreList](ksyntaxhighlighting-definition.md#foldingIgnoreList)(), [State::indentationBasedFoldingEnabled](ksyntaxhighlighting-state.md#indentationBasedFoldingEnabled)()

### QString Definition::indenter() const {#indenter}

Indentation style to be used for this syntax.

### bool Definition::isHidden() const {#isHidden}

Returns `true` if this is an internal definition that should not be displayed to the user.

### bool Definition::isValid() const {#isValid}

Checks whether this object refers to a valid syntax definition.

### bool Definition::isWordDelimiter(QChar *c*) const {#isWordDelimiter}

Returns whether the character `c` is a word delimiter. A delimiter defines whether a characters is a word boundary. Internally, delimiters are used for matching keyword lists. As example, typically the dot '.' is a word delimiter. However, if you have a keyword in a keyword list that contains a dot, you have to add the dot to the weakDeliminator attribute of the general section in your highlighting definition. Similarly, sometimes additional delimiters are required, which can be specified in additionalDeliminator.

Checking whether a character is a delimiter is useful for instance if text is selected with double click. Typically, the whole word should be selected in this case. Similarly to the example above, the dot '.' usually acts as word delimiter. However, using this function you can implement text selection in such a way that keyword lists are correctly selected.

> **Note:** By default, the list of delimiters contains the following characters: \\t !%&()\*+,-./:;\<=\>?\[\\\]^{\|}~

*See also* [isWordWrapDelimiter](ksyntaxhighlighting-definition.md#isWordWrapDelimiter)()

### bool Definition::isWordWrapDelimiter(QChar *c*) const {#isWordWrapDelimiter}

Returns whether it is safe to break a line at before the character `.` This is useful when wrapping a line e.g. by applying static word wrap.

As example, consider the LaTeX code

```cpp
\command1\command2
```

Applying static word wrap could lead to the following code:

```cpp
\command1\
command2
```

command2 without a leading backslash is invalid in LaTeX. If '\\' is set as word wrap delimiter, isWordWrapDelimiter('\\') then returns true, meaning that it is safe to break the line before `.` The resulting code then would be

```cpp
\command1
\command2
```

> **Note:** By default, the word wrap delimiters are equal to the word delimiters in [isWordDelimiter](ksyntaxhighlighting-definition.md#isWordDelimiter)().

*See also* [isWordDelimiter](ksyntaxhighlighting-definition.md#isWordDelimiter)()

### QStringList Definition::keywordList(const QString &*name*) const {#keywordList}

Returns the list of keywords for the keyword list `name`.

*See also* [keywordLists](ksyntaxhighlighting-definition.md#keywordLists)(), [setKeywordList](ksyntaxhighlighting-definition.md#setKeywordList)()

### QStringList Definition::keywordLists() const {#keywordLists}

Returns the section names of keywords.

*See also* [keywordList](ksyntaxhighlighting-definition.md#keywordList)()

### QString Definition::license() const {#license}

License of this syntax definition.

> **Note:** Getter function for property [license](ksyntaxhighlighting-definition.md#license-prop).

### QList\<QString\> Definition::mimeTypes() const {#mimeTypes}

Mime types associated with this syntax definition.

### QPair\<QString, QString\> Definition::multiLineCommentMarker() const {#multiLineCommentMarker}

Returns the markers that start and end multiline comments. For instance, in XML this is defined as "\<!–" and "–\>".

### QString Definition::name() const {#name}

Name of the syntax. Used for internal references, prefer [translatedName](ksyntaxhighlighting-definition.md#translatedName)() for display.

> **Note:** Getter function for property [name](ksyntaxhighlighting-definition.md#name-prop).

### int Definition::priority() const {#priority}

Returns the definition priority. A Definition with higher priority wins over Definitions with lower priorities.

### QString Definition::section() const {#section}

The group this syntax definition belongs to. For display, consider [translatedSection](ksyntaxhighlighting-definition.md#translatedSection)().

> **Note:** Getter function for property [section](ksyntaxhighlighting-definition.md#section-prop).

### bool Definition::setKeywordList(const QString &*name*, const QStringList &*content*) {#setKeywordList}

Set the contents of the keyword list `name` to `content`. Only existing [keywordLists](ksyntaxhighlighting-definition.md#keywordLists)() can be changed. For non-existent keyword lists, false is returned.

Whenever you change a keyword list, make sure to trigger a rehighlight of your documents. In case you are using [QSyntaxHighlighter](https://doc.qt.io/qt-6/qsyntaxhighlighter.html) via [SyntaxHighlighter](ksyntaxhighlighting-syntaxhighlighter.md), this can be done by calling [SyntaxHighlighter::rehighlight](https://doc.qt.io/qt-6/qsyntaxhighlighter.html#rehighlight)().

> **Note:** In general, changing keyword lists via setKeywordList() is discouraged, since if a keyword list name in the syntax highlighting definition file changes, the call setKeywordList() may suddenly fail.

*See also* [keywordList](ksyntaxhighlighting-definition.md#keywordList)(), [keywordLists](ksyntaxhighlighting-definition.md#keywordLists)()

### QString Definition::singleLineCommentMarker() const {#singleLineCommentMarker}

Returns the marker that starts a single line comment. For instance, in C++ the single line comment marker is "//".

*See also* [singleLineCommentPosition](ksyntaxhighlighting-definition.md#singleLineCommentPosition)()

### KSyntaxHighlighting::CommentPosition Definition::singleLineCommentPosition() const {#singleLineCommentPosition}

Returns the insert position of the comment marker for sinle line comments.

*See also* [singleLineCommentMarker](ksyntaxhighlighting-definition.md#singleLineCommentMarker)()

### QString Definition::style() const {#style}

Generalized language style, used for indentation.

### QString Definition::translatedName() const {#translatedName}

Translated name for display.

> **Note:** Getter function for property [translatedName](ksyntaxhighlighting-definition.md#translatedName-prop).

### QString Definition::translatedSection() const {#translatedSection}

Translated group name for display.

> **Note:** Getter function for property [translatedSection](ksyntaxhighlighting-definition.md#translatedSection-prop).

### int Definition::version() const {#version}

Returns the definition version.

### bool Definition::operator!=(const KSyntaxHighlighting::Definition &*other*) const {#operator-not-eq}

Checks two definitions for inequality.

### \[noexcept\] KSyntaxHighlighting::Definition &Definition::operator=(KSyntaxHighlighting::Definition &&*other*) {#operator-eq}

Move assignment operator.

This definition takes the Definition data from `other`.

> **Note:** `other` may only be assigned to or destroyed afterwards.

### KSyntaxHighlighting::Definition &Definition::operator=(const KSyntaxHighlighting::Definition &*rhs*) {#operator-eq-1}

Copy assignment operator.

Both this definition as well as `rhs` share the Definition data.

### bool Definition::operator==(const KSyntaxHighlighting::Definition &*other*) const {#operator-eq-eq}

Checks two definitions for equality.
