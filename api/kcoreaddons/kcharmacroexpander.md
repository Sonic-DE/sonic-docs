---
title: "KCharMacroExpander Class"
description: "Abstract base class for single char macro substitutors."
---

# KCharMacroExpander Class

Abstract base class for single char macro substitutors. [More...](#details)

- **Header:** `#include <KMacroExpander>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`
- **Inherits:** [KMacroExpanderBase](kmacroexpanderbase.md)

[List of all members, including inherited members](kcharmacroexpander-members.md)

## Public Functions

- [KCharMacroExpander(QChar c = QLatin1Char('%'))](#KCharMacroExpander)

## Protected Functions

- [bool expandMacro(QChar chr, QStringList &ret)](#expandMacro)

## Detailed Description {#details}

Use this instead of the functions in the [KMacroExpander](kmacroexpander.md) namespace if speculatively pre-filling the substitution map would be too expensive.

See [KWordMacroExpander](kwordmacroexpander.md) for a sample application.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KCharMacroExpander::KCharMacroExpander(QChar *c* = QLatin1Char('%')) {#KCharMacroExpander}

Constructor.

`c` escape char indicating start of macros, or QChar::null for none

### \[pure virtual protected\] bool KCharMacroExpander::expandMacro(QChar *chr*, QStringList &*ret*) {#expandMacro}

Return substitution list `ret` for single-character macro `chr`.

`chr` the macro to expand

`ret` return variable reference. It is guaranteed to be empty when expandMacro is entered.

Returns true iff `chr` was a recognized macro name
