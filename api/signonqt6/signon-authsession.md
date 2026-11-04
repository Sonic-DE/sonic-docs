---
title: "SignOn::AuthSession Class"
description: "Represents a session to authentication plugin/server."
---

# SignOn::AuthSession Class

Represents a session to authentication plugin/server. [More...](#details)

- **Header:** `#include <SignOn/AuthSession>`
- **CMake:** `find_package(SignOnQt6 REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE SignOnQt6::SignOnQt6)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](signon-authsession-members.md)  
[Deprecated members](signon-authsession-obsolete.md)

## Public Types

- [enum AuthSession::AuthSessionState](#AuthSessionState-enum)

## Public Functions

- [void cancel()](#cancel)
- [void challenge(const SignOn::SessionData &sessionData, const QString &mechanism = QString())](#challenge)
- [const QString name() const](#name)
- [void process(const SignOn::SessionData &sessionData, const QString &mechanism = QString())](#process)
- [void queryAvailableMechanisms(const QStringList &wantedMechanisms = QStringList())](#queryAvailableMechanisms)
- [void request(const SignOn::SessionData &sessionData, const QString &mechanism = QString())](#request)

## Signals

- [void error(const SignOn::Error &err)](#error)
- [void mechanismsAvailable(const QStringList &mechanisms)](#mechanismsAvailable)
- [void response(const SignOn::SessionData &sessionData)](#response)
- [void stateChanged(SignOn::AuthSession::AuthSessionState state, const QString &message)](#stateChanged)

## Detailed Description {#details}

[AuthSession](signon-authsession.md) is used to maintain connection to authentication plugin.

## Member Type Documentation {#member-type-documentation}

### enum AuthSession::AuthSessionState {#AuthSessionState-enum}

Codes for the states of the [AuthSession](signon-authsession.md) object.

| Constant | Value | Description |
| --- | --- | --- |
| `SignOn::AuthSession::SessionNotStarted` | `0` | No message. |
| `SignOn::AuthSession::HostResolving` | `1` | Resolving remote server host name. |
| `SignOn::AuthSession::ServerConnecting` | `2` | Connecting to remote server. |
| `SignOn::AuthSession::DataSending` | `3` | Sending data to remote server. |
| `SignOn::AuthSession::ReplyWaiting` | `4` | Waiting reply from remote server. |
| `SignOn::AuthSession::UserPending` | `5` | Waiting response from user. |
| `SignOn::AuthSession::UiRefreshing` | `6` | Refreshing ui request. |
| `SignOn::AuthSession::ProcessPending` | `7` | Waiting another process to start. |
| `SignOn::AuthSession::SessionStarted` | `8` | Authentication session is started. |
| `SignOn::AuthSession::ProcessCanceling` | `9` | Canceling current process. |
| `SignOn::AuthSession::ProcessDone` | `10` | Authentication completed. |
| `SignOn::AuthSession::CustomState` | `11` | Custom message. |

*See also* [stateChanged](signon-authsession.md#stateChanged)()

## Member Function Documentation {#member-function-documentation}

### void AuthSession::cancel() {#cancel}

Cancels the ongoing challenge. Signal [error](signon-authsession.md#error)() is emitted with [Error::type](signon-error.md#type)() [Error::SessionCanceled](signon-error.md#ErrorType-enum) when process is canceled. If there is no challenge to cancel, [Error::type](signon-error.md#type)() is [Error::WrongState](signon-error.md#ErrorType-enum). If the operation fails, the [error](signon-authsession.md#error)() signal is emitted.

*See also* [error](signon-authsession.md#error)()

### void AuthSession::challenge(const SignOn::SessionData &*sessionData*, const QString &*mechanism* = QString()) {#challenge}

Sends a challenge to the authentication service, with `sessionData`, the information for the authentication session, using the authentication `mechanism`. The service processes the challenge and generates a response token that is emitted with [response](signon-authsession.md#response)() signal. If the operation fails, the [error](signon-authsession.md#error)() signal is emitted.

This is actually a call to [process](signon-authsession.md#process)().

*See also* [process](signon-authsession.md#process)(), [response](signon-authsession.md#response)(), [error](signon-authsession.md#error)()

### \[signal\] void AuthSession::error(const SignOn::Error &*err*) {#error}

Emitted when an error occurs while performing an operation; `err` is the error. Typical error types are generic errors, where [Error::type](signon-error.md#type)() \< [Error::AuthServiceErr](signon-error.md#ErrorType-enum) and [AuthSession](signon-authsession.md) specific, where [Error::AuthSessionErr](signon-error.md#ErrorType-enum) \< [Error::type](signon-error.md#type)() \< [Error::UserErr](signon-error.md#ErrorType-enum)

*See also* [SignOn::Error](signon-error.md), [SignOn::Error::ErrorType](signon-error.md#ErrorType-enum)

### \[signal\] void AuthSession::mechanismsAvailable(const QStringList &*mechanisms*) {#mechanismsAvailable}

Emitted when the list of available `mechanisms` have been obtained for identity.

### const QString AuthSession::name() const {#name}

Returns the name of the authentication method of the session.

### void AuthSession::process(const SignOn::SessionData &*sessionData*, const QString &*mechanism* = QString()) {#process}

Processes `sessionData`, the information for the authentication session, in the authentication service, using the authentication `mechanism`. The service processes the data and generates a response that is emitted with [response](signon-authsession.md#response)() signal. If the operation fails, the [error](signon-authsession.md#error)() signal is emitted.

The format and interpretation of the data is mechanism-specific. The client usually obtains the data from a network protocol, such as the protocols using SASL. In case the mechanism implies generation of the authentication token without a challenge, this method should be called with an empty parameters.

Parameters are key value pairs, and they are given for authentication plugin. For example it can contain server name, realm, client key, etc. If the Identity objected that created this [AuthSession](signon-authsession.md) object was itself created using a [IdentityInfo](signon-identityinfo.md) object having the username and secret set, that data is going to be added to the params map before it is passed to a specific authentication plugin implementation. If credentials have been stored with [Identity::storeCredentials](signon-identity.md#storeCredentials), then the username is overriden from database. Stored secret is used as a default value.

*See also* [response](signon-authsession.md#response)(), [error](signon-authsession.md#error)(), [IdentityInfo](signon-identityinfo.md), AuthPluginInterface

### void AuthSession::queryAvailableMechanisms(const QStringList &*wantedMechanisms* = QStringList()) {#queryAvailableMechanisms}

Query list of available mechanisms. If `wantedMechanisms`, the list of mechanisms that the client would like to use, is provided, only mechanisms available on that list are reported. List is returned by emitting signal [mechanismsAvailable](signon-authsession.md#mechanismsAvailable)(). If the operation fails, the [error](signon-authsession.md#error)() signal is emitted.

*See also* [mechanismsAvailable](signon-authsession.md#mechanismsAvailable)(), [error](signon-authsession.md#error)()

### void AuthSession::request(const SignOn::SessionData &*sessionData*, const QString &*mechanism* = QString()) {#request}

Sends a request to the authentication service, with `sessionData`, the information for the authentication session, using the authentication `mechanism`. The service processes the request and generates a response token that is emitted with [response](signon-authsession.md#response)() signal. If the operation fails, the [error](signon-authsession.md#error)() signal is emitted.

This is actually a call to [process](signon-authsession.md#process)().

*See also* [process](signon-authsession.md#process)(), [response](signon-authsession.md#response)(), [error](signon-authsession.md#error)()

### \[signal\] void AuthSession::response(const SignOn::SessionData &*sessionData*) {#response}

Authentication response generated by the authentication service. It is sent after a [process](signon-authsession.md#process)() call sends a challenge token for authentication is used to request an authentication token, with the response token and accompanying non-opaque information produced by the service.

`sessionData` holds the parameters with the authentication token.

The format and interpretation of the response, as well as names and types of the information parameters, are mechanism-specific.

### \[signal\] void AuthSession::stateChanged(SignOn::AuthSession::AuthSessionState *state*, const QString &*message*) {#stateChanged}

Provides the information about the `state` of the authentication request, with `message`, a textual description of the state.
