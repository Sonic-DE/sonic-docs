---
title: "KMacroExpander Namespace"
description: "A group of functions providing macro expansion (substitution) in strings, optionally with quoting appropriate for shell execution."
---

# KMacroExpander Namespace

A group of functions providing macro expansion (substitution) in strings, optionally with quoting appropriate for shell execution. [More...](#details)

- Header: KMacroExpander
- CMake: find\_package(KF6 REQUIRED COMPONENTS CoreAddons) target\_link\_libraries(mytarget PRIVATE KF6::CoreAddons)

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### QString KMacroExpander::expandMacros(const QString &*str*, const QHash\<QChar, QString\> &*map*, QChar *c* = QLatin1Char('%')) {#expandMacros}

Perform safe macro expansion (substitution) on a string. The escape char must be quoted with itself to obtain its literal representation in the resulting string.

`str` The string to expand

`map` map with substitutions

`c` escape char indicating start of macro, or QChar::null if none

Returns the string with all valid macros expanded

```cpp
// Code example
QHash<QChar,QString> map;
map.insert('u', "/tmp/myfile.txt");
map.insert('n', "My File");
QString s = "%% Title: %u:%n";
s = KMacroExpander::expandMacros(s, map);
// s is now "% Title: /tmp/myfile.txt:My File";
```

### QString KMacroExpander::expandMacros(const QString &*str*, const QHash\<QChar, QStringList\> &*map*, QChar *c* = QLatin1Char('%')) {#expandMacros-1}

Same as above, except that the macros expand to string lists that are simply join(" ")ed together.

### QString KMacroExpander::expandMacros(const QString &*str*, const QHash\<QString, QString\> &*map*, QChar *c* = QLatin1Char('%')) {#expandMacros-2}

Perform safe macro expansion (substitution) on a string. The escape char must be quoted with itself to obtain its literal representation in the resulting string. Macro names can consist of chars in the range \[A-Za-z0-9\_\]; use braces to delimit macros from following words starting with these chars, or to use other chars for macro names.

`str` The string to expand

`map` map with substitutions

`c` escape char indicating start of macro, or QChar::null if none

Returns the string with all valid macros expanded

```cpp
// Code example
QHash<QString,QString> map;
map.insert("url", "/tmp/myfile.txt");
map.insert("name", "My File");
QString s = "Title: %{url}-%name";
s = KMacroExpander::expandMacros(s, map);
// s is now "Title: /tmp/myfile.txt-My File";
```

### QString KMacroExpander::expandMacrosShellQuote(const QString &*str*, const QHash\<QChar, QString\> &*map*, QChar *c* = QLatin1Char('%')) {#expandMacrosShellQuote}

Perform safe macro expansion (substitution) on a string for use in shell commands. The escape char must be quoted with itself to obtain its literal representation in the resulting string.

`str` The string to expand

`map` map with substitutions

`c` escape char indicating start of macro, or QChar::null if none

Returns the string with all valid macros expanded, or a null string if a shell syntax error was detected in the command

```cpp
// Code example
QHash<QChar,QString> map;
map.insert('u', "/tmp/myfile.txt");
map.insert('n', "My File");
QString s = "kwrite --qwindowtitle %n %u";
s = KMacroExpander::expandMacrosShellQuote(s, map);
// s is now "kwrite --qwindowtitle 'My File' '/tmp/myfile.txt'";
system(QFile::encodeName(s));
```

### QString KMacroExpander::expandMacrosShellQuote(const QString &*str*, const QHash\<QChar, QStringList\> &*map*, QChar *c* = QLatin1Char('%')) {#expandMacrosShellQuote-1}

Same as above, except that the macros expand to string lists. If the macro appears inside a quoted string, the list is simply join(" ")ed together; otherwise every element expands to a separate quoted string.

### QString KMacroExpander::expandMacrosShellQuote(const QString &*str*, const QHash\<QString, QString\> &*map*, QChar *c* = QLatin1Char('%')) {#expandMacrosShellQuote-2}

Perform safe macro expansion (substitution) on a string for use in shell commands. See [KMacroExpanderBase::expandMacrosShellQuote](kmacroexpanderbase.md#expandMacrosShellQuote)() for the exact semantics. The escape char must be quoted with itself to obtain its literal representation in the resulting string. Macro names can consist of chars in the range \[A-Za-z0-9\_\]; use braces to delimit macros from following words starting with these chars, or to use other chars for macro names.

`str` The string to expand

`map` map with substitutions

`c` escape char indicating start of macro, or QChar::null if none

Returns the string with all valid macros expanded, or a null string if a shell syntax error was detected in the command

```cpp
// Code example
QHash<QString,QString> map;
map.insert("url", "/tmp/myfile.txt");
map.insert("name", "My File");
QString s = "kwrite --qwindowtitle %name %{url}";
s = KMacroExpander::expandMacrosShellQuote(s, map);
// s is now "kwrite --qwindowtitle 'My File' '/tmp/myfile.txt'";
system(QFile::encodeName(s));
```
