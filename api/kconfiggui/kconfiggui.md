---
title: "KConfigGui Namespace"
description: "Interface-related functions."
---

# KConfigGui Namespace

Interface-related functions.

- Header: KConfigGui
- CMake: find\_package(KF6 REQUIRED COMPONENTS Config) target\_link\_libraries(mytarget PRIVATE KF6::ConfigGui)

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### bool KConfigGui::hasSessionConfig() {#hasSessionConfig}

Indicates if a session config has been created for that application (i.e. if [sessionConfig](kconfiggui.md#sessionConfig)() got called at least once)

Returns `true` if a [sessionConfig](kconfiggui.md#sessionConfig) object was created, `false` otherwise

### KConfig \*KConfigGui::sessionConfig() {#sessionConfig}

Returns the current application session config object.

> **Note:** If Qt is built without session manager support, i.e. QT\_NO\_SESSIONMANAGER is defined, this by default will return nullptr, unless a custom config has been set via [setSessionConfig](kconfiggui.md#setSessionConfig).

Returns a pointer to the application's instance specific [KConfig](../kconfigcore/kconfig.md) object.

*See also* [setSessionConfig](kconfiggui.md#setSessionConfig)()

### void KConfigGui::setSessionConfig(const QString &*id*, const QString &*key*) {#setSessionConfig}

Replaces the current application session config object.

`id` new session id

`key` new session key

*See also* [sessionConfig](kconfiggui.md#sessionConfig)()
