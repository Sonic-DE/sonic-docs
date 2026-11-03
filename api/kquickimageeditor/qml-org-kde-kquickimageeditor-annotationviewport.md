---
title: "AnnotationViewport QML Type"
description: "A QML item which paints its correspondent AnnotationDocument or a sub-part of it, depending from viewportRect and zoom."
---

# AnnotationViewport QML Type

A QML item which paints its correspondent [AnnotationDocument](qml-org-kde-kquickimageeditor-annotationdocument.md) or a sub-part of it, depending from [viewportRect](qml-org-kde-kquickimageeditor-annotationviewport.md#viewportRect-prop) and zoom. [More...](#details)

- Import Statement: import org.kde.kquickimageeditor

## Detailed Description {#details}

This also manages all the input for adding the annotations.

## Property Documentation {#property-documentation}

### anyPressed : bool {#anyPressed-prop}

### colorMatrix : matrix4x4 {#colorMatrix-prop}

Matrix for color transformations after converting to a linear colorspace and before converting back to the original colorspace.

The 3x3 area from `m11` to `m33` is for RGB scale and rotation/shear. `m41`, `m42` and `m43` are for RGB translation. `m14`, `m24` and `m34` are for RGB attenuation. `m44` is a global divisor.

### document : AnnotationDocument {#document-prop}

### gammaAdjustment : real {#gammaAdjustment-prop}

A gamma adjustment to be applied to colors after converting to a linear colorspace and before converting back to the original colorspace.

Gamma is a power applied to color values to transform them in a non-linear way. Usually, gamma is used to make color values match the way we perceive colors more closely. This adjustment stacks with the colorspace's gamma.

A value close to 1 (±0.00001) or less than 0.00001 does nothing. Values equal to or less than 0 are not allowed because the preview shader effect may have undefined behavior with those values.

### hoverPosition : point {#hoverPosition-prop}

### hovered : bool {#hovered-prop}

### hoveredMousePath : QPainterPath {#hoveredMousePath-prop}

### pressPosition : point {#pressPosition-prop}

### pressed : bool {#pressed-prop}

### viewportRect : rect {#viewportRect-prop}
