---
title: "ModemManager::ModemOma Class"
description: "The ModemManager Open Mobile Alliance interface."
---

# ModemManager::ModemOma Class

The [ModemManager](modemmanager.md) Open Mobile Alliance interface. [More...](#details)

- **Header:** `#include <ModemManagerQt/ModemOma>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`
- **Inherits:** [ModemManager::Interface](modemmanager-interface.md)

[List of all members, including inherited members](modemmanager-modemoma-members.md)

## Public Types

- [ModemOma::List](#List-typedef)
- [ModemOma::Ptr](#Ptr-typedef)

## Public Functions

- [ModemOma(const QString &path, QObject \*parent = nullptr)](#ModemOma)
- [QDBusPendingReply\<void\> acceptNetworkInitiatedSession(uint sessionId, bool accept)](#acceptNetworkInitiatedSession)
- [QDBusPendingReply\<void\> cancelSession()](#cancelSession)
- [ModemManager::ModemOma::Features features() const](#features)
- [ModemManager::OmaSessionTypes pendingNetworkInitiatedSessions() const](#pendingNetworkInitiatedSessions)
- [MMOmaSessionState sessionState() const](#sessionState)
- [MMOmaSessionType sessionType() const](#sessionType)
- [void setTimeout(int timeout)](#setTimeout)
- [QDBusPendingReply\<void\> setup(ModemManager::ModemOma::Features features)](#setup)
- [QDBusPendingReply\<void\> startClientInitiatedSession(MMOmaSessionType sessionType)](#startClientInitiatedSession)
- [int timeout() const](#timeout)

## Signals

- [void featuresChanged(QFlags\<MMOmaFeature\> features)](#featuresChanged)
- [void pendingNetworkInitiatedSessionsChanged(const ModemManager::OmaSessionTypes &sessions)](#pendingNetworkInitiatedSessionsChanged)
- [void sessionStateChanged(MMOmaSessionState oldState, MMOmaSessionState newState, MMOmaSessionStateFailedReason failedReason)](#sessionStateChanged)
- [void sessionTypeChanged(MMOmaSessionType sessionType)](#sessionTypeChanged)

## Detailed Description {#details}

This interface allows clients to handle device management operations as specified by the Open Mobile Alliance (OMA).

Device management sessions are either on-demand (client-initiated), or automatically initiated by either the device itself or the network.

## Member Type Documentation {#member-type-documentation}

### ModemOma::List {#List-typedef}

### ModemOma::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ModemOma::ModemOma(const QString &*path*, QObject \**parent* = nullptr) {#ModemOma}

### QDBusPendingReply\<void\> ModemOma::acceptNetworkInitiatedSession(uint *sessionId*, bool *accept*) {#acceptNetworkInitiatedSession}

Accepts or rejects a network-initiated device management session.

`sessionId` unique ID of the network-initiated device management session

`accept` boolean specifying whether the session is accepted or rejected

### QDBusPendingReply\<void\> ModemOma::cancelSession() {#cancelSession}

Cancels the current on-going device management session.

### ModemManager::ModemOma::Features ModemOma::features() const {#features}

Returns MMOmaFeature flags, specifying which device management features are enabled or disabled

### \[signal\] void ModemOma::featuresChanged(QFlags\<MMOmaFeature\> *features*) {#featuresChanged}

### ModemManager::OmaSessionTypes ModemOma::pendingNetworkInitiatedSessions() const {#pendingNetworkInitiatedSessions}

Returns list of network-initiated sessions which are waiting to be accepted or rejected, where:

`the` first integer is a MMOmaSessionType

`the` second integer is the unique session ID.

### \[signal\] void ModemOma::pendingNetworkInitiatedSessionsChanged(const ModemManager::OmaSessionTypes &*sessions*) {#pendingNetworkInitiatedSessionsChanged}

### MMOmaSessionState ModemOma::sessionState() const {#sessionState}

Returns state of the current on-going device management session, given as a MMOmaSessionState

### \[signal\] void ModemOma::sessionStateChanged(MMOmaSessionState *oldState*, MMOmaSessionState *newState*, MMOmaSessionStateFailedReason *failedReason*) {#sessionStateChanged}

Emitted when the session state changed.

`oldState` previous session state, given as a MMOmaSessionState

`newState` current session state, given as a MMOmaSessionState

`failedReason` reason of failure, given as a MMOmaSessionStateFailedReason, if [sessionState](modemmanager-modemoma.md#sessionState)() is MM\_OMA\_SESSION\_STATE\_FAILED

### MMOmaSessionType ModemOma::sessionType() const {#sessionType}

Returns type of the current on-going device management session, given as a MMOmaSessionType

### \[signal\] void ModemOma::sessionTypeChanged(MMOmaSessionType *sessionType*) {#sessionTypeChanged}

### void ModemOma::setTimeout(int *timeout*) {#setTimeout}

Sets the timeout in milliseconds for all async method DBus calls. -1 means the default DBus timeout (usually 25 seconds).

*See also* [timeout](modemmanager-modemoma.md#timeout)()

### QDBusPendingReply\<void\> ModemOma::setup(ModemManager::ModemOma::Features *features*) {#setup}

Configures which OMA device management features should be enabled.

`features` MMModemOmaFeature flags, specifying which device management features should get enabled or disabled. MM\_OMA\_FEATURE\_NONE will disable all features.

### QDBusPendingReply\<void\> ModemOma::startClientInitiatedSession(MMOmaSessionType *sessionType*) {#startClientInitiatedSession}

Starts a client-initiated device management session.

`sessionType` type of client-initiated device management session,given as a MMOmaSessionType

### int ModemOma::timeout() const {#timeout}

Returns the current value of the DBus timeout in milliseconds. -1 means the default DBus timeout (usually 25 seconds).

*See also* [setTimeout](modemmanager-modemoma.md#setTimeout)()
