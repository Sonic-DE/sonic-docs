---
title: "Kuit Namespace"
description: "Global constants and functions related to KUIT markup."
---

# Kuit Namespace

Global constants and functions related to KUIT markup. [More...](#details)

- Header: Kuit
- CMake: find\_package(KF6 REQUIRED COMPONENTS I18n) target\_link\_libraries(mytarget PRIVATE KF6::I18n)

## Detailed Description {#details}

## Type Documentation {#type-documentation}

### enum Kuit::TagClass {#TagClass-enum}

Classification of KUIT tags.

| Constant | Value | Description |
| --- | --- | --- |
| `Kuit::PhraseTag` | `0` | Tags wrapping text inserted into running text. |
| `Kuit::StructTag` | `1` | Tags splitting text into paragraph-level blocks |

### Kuit::TagFormatter {#TagFormatter-typedef}

Functions accepted by tag formatting functions.

`languages` the target languages (by decreasing priority)

`tagName` the wrapping tag name

`attributes` the attribute name-value pairs in the tag

`text` the wrapped text

`tagPath` the ordered list of ancestor tag names, parent first

`format` the target visual format

Returns formatted text

### enum Kuit::VisualFormat {#VisualFormat-enum}

Visual formats into which KUIT markup can be resolved.

| Constant | Value | Description |
| --- | --- | --- |
| `Kuit::UndefinedFormat` | `0` | format not defined. This value can be explicitly set (e.g. through [KLocalizedString::withFormat](klocalizedstring.md#withFormat)) to indicate that the format should be decided by another mechanism (e.g. context UI marker). |
| `Kuit::PlainText` | `10` | Plain Text |
| `Kuit::RichText` | `20` | Qt rich text (HTML subset). |
| `Kuit::TermText` | `30` | Terminal escape sequences. |

## Function Documentation {#function-documentation}

### QString Kuit::escape(const QString &*text*) {#escape}

Convert &, ", ', \<, \> characters into XML entities &amp;, &lt;, &gt;, &apos;, &quot;, respectively.

### KuitSetup &Kuit::setupForDomain(const QByteArray &*domain*) {#setupForDomain}

Get hold of the KUIT setup object for a given domain.

`domain` the translation domain

Returns pointer to KUIT setup object
