---
title: "SearchField QML Type"
description: "This is a standard textfield following KDE HIG. Using Ctrl+F as focus sequence and \"Search…\" as placeholder text."
---

# SearchField QML Type

This is a standard textfield following KDE HIG. Using Ctrl+F as focus sequence and "Search…" as placeholder text. [More...](#details)

- Import Statement: import org.kde.plasma.extras
- Inherits: [ActionTextField](qml-org-kde-plasma-extras-actiontextfield.md)

## Detailed Description {#details}

Example usage for the search field component:

```qml
import org.kde.plasma.extras as PlasmaExtras

PlasmaExtras.SearchField {
    id: searchField
    onAccepted: console.log("Search text is " + searchField.text)
}
```
