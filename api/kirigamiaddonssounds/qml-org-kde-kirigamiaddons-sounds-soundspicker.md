---
title: "SoundsPicker QML Type"
description: "A sound picker component for picking ringtones and notifications. This type is deprecated since org.kde.kirigamiaddons.sounds 1.14.1. We strongly advise against using it in new code."
---

# SoundsPicker QML Type

A sound picker component for picking ringtones and notifications. **This type is deprecated since org.kde.kirigamiaddons.sounds 1.14.1. We strongly advise against using it in new code.** [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.sounds
- Inherits: [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html)
- Status: Deprecated since 1.14.1

**This type is deprecated since org.kde.kirigamiaddons.sounds 1.14.1. We strongly advise against using it in new code.**

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### audioPlayer : MediaPlayer {#audioPlayer-prop}

This property is the internal Audio qml type used for play sound.

*See also* [QtMultimedia.MediaPlayer](https://doc.qt.io/qt-6/qml-qtmultimedia-mediaplayer.html)

### \[default: true\] notification : bool {#notification-prop}

This property controls the sound type (ringtone or notification).

### selectedUrl : string {#selectedUrl-prop}

This property holds the selected audio url.

### \[default: "plasma-mobile"\] theme : string {#theme-prop}

This property lets you choose the sound theme.
