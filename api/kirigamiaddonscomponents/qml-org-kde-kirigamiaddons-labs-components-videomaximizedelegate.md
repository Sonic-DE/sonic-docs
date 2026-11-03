---
title: "VideoMaximizeDelegate QML Type"
description: "Reusable controls and visual components for Kirigami applications.."
---

# VideoMaximizeDelegate QML Type

Reusable controls and visual components for Kirigami applications.. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.labs.components
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### autoPlay : bool {#autoPlay-prop}

Whether the source video should auto-play.

### \[required\] caption : string {#caption-prop}

The caption for the item.

Typically set to the filename if no caption is available.

> **Note:** Declared here so that parent components can access this parameter when used as a [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html) delegate.

### downloadAction : DownloadAction {#downloadAction-prop}

The default action triggered when the download button is pressed.

This exists as a property so that the action can be overridden. The most common use case for this is where a custom URI scheme is used.

### \[default: Kirigami.Units.largeSpacing\] padding : var {#padding-prop}

The padding around the content image.

The padding is factored in when calculating the maximum size of the content image.

### pauseAction : Kirigami.Action {#pauseAction-prop}

The default action triggered when the pause button is pressed.

This exists as a property so that the action can be overridden. For example if you want to be able to interface with a media manager.

### playAction : Kirigami.Action {#playAction-prop}

The default action triggered when the play button is pressed.

This exists as a property so that the action can be overridden. For example if you want to be able to interface with a media manager.

### playbackState : enumeration {#playbackState-prop}

The playback state of the media.

| Constant | Description |
| --- | --- |
| MediaPlayer.PlayingState | The media is playing. |
| MediaPlayer.PausedState | The media is paused. |
| MediaPlayer.StoppedState | The media is stopped. |

*See also* [QtMultimedia.MediaPlayer.playBackState](https://doc.qt.io/qt-6/qml-qtmultimedia-mediaplayer.html#playbackState-prop)

### \[default: 1\] scaleFactor : var {#scaleFactor-prop}

Multiple by which the image is scaled.

### \[required\] source : string {#source-prop}

The source for the image to be viewed.

### \[required\] sourceHeight : real {#sourceHeight-prop}

The size of the source image.

This is used to calculate the maximum size of the content and temporary image.

### \[required\] sourceWidth : real {#sourceWidth-prop}

The size of the source image.

This is used to calculate the maximum size of the content and temporary image.

### \[required\] tempSource : string {#tempSource-prop}

Source for the temporary content.

Typically used when downloading the image to show a thumbnail or other temporary image while the main image downloads.

### \[read-only\] type : int {#type-prop}

The delegate type for this item.

> **Note:** Declared here so that parent components can access this parameter when used as a [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html) delegate.

## Signal Documentation {#signal-documentation}

### backgroundClicked() {#backgroundClicked-signal}

Emitted when the background space around the content item is clicked.

> **Note:** The corresponding handler is `onBackgroundClicked`.

### itemRightClicked() {#itemRightClicked-signal}

Emitted when the content image is right clicked.

> **Note:** The corresponding handler is `onItemRightClicked`.

## Method Documentation {#method-documentation}

### pause() {#pause-method}

Pause media playback.

### play() {#play-method}

Start media playback.
