---
title: "SettingStateProxy QML Type"
description: "Allows to represent the state of a particular setting in a config object in a declarative way."
---

# SettingStateProxy QML Type

Allows to represent the state of a particular setting in a config object in a declarative way. [More...](#details)

- Import Statement: import org.kde.kcmutils

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### configObject : KCoreConfigSkeleton {#configObject-prop}

The config object which will be monitored for setting state changes.

### defaulted : bool {#defaulted-prop}

Indicates if the setting differs from its default value.

### immutable : bool {#immutable-prop}

Indicates if the setting is marked as immutable.

### settingName : string {#settingName-prop}

The name of the setting in the config object.

## Method Documentation {#method-documentation}

### void updateState() {#updateState-method}
