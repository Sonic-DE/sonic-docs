---
title: "AlbumMaximizeComponent QML Type"
description: "A popup that covers the entire window to show an album of one or more media items."
---

# AlbumMaximizeComponent QML Type

A popup that covers the entire window to show an album of one or more media items. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.labs.components
- Inherits: [AbstractMaximizeComponent](qml-org-kde-kirigamiaddons-labs-components-abstractmaximizecomponent.md)

## Detailed Description {#details}

The component supports a model with one or more media components (images or videos) which can be scrolled through.

Example:

```qml
Components.AlbumMaximizeComponent {
 id: root
 property list<AlbumModelItem> model: [
     AlbumModelItem {
         type: AlbumModelItem.Image
         source: "path/to/source"
         tempSource: "path/to/tempSource"
         caption: "caption text"
     },
     AlbumModelItem {
         type: AlbumModelItem.Video
         source: "path/to/source"
         tempSource: "path/to/tempSource"
         caption: "caption text"
     }
 ]
 initialIndex: 0
 model: model
}
```

> **Note:** The model doesn't have to be create using [AlbumModelItem](qml-org-kde-kirigamiaddons-labs-components-albummodelitem.md), it just requires the same roles (i.e. type, source, tempSource (optional) and caption (optional)).

## Property Documentation {#property-documentation}

### \[default: true\] autoPlay : bool {#autoPlay-prop}

Whether any video media should auto-play.

### currentIndex : int {#currentIndex-prop}

The current index in the view.

### currentItem : Item {#currentItem-prop}

The current Item in the view.

### downloadAction : DownloadAction {#downloadAction-prop}

The default action triggered when the video download button is pressed.

The download button is only available when the video source is empty (i.e. QUrl() or "")

This exists as a property so that the default action can be overridden. The most common use case for this is where a custom URI scheme is used for example.

*See also* [DownloadAction](qml-org-kde-kirigamiaddons-labs-components-downloadaction.md)

### \[default: false\] hideCaption : bool {#hideCaption-prop}

Whether the caption is hidden by the user.

### \[default: -1\] initialIndex : int {#initialIndex-prop}

The index of the initial item that should be visible.

### model : var {#model-prop}

Model containing the media item to be shown.

The model can be either a qml or a c++ model but each item needs to have the values defined in [AlbumModelItem](qml-org-kde-kirigamiaddons-labs-components-albummodelitem.md) (note a list of these is the easiest way to create a qml model).

### pauseAction : Kirigami.Action {#pauseAction-prop}

The default action triggered when the pause button is pressed.

This exists as a property so that the action can be overridden. For example if you want to be able to interface with a media manager.

### playAction : Kirigami.Action {#playAction-prop}

The default action triggered when the play button is pressed.

This exists as a property so that the action can be overridden. For example if you want to be able to interface with a media manager.

### \[default: true\] showCaption : bool {#showCaption-prop}

Whether the caption should be shown.

## Signal Documentation {#signal-documentation}

### itemRightClicked() {#itemRightClicked-signal}

Emitted when the content image is right clicked.

> **Note:** The corresponding handler is `onItemRightClicked`.

### saveItem() {#saveItem-signal}

Emitted when the save item button is pressed.

The application needs use this signal to trigger the process to save the file.

> **Note:** The corresponding handler is `onSaveItem`.
