---
title: "ConfigurationModule QML Type"
description: "This object holds the information of configuration module."
---

# ConfigurationModule QML Type

This object holds the information of configuration module. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.settings
- Inherited By: [ShortcutsConfigurationModule](qml-org-kde-kirigamiaddons-settings-shortcutsconfigurationmodule.md) and [SpellcheckingConfigurationModule](qml-org-kde-kirigamiaddons-settings-spellcheckingconfigurationmodule.md)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### \[default: "\_main\_category"\] category : string {#category-prop}

This property holds the category of the module.

This is used to group modules together on mobile.

Do not overwrite the default value if you want your module to be grouped in the default category.

### \[read-only\] icon : Private.ActionIconGroup {#icon-prop}

This property holds the icon of the module.

### initialProperties : var {#initialProperties-prop}

This property holds the initial property that the page needs to be initialized with if any.

This is a function that returns an Javascript object.

```qml
initialProperties: () => {
    return {
        room: root._room,
        connection: root._connection
    };
}
```

### \[required\] moduleId : string {#moduleId-prop}

This property holds the id of the module for when it needs to be referenced.

Primary use case is for setting a default module in [ConfigurationView](qml-org-kde-kirigamiaddons-settings-configurationview.md).

### \[required\] page : var {#page-prop}

This property holds a function that returns a Component.

### \[required\] text : string {#text-prop}

This property holds the name of the module.

This will be displayed in the list of modules.

### \[default: true\] visible : bool {#visible-prop}

This property holds whether the module is visible.
