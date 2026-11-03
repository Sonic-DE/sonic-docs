---
title: "BluezQt::MediaPlayer Class"
description: "Media player."
---

# BluezQt::MediaPlayer Class

Media player. [More...](#details)

- **Header:** `#include <BluezQt/MediaPlayer>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-mediaplayer-members.md)

## Public Types

- [enum MediaPlayer::Equalizer](#Equalizer-enum)
- [enum MediaPlayer::Repeat](#Repeat-enum)
- [enum MediaPlayer::Shuffle](#Shuffle-enum)
- [enum MediaPlayer::Status](#Status-enum)

## Properties

- [equalizer : Equalizer](#equalizer-prop)
- [\[read-only\] name : QString](#name-prop)
- [\[read-only\] position : quint32](#position-prop)
- [repeat : Repeat](#repeat-prop)
- [shuffle : Shuffle](#shuffle-prop)
- [\[read-only\] status : Status](#status-prop)
- [\[read-only\] track : MediaPlayerTrack](#track-prop)

## Public Functions

- [BluezQt::MediaPlayer::Equalizer equalizer() const](#equalizer)
- [QString name() const](#name)
- [quint32 position() const](#position)
- [BluezQt::MediaPlayer::Repeat repeat() const](#repeat)
- [BluezQt::PendingCall \*setEqualizer(BluezQt::MediaPlayer::Equalizer equalizer)](#setEqualizer)
- [BluezQt::PendingCall \*setRepeat(BluezQt::MediaPlayer::Repeat repeat)](#setRepeat)
- [BluezQt::PendingCall \*setShuffle(BluezQt::MediaPlayer::Shuffle shuffle)](#setShuffle)
- [BluezQt::MediaPlayer::Shuffle shuffle() const](#shuffle)
- [BluezQt::MediaPlayer::Status status() const](#status)
- [BluezQt::MediaPlayerPtr toSharedPtr() const](#toSharedPtr)
- [BluezQt::MediaPlayerTrack track() const](#track)

## Public Slots

- [BluezQt::PendingCall \*fastForward()](#fastForward)
- [BluezQt::PendingCall \*next()](#next)
- [BluezQt::PendingCall \*pause()](#pause)
- [BluezQt::PendingCall \*play()](#play)
- [BluezQt::PendingCall \*previous()](#previous)
- [BluezQt::PendingCall \*rewind()](#rewind)
- [BluezQt::PendingCall \*stop()](#stop)

## Signals

- [void equalizerChanged(BluezQt::MediaPlayer::Equalizer equalizer)](#equalizerChanged)
- [void nameChanged(const QString &name)](#nameChanged)
- [void positionChanged(quint32 position)](#positionChanged)
- [void repeatChanged(BluezQt::MediaPlayer::Repeat repeat)](#repeatChanged)
- [void shuffleChanged(BluezQt::MediaPlayer::Shuffle shuffle)](#shuffleChanged)
- [void statusChanged(BluezQt::MediaPlayer::Status status)](#statusChanged)
- [void trackChanged(BluezQt::MediaPlayerTrack track)](#trackChanged)

## Detailed Description {#details}

This class represents a media player interface.

## Member Type Documentation {#member-type-documentation}

### enum MediaPlayer::Equalizer {#Equalizer-enum}

| Constant |   |
| --- | --- |
| `BluezQt::MediaPlayer::EqualizerOn` | `0` |
| `BluezQt::MediaPlayer::EqualizerOff` | `1` |

### enum MediaPlayer::Repeat {#Repeat-enum}

| Constant |   |
| --- | --- |
| `BluezQt::MediaPlayer::RepeatOff` | `0` |
| `BluezQt::MediaPlayer::RepeatSingleTrack` | `1` |
| `BluezQt::MediaPlayer::RepeatAllTracks` | `2` |
| `BluezQt::MediaPlayer::RepeatGroup` | `3` |

### enum MediaPlayer::Shuffle {#Shuffle-enum}

| Constant |   |
| --- | --- |
| `BluezQt::MediaPlayer::ShuffleOff` | `0` |
| `BluezQt::MediaPlayer::ShuffleAllTracks` | `1` |
| `BluezQt::MediaPlayer::ShuffleGroup` | `2` |

### enum MediaPlayer::Status {#Status-enum}

| Constant |   |
| --- | --- |
| `BluezQt::MediaPlayer::Playing` | `0` |
| `BluezQt::MediaPlayer::Stopped` | `1` |
| `BluezQt::MediaPlayer::Paused` | `2` |
| `BluezQt::MediaPlayer::ForwardSeek` | `3` |
| `BluezQt::MediaPlayer::ReverseSeek` | `4` |
| `BluezQt::MediaPlayer::Error` | `5` |

## Property Documentation {#property-documentation}

### equalizer : Equalizer {#equalizer-prop}

**Access functions:**

- `BluezQt::MediaPlayer::Equalizer` **[equalizer](bluezqt-mediaplayer.md#equalizer)**() const
- `BluezQt::PendingCall` \***[setEqualizer](bluezqt-mediaplayer.md#setEqualizer)**(`BluezQt::MediaPlayer::Equalizer` *equalizer*)

**Notifier signal:**

- `void` **[equalizerChanged](bluezqt-mediaplayer.md#equalizerChanged)**(`BluezQt::MediaPlayer::Equalizer` *equalizer*)

### \[read-only\] name : QString {#name-prop}

**Access functions:**

- `QString` **[name](bluezqt-mediaplayer.md#name)**() const

**Notifier signal:**

- `void` **[nameChanged](bluezqt-mediaplayer.md#nameChanged)**(const `QString` &*name*)

### \[read-only\] position : quint32 {#position-prop}

**Access functions:**

- `quint32` **[position](bluezqt-mediaplayer.md#position)**() const

**Notifier signal:**

- `void` **[positionChanged](bluezqt-mediaplayer.md#positionChanged)**(`quint32` *position*)

### repeat : Repeat {#repeat-prop}

**Access functions:**

- `BluezQt::MediaPlayer::Repeat` **[repeat](bluezqt-mediaplayer.md#repeat)**() const
- `BluezQt::PendingCall` \***[setRepeat](bluezqt-mediaplayer.md#setRepeat)**(`BluezQt::MediaPlayer::Repeat` *repeat*)

**Notifier signal:**

- `void` **[repeatChanged](bluezqt-mediaplayer.md#repeatChanged)**(`BluezQt::MediaPlayer::Repeat` *repeat*)

### shuffle : Shuffle {#shuffle-prop}

**Access functions:**

- `BluezQt::MediaPlayer::Shuffle` **[shuffle](bluezqt-mediaplayer.md#shuffle)**() const
- `BluezQt::PendingCall` \***[setShuffle](bluezqt-mediaplayer.md#setShuffle)**(`BluezQt::MediaPlayer::Shuffle` *shuffle*)

**Notifier signal:**

- `void` **[shuffleChanged](bluezqt-mediaplayer.md#shuffleChanged)**(`BluezQt::MediaPlayer::Shuffle` *shuffle*)

### \[read-only\] status : Status {#status-prop}

**Access functions:**

- `BluezQt::MediaPlayer::Status` **[status](bluezqt-mediaplayer.md#status)**() const

**Notifier signal:**

- `void` **[statusChanged](bluezqt-mediaplayer.md#statusChanged)**(`BluezQt::MediaPlayer::Status` *status*)

### \[read-only\] track : MediaPlayerTrack {#track-prop}

**Access functions:**

- `BluezQt::MediaPlayerTrack` **[track](bluezqt-mediaplayer.md#track)**() const

**Notifier signal:**

- `void` **[trackChanged](bluezqt-mediaplayer.md#trackChanged)**(`BluezQt::MediaPlayerTrack` *track*)

## Member Function Documentation {#member-function-documentation}

### BluezQt::MediaPlayer::Equalizer MediaPlayer::equalizer() const {#equalizer}

Returns the equalizer state of the player.

> **Note:** Getter function for property [equalizer](bluezqt-mediaplayer.md#equalizer-prop).

*See also* [setEqualizer](bluezqt-mediaplayer.md#setEqualizer)()

### \[signal\] void MediaPlayer::equalizerChanged(BluezQt::MediaPlayer::Equalizer *equalizer*) {#equalizerChanged}

Indicates that the player's `equalizer` state has changed.

> **Note:** Notifier signal for property [equalizer](bluezqt-mediaplayer.md#equalizer-prop).

### \[slot\] BluezQt::PendingCall \*MediaPlayer::fastForward() {#fastForward}

Fast forwards playback.

Possible errors:

- [PendingCall::NotSupported](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### QString MediaPlayer::name() const {#name}

Returns the name of the player.

> **Note:** Getter function for property [name](bluezqt-mediaplayer.md#name-prop).

### \[signal\] void MediaPlayer::nameChanged(const QString &*name*) {#nameChanged}

Indicates that the player's `name` has changed.

> **Note:** Notifier signal for property [name](bluezqt-mediaplayer.md#name-prop).

### \[slot\] BluezQt::PendingCall \*MediaPlayer::next() {#next}

Switches to the next track.

Possible errors:

- [PendingCall::NotSupported](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### \[slot\] BluezQt::PendingCall \*MediaPlayer::pause() {#pause}

Pauses playback.

Possible errors:

- [PendingCall::NotSupported](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### \[slot\] BluezQt::PendingCall \*MediaPlayer::play() {#play}

Resumes playback.

Possible errors:

- [PendingCall::NotSupported](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### quint32 MediaPlayer::position() const {#position}

Returns the playback position in milliseconds.

> **Note:** Getter function for property [position](bluezqt-mediaplayer.md#position-prop).

### \[signal\] void MediaPlayer::positionChanged(quint32 *position*) {#positionChanged}

Indicates that the player's playback `position` has changed.

> **Note:** Notifier signal for property [position](bluezqt-mediaplayer.md#position-prop).

### \[slot\] BluezQt::PendingCall \*MediaPlayer::previous() {#previous}

Switch to previous track.

Possible errors:

- [PendingCall::NotSupported](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### BluezQt::MediaPlayer::Repeat MediaPlayer::repeat() const {#repeat}

Returns the repeat state of the player.

> **Note:** Getter function for property [repeat](bluezqt-mediaplayer.md#repeat-prop).

*See also* [setRepeat](bluezqt-mediaplayer.md#setRepeat)()

### \[signal\] void MediaPlayer::repeatChanged(BluezQt::MediaPlayer::Repeat *repeat*) {#repeatChanged}

Indicates that the player's `repeat` state has changed.

> **Note:** Notifier signal for property [repeat](bluezqt-mediaplayer.md#repeat-prop).

### \[slot\] BluezQt::PendingCall \*MediaPlayer::rewind() {#rewind}

Rewinds playback.

Possible errors:

- [PendingCall::NotSupported](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### BluezQt::PendingCall \*MediaPlayer::setEqualizer(BluezQt::MediaPlayer::Equalizer *equalizer*) {#setEqualizer}

Sets the `equalizer` state of the player.

Returns void pending call.

> **Note:** Setter function for property [equalizer](bluezqt-mediaplayer.md#equalizer-prop).

*See also* [equalizer](bluezqt-mediaplayer.md#equalizer)()

### BluezQt::PendingCall \*MediaPlayer::setRepeat(BluezQt::MediaPlayer::Repeat *repeat*) {#setRepeat}

Sets the `repeat` state of the player.

Returns void pending call.

> **Note:** Setter function for property [repeat](bluezqt-mediaplayer.md#repeat-prop).

*See also* [repeat](bluezqt-mediaplayer.md#repeat)()

### BluezQt::PendingCall \*MediaPlayer::setShuffle(BluezQt::MediaPlayer::Shuffle *shuffle*) {#setShuffle}

Sets the `shuffle` state of the player.

Returns void pending call.

> **Note:** Setter function for property [shuffle](bluezqt-mediaplayer.md#shuffle-prop).

*See also* [shuffle](bluezqt-mediaplayer.md#shuffle)()

### BluezQt::MediaPlayer::Shuffle MediaPlayer::shuffle() const {#shuffle}

Returns the shuffle state of the player.

> **Note:** Getter function for property [shuffle](bluezqt-mediaplayer.md#shuffle-prop).

*See also* [setShuffle](bluezqt-mediaplayer.md#setShuffle)()

### \[signal\] void MediaPlayer::shuffleChanged(BluezQt::MediaPlayer::Shuffle *shuffle*) {#shuffleChanged}

Indicates that the player's `shuffle` state has changed.

> **Note:** Notifier signal for property [shuffle](bluezqt-mediaplayer.md#shuffle-prop).

### BluezQt::MediaPlayer::Status MediaPlayer::status() const {#status}

Returns the status of the player.

> **Note:** Getter function for property [status](bluezqt-mediaplayer.md#status-prop).

### \[signal\] void MediaPlayer::statusChanged(BluezQt::MediaPlayer::Status *status*) {#statusChanged}

Indicates that the player's `status` has changed.

> **Note:** Notifier signal for property [status](bluezqt-mediaplayer.md#status-prop).

### \[slot\] BluezQt::PendingCall \*MediaPlayer::stop() {#stop}

Stops playback.

Possible errors:

- [PendingCall::NotSupported](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### BluezQt::MediaPlayerPtr MediaPlayer::toSharedPtr() const {#toSharedPtr}

Returns a shared pointer from this.

### BluezQt::MediaPlayerTrack MediaPlayer::track() const {#track}

Returns the current track.

> **Note:** Getter function for property [track](bluezqt-mediaplayer.md#track-prop).

### \[signal\] void MediaPlayer::trackChanged(BluezQt::MediaPlayerTrack *track*) {#trackChanged}

Indicates that the player's current `track` has changed.

> **Note:** Notifier signal for property [track](bluezqt-mediaplayer.md#track-prop).
