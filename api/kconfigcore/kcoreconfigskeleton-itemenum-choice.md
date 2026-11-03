---
title: ""
description: "Provides strongly typed enum options for use with KConfigXT."
---

# 

Provides strongly typed enum options for use with KConfigXT.

- Header: Choice
- CMake: find\_package(KF6 REQUIRED COMPONENTS Config) target\_link\_libraries(mytarget PRIVATE KF6::ConfigCore)

## Detailed Description {#details}

Enums specified with KConfigXT should be mapped to enums in the C++ codebase, as the generated getter for the [ItemEnum](kcoreconfigskeleton-itemenum.md) will return an int.

*See also* [Using KConfig XT](https://develop.kde.org/docs/features/configuration/kconfig_xt/), [ItemEnum](kcoreconfigskeleton-itemenum.md)

## Member Variable Documentation {#member-variable-documentation}

### QString Choice::label {#label-var}

The short description for the entry.

This tag will be ignored unless you set `SetUserTexts=true`.

### QString Choice::name {#name-var}

The choice name. This should match the key name in the C++ codebase.

This will be used as the value of the enum key if [Choice::value](kcoreconfigskeleton-itemenum-choice.md#value-var) is not specified.

### QString Choice::toolTip {#toolTip-var}

A more verbose description for the entry.

This tag will be ignored unless you set `SetUserTexts=true`.

### QString Choice::value {#value-var}

The value for the entry key as displayed in the configuration file.

### QString Choice::whatsThis {#whatsThis-var}

The WhatsThis description for this entry.
