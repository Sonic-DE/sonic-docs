---
title: "AuthPluginInterface Class"
description: "Interface definition for authentication plugins."
---

# AuthPluginInterface Class

Interface definition for authentication plugins. [More...](#details)

- **Header:** `#include <SignOn/AuthPluginInterface>`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](authplugininterface-members.md)

## Public Functions

- [AuthPluginInterface(QObject \*parent = 0)](#AuthPluginInterface)
- [~AuthPluginInterface()](#dtor.AuthPluginInterface)
- [void abort()](#abort)
- [void cancel()](#cancel)
- [QStringList mechanisms() const](#mechanisms)
- [void process(const SignOn::SessionData &inData, const QString &mechanism = QString())](#process)
- [QString type() const](#type)

## Public Slots

- [void refresh(const SignOn::UiSessionData &data)](#refresh)
- [void userActionFinished(const SignOn::UiSessionData &data)](#userActionFinished)

## Signals

- [void error(const SignOn::Error &err)](#error)
- [void refreshed(const SignOn::UiSessionData &data)](#refreshed)
- [void result(const SignOn::SessionData &data)](#result)
- [void statusChanged(const AuthPluginState state, const QString &message = QString())](#statusChanged)
- [void store(const SignOn::SessionData &data)](#store)
- [void userActionRequired(const SignOn::UiSessionData &data)](#userActionRequired)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### AuthPluginInterface::AuthPluginInterface(QObject \**parent* = 0) {#AuthPluginInterface}

Creates the plugin with the given `parent`.

### \[virtual noexcept\] AuthPluginInterface::~AuthPluginInterface() {#dtor.AuthPluginInterface}

Destructor

### \[virtual\] void AuthPluginInterface::abort() {#abort}

Requests to abort the process. Process is terminated after this call. Reimplement this in order to execute specific instructions before process is killed.

### \[virtual\] void AuthPluginInterface::cancel() {#cancel}

Requests to cancel the process. Process is terminated after this call. Reimplement this in order to execute specific instructions before the effective cancel occurres.

### \[signal\] void AuthPluginInterface::error(const SignOn::Error &*err*) {#error}

Emitted when authentication process has been completed for given data and resulting in the error `err`.

### \[pure virtual\] QStringList AuthPluginInterface::mechanisms() const {#mechanisms}

Gets the list of supported mechanisms.

### \[pure virtual\] void AuthPluginInterface::process(const SignOn::SessionData &*inData*, const QString &*mechanism* = QString()) {#process}

Process authentication with the input data `inData`, using the authentication `mechanism`. Authentication can be logging to a server, obtain token(s) from a server, calculate response using given challenge, etc. Given session data is used to do authentication and return response. Signal [result](authplugininterface.md#result)() is emitted when authentication is completed, or signal [error](authplugininterface.md#error)() if authentication failed.

*See also* [result](authplugininterface.md#result)(), [error](authplugininterface.md#error)()

### \[virtual slot\] void AuthPluginInterface::refresh(const SignOn::UiSessionData &*data*) {#refresh}

Refreshes the ui session `data`. Signond uses this slot to refresh data in given ui session. Mostly used to refresh a captcha images during the user interaction. Signal [refreshed](authplugininterface.md#refreshed)() or [error](authplugininterface.md#error)() must be emitted when refresh is completed. This must be reimplemented to refresh the captcha image.

> **Note:** Emitting signal [userActionRequired](authplugininterface.md#userActionRequired)() is not allowed before ui session is finished.

*See also* [SignOn::UiSessionData](signon-uisessiondata.md), [refreshed](authplugininterface.md#refreshed)()

### \[signal\] void AuthPluginInterface::refreshed(const SignOn::UiSessionData &*data*) {#refreshed}

Emitted when authentication process has completed refresh request, with the refreshed ui session `data`. Plugin must emit signal refreshed() to response to [refresh](authplugininterface.md#refresh)() call.

*See also* [refresh](authplugininterface.md#refresh)()

### \[signal\] void AuthPluginInterface::result(const SignOn::SessionData &*data*) {#result}

Emitted when authentication process has been completed for given data and there are no errors; `data` is the resulting SessionData, which needs to be returned to the client.

### \[signal\] void AuthPluginInterface::statusChanged(const AuthPluginState *state*, const QString &*message* = QString()) {#statusChanged}

\* Emitted to report status of authentication process to signond for \* informing client application: the plugin process `state`, and an \* optional `message` for the client application. \* \*

*See also* [AuthPluginState](authplugininterface.md#AuthPluginState-enum)

### \[signal\] void AuthPluginInterface::store(const SignOn::SessionData &*data*) {#store}

Emitted when authentication process want to store session data parameters `data` for later use. Stored parameters are added into SessionData in following process calls. This is useful when authentication is using permanent tokens.

> **Note:** This is shared within same identity using same method only. There can be storage size limitation for data that can be stored.

### \[pure virtual\] QString AuthPluginInterface::type() const {#type}

Gets the type of the plugin

### \[virtual slot\] void AuthPluginInterface::userActionFinished(const SignOn::UiSessionData &*data*) {#userActionFinished}

User interaction completed, with the ui session `data` the user completed. Signond uses this slot to notice the end of ui session. This is a response to [userActionRequired](authplugininterface.md#userActionRequired)() signal. This must be reimplemented to get the response from the user interaction.

*See also* [SignOn::UiSessionData](signon-uisessiondata.md), [userActionRequired](authplugininterface.md#userActionRequired)()

### \[signal\] void AuthPluginInterface::userActionRequired(const SignOn::UiSessionData &*data*) {#userActionRequired}

Emitted when authentication process need to interact with user; `data` is the ui session data to be filled within user interaction. Basic use cases are: query password, verify captcha, show url. Can also be used to get username/password for proxy authentication etc. Slot [userActionFinished](authplugininterface.md#userActionFinished)() is called when interaction is completed.

> **Note:** Slot [userActionFinished](authplugininterface.md#userActionFinished)() should be reimplemented to get result.

*See also* [userActionFinished](authplugininterface.md#userActionFinished)(), [SignOn::UiSessionData](signon-uisessiondata.md)

## Related Non-Members {#related-non-members}

### enum AuthPluginState {#AuthPluginState-enum}

Predefined states to be used for progress reporting.

| Constant | Value | Description |
| --- | --- | --- |
| `AuthPluginInterface::PLUGIN_STATE_NONE` | `0` | State unknown. |
| `AuthPluginInterface::PLUGIN_STATE_RESOLVING` | `1` | Resolving remote server host name. |
| `AuthPluginInterface::PLUGIN_STATE_CONNECTING` | `2` | Connecting to remote server. |
| `AuthPluginInterface::PLUGIN_STATE_SENDING` | `3` | Sending data to remote server. |
| `AuthPluginInterface::PLUGIN_STATE_WAITING` | `4` | Waiting for reply from remote server. |
| `AuthPluginInterface::PLUGIN_STATE_PENDING` | `5` | Waiting for response from user. |
| `AuthPluginInterface::PLUGIN_STATE_REFRESHING` | `6` | Refreshing ui request. |
| `AuthPluginInterface::PLUGIN_STATE_CANCELING` | `7` | Canceling current process. |
| `AuthPluginInterface::PLUGIN_STATE_HOLDING` | `8` | Holding long non-expired token. Process should be kept alive. |
| `AuthPluginInterface::PLUGIN_STATE_DONE` | `9` | Process is finished. Process can be terminated. |

## Macro Documentation {#macro-documentation}

### SIGNON\_DECL\_AUTH\_PLUGIN(*pluginclass*) {#SIGNON_DECL_AUTH_PLUGIN}

Declares `pluginclass` as the plugin's [AuthPluginInterface](authplugininterface.md): defines the exported auth\_plugin\_instance() function signond looks for.

### SIGNON\_PLUGIN\_INSTANCE(*pluginclass*) {#SIGNON_PLUGIN_INSTANCE}

Macro to create declarations of SSO authentication plugin: the body of a function that returns the single instance of `pluginclass`.
