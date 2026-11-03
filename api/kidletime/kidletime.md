---
title: "KIdleTime Class"
description: "KIdleTime is a singleton reporting information on idle time."
---

# KIdleTime Class

[KIdleTime](kidletime.md) is a singleton reporting information on idle time. [More...](#details)

- **Header:** `#include <KIdleTime>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS IdleTime)`  
  `target_link_libraries(mytarget PRIVATE KF6::IdleTime)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kidletime-members.md)

## Public Functions

- [int idleTime() const](#idleTime)
- [QHash\<int, int\> idleTimeouts() const](#idleTimeouts)
- [void simulateUserActivity()](#simulateUserActivity)

## Public Slots

- [int addIdleTimeout(int msec)](#addIdleTimeout)
- [int addIdleTimeout(std::chrono::milliseconds msec)](#addIdleTimeout-1)
- [void catchNextResumeEvent()](#catchNextResumeEvent)
- [void removeAllIdleTimeouts()](#removeAllIdleTimeouts)
- [void removeIdleTimeout(int identifier)](#removeIdleTimeout)
- [void stopCatchingResumeEvent()](#stopCatchingResumeEvent)

## Signals

- [void resumingFromIdle()](#resumingFromIdle)
- [void timeoutReached(int identifier, int msec)](#timeoutReached)

## Static Public Members

- [KIdleTime \*instance()](#instance)

## Detailed Description {#details}

It is useful not only for finding out about the current idle time of the PC, but also for getting notified upon idle time events, such as custom timeouts, or user activity.

> **Note:** All the intervals and times in this library are in milliseconds, unless specified otherwise.

## Member Function Documentation {#member-function-documentation}

### \[slot\] int KIdleTime::addIdleTimeout(int *msec*) {#addIdleTimeout}

Adds a new timeout to catch. When calling this method, after the system will be idle for `msec` milliseconds, the signal [timeoutReached](kidletime.md#timeoutReached)() will be triggered. Please note that until you will call [removeIdleTimeout](kidletime.md#removeIdleTimeout)() or [removeAllIdleTimeouts](kidletime.md#removeAllIdleTimeouts)(), the signal will be triggered every time the system will be idle for `msec` milliseconds. This function also returns an unique token for the timeout just added to allow easier identification.

`msec` the time, in milliseconds, after which the signal will be triggered.

Returns an unique identifier for the timeout being added, that will be streamed by [timeoutReached](kidletime.md#timeoutReached)().

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kIdleTime, qOverload<int>(&KIdleTime::addIdleTimeout));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kIdleTime, [receiver = kIdleTime](int msec) { receiver->addIdleTimeout(msec); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).

*See also* [removeIdleTimeout](kidletime.md#removeIdleTimeout)(), [removeAllIdleTimeouts](kidletime.md#removeAllIdleTimeouts)(), [timeoutReached](kidletime.md#timeoutReached)()

### \[slot\] int KIdleTime::addIdleTimeout(std::chrono::milliseconds *msec*) {#addIdleTimeout-1}

Convenience overload supporting C++ chrono types. May also be used with chrono literals.

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kIdleTime, qOverload<std::chrono::milliseconds>(&KIdleTime::addIdleTimeout));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kIdleTime, [receiver = kIdleTime](std::chrono::milliseconds msec) { receiver->addIdleTimeout(msec); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).

### \[slot\] void KIdleTime::catchNextResumeEvent() {#catchNextResumeEvent}

Catches the next resume from idle event. This means that whenever user activity will be registered, or [simulateUserActivity](kidletime.md#simulateUserActivity)() is called, the signal [resumingFromIdle](kidletime.md#resumingFromIdle)() will be triggered.

Please note that this method will trigger the signal just for the very first resume event after the call: this means you explicitly have to request to track every single resume event you are interested in.

> **Note:** This behavior is due to the fact that a resume event happens whenever the user sends an input to the system. This would lead to a massive amount of signals being delivered when the PC is being used. Moreover, you are usually interested in catching just significant resume events, such as the ones after a significant period of inactivity. For tracking user input, you can use the more efficient methods provided by Qt. The purpose of this library is just monitoring the activity of the user.

*See also* [resumingFromIdle](kidletime.md#resumingFromIdle)(), [simulateUserActivity](kidletime.md#simulateUserActivity)()

### int KIdleTime::idleTime() const {#idleTime}

Retrieves the idle time of the system, in milliseconds

### QHash\<int, int\> KIdleTime::idleTimeouts() const {#idleTimeouts}

Returns the list of timeout identifiers associated with their duration, in milliseconds, the library is currently listening to.

*See also* [addIdleTimeout](kidletime.md#addIdleTimeout)(), [removeIdleTimeout](kidletime.md#removeIdleTimeout)(), [timeoutReached](kidletime.md#timeoutReached)()

### \[static\] KIdleTime \*KIdleTime::instance() {#instance}

Returns the singleton instance. Use this method to access [KIdleTime](kidletime.md).

### \[slot\] void KIdleTime::removeAllIdleTimeouts() {#removeAllIdleTimeouts}

Stops catching every set timeout (if any). This means that after calling this method, the signal [timeoutReached](kidletime.md#timeoutReached)() won't be called again until you will add another timeout.

*See also* [timeoutReached](kidletime.md#timeoutReached)(), [addIdleTimeout](kidletime.md#addIdleTimeout)()

### \[slot\] void KIdleTime::removeIdleTimeout(int *identifier*) {#removeIdleTimeout}

Stops catching the idle timeout identified by the token `identifier`, if it was registered earlier with [addIdleTimeout](kidletime.md#addIdleTimeout). Otherwise does nothing.

`identifier` the token returned from [addIdleTimeout](kidletime.md#addIdleTimeout) of the timeout you want to stop listening to

### \[signal\] void KIdleTime::resumingFromIdle() {#resumingFromIdle}

Triggered, if [KIdleTime](kidletime.md) is catching resume events, when the system resumes from an idle state. This means that either [simulateUserActivity](kidletime.md#simulateUserActivity)() was called or the user sent an input to the system.

*See also* [catchNextResumeEvent](kidletime.md#catchNextResumeEvent)()

### void KIdleTime::simulateUserActivity() {#simulateUserActivity}

Attempts to simulate user activity. This implies that after calling this method, the idle time of the system will become 0 and eventually [resumingFromIdle](kidletime.md#resumingFromIdle)() will be triggered.

*See also* [resumingFromIdle](kidletime.md#resumingFromIdle)()

### \[slot\] void KIdleTime::stopCatchingResumeEvent() {#stopCatchingResumeEvent}

Stops listening for resume event. This function serves for canceling [catchNextResumeEvent](kidletime.md#catchNextResumeEvent)(), as it will have effect just when [catchNextResumeEvent](kidletime.md#catchNextResumeEvent)() has been called and [resumingFromIdle](kidletime.md#resumingFromIdle)() not yet triggered.

*See also* [resumingFromIdle](kidletime.md#resumingFromIdle)(), [catchNextResumeEvent](kidletime.md#catchNextResumeEvent)()

### \[signal\] void KIdleTime::timeoutReached(int *identifier*, int *msec*) {#timeoutReached}

Triggered when the system has been idle for x milliseconds, identified by the previously set timeout.

This signal is triggered whenever each timeout previously registered with [addIdleTimeout](kidletime.md#addIdleTimeout)(int) is reached. It is guaranteed that `msec` will exactly correspond to the identified timeout.

`identifier` the identifier of the timeout the system has reached.

`msec` the time, in milliseconds, the system has been idle for.

*See also* [addIdleTimeout](kidletime.md#addIdleTimeout)(), [removeIdleTimeout](kidletime.md#removeIdleTimeout)()
