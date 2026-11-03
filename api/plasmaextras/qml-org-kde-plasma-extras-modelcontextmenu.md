---
title: "ModelContextMenu QML Type"
description: "A ModelContextMenu creates a context menu with items populated from a model or a QList<QAction>."
---

# ModelContextMenu QML Type

A [ModelContextMenu](qml-org-kde-plasma-extras-modelcontextmenu.md) creates a context menu with items populated from a model or a [QList](https://doc.qt.io/qt-6/qlist.html)\<[QAction](https://doc.qt.io/qt-6/qaction.html)\*\>. [More...](#details)

- Import Statement: import org.kde.plasma.extras

## Detailed Description {#details}

For standard item models, actions are created using the following model role names or properties:

- display - a string contains the action name
- decoration - an icon to display
- separator - boolean that will add a separator in the list

Example code:

```qml
ModelContextMenu {
    id: menu
    visualParent: someButton
    model: myModel
}

Button {
     id: someButton
     onClicked: menu.popup()
}
```

## Property Documentation {#property-documentation}

### model : model {#model-prop}

The model containing menu items

## Signal Documentation {#signal-documentation}

### clicked(var *model*) {#clicked-signal}

This signal is emitted when a menu item is clicked. The attached model properties for that menu item are passed as an argument

> **Note:** The corresponding handler is `onClicked`.
