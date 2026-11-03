---
title: "Heading QML Type"
description: "A heading label used for subsections of texts."
---

# Heading QML Type

A heading label used for subsections of texts. [More...](#details)

- Import Statement: import org.kde.plasma.extras
- Inherits: [Label](../plasmacomponents/qml-org-kde-plasma-components-label.md)

## Detailed Description {#details}

The characteristics of the text will be automatically set according to the plasma theme. Use this components for section titles or headings in your UI, for example page or section titles.

Example usage:

```cpp
import org.kde.plasma.components as PlasmaComponents3
import org.kde.plasma.extras as PlasmaExtras
[...]
Column {
    PlasmaExtras.Heading { text: "Fruit sweetness on the rise"; level: 1 }
    PlasmaExtras.Heading { text: "Apples in the sunlight"; level: 2 }
    PlasmaComponents3.Label { text: "Long text about fruit and apples [...]" }
  [...]
}
```

The most important property is "text", which applies to the text property of Label. See PlasmaComponents Label and primitive QML Text element API for additional properties, methods and signals.

TODO qdoc how to document the inheritance from PC3?

## Property Documentation {#property-documentation}

### level : int {#level-prop}

The level determines how big the section header is display, values between 1 (big) and 5 (small) are accepted. (default: 1)

### type : int {#type-prop}

The type of the heading. This can be:

- PlasmaExtras.Heading.Type.Normal: Create a normal heading (default)
- PlasmaExtras.Heading.Type.Primary: Makes the heading more prominent. Useful when making the heading bigger is not enough.
- PlasmaExtras.Heading.Type.Secondary: Makes the heading less prominent. Useful when an heading is for a less important section in an application.
