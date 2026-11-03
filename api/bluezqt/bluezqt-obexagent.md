---
title: "BluezQt::ObexAgent Class"
description: "Bluetooth OBEX agent."
---

# BluezQt::ObexAgent Class

Bluetooth OBEX agent. [More...](#details)

- **Header:** `#include <BluezQt/ObexAgent>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-obexagent-members.md)

## Public Functions

- [ObexAgent(QObject \*parent = nullptr)](#ObexAgent)
- [void authorizePush(BluezQt::ObexTransferPtr transfer, BluezQt::ObexSessionPtr session, const BluezQt::Request\<QString\> &request)](#authorizePush)
- [void cancel()](#cancel)
- [QDBusObjectPath objectPath() const](#objectPath)
- [void release()](#release)

## Detailed Description {#details}

This class represents a Bluetooth OBEX agent.

The agent is used to authorize an incoming object push requests.

> **Note:** The return value of request will be sent asynchronously with Request class. It is also possible to cancel/reject the request.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ObexAgent::ObexAgent(QObject \**parent* = nullptr) {#ObexAgent}

Creates a new [ObexAgent](bluezqt-obexagent.md) object as a child of `parent`.

### \[virtual\] void ObexAgent::authorizePush(BluezQt::ObexTransferPtr *transfer*, BluezQt::ObexSessionPtr *session*, const BluezQt::Request\<QString\> &*request*) {#authorizePush}

Requests the agent to authorize an incoming object push request.

This method gets called when the Bluetooth daemon needs to accept/reject a Bluetooth object push request.

The return value should be full path where the incoming object will be saved.

The [ObexTransfer::fileName](bluezqt-obextransfer.md#fileName)() contains the default location and name that can be returned.

You can use `session` to get the device and adapter this transfer belongs to.

`transfer` The transfer object.

`session` The transfer session.

`request` The request to be used for sending a reply.

### \[virtual\] void ObexAgent::cancel() {#cancel}

Indicates that the agent request failed before receiving reply.

This method gets called to indicate that the agent request failed before a reply was returned.

It cancels the previous request.

### \[pure virtual\] QDBusObjectPath ObexAgent::objectPath() const {#objectPath}

Returns the D-Bus object path of the agent.

The path where the agent will be registered.

> **Note:** You must provide valid object path!

### \[virtual\] void ObexAgent::release() {#release}

Indicates that the agent was unregistered.

This method gets called when the Bluetooth daemon unregisters the agent.

An agent can use it to do cleanup tasks. There is no need to unregister the agent, because when this method gets called it has already been unregistered.
