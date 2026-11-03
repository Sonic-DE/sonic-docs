---
title: "Solid::DeviceNotifier Class"
description: "This class allow to query the underlying system for information about the hardware available."
---

# Solid::DeviceNotifier Class

This class allow to query the underlying system for information about the hardware available. [More...](#details)

- **Header:** `#include <Solid/DeviceNotifier>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Solid)`  
  `target_link_libraries(mytarget PRIVATE KF6::Solid)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](solid-devicenotifier-members.md)

## Signals

- [void deviceAdded(const QString &udi)](#deviceAdded)
- [void deviceRemoved(const QString &udi)](#deviceRemoved)

## Static Public Members

- [Solid::DeviceNotifier \*instance()](#instance)

## Detailed Description {#details}

Applications should use this to be notified about hardware changes.

Note that it's implemented as a singleton and encapsulates the backend logic.

## Member Function Documentation {#member-function-documentation}

### \[signal\] void DeviceNotifier::deviceAdded(const QString &*udi*) {#deviceAdded}

This signal is emitted when a new device with the given `udi` appears in the underlying system.

### \[signal\] void DeviceNotifier::deviceRemoved(const QString &*udi*) {#deviceRemoved}

This signal is emitted when a device with the given `udi` disappears from the underlying system.

### \[static\] Solid::DeviceNotifier \*DeviceNotifier::instance() {#instance}

Returns a pointer to the global [DeviceNotifier](solid-devicenotifier.md) instance to allow for its use with [QObject::connect](https://doc.qt.io/qt-6/qobject.html#connect)();

```cpp
auto notifier = Solid::DeviceNotifier::instance();

auto refresh = [this] (const QString &udi) {
    Solid::Device device(udi);
    if (device.is<Solid::StorageDrive>()) {
        qInfo() << "A new storage drive was added!";
    }
};
QObject::connect(notifier, &Solid::DeviceNotifier::deviceAdded, refresh);
```
