---
title: "KShellCompletion Class"
description: "This class does shell-like completion of file names."
---

# KShellCompletion Class

This class does shell-like completion of file names. [More...](#details)

- **Header:** `#include <KShellCompletion>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [KUrlCompletion](kurlcompletion.md)

[List of all members, including inherited members](kshellcompletion-members.md)

## Public Functions

- [KShellCompletion()](#KShellCompletion)
- [QString makeCompletion(const QString &text)](#makeCompletion)

## Detailed Description {#details}

A string passed to [makeCompletion](kshellcompletion.md#makeCompletion)() will be interpreted as a shell command line. Completion will be done on the last argument on the line. Returned matches consist of the first arguments (uncompleted) plus the completed last argument.

## Member Function Documentation {#member-function-documentation}

### KShellCompletion::KShellCompletion() {#KShellCompletion}

Constructs a [KShellCompletion](kshellcompletion.md) object.

### \[override virtual\] QString KShellCompletion::makeCompletion(const QString &*text*) {#makeCompletion}

Reimplements: [KUrlCompletion::makeCompletion(const QString &text)](kurlcompletion.md#makeCompletion).

Finds completions to the given text. The first match is returned and emitted in the signal match().

`text` the text to complete

Returns the first match, or QString() if not found
