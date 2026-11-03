---
title: "KNSCore::Transaction Class"
description: "KNewStuff Transaction. This class was introduced in Qt 6.0."
---

# KNSCore::Transaction Class

KNewStuff Transaction. This class was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <Transaction>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NewStuff)`  
  `target_link_libraries(mytarget PRIVATE KF6::NewStuff)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](knscore-transaction-members.md)  
[Deprecated members](knscore-transaction-obsolete.md)

## Public Functions

- [bool isFinished() const](#isFinished)

## Signals

- [void signalEntryEvent(const KNSCore::Entry &entry, KNSCore::Entry::EntryEvent event)](#signalEntryEvent)
- [void signalErrorCode(KNSCore::ErrorCode::ErrorCode errorCode, const QString &message, const QVariant &metadata)](#signalErrorCode)
- [void signalMessage(const QString &message)](#signalMessage)

## Static Public Members

- [KNSCore::Transaction \*adopt(KNSCore::EngineBase \*engine, const KNSCore::Entry &entry)](#adopt)
- [KNSCore::Transaction \*installLatest(KNSCore::EngineBase \*engine, const KNSCore::Entry &entry)](#installLatest) (since 6.9)
- [KNSCore::Transaction \*installLinkId(KNSCore::EngineBase \*engine, const KNSCore::Entry &entry, quint8 linkId)](#installLinkId) (since 6.9)
- [KNSCore::Transaction \*uninstall(KNSCore::EngineBase \*engine, const KNSCore::Entry &entry)](#uninstall)

## Detailed Description {#details}

Exposes different actions that can be done on an entry and means to track them to completion.

To create a Transaction we should call one of the static methods that represent the different actions we can take. These will return the Transaction and we can use it to track mesages, the entries' states and eventually its completion using the `finished` signal.

The Transaction will delete itself once it has finished.

## Member Function Documentation {#member-function-documentation}

### \[static\] KNSCore::Transaction \*Transaction::adopt(KNSCore::EngineBase \**engine*, const KNSCore::Entry &*entry*) {#adopt}

Adopt the `entry` from `engine` using the adoption command.

For more information, see the documentation about AdoptionCommand from the knsrc file.

### \[static, since 6.9\] KNSCore::Transaction \*Transaction::installLatest(KNSCore::EngineBase \**engine*, const KNSCore::Entry &*entry*) {#installLatest}

Performs an install of the latest version on the given `entry` from the `engine`.

The latest version is determined using heuristics. If you want tight control over which offering gets installed you need to use [installLinkId](knscore-transaction.md#installLinkId) and manually figure out the id.

Returns a Transaction object that we can use to track the progress to completion

This function was introduced in Qt 6.9.

### \[static, since 6.9\] KNSCore::Transaction \*Transaction::installLinkId(KNSCore::EngineBase \**engine*, const KNSCore::Entry &*entry*, quint8 *linkId*) {#installLinkId}

Performs an install on the given `entry` from the `engine`.

`linkId` specifies which of the assets we want to see installed.

Returns a Transaction object that we can use to track the progress to completion

This function was introduced in Qt 6.9.

### bool Transaction::isFinished() const {#isFinished}

Returns true as soon as the Transaction is completed as it gets ready to clean itself up

### \[signal\] void Transaction::signalEntryEvent(const KNSCore::Entry &*entry*, KNSCore::Entry::EntryEvent *event*) {#signalEntryEvent}

Informs about how the `entry` has changed

`event` nature of the change

### \[signal\] void Transaction::signalErrorCode(KNSCore::ErrorCode::ErrorCode *errorCode*, const QString &*message*, const QVariant &*metadata*) {#signalErrorCode}

Fires in the case of any critical or serious errors, such as network or API problems.

`errorCode` Represents the specific type of error which has occurred

`message` A human-readable message which can be shown to the end user

`metadata` Any additional data which might be helpful to further work out the details of the error (see KNSCore::Entry::ErrorCode for the metadata details)

*See also* [KNSCore::ErrorCode](knscore-errorcode.md)

### \[signal\] void Transaction::signalMessage(const QString &*message*) {#signalMessage}

Provides the `message` to update our users about how the Transaction progressed

### \[static\] KNSCore::Transaction \*Transaction::uninstall(KNSCore::EngineBase \**engine*, const KNSCore::Entry &*entry*) {#uninstall}

Uninstalls the given `entry` from the `engine`.

It reverses the step done when install() was called. Returns a Transaction object that we can use to track the progress to completion
