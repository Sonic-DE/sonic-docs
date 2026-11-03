---
title: "BluezQt::Job Class"
description: "Async job."
---

# BluezQt::Job Class

Async job. [More...](#details)

- **Header:** `#include <BluezQt/Job>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)
- **Inherited By:** [BluezQt::InitManagerJob](bluezqt-initmanagerjob.md) and [BluezQt::InitObexManagerJob](bluezqt-initobexmanagerjob.md)

[List of all members, including inherited members](bluezqt-job-members.md)

## Public Types

- [enum Job::Error](#Error-enum)

## Properties

- [\[read-only\] error : int](#error-prop)
- [\[read-only\] errorText : QString](#errorText-prop)
- [\[read-only\] finished : bool](#finished-prop)
- [\[read-only\] running : bool](#running-prop)

## Public Functions

- [Job(QObject \*parent = nullptr)](#Job)
- [int error() const](#error)
- [QString errorText() const](#errorText)
- [bool exec()](#exec)
- [bool isFinished() const](#isFinished)
- [bool isRunning() const](#isRunning)

## Public Slots

- [void doStart()](#doStart)
- [void kill()](#kill)
- [void start()](#start)

## Protected Functions

- [void doEmitResult()](#doEmitResult)
- [void emitResult()](#emitResult)
- [void setError(int errorCode)](#setError)
- [void setErrorText(const QString &errorText)](#setErrorText)

## Detailed Description {#details}

This class represents an asynchronous job performed by [BluezQt](bluezqt-module.md), it is usually not used directly but instead it is inherit by some other class.

There are two ways of using this class, one is via [exec](bluezqt-job.md#exec)() which will block the thread until a result is fetched, the other is via connecting to the signal result()

Please, think twice before using [exec](bluezqt-job.md#exec)(), it should be used only in either unittest or cli apps.

> **Note:** Job and its subclasses are meant to be used in a fire-and-forget way. Jobs will delete themselves when they finish using [deleteLater](https://doc.qt.io/qt-6/qobject.html#deleteLater)().

> **Note:** Even given their asynchronous nature, Jobs are still executed in the main thread, so any blocking code executed in it will block the app calling it.

*See also* [InitManagerJob](bluezqt-initmanagerjob.md), [InitObexManagerJob](bluezqt-initobexmanagerjob.md)

## Member Type Documentation {#member-type-documentation}

### enum Job::Error {#Error-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `BluezQt::Job::NoError` | `0` | Indicates there is no error. |
| `BluezQt::Job::UserDefinedError` | `100` | Subclasses should define error codes starting at this value. |

*See also* [error](bluezqt-job.md#error)()

## Property Documentation {#property-documentation}

### \[read-only\] error : int {#error-prop}

**Access functions:**

- `int` **[error](bluezqt-job.md#error)**() const

### \[read-only\] errorText : QString {#errorText-prop}

**Access functions:**

- `QString` **[errorText](bluezqt-job.md#errorText)**() const

### \[read-only\] finished : bool {#finished-prop}

**Access functions:**

- `bool` **[isFinished](bluezqt-job.md#isFinished)**() const

### \[read-only\] running : bool {#running-prop}

**Access functions:**

- `bool` **[isRunning](bluezqt-job.md#isRunning)**() const

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Job::Job(QObject \**parent* = nullptr) {#Job}

Creates a new Job object as a child of `parent`.

### \[pure virtual protected\] void Job::doEmitResult() {#doEmitResult}

Implementation for emitting the result signal.

This function is needed to be able to emit result() signal with the job pointer's type being subclass.

### \[pure virtual protected slot\] void Job::doStart() {#doStart}

Implementation for [start](bluezqt-job.md#start)() that will be executed in next loop

This slot is always called in the next loop, triggered by [start](bluezqt-job.md#start)().

When implementing this method is important to remember that jobs are not executed on a different thread (unless done that way), so any blocking task has to be done in a different thread or process.

### \[protected\] void Job::emitResult() {#emitResult}

Utility function to emit the result signal, and remove this job.

> **Note:** Deletes this job using [deleteLater](https://doc.qt.io/qt-6/qobject.html#deleteLater)().

*See also* result()

### int Job::error() const {#error}

Returns the error code for this job if there has been an error.

Make sure to call this once result() has been emitted.

> **Note:** Getter function for property [error](bluezqt-job.md#error-prop).

*See also* [setError](bluezqt-job.md#setError)()

### QString Job::errorText() const {#errorText}

Returns the error text if there has been an error.

Only call if error is not 0.

This is usually some extra data associated with the error, such as a URL. Use errorString() to get a human-readable, translated message.

> **Note:** Getter function for property [errorText](bluezqt-job.md#errorText-prop).

*See also* [setErrorText](bluezqt-job.md#setErrorText)()

### bool Job::exec() {#exec}

Executes the job synchronously.

This will start a nested [QEventLoop](https://doc.qt.io/qt-6/qeventloop.html) internally. Nested event loop can be dangerous and can have unintended side effects, you should avoid calling exec() whenever you can and use the asynchronous interface of Job instead.

Should you indeed call this method, you need to make sure that all callers are reentrant, so that events delivered by the inner event loop don't cause non-reentrant functions to be called, which usually wreaks havoc.

Note that the event loop started by this method does not process user input events, which means your user interface will effectively be blocked. Other events like paint or network events are still being processed. The advantage of not processing user input events is that the chance of accidental reentrancy is greatly reduced. Still you should avoid calling this function.

> **Warning:** This method blocks until the job finishes!

Returns `true` if the job has been executed without error, `false` otherwise.

### bool Job::isFinished() const {#isFinished}

Returns whether the job has already finished.

> **Note:** Getter function for property [finished](bluezqt-job.md#finished-prop).

### bool Job::isRunning() const {#isRunning}

Returns whether the job is currently running.

> **Note:** Getter function for property [running](bluezqt-job.md#running-prop).

### \[slot\] void Job::kill() {#kill}

Kills the job.

This method will kill the job and then call [deleteLater](https://doc.qt.io/qt-6/qobject.html#deleteLater)(). Only jobs started with [start](bluezqt-job.md#start)() can be killed.

It will not emit the result signal.

### \[protected\] void Job::setError(int *errorCode*) {#setError}

Sets the `errorCode`.

It should be called when an error is encountered in the job, just before calling [emitResult](bluezqt-job.md#emitResult)().

You should define an enum of error codes, with values starting at [Job::UserDefinedError](bluezqt-job.md#Error-enum), and use those. For example:

```cpp
enum ExampleErrors{
  InvalidFoo = UserDefinedError,
  BarNotFound
};
```

*See also* [error](bluezqt-job.md#error)(), [emitResult](bluezqt-job.md#emitResult)()

### \[protected\] void Job::setErrorText(const QString &*errorText*) {#setErrorText}

Sets the `errorText`.

It should be called when an error is encountered in the job, just before calling [emitResult](bluezqt-job.md#emitResult)().

Provides extra information about the error that cannot be determined directly from the error code. For example, a URL or filename. This string is not normally translatable.

*See also* [errorText](bluezqt-job.md#errorText)(), [emitResult](bluezqt-job.md#emitResult)(), [setError](bluezqt-job.md#setError)()

### \[slot\] void Job::start() {#start}

Starts the job asynchronously.

This method will schedule [doStart](bluezqt-job.md#doStart)() to be executed in the next loop. This is done so this method returns as soon as possible.

When the job is finished, result() is emitted.
