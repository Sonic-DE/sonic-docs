---
title: "BluezQt::MediaTransport Class"
description: "Media transport."
---

# BluezQt::MediaTransport Class

Media transport. [More...](#details)

- **Header:** `#include <BluezQt/MediaTransport>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-mediatransport-members.md)

## Public Types

- [enum MediaTransport::State](#State-enum)

## Properties

- [\[read-only\] state : State](#state-prop)
- [\[read-only\] volume : quint16](#volume-prop)

## Public Functions

- [BluezQt::AudioConfiguration audioConfiguration() const](#audioConfiguration)
- [BluezQt::PendingCall \*setVolume(quint16 volume)](#setVolume) (since 6.6)
- [BluezQt::MediaTransport::State state() const](#state)
- [quint16 volume() const](#volume)

## Public Slots

- [BluezQt::TPendingCall\<QDBusUnixFileDescriptor, uint16\_t, uint16\_t\> \*acquire()](#acquire)
- [BluezQt::TPendingCall\<void\> \*release()](#release)
- [BluezQt::TPendingCall\<QDBusUnixFileDescriptor, uint16\_t, uint16\_t\> \*tryAcquire()](#tryAcquire)

## Signals

- [void stateChanged(BluezQt::MediaTransport::State state)](#stateChanged)
- [void volumeChanged(quint16 volume)](#volumeChanged)

## Detailed Description {#details}

This class represents a media transport interface.

## Member Type Documentation {#member-type-documentation}

### enum MediaTransport::State {#State-enum}

Indicates the state of the transport.

| Constant |   |
| --- | --- |
| `BluezQt::MediaTransport::State::Idle` | `0` |
| `BluezQt::MediaTransport::State::Pending` | `1` |
| `BluezQt::MediaTransport::State::Active` | `2` |

## Property Documentation {#property-documentation}

### \[read-only\] state : State {#state-prop}

**Access functions:**

- `BluezQt::MediaTransport::State` **[state](bluezqt-mediatransport.md#state)**() const

**Notifier signal:**

- `void` **[stateChanged](bluezqt-mediatransport.md#stateChanged)**(`BluezQt::MediaTransport::State` *state*)

### \[read-only\] volume : quint16 {#volume-prop}

**Access functions:**

- `quint16` **[volume](bluezqt-mediatransport.md#volume)**() const

**Notifier signal:**

- `void` **[volumeChanged](bluezqt-mediatransport.md#volumeChanged)**(`quint16` *volume*)

## Member Function Documentation {#member-function-documentation}

### \[slot\] BluezQt::TPendingCall\<QDBusUnixFileDescriptor, uint16\_t, uint16\_t\> \*MediaTransport::acquire() {#acquire}

Acquires the transport file descriptor and the MTU for read and write respectively.

Possible errors:

- [PendingCall::NotAuthorized](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns \<fd, uint16, uint16\> pending call.

### BluezQt::AudioConfiguration MediaTransport::audioConfiguration() const {#audioConfiguration}

Returns the (audio) configuration of the transport.

### \[slot\] BluezQt::TPendingCall\<void\> \*MediaTransport::release() {#release}

Releases file descriptor.

### \[since 6.6\] BluezQt::PendingCall \*MediaTransport::setVolume(quint16 *volume*) {#setVolume}

Sets the `volume` of the transport.

Only works when the transport was acquired by the sender.

The volume of the transport should be within the range \[0x00..0x7F\] (0-127)

Returns void pending call.

This function was introduced in Qt 6.6.

*See also* [volume](bluezqt-mediatransport.md#volume)()

### BluezQt::MediaTransport::State MediaTransport::state() const {#state}

Returns the state of the transport.

> **Note:** Getter function for property [state](bluezqt-mediatransport.md#state-prop).

### \[signal\] void MediaTransport::stateChanged(BluezQt::MediaTransport::State *state*) {#stateChanged}

Indicates that the transport's `state` has changed.

> **Note:** Notifier signal for property [state](bluezqt-mediatransport.md#state-prop).

### \[slot\] BluezQt::TPendingCall\<QDBusUnixFileDescriptor, uint16\_t, uint16\_t\> \*MediaTransport::tryAcquire() {#tryAcquire}

Acquire transport file descriptor only if the transport is in "pending" state at the time the message is received by BlueZ. Otherwise no request will be sent to the remote device and the function will just fail with org.bluez.Error.NotAvailable.

Possible errors:

- [PendingCall::NotAuthorized](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)
- PendingCall::NotAvailable

Returns \<fd, uint16, uint16\> pending call.

### quint16 MediaTransport::volume() const {#volume}

Returns the volume of the transport.

The volume is a percentage of the maximum. The value 0x00 corresponds to 0%. The value 0x7F corresponds to 100%. Scaling should be applied to achieve values between these two.

The existence of this scale does not impose any restriction on the granularity of the volume control scale on the target.

As this command specifies a percentage rather than an absolute dB level the controller should exercise caution when sending this command.

> **Note:** Getter function for property [volume](bluezqt-mediatransport.md#volume-prop).

*See also* [setVolume](bluezqt-mediatransport.md#setVolume)()

### \[signal\] void MediaTransport::volumeChanged(quint16 *volume*) {#volumeChanged}

Indicates that the transport's `volume` has changed.

> **Note:** Notifier signal for property [volume](bluezqt-mediatransport.md#volume-prop).
