---
title: "BluezQt::Agent Class"
description: "Bluetooth agent."
---

# BluezQt::Agent Class

Bluetooth agent. [More...](#details)

- **Header:** `#include <BluezQt/Agent>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-agent-members.md)

## Public Types

- [enum Agent::Capability](#Capability-enum)

## Properties

- [\[read-only\] capability : Capability](#capability-prop)

## Public Functions

- [Agent(QObject \*parent = nullptr)](#Agent)
- [void authorizeService(BluezQt::DevicePtr device, const QString &uuid, const BluezQt::Request\<\> &request)](#authorizeService)
- [void cancel()](#cancel)
- [BluezQt::Agent::Capability capability() const](#capability)
- [void displayPasskey(BluezQt::DevicePtr device, const QString &passkey, const QString &entered)](#displayPasskey)
- [void displayPinCode(BluezQt::DevicePtr device, const QString &pinCode)](#displayPinCode)
- [QDBusObjectPath objectPath() const](#objectPath)
- [void release()](#release)
- [void requestAuthorization(BluezQt::DevicePtr device, const BluezQt::Request\<\> &request)](#requestAuthorization)
- [void requestConfirmation(BluezQt::DevicePtr device, const QString &passkey, const BluezQt::Request\<\> &request)](#requestConfirmation)
- [void requestPasskey(BluezQt::DevicePtr device, const BluezQt::Request\<quint32\> &request)](#requestPasskey)
- [void requestPinCode(BluezQt::DevicePtr device, const BluezQt::Request\<QString\> &request)](#requestPinCode)

## Detailed Description {#details}

This class represents a Bluetooth agent.

The agent is used in pairing process to do various actions.

> **Note:** The return value of requests will be sent asynchronously with Request class. It is also possible to cancel/reject all requests.

## Member Type Documentation {#member-type-documentation}

### enum Agent::Capability {#Capability-enum}

The input/output capabilities of Agent.

| Constant |   |
| --- | --- |
| `BluezQt::Agent::DisplayOnly` | `0` |
| `BluezQt::Agent::DisplayYesNo` | `1` |
| `BluezQt::Agent::KeyboardOnly` | `2` |
| `BluezQt::Agent::NoInputNoOutput` | `3` |

## Property Documentation {#property-documentation}

### \[read-only\] capability : Capability {#capability-prop}

**Access functions:**

- virtual `BluezQt::Agent::Capability` **[capability](bluezqt-agent.md#capability)**() const

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Agent::Agent(QObject \**parent* = nullptr) {#Agent}

Creates a new Agent object as a child of `parent`.

### \[virtual\] void Agent::authorizeService(BluezQt::DevicePtr *device*, const QString &*uuid*, const BluezQt::Request\<\> &*request*) {#authorizeService}

Requests the agent to authorize a connection/service request.

This method gets called when the Bluetooth daemon needs to authorize a connection/service request.

`device` The device that invoked the action.

`uuid` The UUID of the service.

`request` The request to be used for sending a reply.

### \[virtual\] void Agent::cancel() {#cancel}

Indicate that the agent request failed before receiving reply.

This method gets called to indicate that the agent request failed before a reply was returned.

It cancels the previous request.

### \[virtual\] BluezQt::Agent::Capability Agent::capability() const {#capability}

Returns the input/output capability of the agent.

By default, this method returns [DisplayYesNo](bluezqt-agent.md#Capability-enum).

> **Note:** Getter function for property [capability](bluezqt-agent.md#capability-prop).

### \[virtual\] void Agent::displayPasskey(BluezQt::DevicePtr *device*, const QString &*passkey*, const QString &*entered*) {#displayPasskey}

Requests the agent to display a passkey.

This method gets called when the Bluetooth daemon needs to display a passkey for an authentication.

When the passkey needs no longer to be displayed, the [cancel](bluezqt-agent.md#cancel)() method will be called.

`device` The device that invoked the action.

`passkey` The passkey to be displayed.

`entered` The number of already typed keys on the remote side.

### \[virtual\] void Agent::displayPinCode(BluezQt::DevicePtr *device*, const QString &*pinCode*) {#displayPinCode}

Requests the agent to display a PIN code.

This method gets called when the Bluetooth daemon needs to display a pincode for an authentication.

When the PIN code needs no longer to be displayed, the [cancel](bluezqt-agent.md#cancel)() method will be called.

`device` The device that invoked the action.

`pinCode` The PIN code to be displayed.

### \[pure virtual\] QDBusObjectPath Agent::objectPath() const {#objectPath}

Returns the D-Bus object path where the agent will be registered.

> **Note:** You must provide valid object path!

### \[virtual\] void Agent::release() {#release}

Indicates that the agent was unregistered.

This method gets called when the Bluetooth daemon unregisters the agent.

An agent can use it to do cleanup tasks. There is no need to unregister the agent, because when this method gets called it has already been unregistered.

### \[virtual\] void Agent::requestAuthorization(BluezQt::DevicePtr *device*, const BluezQt::Request\<\> &*request*) {#requestAuthorization}

Requests the agent to authorize an incoming pairing attempt.

This method gets called to request the user to authorize an incoming pairing attempt which would in other circumstances trigger the just-works model.

`device` The device that invoked the action.

`request` The request to be used for sending reply.

### \[virtual\] void Agent::requestConfirmation(BluezQt::DevicePtr *device*, const QString &*passkey*, const BluezQt::Request\<\> &*request*) {#requestConfirmation}

Requests the agent to confirm a passkey.

This method gets called when the Bluetooth daemon needs to confirm a passkey for an authentication.

`device` The device that invoked the action.

`passkey` The passkey to be confirmed.

`request` The request to be used for sending reply.

### \[virtual\] void Agent::requestPasskey(BluezQt::DevicePtr *device*, const BluezQt::Request\<quint32\> &*request*) {#requestPasskey}

Requests a passkey from the agent.

This method gets called when the Bluetooth daemon needs to get the passkey for an authentication.

The return value should be a numeric value between 0-999999.

`device` The device that invoked the action.

`request` The request to be used for sending a reply.

### \[virtual\] void Agent::requestPinCode(BluezQt::DevicePtr *device*, const BluezQt::Request\<QString\> &*request*) {#requestPinCode}

Requests a PIN code from the agent.

This method gets called when the Bluetooth daemon needs to get the PIN code for an authentication.

The return value should be a string of 1-16 characters length. The string can be alphanumeric.

`device` The device that invoked the action.

`request` The request to be used for sending reply.
