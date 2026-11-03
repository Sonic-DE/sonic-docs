---
title: "KSignalHandler Class"
description: "Allows getting ANSI C signals and forward them onto the Qt eventloop."
---

# KSignalHandler Class

Allows getting ANSI C signals and forward them onto the Qt eventloop. [More...](#details)

- **Header:** `#include <KSignalHandler>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](ksignalhandler-members.md)

## Public Functions

- [void watchSignal(int signal)](#watchSignal)

## Signals

- [void signalReceived(int signal)](#signalReceived)

## Static Public Members

- [KSignalHandler \*self()](#self)

## Detailed Description {#details}

It's a singleton as it relies on static data getting defined.

```cpp
{
  KSignalHandler::self()->watchSignal(SIGTERM);
  connect(KSignalHandler::self(), &KSignalHandler::signalReceived,
          this, &SomeClass::handleSignal);
  job->start();
}
```

## Member Function Documentation {#member-function-documentation}

### \[static\] KSignalHandler \*KSignalHandler::self() {#self}

Fetches an instance we can use to register our signals.

### \[signal\] void KSignalHandler::signalReceived(int *signal*) {#signalReceived}

Notifies that `signal` is emitted.

To catch a signal, we need to make sure it's registered using @m [watchSignal](ksignalhandler.md#watchSignal).

*See also* [watchSignal](ksignalhandler.md#watchSignal)

### void KSignalHandler::watchSignal(int *signal*) {#watchSignal}

Adds `signal` to be watched for. Once the process is notified about this signal, @m [signalReceived](ksignalhandler.md#signalReceived) will be emitted with the same `signal` as an argument.

*See also* [signalReceived](ksignalhandler.md#signalReceived)
