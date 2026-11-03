---
title: "SearchField QML Type"
description: "Standard TextField following the KDE HIG."
---

# SearchField QML Type

Standard [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html) following the KDE HIG. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [ActionTextField](qml-org-kde-kirigami-actiontextfield.md)

## Detailed Description {#details}

By default uses Ctrl+F as the focus keyboard shortcut and "Search…" as a placeholder text.

Example usage for the search field component:

```cpp
import org.kde.kirigami as Kirigami

Kirigami.SearchField {
    id: searchField
    onAccepted: console.log("Search text is " + searchField.text)
}
```

## Property Documentation {#property-documentation}

### autoAccept : bool {#autoAccept-prop}

This property sets whether the accepted signal is fired automatically when the text is changed.

Setting this to false will require that the user presses return or enter (the same way a [TextInput](https://doc.qt.io/qt-6/qml-qtquick-textinput.html) works).

default: `true`

### delaySearch : bool {#delaySearch-prop}

This property sets whether to delay automatic acceptance of the search input.

Set this to true if your search is expensive (such as for online operations or in exceptionally slow data sets) and want to delay it for 2.5 seconds.

> **Note:** If you must have immediate feedback (filter-style), use the text property directly instead of accepted()

default: `false`
