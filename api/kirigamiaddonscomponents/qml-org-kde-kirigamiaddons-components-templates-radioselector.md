---
title: "RadioSelector QML Type"
description: "Shared actions, exclusive selection and layout for radio selectors."
---

# RadioSelector QML Type

Shared actions, exclusive selection and layout for radio selectors. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.components.templates
- Inherited By: [RadioSelector](qml-org-kde-kirigamiaddons-components-radioselector.md) (org.kde.kirigamiaddons.components)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### actions : list\<Action\> {#actions-prop}

This property holds a list of actions, each holding one of the options.

### \[default: false\] consistentWidth : bool {#consistentWidth-prop}

This property holds whether all the items should have the same width.

### selectedIndex : int {#selectedIndex-prop}

This property holds the currently selected option.

By default, it's the first actions or -1 if no actions is set.
