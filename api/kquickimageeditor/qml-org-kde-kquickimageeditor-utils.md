---
title: "Utils QML Type"
description: "QML components providing basic image editing capabilities."
---

# Utils QML Type

QML components providing basic image editing capabilities. [More...](#details)

- Import Statement: import org.kde.kquickimageeditor

## Detailed Description {#details}

## Method Documentation {#method-documentation}

### matrix4x4 brightnessMatrix(real *brightness*) {#brightnessMatrix-method}

Get a matrix4x4 with a brightness transformation.

If you have an existing matrix you want to modify, multiply it with this matrix. The order in which you multiply matters.

In QML, `brightnessMatrix.times(otherMatrix)` will apply an absolute brightness change to the other matrix, except it will still be multiplied by the other matrix's global divisor (QML: `matrix.m44`, C++: `matrix(3,3)`). `otherMatrix.times(brightnessMatrix)` will apply a brightness change that is affected by the other matrix's existing scale, rotation and perspective operations, but not the other matrix's global divisor. Read the C++ code of `QMatrix4x4 operator*(const QMatrix4x4& m1, const QMatrix4x4& m2)` to understand all the details. In QML, `m1.times(m2)` uses matrices in the same order as `QMatrix4x4 operator*(m1, m2)`.

`brightness` An absolute brightness offset. You typically wouldn't use values outside of \[-1,1\] so that you don't stray too far outside the range of valid color values. However, there is nothing stopping you from doing so. Brightness is not clamped because the brightness change may be combined with scale, rotation or perspective operations. Either way, the effect applying the brightness change will need to clamp color channel values unless you are using a floating point image format where values outside of \[0,1\] are valid. Values within \[-1e-5, 1e-5\] and non-finite values will do nothing.

### real clamp(real *value*, real *min* = infinity, real *max* = infinity) {#clamp-method}

Behaves like [qBound](https://doc.qt.io/qt-6/qtminmax.html#qBound), which behaves differently from std::clamp, but uses the same argument order as std::clamp.

### real combinedScale(matrix4x4 *matrix*) {#combinedScale-method}

### matrix4x4 contrastMatrix(real *contrast*) {#contrastMatrix-method}

Get a matrix4x4 with a contrast transformation.

If you have an existing matrix you want to modify, multiply it with this matrix. The order in which you multiply matters in much the same way as [brightnessMatrix](qml-org-kde-kquickimageeditor-utils.md#brightnessMatrix-method) for translations caused by the contrast change. Either way, the scales of this matrix and another matrix will be multiplied with each other. If there are rotation and perspective operations in the other matrix, those will affect the scales from this matrix. Read the C++ code of `QMatrix4x4 operator*(m1, m2)` to understand all the details.

`contrast` A multiplier and offset that changes contrast. A typical value range might be (0,2\] or (0,4\], but there is nothing stopping you from using values outside that range. Values greater than 1 increase contrast. Values less than 1 decrease contrast. Values less than 0 will give the same result as 0. Values within 1±1e-5 and non-finite values will do nothing. Values greater than 1 may technically be able to change contrast up to the maximum value of a 32-bit float, but you probably won't notice any difference above 55.5.

### point dprRound(point *value*, real *dpr*) {#dprRound-method}

### real dprRound(real *value*, real *dpr*) {#dprRound-method-1}

### vector2d dprRound(vector2d *value*, real *dpr*) {#dprRound-method-2}

### Object handleResizeProperties(real *dx*, real *dy*, int *edges*, AnnotationDocument *document*) {#handleResizeProperties-method}

Get a [QVariantMap](https://doc.qt.io/qt-6/qvariant.html#QVariantMap-typedef) of properties for resizing an item in response to the movement of handles.

The map contains the effective handle edges so movement can be tracked properly and the [QMatrix4x4](https://doc.qt.io/qt-6/qmatrix4x4.html) to be used that are positioned along the edges of the item's bounding box.

The `dx` should be the X axis difference between 2 points in document coordinates.

The `dy` should be the Y axis difference between 2 points in document coordinates.

The `edges` should be the bounding box edges a handle touches.

The `document` should be the [AnnotationDocument](qml-org-kde-kquickimageeditor-annotationdocument.md) with the item being transformed.

### rect rectScaled(rect *rect*, real *factor*) {#rectScaled-method}

### matrix4x4 relativeLuminanceMatrix(real *rY*, real *gY*, real *bY*) {#relativeLuminanceMatrix-method}

Get a matrix4x4 with relative luminance weights. This may be necessary for some effects like saturation.

If you have an existing matrix you want to modify, add it to this matrix. The order in which you add does not matter.

### matrix4x4 saturationMatrix(real *saturation*) {#saturationMatrix-method}

Get a matrix4x4 with a saturation transformation.

If you have an existing matrix you want to modify, multiply it with this matrix. The order in which you multiply matters in much the same way as [contrastMatrix](qml-org-kde-kquickimageeditor-utils.md#contrastMatrix-method). Read the C++ code of `QMatrix4x4 operator*(m1, m2)` to understand all the details.

`saturation` A multiplier that changes saturation. A typical value range might be (0,2\] or (0,4\], but there is nothing stopping you from using values outside that range. Values greater than 1 increase saturation. Values less than 1 decrease saturation. Values less than 0 will invert the colors and apply saturation to the inverted colors. Values within 1±1e-5 and non-finite values will do nothing. Values greater than 1 may technically be able to change saturation up to the maximum value of a 32-bit float, but you probably won't notice any difference above 50.

### point sceneToDocumentPoint(point *point*, AnnotationViewport *viewport*) {#sceneToDocumentPoint-method}
