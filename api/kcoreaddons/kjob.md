---
title: "KJob Class"
description: "The base class for all jobs."
---

# KJob Class

The base class for all jobs. [More...](#details)

- **Header:** `#include <KJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)
- **Inherited By:** [KCompositeJob](kcompositejob.md)

[List of all members, including inherited members](kjob-members.md)

## Public Types

- [enum KJob::Capability](#Capability-enum)
- [enum KJob::KillVerbosity](#KillVerbosity-enum)
- [enum KJob::Unit](#Unit-enum)
- [\[anonymous\] enum](#anonymous-kjob-h-307-enum)

## Properties

- [\[read-only\] capabilities : const Capabilities](#capabilities-prop)
- [\[read-only\] error : int](#error-prop)
- [\[read-only\] errorString : QString](#errorString-prop)
- [\[read-only\] errorText : QString](#errorText-prop)
- [\[read-only\] percent : ulong](#percent-prop)

## Public Functions

- [KJob(QObject \*parent = nullptr)](#KJob)
- [KJob::Capabilities capabilities() const](#capabilities)
- [qint64 elapsedTime() const](#elapsedTime) (since 6.8)
- [int error() const](#error)
- [QString errorString() const](#errorString)
- [QString errorText() const](#errorText)
- [bool exec()](#exec)
- [bool isAutoDelete() const](#isAutoDelete)
- [bool isFinishedNotificationHidden() const](#isFinishedNotificationHidden)
- [bool isStartedWithExec() const](#isStartedWithExec)
- [bool isSuspended() const](#isSuspended)
- [unsigned long percent() const](#percent)
- [qulonglong processedAmount(KJob::Unit unit) const](#processedAmount)
- [void setAutoDelete(bool autodelete)](#setAutoDelete)
- [void setFinishedNotificationHidden(bool hide = true)](#setFinishedNotificationHidden)
- [void setUiDelegate(KJobUiDelegate \*delegate)](#setUiDelegate)
- [void start()](#start)
- [qulonglong totalAmount(KJob::Unit unit) const](#totalAmount)
- [KJobUiDelegate \*uiDelegate() const](#uiDelegate)

## Public Slots

- [bool kill(KJob::KillVerbosity verbosity = KJob::Quietly)](#kill)
- [bool resume()](#resume)
- [bool suspend()](#suspend)

## Signals

- [void description(KJob \*job, const QString &title, const QPair\<QString, QString\> &field1 = QPair\<QString, QString\>(), const QPair\<QString, QString\> &field2 = QPair\<QString, QString\>())](#description)
- [void finished(KJob \*job)](#finished)
- [void infoMessage(KJob \*job, const QString &message)](#infoMessage)
- [void percentChanged(KJob \*job, unsigned long percent)](#percentChanged)
- [void processedAmountChanged(KJob \*job, KJob::Unit unit, qulonglong amount)](#processedAmountChanged)
- [void processedSize(KJob \*job, qulonglong size)](#processedSize)
- [void result(KJob \*job)](#result)
- [void resumed(KJob \*job)](#resumed)
- [void speed(KJob \*job, unsigned long speed)](#speed)
- [void suspended(KJob \*job)](#suspended)
- [void totalAmountChanged(KJob \*job, KJob::Unit unit, qulonglong amount)](#totalAmountChanged)
- [void totalSize(KJob \*job, qulonglong size)](#totalSize)
- [void warning(KJob \*job, const QString &message)](#warning)

## Protected Functions

- [bool doKill()](#doKill)
- [bool doResume()](#doResume)
- [bool doSuspend()](#doSuspend)
- [void emitPercent(qulonglong processedAmount, qulonglong totalAmount)](#emitPercent)
- [void emitResult()](#emitResult)
- [void emitSpeed(unsigned long speed)](#emitSpeed)
- [void setCapabilities(KJob::Capabilities capabilities)](#setCapabilities)
- [void setError(int errorCode)](#setError)
- [void setErrorText(const QString &errorText)](#setErrorText)
- [void setPercent(unsigned long percentage)](#setPercent)
- [void setProcessedAmount(KJob::Unit unit, qulonglong amount)](#setProcessedAmount)
- [void setProgressUnit(KJob::Unit unit)](#setProgressUnit)
- [void setTotalAmount(KJob::Unit unit, qulonglong amount)](#setTotalAmount)
- [void startElapsedTimer()](#startElapsedTimer) (since 6.8)

## Detailed Description {#details}

For all jobs created in an application, the code looks like

```cpp
void SomeClass::methodWithAsynchronousJobCall()
{
  KJob *job = someoperation(some parameters);
  connect(job, &KJob::result, this, &SomeClass::handleResult);
  job->start();
}
```

(other connects, specific to the job)

And handleResult is usually at least:

```cpp
void SomeClass::handleResult(KJob *job)
{
  if (job->error()) {
      doSomething();
  }
}
```

With the synchronous interface the code looks like

```cpp
void SomeClass::methodWithSynchronousJobCall()
{
  KJob *job = someoperation( some parameters );
  if (!job->exec()) {
      // An error occurred
  } else {
      // Do something
  }
}
```

Subclasses must implement [start](kjob.md#start)(), which should trigger the execution of the job (although the work should be done asynchronously). [errorString](kjob.md#errorString)() should also be reimplemented by any subclasses that introduce new error codes.

> **Note:** [KJob](kjob.md) and its subclasses are meant to be used in a fire-and-forget way. Jobs will delete themselves when they finish using [deleteLater](https://doc.qt.io/qt-6/qobject.html#deleteLater)() (although this behaviour can be changed), so a job instance will disappear after the next event loop run.

## Member Type Documentation {#member-type-documentation}

### enum KJob::Capability {#Capability-enum}

**flags KJob::Capabilities**

| Constant | Value | Description |
| --- | --- | --- |
| `KJob::NoCapabilities` | `0x0000` | None of the capabilities exist |
| `KJob::Killable` | `0x0001` | The job can be killed |
| `KJob::Suspendable` | `0x0002` | The job can be suspended |

The `Capabilities` type is a typedef for `QFlags<Capability>. `It stores an OR combination of `Capability` values.

### enum KJob::KillVerbosity {#KillVerbosity-enum}

| Constant |   |
| --- | --- |
| `KJob::Quietly` | `0` |
| `KJob::EmitResult` | `1` |

### enum KJob::Unit {#Unit-enum}

Describes the unit used in the methods that handle reporting the job progress info.

| Constant | Value | Description |
| --- | --- | --- |
| `KJob::Bytes` | `0` | Directory and file sizes in bytes |
| `KJob::Files` | `1` | The number of files handled by the job |
| `KJob::Directories` | `2` | The number of directories handled by the job |
| `KJob::Items (since Qt 5.72)` | `3` | The number of items (e.g. both directories and files) handled by the job |
| `KJob::UnitsCount (since Qt 5.87)` | `4` | Used internally only, do not use |

*See also* [totalAmount](kjob.md#totalAmount)

### \[anonymous\] enum {#anonymous-kjob-h-307-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KJob::NoError` | `0` | Indicates there is no error |
| `KJob::KilledJobError` | `1` | Indicates the job was killed |
| `KJob::UserDefinedError` | `100` | Subclasses should define error codes starting at this value |

## Property Documentation {#property-documentation}

### \[read-only\] capabilities : const Capabilities {#capabilities-prop}

**Access functions:**

- `KJob::Capabilities` **[capabilities](kjob.md#capabilities)**() const

### \[read-only\] error : int {#error-prop}

**Access functions:**

- `int` **[error](kjob.md#error)**() const

**Notifier signal:**

- `void` **[result](kjob.md#result)**(`KJob` \**job*)

> **Note:** This is a private signal. It can be used in signal connections but cannot be emitted by the user.

### \[read-only\] errorString : QString {#errorString-prop}

**Access functions:**

- virtual `QString` **[errorString](kjob.md#errorString)**() const

**Notifier signal:**

- `void` **[result](kjob.md#result)**(`KJob` \**job*)

> **Note:** This is a private signal. It can be used in signal connections but cannot be emitted by the user.

### \[read-only\] errorText : QString {#errorText-prop}

**Access functions:**

- `QString` **[errorText](kjob.md#errorText)**() const

**Notifier signal:**

- `void` **[result](kjob.md#result)**(`KJob` \**job*)

> **Note:** This is a private signal. It can be used in signal connections but cannot be emitted by the user.

### \[read-only\] percent : ulong {#percent-prop}

**Access functions:**

- `unsigned` `long` **[percent](kjob.md#percent)**() const

**Notifier signal:**

- `void` **[percentChanged](kjob.md#percentChanged)**(`KJob` \**job*, `unsigned` `long` *percent*)

> **Note:** This is a private signal. It can be used in signal connections but cannot be emitted by the user.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KJob::KJob(QObject \**parent* = nullptr) {#KJob}

Creates a new [KJob](kjob.md) object.

`parent` the parent [QObject](https://doc.qt.io/qt-6/qobject.html)

### KJob::Capabilities KJob::capabilities() const {#capabilities}

Returns the capabilities that this job supports

> **Note:** Getter function for property [capabilities](kjob.md#capabilities-prop).

*See also* [setCapabilities](kjob.md#setCapabilities)()

### \[signal\] void KJob::description(KJob \**job*, const QString &*title*, const QPair\<QString, QString\> &*field1* = QPair\<QString, QString\>(), const QPair\<QString, QString\> &*field2* = QPair\<QString, QString\>()) {#description}

Emitted to display general description of this job. A description has a title and two optional fields which can be used to complete the description.

Examples of titles are "Copying", "Creating resource", etc. The fields of the description can be "Source" with an URL, and, "Destination" with an URL for a "Copying" description.

`job` the job that emitted this signal

`title` the general description of the job

`field1` first field (localized name and value)

`field2` second field (localized name and value)

### \[virtual protected\] bool KJob::doKill() {#doKill}

Aborts this job quietly.

This simply kills the job, no error reporting or job deletion should be involved.

Returns `true` if the operation is supported and succeeded, `false` otherwise

### \[virtual protected\] bool KJob::doResume() {#doResume}

Resumes this job.

Returns `true` if the operation is supported and succeeded, `false` otherwise

### \[virtual protected\] bool KJob::doSuspend() {#doSuspend}

Suspends this job.

Returns `true` if the operation is supported and succeeded, `false` otherwise

### \[since 6.8\] qint64 KJob::elapsedTime() const {#elapsedTime}

The number of milliseconds the job has been running for. Starting from the last [start](kjob.md#start)() call.

Sub-classes must call [startElapsedTimer](kjob.md#startElapsedTimer)() from their [start](kjob.md#start)() implementation, to get elapsedTime() measurement. Otherwise this method will always return 0.

The time when paused is excluded.

This function was introduced in Qt 6.8.

### \[protected\] void KJob::emitPercent(qulonglong *processedAmount*, qulonglong *totalAmount*) {#emitPercent}

Utility function for inherited jobs. Emits the percent signal if bigger than previous value, after calculating it from the parameters.

`processedAmount` the processed amount

`totalAmount` the total amount

*See also* [percent](kjob.md#percent)()

### \[protected\] void KJob::emitResult() {#emitResult}

Utility function to emit the result signal, and end this job. It first notifies the observers to hide the progress for this job using the [finished](kjob.md#finished)() signal.

> **Note:** Deletes this job using [deleteLater](https://doc.qt.io/qt-6/qobject.html#deleteLater)().

*See also* [result](kjob.md#result)(), [finished](kjob.md#finished)()

### \[protected\] void KJob::emitSpeed(unsigned long *speed*) {#emitSpeed}

Utility function for inherited jobs. Emits the speed signal and starts the timer for removing that info

`speed` the speed in bytes/s

### int KJob::error() const {#error}

Returns the error code, if there has been an error.

Only call this method from the slot connected to [result](kjob.md#result)().

Returns the error code for this job, 0 if no error.

> **Note:** Getter function for property [error](kjob.md#error-prop).

*See also* [setError](kjob.md#setError)()

### \[virtual\] QString KJob::errorString() const {#errorString}

A human-readable error message.

This provides a translated, human-readable description of the error. Only call if error is not 0.

Subclasses should implement this to create a translated error message from the error code and error text. For example:

```cpp
if (error() == ReadFailed) {
  i18n("Could not read \"%1\"", errorText());
}
```

Returns a translated error message, providing [error](kjob.md#error)() is not 0

> **Note:** Getter function for property [errorString](kjob.md#errorString-prop).

### QString KJob::errorText() const {#errorText}

Returns the error text if there has been an error.

Only call if error is not 0.

This is usually some extra data associated with the error, such as a URL. Use [errorString](kjob.md#errorString)() to get a human-readable, translated message.

Returns a string to help understand the error

> **Note:** Getter function for property [errorText](kjob.md#errorText-prop).

*See also* [setErrorText](kjob.md#setErrorText)()

### bool KJob::exec() {#exec}

Executes the job synchronously.

This will start a nested [QEventLoop](https://doc.qt.io/qt-6/qeventloop.html) internally. Nested event loop can be dangerous and can have unintended side effects, you should avoid calling exec() whenever you can and use the asynchronous interface of [KJob](kjob.md) instead.

Should you indeed call this method, you need to make sure that all callers are reentrant, so that events delivered by the inner event loop don't cause non-reentrant functions to be called, which usually wreaks havoc.

Note that the event loop started by this method does not process user input events, which means your user interface will effectively be blocked. Other events like paint or network events are still being processed. The advantage of not processing user input events is that the chance of accidental reentrance is greatly reduced. Still you should avoid calling this function.

Returns `true` if the job has been executed without error, `false` otherwise

### \[private signal\] void KJob::finished(KJob \**job*) {#finished}

Emitted when the job is finished, in any case. It is used to notify observers that the job is terminated and that progress can be hidden.

Since 5.75 this signal is guaranteed to be emitted exactly once.

This is a private signal, it can't be emitted directly by subclasses of [KJob](kjob.md), use [emitResult](kjob.md#emitResult)() instead.

In general, to be notified of a job's completion, client code should connect to [result](kjob.md#result)() rather than finished(), so that kill(Quietly) is indeed quiet. However if you store a list of jobs and they might get killed silently, then you must connect to this instead of [result](kjob.md#result)(), to avoid dangling pointers in your list.

`job` the job that emitted this signal

> **Note:** This is a private signal. It can be used in signal connections but cannot be emitted by the user.

*See also* [result](kjob.md#result)

### \[signal\] void KJob::infoMessage(KJob \**job*, const QString &*message*) {#infoMessage}

Emitted to display state information about this job. Examples of message are "Resolving host", "Connecting to host...", etc.

`job` the job that emitted this signal

`message` the info message

### bool KJob::isAutoDelete() const {#isAutoDelete}

Returns whether this job automatically deletes itself once the job is finished.

### bool KJob::isFinishedNotificationHidden() const {#isFinishedNotificationHidden}

Whether to not show a finished notification when a job's finished signal is emitted.

*See also* [setFinishedNotificationHidden](kjob.md#setFinishedNotificationHidden)()

### bool KJob::isStartedWithExec() const {#isStartedWithExec}

Returns `true` if this job was started with [exec](kjob.md#exec)(), which starts a nested event-loop (with [QEventLoop::ExcludeUserInputEvents](https://doc.qt.io/qt-6/qeventloop.html#ProcessEventsFlag-enum), which blocks the GUI), otherwise returns `false` which indicates this job was started asynchronously with [start](kjob.md#start)().

This is useful for code that for example shows a dialog to ask the user a question, and that would be no-op since the user cannot interact with the dialog.

### bool KJob::isSuspended() const {#isSuspended}

Returns if the job was suspended with the [suspend](kjob.md#suspend)() call.

*See also* [suspend](kjob.md#suspend)(), [resume](kjob.md#resume)()

### \[slot\] bool KJob::kill(KJob::KillVerbosity *verbosity* = KJob::Quietly) {#kill}

Aborts this job.

This kills and deletes the job.

`verbosity` if equals to [EmitResult](kjob.md#KillVerbosity-enum), Job will emit signal result and ask uiserver to close the progress window.

`verbosity` is set to [EmitResult](kjob.md#KillVerbosity-enum) for subjobs. Whether applications should call with Quietly or [EmitResult](kjob.md#KillVerbosity-enum) depends on whether they rely on result being emitted or not. Please notice that if `verbosity` is set to Quietly, signal result will NOT be emitted.

Returns `true` if the operation is supported and succeeded, false otherwise

### unsigned long KJob::percent() const {#percent}

Returns the overall progress of this job

> **Note:** Getter function for property [percent](kjob.md#percent-prop).

*See also* [setPercent](kjob.md#setPercent)()

### \[private signal\] void KJob::percentChanged(KJob \**job*, unsigned long *percent*) {#percentChanged}

Progress signal showing the overall progress of the job. This is valid for any kind of job, and allows using a progress bar very easily. (see KProgressBar).

Note that this signal is not emitted for finished jobs.

> **Note:** This is a private signal, it shouldn't be emitted directly by subclasses of [KJob](kjob.md), use [emitPercent](kjob.md#emitPercent)(), [setPercent](kjob.md#setPercent)() [setTotalAmount](kjob.md#setTotalAmount)() or [setProcessedAmount](kjob.md#setProcessedAmount)() instead.

`job` the job that emitted this signal

`percent` the percentage

> **Note:** This is a private signal. It can be used in signal connections but cannot be emitted by the user.

> **Note:** Notifier signal for property [percent](kjob.md#percent-prop).

### qulonglong KJob::processedAmount(KJob::Unit *unit*) const {#processedAmount}

Returns the processed amount of a given unit for this job.

`unit` the unit of the requested amount

*See also* [setProcessedAmount](kjob.md#setProcessedAmount)()

### \[private signal\] void KJob::processedAmountChanged(KJob \**job*, KJob::Unit *unit*, qulonglong *amount*) {#processedAmountChanged}

Regularly emitted to show the progress of this job by giving the current amount. The unit of this amount is sent too. It can be emitted several times if the job manages several different units.

> **Note:** This is a private signal, it shouldn't be emitted directly by subclasses of [KJob](kjob.md), use [setProcessedAmount](kjob.md#setProcessedAmount)() instead.

`job` the job that emitted this signal

`unit` the unit of the processed amount

`amount` the processed amount

> **Note:** This is a private signal. It can be used in signal connections but cannot be emitted by the user.

### \[signal\] void KJob::processedSize(KJob \**job*, qulonglong *size*) {#processedSize}

Regularly emitted to show the progress of this job (current data size in bytes for transfers, entries listed, etc.).

> **Note:** This is a private signal, it shouldn't be emitted directly by subclasses of [KJob](kjob.md), use [setProcessedAmount](kjob.md#setProcessedAmount)() instead.

`job` the job that emitted this signal

`size` the processed size

### \[private signal\] void KJob::result(KJob \**job*) {#result}

Emitted when the job is finished (except when killed with [KJob::Quietly](kjob.md#KillVerbosity-enum)).

Since 5.75 this signal is guaranteed to be emitted at most once.

Use error to know if the job was finished with error.

This is a private signal, it can't be emitted directly by subclasses of [KJob](kjob.md), use [emitResult](kjob.md#emitResult)() instead.

Please connect to this signal instead of finished.

`job` the job that emitted this signal

> **Note:** This is a private signal. It can be used in signal connections but cannot be emitted by the user.

> **Note:** Notifier signal for properties [error](kjob.md#error-prop), [errorString](kjob.md#errorString-prop), and [errorText](kjob.md#errorText-prop).

*See also* [kill](kjob.md#kill)

### \[slot\] bool KJob::resume() {#resume}

Resumes this job.

Returns `true` if the operation is supported and succeeded, `false` otherwise

### \[private signal\] void KJob::resumed(KJob \**job*) {#resumed}

Emitted when the job is resumed.

`job` the job that emitted this signal

> **Note:** This is a private signal. It can be used in signal connections but cannot be emitted by the user.

### void KJob::setAutoDelete(bool *autodelete*) {#setAutoDelete}

Sets the auto-delete property of the job. If `autodelete` is set to `false` the job will not delete itself once it is finished.

The default for any [KJob](kjob.md) is to automatically delete itself, which implies that the job was created on the heap (using new). If the job is created on the stack (which isn't the typical use-case for a job) then you must set auto-delete to `false`, otherwise you could get a crash when the job finishes and tries to delete itself.

> **Note:** If you set auto-delete to `false` then you need to kill the job manually, ideally by calling [kill](kjob.md#kill)().

`autodelete` set to `false` to disable automatic deletion of the job.

*See also* [isAutoDelete](kjob.md#isAutoDelete)()

### \[protected\] void KJob::setCapabilities(KJob::Capabilities *capabilities*) {#setCapabilities}

Sets the capabilities for this job.

`capabilities` are the capabilities supported by this job

*See also* [capabilities](kjob.md#capabilities)()

### \[protected\] void KJob::setError(int *errorCode*) {#setError}

Sets the error code.

It should be called when an error is encountered in the job, just before calling [emitResult](kjob.md#emitResult)().

You should define an (anonymous) enum of error codes, with values starting at [KJob::UserDefinedError](kjob.md#anonymous-kjob-h-307-enum), and use those. For example,

```cpp
enum {
  InvalidFoo = UserDefinedError,
  BarNotFound,
};
```

`errorCode` the error code

*See also* [error](kjob.md#error)(), [emitResult](kjob.md#emitResult)()

### \[protected\] void KJob::setErrorText(const QString &*errorText*) {#setErrorText}

Sets the error text.

It should be called when an error is encountered in the job, just before calling [emitResult](kjob.md#emitResult)().

Provides extra information about the error that cannot be determined directly from the error code. For example, a URL or filename. This string is not normally translatable.

`errorText` the error text

*See also* [errorText](kjob.md#errorText)(), [emitResult](kjob.md#emitResult)(), [errorString](kjob.md#errorString)(), [setError](kjob.md#setError)()

### void KJob::setFinishedNotificationHidden(bool *hide* = true) {#setFinishedNotificationHidden}

This method can be used to indicate to classes listening to signals from a job that they should ideally show a progress bar, but not a finished notification.

For example when opening a remote URL, a job will emit the progress of the download, which can be used to show a progress dialog or a Plasma notification, then when the job is done it'll emit e.g. the finished signal. Showing the user the progress dialog is useful, however the dialog/notification about the download being finished isn't of much interest, because the user can see the application that invoked the job opening the actual file that was downloaded.

*See also* [isFinishedNotificationHidden](kjob.md#isFinishedNotificationHidden)()

### \[protected\] void KJob::setPercent(unsigned long *percentage*) {#setPercent}

Sets the overall progress of the job. The [percent](kjob.md#percent)() signal is emitted if the value changed.

The job takes care of this if you call [setProcessedAmount](kjob.md#setProcessedAmount) in Bytes (or the unit set by [setProgressUnit](kjob.md#setProgressUnit)). This method allows you to set your own progress, as an alternative.

`percentage` the new overall progress

*See also* [percent](kjob.md#percent)()

### \[protected\] void KJob::setProcessedAmount(KJob::Unit *unit*, qulonglong *amount*) {#setProcessedAmount}

Sets the processed size. The [processedAmount](kjob.md#processedAmount)() and [percent](kjob.md#percent)() signals are emitted if the values changed. The [percent](kjob.md#percent)() signal is emitted only for the progress unit.

`unit` the unit of the new processed amount

`amount` the new processed amount

*See also* [processedAmount](kjob.md#processedAmount)()

### \[protected\] void KJob::setProgressUnit(KJob::Unit *unit*) {#setProgressUnit}

Sets the unit that will be used internally to calculate the progress percentage. The default progress unit is Bytes.

### \[protected\] void KJob::setTotalAmount(KJob::Unit *unit*, qulonglong *amount*) {#setTotalAmount}

Sets the total size. The [totalSize](kjob.md#totalSize)() and [percent](kjob.md#percent)() signals are emitted if the values changed. The [percent](kjob.md#percent)() signal is emitted only for the progress unit.

`unit` the unit of the new total amount

`amount` the new total amount

*See also* [totalAmount](kjob.md#totalAmount)()

### void KJob::setUiDelegate(KJobUiDelegate \**delegate*) {#setUiDelegate}

Attach a UI delegate to this job.

If the job had another UI delegate, it's automatically deleted. Once attached to the job, the UI delegate will be deleted with the job.

`delegate` the new UI delegate to use

*See also* [uiDelegate](kjob.md#uiDelegate)(), [KJobUiDelegate](kjobuidelegate.md)

### \[signal\] void KJob::speed(KJob \**job*, unsigned long *speed*) {#speed}

Emitted to display information about the speed of this job.

> **Note:** This is a private signal, it shouldn't be emitted directly by subclasses of [KJob](kjob.md), use [emitSpeed](kjob.md#emitSpeed)() instead.

`job` the job that emitted this signal

`speed` the speed in bytes/s

### \[pure virtual\] void KJob::start() {#start}

Starts the job asynchronously.

When the job is finished, [result](kjob.md#result)() is emitted.

Warning: Never implement any synchronous workload in this method. This method should just trigger the job startup, not do any work itself. It is expected to be non-blocking.

This is the method all subclasses need to implement. It should setup and trigger the workload of the job. It should not do any work itself. This includes all signals and terminating the job, e.g. by [emitResult](kjob.md#emitResult)(). The workload, which could be another method of the subclass, is to be triggered using the event loop, e.g. by code like:

```cpp
void ExampleJob::start()
{
 QTimer::singleShot(0, this, &ExampleJob::doWork);
}
```

### \[protected, since 6.8\] void KJob::startElapsedTimer() {#startElapsedTimer}

Starts the internal elapsed time measurement timer.

Sub-classes must call startElapsedTimer() from their [start](kjob.md#start)() implementation, to get [elapsedTime](kjob.md#elapsedTime)() measurement. Otherwise elapsedTimer() method will always return 0.

This function was introduced in Qt 6.8.

### \[slot\] bool KJob::suspend() {#suspend}

Suspends this job.

The job should be kept in a state in which it is possible to resume it.

Returns `true` if the operation is supported and succeeded, `false` otherwise

### \[private signal\] void KJob::suspended(KJob \**job*) {#suspended}

Emitted when the job is suspended.

This is a private signal, it can't be emitted directly by subclasses of [KJob](kjob.md).

`job` the job that emitted this signal

> **Note:** This is a private signal. It can be used in signal connections but cannot be emitted by the user.

### qulonglong KJob::totalAmount(KJob::Unit *unit*) const {#totalAmount}

Returns the total amount of a given unit for this job.

`unit` the unit of the requested amount

*See also* [setTotalAmount](kjob.md#setTotalAmount)()

### \[private signal\] void KJob::totalAmountChanged(KJob \**job*, KJob::Unit *unit*, qulonglong *amount*) {#totalAmountChanged}

Emitted when we know the amount the job will have to process. The unit of this amount is sent too. It can be emitted several times if the job manages several different units.

> **Note:** This is a private signal, it shouldn't be emitted directly by subclasses of [KJob](kjob.md), use [setTotalAmount](kjob.md#setTotalAmount)() instead.

`job` the job that emitted this signal

`unit` the unit of the total amount

`amount` the total amount

> **Note:** This is a private signal. It can be used in signal connections but cannot be emitted by the user.

### \[signal\] void KJob::totalSize(KJob \**job*, qulonglong *size*) {#totalSize}

Emitted when we know the size of this job (data size in bytes for transfers, number of entries for listings, etc).

> **Note:** This is a private signal, it shouldn't be emitted directly by subclasses of [KJob](kjob.md), use [setTotalAmount](kjob.md#setTotalAmount)() instead.

`job` the job that emitted this signal

`size` the total size

### KJobUiDelegate \*KJob::uiDelegate() const {#uiDelegate}

Returns the delegate attached to this job, or `nullptr` if there's no such delegate

*See also* [setUiDelegate](kjob.md#setUiDelegate)()

### \[signal\] void KJob::warning(KJob \**job*, const QString &*message*) {#warning}

Emitted to display a warning about this job.

`job` the job that emitted this signal

`message` the warning message
