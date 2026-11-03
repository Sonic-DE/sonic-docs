---
title: "KOSRelease QML Type"
description: "Parses /etc/os-release files. This type was introduced in Qt 6.11."
---

# KOSRelease QML Type

Parses /etc/os-release files. This type was introduced in Qt 6.11. [More...](#details)

- Import Statement: import org.kde.coreaddons
- Since: Qt 6.11
- In C++: [KOSRelease](../kcoreaddons/kosrelease.md)

## Detailed Description {#details}

This is a QML singleton

```qml
import QtQuick
import org.kde.coreaddons

Item {
    Component.onCompleted: console.log(KOSRelease.name)
}
```

## Property Documentation {#property-documentation}

### ansiColor : string {#ansiColor-prop}

### bugReportUrl : string {#bugReportUrl-prop}

### buildId : string {#buildId-prop}

### cpeName : string {#cpeName-prop}

### documentationUrl : string {#documentationUrl-prop}

### homeUrl : string {#homeUrl-prop}

### id : string {#id-prop}

### idLike : list\<string\> {#idLike-prop}

### logo : string {#logo-prop}

### name : string {#name-prop}

### prettyName : string {#prettyName-prop}

### privacyPolicyUrl : string {#privacyPolicyUrl-prop}

### supportUrl : string {#supportUrl-prop}

### variant : string {#variant-prop}

### variantId : string {#variantId-prop}

### version : string {#version-prop}

### versionCodename : string {#versionCodename-prop}

### versionId : string {#versionId-prop}

## Method Documentation {#method-documentation}

### list\<string\> extraKeys() {#extraKeys-method}

### string extraValue(string *key*) {#extraValue-method}
