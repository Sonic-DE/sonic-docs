---
title: "Lanczos QML Type"
description: "A ShaderEffect that makes use of the Lanczos resampling method for scaling textures."
---

# Lanczos QML Type

A [ShaderEffect](https://doc.qt.io/qt-6/qml-qtquick-shadereffect.html) that makes use of the Lanczos resampling method for scaling textures. [More...](#details)

- Import Statement: import org.kde.graphicaleffects
- Inherits: [ShaderEffect](https://doc.qt.io/qt-6/qml-qtquick-shadereffect.html)

## Detailed Description {#details}

Lanczos resampling tries to preserve detail when scaling down images and thus looks less blurry compared to a simple linear interpolation.

This effect implements a single-pass Lanczos resampling filter using two lobes. Everything is done in the shader, with some defaults set for parameters. These defaults were designed to provide a good visual result when scaling down window thumbnails.

## Property Documentation {#property-documentation}

### \[default: 0.65\] antiRingingStrength : real {#antiRingingStrength-prop}

The amount of anti-ringing to apply.

### resolution : real {#resolution-prop}

The resolution of the Lanczos effect.

Larger values mean reduced (more pixelated) results. Defaults to 0.98 for good results.

### \[default: 1.0\] sinc : real {#sinc-prop}

Lanczos Sinc function factor.

### \[required\] source : var {#source-prop}

The source texture. Can be any QQuickTextureProvider.

### \[required\] sourceSize : size {#sourceSize-prop}

The size of the source texture. Used to perform aspect ratio correction.

### targetSize : size {#targetSize-prop}

The target size of the Lanczos effect.

Defaults to the width and height of this effect.

### \[default: 0.4\] windowSinc : real {#windowSinc-prop}

Lanczos window Sinc function factor.
