---
title: "KPluginFactory::Result Class"
description: "Additions to Qt Core."
---

# KPluginFactory::Result Class

Additions to Qt Core. [More...](#details)

- **Header:** `#include <Result>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`

[List of all members, including inherited members](kpluginfactory-result-members.md)

## Public Functions

- [Result::operator bool() const](#operator-bool)

## Detailed Description {#details}

Holds the result of a plugin load operation, i.e. the loaded plugin on success or information about the error on failure

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Result::operator bool() const {#operator-bool}

## Member Variable Documentation {#member-variable-documentation}

### KPluginFactory::ResultErrorReason Result::errorReason {#errorReason-var}

This variable holds the error reason

### QString Result::errorString {#errorString-var}

This variable holds the translated, user-visible error string

### QString Result::errorText {#errorText-var}

This variable holds the untranslated error text

### T \* Result::plugin {#plugin-var}

This variable holds the loaded object, or `nullptr` if loading fails
