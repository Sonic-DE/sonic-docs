---
title: "BluezQt::Request Class"
description: "D-Bus request."
---

# BluezQt::Request Class

D-Bus request. [More...](#details)

- **Header:** `#include <BluezQt/Request>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`

[List of all members, including inherited members](bluezqt-request-members.md)

## Public Functions

- [Request()](#Request)
- [Request(const BluezQt::Request\<T\> &other)](#Request-1)
- [void accept(T returnValue) const](#accept)
- [void cancel() const](#cancel)
- [void reject() const](#reject)
- [BluezQt::Request\<T\> &Request::operator=(const BluezQt::Request\<T\> &other)](#operator-eq)

## Detailed Description {#details}

This class represents a request from a Bluetooth daemon. It is a convenient wrapper around QDBusMessage and easily allows sending replies and handling errors.

*See also* [Agent](bluezqt-agent.md), [ObexAgent](bluezqt-obexagent.md), [Profile](bluezqt-profile.md)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Request::Request() {#Request}

Creates a new Request object.

### Request::Request(const BluezQt::Request\<T\> &*other*) {#Request-1}

Constructs a new Request object from `other`.

### void Request::accept(T *returnValue*) const {#accept}

Accepts the request.

This method should be called to send a reply to indicate the request was accepted.

In case the request is of type void, this method does not take any parameter.

`returnValue` The return value of the request.

### void Request::cancel() const {#cancel}

Cancels the request.

This method should be called to send an error reply to indicate the request was canceled.

### void Request::reject() const {#reject}

Rejects the request.

This method should be called to send an error reply to indicate the request was rejected.

### BluezQt::Request\<T\> &Request::operator=(const BluezQt::Request\<T\> &*other*) {#operator-eq}

Copies the Request object from `other`.
