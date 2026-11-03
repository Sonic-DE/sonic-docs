---
title: "ShadowedTexture QML Type"
description: "A rectangle with a shadow, using a Item as texture."
---

# ShadowedTexture QML Type

A rectangle with a shadow, using a Item as texture. [More...](#details)

- Import Statement: import org.kde.kirigami.primitives
- Inherits: [ShadowedRectangle](qml-org-kde-kirigami-primitives-shadowedrectangle.md)

## Detailed Description {#details}

This item will render a source item, with a shadow below it. The rendering is done using distance fields, which provide greatly improved performance. The shadow is rendered outside of the item's bounds, so the item's width and height are the rectangle's width and height.

## Property Documentation {#property-documentation}

### source : Item {#source-prop}

This property holds the source item that will get rendered with the shadow.
