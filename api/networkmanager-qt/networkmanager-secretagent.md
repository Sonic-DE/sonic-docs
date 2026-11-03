---
title: "NetworkManager::SecretAgent Class"
description: "Implementation of a private D-Bus interface used by secret agents that store and provide secrets to NetworkManager."
---

# NetworkManager::SecretAgent Class

Implementation of a private D-Bus interface used by secret agents that store and provide secrets to [NetworkManager](networkmanager.md). [More...](#details)

- **Header:** `#include <NetworkManagerQt/SecretAgent>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html) and [QDBusContext](https://doc.qt.io/qt-6/qdbuscontext.html) (protected)

[List of all members, including inherited members](networkmanager-secretagent-members.md)

## Public Types

- [enum SecretAgent::Capability](#Capability-enum)
- [enum SecretAgent::Error](#Error-enum)
- [enum SecretAgent::GetSecretsFlag](#GetSecretsFlag-enum)

## Public Functions

- [SecretAgent(const QString &id, QObject \*parent = nullptr)](#SecretAgent)
- [SecretAgent(const QString &id, NetworkManager::SecretAgent::Capabilities capabilities, QObject \*parent = nullptr)](#SecretAgent-1)
- [void sendError(NetworkManager::SecretAgent::Error error, const QString &explanation, const QDBusMessage &callMessage = QDBusMessage()) const](#sendError)

## Public Slots

- [void CancelGetSecrets(const QDBusObjectPath &connection\_path, const QString &setting\_name)](#CancelGetSecrets)
- [void DeleteSecrets(const NMVariantMapMap &connection, const QDBusObjectPath &connection\_path)](#DeleteSecrets)
- [NMVariantMapMap GetSecrets(const NMVariantMapMap &connection, const QDBusObjectPath &connection\_path, const QString &setting\_name, const QStringList &hints, uint flags)](#GetSecrets)
- [void SaveSecrets(const NMVariantMapMap &connection, const QDBusObjectPath &connection\_path)](#SaveSecrets)

## Detailed Description {#details}

If an agent provides secrets to [NetworkManager](networkmanager.md) as part of connection creation, and the some of those secrets are "agent owned" the agent should store those secrets itself and should not expect its [SaveSecrets](networkmanager-secretagent.md#SaveSecrets)() method to be called. [SaveSecrets](networkmanager-secretagent.md#SaveSecrets)() will be called eg if some program other than the agent itself (like a connection editor) changes the secrets out of band.

## Member Type Documentation {#member-type-documentation}

### enum SecretAgent::Capability {#Capability-enum}

**flags SecretAgent::Capabilities**

Capabilities to pass to secret agents

| Constant | Value | Description |
| --- | --- | --- |
| `NetworkManager::SecretAgent::NoCapability` | `0` | No capability |
| `NetworkManager::SecretAgent::VpnHints` | `0x01` | Pass hints to secret agent |

The `Capabilities` type is a typedef for `QFlags<Capability>. `It stores an OR combination of `Capability` values.

### enum SecretAgent::Error {#Error-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::SecretAgent::NotAuthorized` | `0` |
| `NetworkManager::SecretAgent::InvalidConnection` | `1` |
| `NetworkManager::SecretAgent::UserCanceled` | `2` |
| `NetworkManager::SecretAgent::AgentCanceled` | `3` |
| `NetworkManager::SecretAgent::InternalError` | `4` |
| `NetworkManager::SecretAgent::NoSecrets` | `5` |

### enum SecretAgent::GetSecretsFlag {#GetSecretsFlag-enum}

**flags SecretAgent::GetSecretsFlags**

Flags modifying the behavior of [GetSecrets](networkmanager-secretagent.md#GetSecrets) request.

| Constant | Value | Description |
| --- | --- | --- |
| `NetworkManager::SecretAgent::None` | `0` | No special behavior; by default no user interaction is allowed and requests for secrets are fulfilled from persistent storage, or if no secrets are available an error is returned. |
| `NetworkManager::SecretAgent::AllowInteraction` | `0x01` | Allows the request to interact with the user, possibly prompting via UI for secrets if any are required, or if none are found in persistent storage. |
| `NetworkManager::SecretAgent::RequestNew` | `0x02` | Explicitly prompt for new secrets from the user. This flag signals that [NetworkManager](networkmanager.md) thinks any existing secrets are invalid or wrong. This flag implies that interaction is allowed. |
| `NetworkManager::SecretAgent::UserRequested` | `0x04` | Set if the request was initiated by user-requested action via the D-Bus interface, as opposed to automatically initiated by [NetworkManager](networkmanager.md) in response to (for example) scan results or carrier changes. |

The `GetSecretsFlags` type is a typedef for `QFlags<GetSecretsFlag>. `It stores an OR combination of `GetSecretsFlag` values.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] SecretAgent::SecretAgent(const QString &*id*, QObject \**parent* = nullptr) {#SecretAgent}

Registers a [SecretAgent](networkmanager-secretagent.md) with the `id` on [NetworkManager](networkmanager.md) Optionally add a capabilities argument

### \[explicit\] SecretAgent::SecretAgent(const QString &*id*, NetworkManager::SecretAgent::Capabilities *capabilities*, QObject \**parent* = nullptr) {#SecretAgent-1}

### \[pure virtual slot\] void SecretAgent::CancelGetSecrets(const QDBusObjectPath &*connection\_path*, const QString &*setting\_name*) {#CancelGetSecrets}

Called when the subclass should cancel an outstanding request to get secrets for a given connection. Cancelling the request MUST [sendError](networkmanager-secretagent.md#sendError)() with the original DBus message using [AgentCanceled](networkmanager-secretagent.md#Error-enum) param as the error type.

`connection_path` Object path of the connection for which, if secrets for the given 'setting\_name' are being requested, the request should be canceled.

`setting_name` Setting name for which secrets for this connection were originally being requested.

### \[pure virtual slot\] void SecretAgent::DeleteSecrets(const NMVariantMapMap &*connection*, const QDBusObjectPath &*connection\_path*) {#DeleteSecrets}

Called when the subclass should delete the secrets contained in the connection from backing storage.

`connection` Nested settings maps containing the connection properties (sans secrets), for which the agent should delete the secrets from backing storage.

`connection_path` Object path of the connection for which the agent should delete secrets from backing storage.

### \[pure virtual slot\] NMVariantMapMap SecretAgent::GetSecrets(const NMVariantMapMap &*connection*, const QDBusObjectPath &*connection\_path*, const QString &*setting\_name*, const QStringList &*hints*, uint *flags*) {#GetSecrets}

Called when the subclass should retrieve and return secrets. If the request is canceled, called function should call [sendError](networkmanager-secretagent.md#sendError)(), in this case the return value is ignored.

`connection` Nested settings maps containing the connection for which secrets are being requested. This may contain system-owned secrets if the agent has successfully authenticated to modify system network settings and the GetSecrets request flags allow user interaction.

`connection_path` Object path of the connection for which secrets are being requested.

`setting_name` Setting name for which secrets are being requested.

`hints` Array of strings of key names in the requested setting for which [NetworkManager](networkmanager.md) thinks a secrets may be required, and/or well-known identifiers and data that may be useful to the client in processing the secrets request. Note that it's not always possible to determine which secret is required, so in some cases no hints may be given. The Agent should return any secrets it has, or that it thinks are required, regardless of what hints [NetworkManager](networkmanager.md) sends in this request.

`flags` Flags which modify the behavior of the secrets request (see [GetSecretsFlag](networkmanager-secretagent.md#GetSecretsFlag-enum))

### \[pure virtual slot\] void SecretAgent::SaveSecrets(const NMVariantMapMap &*connection*, const QDBusObjectPath &*connection\_path*) {#SaveSecrets}

Called when the subclass should save the secrets contained in the connection to backing storage.

`connection` Nested settings maps containing the connection for which secrets are being saved. This may contain system-owned secrets if the agent has successfully authenticated to modify system network settings and the [GetSecrets](networkmanager-secretagent.md#GetSecrets) request flags allow user interaction.

`connection_path` Object path of the connection for which the agent should save secrets to backing storage.

### void SecretAgent::sendError(NetworkManager::SecretAgent::Error *error*, const QString &*explanation*, const QDBusMessage &*callMessage* = QDBusMessage()) const {#sendError}

Send to [NetworkManager](networkmanager.md) the `error` the subclass has found, the `explanation` is useful for debugging purposes, and the `callMessage` is ONLY needed if [setDelayedReply](https://doc.qt.io/qt-6/qdbuscontext.html#setDelayedReply)() was set to `true` when the method was called.
