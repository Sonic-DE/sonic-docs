---
title: "DescriptiveLabel QML Type"
description: "This is a descriptive label which uses the plasma theme."
---

# DescriptiveLabel QML Type

This is a descriptive label which uses the plasma theme. [More...](#details)

- Import Statement: import org.kde.plasma.extras
- Inherits: [Label](../plasmacomponents/qml-org-kde-plasma-components-label.md)

## Detailed Description {#details}

The characteristics of the text will be automatically set according to the plasma theme. Use this components for less important additional data to show in a user interface.

Example usage:

```qml
import org.kde.plasma.extras as PlasmaExtras
[...]
Column {
    PlasmaComponents.Label { text: "Firefox" }
    PlasmaExtras.DescriptiveLabel { text: "Web Browser"}
  [...]
}
```

See PlasmaComponents Label and primitive QML Text element API for additional properties, methods and signals.

## Property Documentation {#property-documentation}

### active : bool {#active-prop}

If a user can interact with this item, for example in a [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html) delegate, this property should be set to true when the label is being interacted with.

The default is false.
