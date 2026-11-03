---
title: "BluezQt::MediaPlayerTrack Class"
description: "Media player track."
---

# BluezQt::MediaPlayerTrack Class

Media player track. [More...](#details)

- **Header:** `#include <BluezQt/MediaPlayerTrack>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`

[List of all members, including inherited members](bluezqt-mediaplayertrack-members.md)

## Public Functions

- [MediaPlayerTrack()](#MediaPlayerTrack)
- [MediaPlayerTrack(const BluezQt::MediaPlayerTrack &other)](#MediaPlayerTrack-1)
- [QString album() const](#album)
- [QString artist() const](#artist)
- [quint32 duration() const](#duration)
- [QString genre() const](#genre)
- [bool isValid() const](#isValid)
- [quint32 numberOfTracks() const](#numberOfTracks)
- [QString title() const](#title)
- [quint32 trackNumber() const](#trackNumber)
- [BluezQt::MediaPlayerTrack &MediaPlayerTrack::operator=(const BluezQt::MediaPlayerTrack &other)](#operator-eq)

## Detailed Description {#details}

This class represents a track in media player.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] MediaPlayerTrack::MediaPlayerTrack() {#MediaPlayerTrack}

Creates a new invalid [MediaPlayerTrack](bluezqt-mediaplayertrack.md) object.

### MediaPlayerTrack::MediaPlayerTrack(const BluezQt::MediaPlayerTrack &*other*) {#MediaPlayerTrack-1}

Constructs a new [MediaPlayerTrack](bluezqt-mediaplayertrack.md) object from `other`.

### QString MediaPlayerTrack::album() const {#album}

Returns the track album.

### QString MediaPlayerTrack::artist() const {#artist}

Returns the track artist.

### quint32 MediaPlayerTrack::duration() const {#duration}

Returns the track duration.

### QString MediaPlayerTrack::genre() const {#genre}

Returns the track genre.

### bool MediaPlayerTrack::isValid() const {#isValid}

Returns whether the track is valid.

### quint32 MediaPlayerTrack::numberOfTracks() const {#numberOfTracks}

Returns the total number of tracks.

### QString MediaPlayerTrack::title() const {#title}

Returns the track title.

### quint32 MediaPlayerTrack::trackNumber() const {#trackNumber}

Returns the track number.

### BluezQt::MediaPlayerTrack &MediaPlayerTrack::operator=(const BluezQt::MediaPlayerTrack &*other*) {#operator-eq}

Copies the [MediaPlayerTrack](bluezqt-mediaplayertrack.md) object from `other`.
