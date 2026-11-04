---
title: "SignOn::AbstractKeyAuthorizer Class"
description: "Object holding the keys to the secure storage."
---

# SignOn::AbstractKeyAuthorizer Class

Object holding the keys to the secure storage. [More...](#details)

- **Header:** `#include <SignOn/AbstractKeyAuthorizer>`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](signon-abstractkeyauthorizer-members.md)

## Public Types

- [enum AbstractKeyAuthorizer::Reasons](#Reasons-enum)
- [enum AbstractKeyAuthorizer::Result](#Result-enum)

## Public Functions

- [AbstractKeyAuthorizer(SignOn::KeyHandler \*keyHandler, QObject \*parent = 0)](#AbstractKeyAuthorizer)
- [~AbstractKeyAuthorizer()](#dtor.AbstractKeyAuthorizer)
- [SignOn::KeyHandler \*keyHandler() const](#keyHandler)
- [void queryKeyAuthorization(const SignOn::Key &key, SignOn::AbstractKeyAuthorizer::Reason reason)](#queryKeyAuthorization)

## Signals

- [void keyAuthorizationQueried(const SignOn::Key key, int result)](#keyAuthorizationQueried)

## Detailed Description {#details}

The [AbstractKeyAuthorizer](signon-abstractkeyauthorizer.md) is where all keys to the secure storage are held. It provides signals to notify when keys are inserted, authorized, removed, disabled, as well as methods to authorize and unauthorize keys.

## Member Type Documentation {#member-type-documentation}

### enum AbstractKeyAuthorizer::Reasons {#Reasons-enum}

**flags AbstractKeyAuthorizer::Reason**

Flags specifying why signond is asking for authorizing a key.

| Constant | Value | Description |
| --- | --- | --- |
| `SignOn::AbstractKeyAuthorizer::SystemStarted` | `1 << 0` | signond has just started. |
| `SignOn::AbstractKeyAuthorizer::KeyInserted` | `1 << 1` | A key was inserted. |
| `SignOn::AbstractKeyAuthorizer::StorageNeeded` | `1 << 2` | The secure storage is needed. |

The `Reason` type is a typedef for `QFlags<Reasons>. `It stores an OR combination of `Reasons` values.

*See also* [queryKeyAuthorization](signon-abstractkeyauthorizer.md#queryKeyAuthorization)()

### enum AbstractKeyAuthorizer::Result {#Result-enum}

The answer to [queryKeyAuthorization](signon-abstractkeyauthorizer.md#queryKeyAuthorization)().

| Constant | Value | Description |
| --- | --- | --- |
| `SignOn::AbstractKeyAuthorizer::Denied` | `0` | Key should not be added to the keyring |
| `SignOn::AbstractKeyAuthorizer::Approved` | `1` | Key can be added to the keyring |
| `SignOn::AbstractKeyAuthorizer::Exclusive` | `2` | Key can be set as the only key in the ring |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] AbstractKeyAuthorizer::AbstractKeyAuthorizer(SignOn::KeyHandler \**keyHandler*, QObject \**parent* = 0) {#AbstractKeyAuthorizer}

Constructor, using `keyHandler`, with the given `parent`.

### \[virtual noexcept\] AbstractKeyAuthorizer::~AbstractKeyAuthorizer() {#dtor.AbstractKeyAuthorizer}

Destructor

### \[signal\] void AbstractKeyAuthorizer::keyAuthorizationQueried(const SignOn::Key *key*, int *result*) {#keyAuthorizationQueried}

Emitted to deliver an asynchronous response to the [queryKeyAuthorization](signon-abstractkeyauthorizer.md#queryKeyAuthorization)() method: `key` is the key whose authorization has been queried, and `result` the result of the query, as specified by the Result enum.

### SignOn::KeyHandler \*AbstractKeyAuthorizer::keyHandler() const {#keyHandler}

Returns the [KeyHandler](signon-keyhandler.md) object.

### \[virtual\] void AbstractKeyAuthorizer::queryKeyAuthorization(const SignOn::Key &*key*, SignOn::AbstractKeyAuthorizer::Reason *reason*) {#queryKeyAuthorization}

This method is called by signond when a decision needs to be taken on whether `key` should be added to the list of keys authorized to access the secure storage; `reason` tells why signond asks. The result is delivered asynchronously through the [keyAuthorizationQueried](signon-abstractkeyauthorizer.md#keyAuthorizationQueried)() signal.

> **Note:** This method doesn't effectively add `key` to the secure storage keyring; it simply asks whether `key` should be authorized or not.

*See also* [keyAuthorizationQueried](signon-abstractkeyauthorizer.md#keyAuthorizationQueried)()
