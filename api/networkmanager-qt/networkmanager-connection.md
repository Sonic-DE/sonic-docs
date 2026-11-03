---
title: "NetworkManager::Connection Class"
description: "This class represents a single network connection configuration."
---

# NetworkManager::Connection Class

This class represents a single network connection configuration. [More...](#details)

- **Header:** `#include <NetworkManagerQt/Connection>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](networkmanager-connection-members.md)

## Public Types

- [Connection::List](#List-typedef)
- [Connection::Ptr](#Ptr-typedef)

## Public Functions

- [Connection(const QString &path, QObject \*parent = nullptr)](#Connection)
- [QDBusPendingReply\<\> clearSecrets()](#clearSecrets)
- [bool isUnsaved() const](#isUnsaved)
- [bool isValid() const](#isValid)
- [QString name() const](#name)
- [QString path() const](#path)
- [QDBusPendingReply\<\> remove()](#remove)
- [QDBusPendingReply\<\> save()](#save)
- [QDBusPendingReply\<NMVariantMapMap\> secrets(const QString &setting)](#secrets)
- [ConnectionSettings::Ptr settings()](#settings)
- [QDBusPendingReply\<\> update(const NMVariantMapMap &settings)](#update)
- [QDBusPendingReply\<\> updateUnsaved(const NMVariantMapMap &settings)](#updateUnsaved)
- [QString uuid() const](#uuid)

## Signals

- [void removed(const QString &path)](#removed)
- [void unsavedChanged(bool unsaved)](#unsavedChanged)
- [void updated()](#updated)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### Connection::List {#List-typedef}

### Connection::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Connection::Connection(const QString &*path*, QObject \**parent* = nullptr) {#Connection}

Constructs a connection object for the given path

### QDBusPendingReply\<\> Connection::clearSecrets() {#clearSecrets}

Clear the secrets belonging to this network connection profile.

### bool Connection::isUnsaved() const {#isUnsaved}

If set, indicates that the in-memory state of the connection does not match the on-disk state. This flag will be set when [updateUnsaved](networkmanager-connection.md#updateUnsaved)() is called or when any connection details change, and cleared when the connection is saved to disk via [save](networkmanager-connection.md#save)() or from internal operations.

### bool Connection::isValid() const {#isValid}

Returns if this connection is valid

### QString Connection::name() const {#name}

Returns the name of this connection

### QString Connection::path() const {#path}

Returns the path (DBus) of this connection

### QDBusPendingReply\<\> Connection::remove() {#remove}

Removes the connection from [NetworkManager](networkmanager.md) database, this operation does not ask for confirmation but a policykit rule might prevent it from being removed without the proper password.

### \[signal\] void Connection::removed(const QString &*path*) {#removed}

Emitted when the connection was removed

`path` connections's path.

### QDBusPendingReply\<\> Connection::save() {#save}

Saves a "dirty" connection (that had previously been updated with [updateUnsaved](networkmanager-connection.md#updateUnsaved)()) to persistent storage.

### QDBusPendingReply\<NMVariantMapMap\> Connection::secrets(const QString &*setting*) {#secrets}

Retrieves this connections's secrets (passwords and / or encryption keys).

`setting` the setting identifier.

### ConnectionSettings::Ptr Connection::settings() {#settings}

Returns the settings of this connection

### \[signal\] void Connection::unsavedChanged(bool *unsaved*) {#unsavedChanged}

Emitted when the connection unsaved state changes

### QDBusPendingReply\<\> Connection::update(const NMVariantMapMap &*settings*) {#update}

Update the connection with new `settings` and properties, replacing all previous settings and properties. Secrets may be part of the update request, and will be either stored in persistent storage or given to a Secret Agent for storage, depending on the request.

### QDBusPendingReply\<\> Connection::updateUnsaved(const NMVariantMapMap &*settings*) {#updateUnsaved}

Update the connection with new `settings` and properties (replacing all previous settings and properties) but do not immediately save the connection to disk. Secrets may be part of the update request and may sent to a Secret Agent for storage, depending on the flags associated with each secret.

Use the [save](networkmanager-connection.md#save)() method to save these changes to disk. Note that unsaved changes will be lost if the connection is reloaded from disk (either automatically on file change or due to an explicit [reloadConnections](networkmanager.md#reloadConnections)() call).

### \[signal\] void Connection::updated() {#updated}

Emitted when the connection settings changes

### QString Connection::uuid() const {#uuid}

Returns the unique identifier of this connection
