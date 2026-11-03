---
title: "KIO::SslUi Namespace"
description: "UI methods for handling SSL errors."
---

# KIO::SslUi Namespace

UI methods for handling SSL errors. [More...](#details)

- Header: KIO/SslUi
- CMake: find\_package(KF6 REQUIRED COMPONENTS KIO) target\_link\_libraries(mytarget PRIVATE KF6::KIOWidgets)

## Detailed Description {#details}

## Type Documentation {#type-documentation}

### enum SslUi::RulesStorage {#RulesStorage-enum}

Error rule storage behavior

| Constant | Value | Description |
| --- | --- | --- |
| `KIO::SslUi::RecallRules` | `1` | Apply stored certificate rules (typically ignored errors) |
| `KIO::SslUi::StoreRules` | `2` | Make new ignore rules from the user's choice and store them |
| `KIO::SslUi::RecallAndStoreRules` | `3` | Apply stored rules and store new rules |

## Function Documentation {#function-documentation}

### bool SslUi::askIgnoreSslErrors(const KSslErrorUiData &*uiData*, KIO::SslUi::RulesStorage *storedRules* = RecallAndStoreRules) {#askIgnoreSslErrors}

If there are errors while establishing an SSL encrypted connection to a peer, usually due to certificate issues, and since this poses a security issue, we need confirmation from the user about how they wish to proceed.

This function provides a dialog asking the user if they wish to abort the connection or ignore the SSL errors that occurred and continue connecting. And in case of the latter whether to remember the decision in the future or ignore the error temporarily.

`uiData` the [KSslErrorUiData](../kiocore/ksslerroruidata.md) object constructed from the socket that is trying to establish the encrypted connection

`storedRules` see [RulesStorage](kio-sslui.md#RulesStorage-enum) Enum
