---
title: "SignOn::AccessReply Class"
description: "The asynchronous reply to an AccessRequest."
---

# SignOn::AccessReply Class

The asynchronous reply to an [AccessRequest](signon-accessrequest.md). [More...](#details)

- **Header:** `#include <SignOn/AbstractAccessControlManager>`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](signon-accessreply-members.md)

## Public Functions

- [bool isAccepted() const](#isAccepted)
- [const SignOn::AccessRequest &request() const](#request)

## Public Slots

- [void accept()](#accept)
- [void decline()](#decline)

## Signals

- [void finished()](#finished)

## Protected Functions

- [AccessReply(const SignOn::AccessRequest &request, QObject \*parent = 0)](#AccessReply)

## Detailed Description {#details}

*See also* [AbstractAccessControlManager::handleRequest](signon-abstractaccesscontrolmanager.md#handleRequest)()

## Member Function Documentation {#member-function-documentation}

### \[explicit protected\] AccessReply::AccessReply(const SignOn::AccessRequest &*request*, QObject \**parent* = 0) {#AccessReply}

Creates the reply to `request`, with the given `parent`.

### \[protected slot\] void AccessReply::accept() {#accept}

Grants the access and emits [finished](signon-accessreply.md#finished)().

### \[protected slot\] void AccessReply::decline() {#decline}

Denies the access and emits [finished](signon-accessreply.md#finished)().

### \[signal\] void AccessReply::finished() {#finished}

The request was accepted or declined.

### bool AccessReply::isAccepted() const {#isAccepted}

Whether the access was granted.

### const SignOn::AccessRequest &AccessReply::request() const {#request}

The request this reply answers.
