---
title: "BluezQt::MediaEndpoint Class"
description: "Bluetooth MediaEndpoint."
---

# BluezQt::MediaEndpoint Class

Bluetooth [MediaEndpoint](bluezqt-mediaendpoint.md). [More...](#details)

- **Header:** `#include <BluezQt/MediaEndpoint>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-mediaendpoint-members.md)

## Public Types

- [enum MediaEndpoint::Codec](#Codec-enum)
- [enum MediaEndpoint::Role](#Role-enum)

## Public Functions

- [MediaEndpoint(const BluezQt::MediaEndpoint::Configuration &configuration, QObject \*parent = nullptr)](#MediaEndpoint)
- [void clearConfiguration(const QString &transportObjectPath)](#clearConfiguration)
- [QDBusObjectPath objectPath() const](#objectPath)
- [const QVariantMap &properties() const](#properties)
- [void release()](#release)
- [void selectConfiguration(const QByteArray &capabilities, const BluezQt::Request\<QByteArray\> &request)](#selectConfiguration)
- [void setConfiguration(const QString &transportObjectPath, const QVariantMap &properties)](#setConfiguration)

## Signals

- [void configurationCleared(const QString &transportObjectPath)](#configurationCleared)
- [void configurationSelected(const QByteArray &capabilities, const QByteArray &configuration)](#configurationSelected)
- [void configurationSet(const QString &transportObjectPath, const QVariantMap &properties)](#configurationSet)

## Detailed Description {#details}

This class represents a Bluetooth [MediaEndpoint](bluezqt-mediaendpoint.md).

## Member Type Documentation {#member-type-documentation}

### enum MediaEndpoint::Codec {#Codec-enum}

Codec which this [MediaEndpoint](bluezqt-mediaendpoint.md) supports.

| Constant |   |
| --- | --- |
| `BluezQt::MediaEndpoint::Codec::Sbc` | `0` |
| `BluezQt::MediaEndpoint::Codec::Aac` | `1` |

### enum MediaEndpoint::Role {#Role-enum}

Role which this [MediaEndpoint](bluezqt-mediaendpoint.md) acts as.

| Constant |   |
| --- | --- |
| `BluezQt::MediaEndpoint::Role::AudioSource` | `0` |
| `BluezQt::MediaEndpoint::Role::AudioSink` | `1` |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] MediaEndpoint::MediaEndpoint(const BluezQt::MediaEndpoint::Configuration &*configuration*, QObject \**parent* = nullptr) {#MediaEndpoint}

Creates a new [MediaEndpoint](bluezqt-mediaendpoint.md) object with the given `configuration` as a child of `parent`.

### \[virtual\] void MediaEndpoint::clearConfiguration(const QString &*transportObjectPath*) {#clearConfiguration}

Clear the transport configuration at `transportObjectPath`.

### \[signal\] void MediaEndpoint::configurationCleared(const QString &*transportObjectPath*) {#configurationCleared}

Indicates that the configuration was cleared for transport.

### \[signal\] void MediaEndpoint::configurationSelected(const QByteArray &*capabilities*, const QByteArray &*configuration*) {#configurationSelected}

Indicates that the configuration was selected.

### \[signal\] void MediaEndpoint::configurationSet(const QString &*transportObjectPath*, const QVariantMap &*properties*) {#configurationSet}

Indicates that the configuration was set for transport.

### \[virtual\] QDBusObjectPath MediaEndpoint::objectPath() const {#objectPath}

Returns the D-Bus object path of the [MediaEndpoint](bluezqt-mediaendpoint.md).

The path where the [MediaEndpoint](bluezqt-mediaendpoint.md) will be registered.

> **Note:** You must provide valid object path!

### \[virtual\] const QVariantMap &MediaEndpoint::properties() const {#properties}

Returns the properties of the endpoint.

### \[virtual\] void MediaEndpoint::release() {#release}

Indicates that the [MediaEndpoint](bluezqt-mediaendpoint.md) was unregistered.

This method gets called when the Bluetooth daemon unregisters the [MediaEndpoint](bluezqt-mediaendpoint.md).

A [MediaEndpoint](bluezqt-mediaendpoint.md) can use it to do cleanup tasks. There is no need to unregister the [MediaEndpoint](bluezqt-mediaendpoint.md), because when this method gets called it has already been unregistered.

### \[virtual\] void MediaEndpoint::selectConfiguration(const QByteArray &*capabilities*, const BluezQt::Request\<QByteArray\> &*request*) {#selectConfiguration}

Select preferable configuration from the supported `capabilities` with a `request` to be used for sending the reply.

> **Note:** There is no need to cache the selected configuration since on success the configuration is send back as parameter of SetConfiguration.

### \[virtual\] void MediaEndpoint::setConfiguration(const QString &*transportObjectPath*, const QVariantMap &*properties*) {#setConfiguration}

Set configuration for the transport at the `transportObjectPath` with the given `properties`.
