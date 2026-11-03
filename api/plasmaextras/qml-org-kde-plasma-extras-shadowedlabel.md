---
title: "ShadowedLabel QML Type"
description: "White text label with a black shadow behind it."
---

# ShadowedLabel QML Type

White text label with a black shadow behind it. [More...](#details)

- Import Statement: import org.kde.plasma.extras
- Inherits: [Label](../plasmacomponents/qml-org-kde-plasma-components-label.md)

## Detailed Description {#details}

A standardized label with white text and a black shadow behind it. When using software rendering such that the shadow is not available, a black rounded rectangle is used in its stead.

By default it elides text on the right, wraps in a way that prefers word boundaries, and uses plain text formatting.

The most important property is "text", which applies to the text property of the underlying Label component. See the Label component from [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html).Controls 2 and primitive QML Text element API for additional properties, methods, and signals.

## Property Documentation {#property-documentation}

### renderShadow : bool {#renderShadow-prop}

This property can be used to conditionally \*not\* render the shadow, even when it's technically possible to render it.

default: `true`
