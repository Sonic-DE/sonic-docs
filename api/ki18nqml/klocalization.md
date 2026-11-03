---
title: "KLocalization Namespace"
description: "Namespace containing helpers for localization."
---

# KLocalization Namespace

Namespace containing helpers for localization. [More...](#details)

- Header: KLocalization
- CMake: find\_package(KF6 REQUIRED COMPONENTS I18n) target\_link\_libraries(mytarget PRIVATE KF6::I18nQml)

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### \[since 6.8\] KLocalizedQmlContext \*setupLocalizedContext(QQmlEngine \**engine*) {#setupLocalizedContext}

Creates a [KLocalizedQmlContext](klocalizedqmlcontext.md) engine and sets it up in the root context of `engine`.

If `TRANSLATION_DOMAIN` is defined, that is also set on the created context.

This function was introduced in Qt 6.8.
