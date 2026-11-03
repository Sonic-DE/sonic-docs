---
title: "AnnotationDocument QML Type"
description: "This class is used to render an image with annotations."
---

# AnnotationDocument QML Type

This class is used to render an image with annotations. [More...](#details)

- Import Statement: import org.kde.kquickimageeditor

## Detailed Description {#details}

The annotations are vector graphics and image effects created from a stack of history items that can be undone or redone.

paint() and renderToImage() will be used by clients (e.g., [AnnotationViewport](qml-org-kde-kquickimageeditor-annotationviewport.md)) to render their own content.

There can be any amount of clients sharing the same [AnnotationDocument](qml-org-kde-kquickimageeditor-annotationdocument.md).

## Property Documentation {#property-documentation}

### ContinueOption : enumeration {#ContinueOption-prop}

| Constant |
| --- |
| NoOptions |
| Snap |
| CenterResize |

### RepaintType : enumeration {#RepaintType-prop}

| Constant |
| --- |
| NoTypes |
| BaseImage |
| Annotations |
| All |

### canvasRect : rect {#canvasRect-prop}

### imageDpr : real {#imageDpr-prop}

### imageSize : size {#imageSize-prop}

### inputTransform : matrix4x4 {#inputTransform-prop}

### modified : bool {#modified-prop}

This property holds whether the document has been modified by the user.

By default, this property is false.

### redoStackDepth : int {#redoStackDepth-prop}

### renderTransform : matrix4x4 {#renderTransform-prop}

### selectedItem : SelectedItemWrapper {#selectedItem-prop}

### tool : AnnotationTool {#tool-prop}

### transform : matrix4x4 {#transform-prop}

### undoStackDepth : int {#undoStackDepth-prop}

## Method Documentation {#method-documentation}

### void applyColorAdjustment(matrix4x4 *matrix*, real *gamma*) {#applyColorAdjustment-method}

Apply a color adjustment and combine it with any existing color adjustments.

`matrix` provides a color transformation in a linear colorspace. If `matrix` is an identity matrix, a matrix transformation will not be applied.

`gamma` provides a gamma adjustment for colors in the linear colorspace. If `gamma` is close to or less than 0 or close to 1 (see the `float` variant of `qFuzzyIsNull` and `qFuzzyCompare`), a new gamma will not be applied.

### void applyTransform(matrix4x4 *matrix*) {#applyTransform-method}

Apply a transform and combine it with the existing transform. This is not part of the \`transform\` property. It adds an item to history and we don't want this to be rapidly called through bindings.

### void clear() {#clear-method}

Clear all annotations and the image. Cannot be undone.

### void clearAnnotations() {#clearAnnotations-method}

Clear all annotations. Cannot be undone.

### void cropCanvas(rect *cropRect*) {#cropCanvas-method}

Hide annotations that do not intersect with the rectangle and crop the image.

### void deleteSelectedItem() {#deleteSelectedItem-method}

### void deselectItem() {#deselectItem-method}

### bool saveImage(string *path*) {#saveImage-method}

Render to an image and save it to the given path.

### void selectItem(rect *rect*) {#selectItem-method}

### void setBaseImage(string *path*) {#setBaseImage-method}

Set the base image from the given file path.

### void setBaseImage(url *localFile*) {#setBaseImage-method-1}

Set the base image from the given local file URL.

We only support local files because [QImage](https://doc.qt.io/qt-6/qimage.html) can only load directly from local files. This overload exists so that we don't have to convert URLs into path strings.

### void undo() {#undo-method}
