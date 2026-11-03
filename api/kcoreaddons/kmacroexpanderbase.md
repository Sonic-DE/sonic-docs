---
title: "KMacroExpanderBase Class"
description: "Abstract base class for the worker classes behind the KMacroExpander namespace and the KCharMacroExpander and KWordMacroExpander classes."
---

# KMacroExpanderBase Class

Abstract base class for the worker classes behind the [KMacroExpander](kmacroexpander.md) namespace and the [KCharMacroExpander](kcharmacroexpander.md) and [KWordMacroExpander](kwordmacroexpander.md) classes. [More...](#details)

- **Header:** `#include <KMacroExpander>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`
- **Inherited By:** [KCharMacroExpander](kcharmacroexpander.md) and [KWordMacroExpander](kwordmacroexpander.md)

[List of all members, including inherited members](kmacroexpanderbase-members.md)

## Public Functions

- [KMacroExpanderBase(QChar c = QLatin1Char('%'))](#KMacroExpanderBase)
- [QChar escapeChar() const](#escapeChar)
- [void expandMacros(QString &str)](#expandMacros)
- [bool expandMacrosShellQuote(QString &str)](#expandMacrosShellQuote)
- [bool expandMacrosShellQuote(QString &str, int &pos)](#expandMacrosShellQuote-1)
- [void setEscapeChar(QChar c)](#setEscapeChar)

## Protected Functions

- [int expandEscapedMacro(const QString &str, int pos, QStringList &ret)](#expandEscapedMacro)
- [int expandPlainMacro(const QString &str, int pos, QStringList &ret)](#expandPlainMacro)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KMacroExpanderBase::KMacroExpanderBase(QChar *c* = QLatin1Char('%')) {#KMacroExpanderBase}

Constructor. `c` escape char indicating start of macros, or QChar::null for none

### QChar KMacroExpanderBase::escapeChar() const {#escapeChar}

Obtain the macro escape character. Returns escape char indicating start of macros, or QChar::null if none

*See also* [setEscapeChar](kmacroexpanderbase.md#setEscapeChar)()

### \[virtual protected\] int KMacroExpanderBase::expandEscapedMacro(const QString &*str*, int *pos*, QStringList &*ret*) {#expandEscapedMacro}

This function is called every time the escape char is found if it is not QChar::null. It should determine whether the string starting at `pos` witin `str` is a valid macro and return the substitution value for it if so.

`str` the input string

`pos` the offset within `str`. Note that this is the position of the occurrence of the escape char

`ret` return value: the string to substitute for the macro

Returns If greater than zero, the number of chars at `pos` in `str` to substitute with `ret` (i.e., a valid macro was found). If less than zero, subtract this value from `pos` (to skip a macro, i.e., substitute it with itself). If zero, scanning continues as if no escape char was encountered at all.

### void KMacroExpanderBase::expandMacros(QString &*str*) {#expandMacros}

Perform safe macro expansion (substitution) on a string.

`str` the string in which macros are expanded in-place

### bool KMacroExpanderBase::expandMacrosShellQuote(QString &*str*) {#expandMacrosShellQuote}

Same as above, but always starts at position 0, and unmatched closing parens and braces are treated as errors.

### bool KMacroExpanderBase::expandMacrosShellQuote(QString &*str*, int &*pos*) {#expandMacrosShellQuote-1}

Perform safe macro expansion (substitution) on a string for use in shell commands.

\*NIX notes:

Explicitly supported shell constructs: '' "" $'' $"" {} () $(()) ${} $() \`\`

Implicitly supported shell constructs: (())

Unsupported shell constructs that will cause problems: Shortened `case $v in pat)` syntax. Use `case $v in (pat)` instead.

The rest of the shell (incl. bash) syntax is simply ignored, as it is not expected to cause problems.

Note that bash contains a bug which makes macro expansion within double quoted substitutions (`"${VAR:-%macro}"`) inherently insecure.

For security reasons, *never* put expandos in command line arguments that are shell commands by themselves - `sh -c 'foo %f'` is taboo. `file=%f sh -c 'foo "$file"'` is OK.

Windows notes:

All quoting syntax supported by [KShell](kshell.md) is supported here as well. Additionally, command grouping via parentheses is recognized - note however, that the parser is much stricter about unquoted parentheses than cmd itself. The rest of the cmd syntax is simply ignored, as it is not expected to cause problems - do not use commands that embed other commands, though - `for /f ...` is taboo.

`str` the string in which macros are expanded in-place

`pos` the position inside the string at which parsing/substitution should start, and upon exit where processing stopped

Returns false if the string could not be parsed and therefore no safe substitution was possible. Note that macros will have been processed up to the point where the error occurred. An unmatched closing paren or brace outside any shell construct is *not* an error (unlike in the function below), but still prematurely terminates processing.

### \[virtual protected\] int KMacroExpanderBase::expandPlainMacro(const QString &*str*, int *pos*, QStringList &*ret*) {#expandPlainMacro}

This function is called for every single char within the string if the escape char is QChar::null. It should determine whether the string starting at `pos` within `str` is a valid macro and return the substitution value for it if so.

`str` the input string

`pos` the offset within `str`

`ret` return value: the string to substitute for the macro

Returns If greater than zero, the number of chars at `pos` in `str` to substitute with `ret` (i.e., a valid macro was found). If less than zero, subtract this value from `pos` (to skip a macro, i.e., substitute it with itself). If zero, no macro starts at `pos`.

### void KMacroExpanderBase::setEscapeChar(QChar *c*) {#setEscapeChar}

Set the macro escape character.

`c` escape char indicating start of macros, or QChar::null if none

*See also* [escapeChar](kmacroexpanderbase.md#escapeChar)()
