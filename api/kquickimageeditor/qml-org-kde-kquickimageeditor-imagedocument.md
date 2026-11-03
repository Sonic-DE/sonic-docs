---
title: "ImageDocument QML Type"
description: "An ImageDocument is the base class of the ImageEditor."
---

# ImageDocument QML Type

An [ImageDocument](qml-org-kde-kquickimageeditor-imagedocument.md) is the base class of the ImageEditor. [More...](#details)

- Import Statement: import org.kde.kquickimageeditor

## Detailed Description {#details}

This class handles various image manipulation and contains an undo stack to allow reverting the last actions. This class does not display the image, use [ImageItem](qml-org-kde-kquickimageeditor-imageitem.md) for this task.

```qml
KQuickImageEditor.ImageDocument {
   id: imageDocument
   path: myModel.image
}

Kirigami.Actions {
   iconName: "object-rotate-left"
   onTriggered: imageDocument.rotate(-90);
}

KQuickImageEditor.ImageItem {
    image: imageDocument.image
}
```

## Property Documentation {#property-documentation}

### edited : bool {#edited-prop}

Whether the document was changed or not.

Allows to change the edited value.

### image : image {#image-prop}

The image was is displayed.

This property is updated when the path changes or commands are applied.

### path : url {#path-prop}

The path to the image.

## Method Documentation {#method-documentation}

### void cancel() {#cancel-method}

Cancel all edits.

### void crop(int *x*, int *y*, int *width*, int *height*) {#crop-method}

Crop the image.

Requires specifying the initial `x` and `y` coordinates for the crop in the old image as well as the `width` and `height` of the crop selection.

### void mirror(bool *horizontal*, bool *vertical*) {#mirror-method}

Mirror the image `horizontally` and/or `vertically`.

### void resize(int *width*, int *height*) {#resize-method}

Resize the image to the new `width` and `height`.

### void rotate(int *angle*) {#rotate-method}

Rotate the image with the given `angle`.

### bool save() {#save-method}

Save current edited image in place.

This is a destructive operation and can't be reverted.

Returns `true` if the file saving operation was successful.

### bool saveSas(url *location*) {#saveSas-method}

Save current edited image as a new image in `location`.

Returns `true` if the file saving operation was successful.

### void undo() {#undo-method}

Undo the last edit on the images.
