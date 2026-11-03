---
title: "KCMLauncher QML Type (Singleton)"
description: "Utilities for KDE System Settings modules."
---

# KCMLauncher QML Type (Singleton)

Utilities for KDE System Settings modules. [More...](#details)

- Import Statement: import org.kde.kcmutils

> **Note:** **Note:** This type is a QML singleton. There is only one instance of this type in the QML engine.

## Detailed Description {#details}

This is a QML singleton.

## Method Documentation {#method-documentation}

### void open(list\<string\> *names*) {#open-method}

### void openInfoCenter(string *name*) {#openInfoCenter-method}

Opens the specified module in InfCenter. Only a single KCM name may be provided.

```cpp
import QtQuick.Controls as QQC2
import org.kde.kcmutils as KCMUtils
QQC2.Button {
    onClicked: KCMUtils.KCMLauncher.openInfoCenter("kcm_energy")
}
```

`name` A single kcm name to open in Info Center. Opening multiple KCMs using this function is not supported; to do that, use [KCMLauncher](qml-org-kde-kcmutils-kcmlauncher.md).[open](qml-org-kde-kcmutils-kcmlauncher.md#open-method)().

### void openSystemSettings(string *name*, list\<string\> *args* = \[\]) {#openSystemSettings-method}

Opens the specified module in System Settings. Only a single KCM name may be provided.

```cpp
import QtQuick.Controls as QQC2
import org.kde.kcmutils as KCMUtils

QQC2.Button {
    onClicked: KCMUtils.KCMLauncher.openSystemSettings("kcm_kscreen")
}
```

`name` A single kcm name to open in System Settings. Opening multiple KCMs using this function is not supported; to do that, use [KCMLauncher](qml-org-kde-kcmutils-kcmlauncher.md).[open](qml-org-kde-kcmutils-kcmlauncher.md#open-method)(). `args` Additional arguments to pass to the module.
