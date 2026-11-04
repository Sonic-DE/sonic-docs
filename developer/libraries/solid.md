---
title: Solid
description: Hardware abstraction.
source_url: https://develop.kde.org/docs/features/solid/
source_authors: [Carl Schwan, Marius P, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-frameworks-device-integration (Solid frontend, upower backend, solid-hardware6), sonic-workspace d0b84fd142 (applets/devicenotifier), sonic-desktop-interface (kcms/solid_actions), sonic-system-settings (categories); the device examples were built against SonicDE's Solid and run, as was solid-hardware6
---

# Solid

## Introduction

Solid, in `sonic-frameworks-device-integration` (`find_package(KF6Solid)`, `KF6::Solid`), lets you write applications that work with hardware. Its API provides the abstraction needed to support several platforms.

Solid finds devices and gives you the information it has about them: you can look at the features of the CPU, the driver of your camera, or the mount point of your USB stick.

You get information about a device without knowing its specifics, and can then control it with another library. This works for network devices too.

## Finding devices

### Listing devices

The first program is a simple console application that lists all hardware devices:

```cpp
#include <Solid/Device>
// ...
for(const Solid::Device &device : Solid::Device::allDevices()) {
    qInfo() << device.udi();
}
```

`device.udi()` returns the device's unique device identifier (UDI) as a QString. It is guaranteed to be unique: if a machine has two identical TV capture cards, you can refer to each by its UDI.

### Finding specific devices

The second program uses Solid's filters, which list only devices of given types, devices below a given parent, or devices matching [predicates](#action-predicates). This example lists only batteries. The device types are listed in [Solid::DeviceInterface::Type](/docs/api/solid/solid-deviceinterface#Type-enum).

```cpp
#include <Solid/Device>
#include <Solid/DeviceInterface>
// ...

// get a list of battery devices
const auto devices = Solid::Device::listFromType(Solid::DeviceInterface::Battery, QString());
for (const Solid::Device &device : devices)
{
   qDebug() << device.udi();
}
```

[Solid::Device::listFromType()](/docs/api/solid/solid-device#listFromType) finds devices of type `Solid::DeviceInterface::Battery` with any parent. To find only batteries below the parent `/org/freedesktop/UPower` (the UPower backend's devices), write:

```cpp
Solid::Device::listFromType(Solid::DeviceInterface::Battery, QStringLiteral("/org/freedesktop/UPower"));
```

### What to do with a device

A [Solid::Device](/docs/api/solid/solid-device) can have several [types](/docs/api/solid/solid-deviceinterface#Type-enum) (device interfaces). Test for one and use it like this:

```cpp
#include <Solid/Device>
#include <Solid/DeviceInterface>
#include <Solid/Processor>
// ...

const auto list = Solid::Device::listFromType(Solid::DeviceInterface::Processor, QString());

// take the first processor in the list
Solid::Device device = list[0];
if (device.is<Solid::Processor>()) {
    qDebug() << "We've got a processor!";
} else {
    qDebug() << "Device is not a processor.";
}

auto processor = device.as<Solid::Processor>();
qInfo() << "This processors maximum speed is:" << processor->maxSpeed();
```

### Being notified of new devices

The device notifier signals when devices are added, so your application can react:

```cpp
#include <Solid/Device>
#include <Solid/DeviceNotifier>
#include <Solid/StorageDrive>
// ...

auto notifier = Solid::DeviceNotifier::instance();

auto refresh = [this] (const QString &udi) {
    Solid::Device device(udi);
    if (device.is<Solid::StorageDrive>()) {
        qInfo() << "A new storage drive was added!";
    }
};

QObject::connect(notifier, &Solid::DeviceNotifier::deviceAdded, refresh);
```

### Network devices

With [NetworkShare](/docs/api/solid/solid-networkshare) you can find network shares and handle each kind differently:

```cpp
const auto devices = Solid::Device::listFromType(Solid::DeviceInterface::NetworkShare);

for (const auto &device : devices) {
    switch (device.as<Solid::NetworkShare>()->type()) {
    case Solid::NetworkShare::Cifs:
        hasCifsShare = true;
        continue;
    case Solid::NetworkShare::Smb3:
        hasSmb3Share = true;
        continue;
    case Solid::NetworkShare::Nfs:
        hasNfsShare = true;
        continue;
    default:
        continue;
    }
}
```

### The solid-hardware6 tool

Solid also provides `solid-hardware6`, a command-line tool for looking at the available devices.

List the UDIs of all devices:

```bash
solid-hardware6 list
```

List all devices with all their details:

```bash
solid-hardware6 list details
```

List all batteries:

```bash
solid-hardware6 query 'IS Battery'
```

This query is a [Solid predicate](#action-predicates).

## Device actions

When Solid finds a new data device, it appears in SonicDE's "Disks & Devices" widget, which handles device events, in the Places panel of the Ecco file manager, and elsewhere in the user interface.

Each device has actions the user can perform on it, depending on its type and contents. For an audio CD, for example, "Disks & Devices" may offer to play it with a music player. Default actions are defined by desktop files that the application handling the action installs, and they disappear when the application is removed.

Users add and change actions in System Settings → Disks & Cameras → Device Actions; those changes only apply to that user. To install an action with your application, read on.

### Anatomy of an action

An action is a desktop file in `~/.local/share/solid/actions` or `/usr/share/solid/actions` with an [additional application action](https://specifications.freedesktop.org/desktop-entry/latest/extra-actions.html), like this:

```ini
[Desktop Entry]
X-KDE-Solid-Predicate=OpticalDisc.availableContent & 'Audio'
Type=Service
Actions=Play;

[Desktop Action Play]
Name=Play Audio CD with Amarok
Name[fr]=Jouer CD Audio avec Amarok
# names in other languages
Icon=amarok
Exec=amarok --cdplay %f
```

The value of `Actions=` must match the `Desktop Action` group.

### Actions and devices

"Disks & Devices" gets the devices from Solid and reads the actions from the `solid/actions` folders (`~/.local/share/solid/actions`, `/usr/share/solid/actions`). It decides which actions belong to a device by evaluating each action's [predicate](#action-predicates) against the device's physical and logical properties: if the predicate matches, the action is offered. Any application can query Solid for the same actions in the same way.

### Action predicates

The predicate of an action is in its `X-KDE-Solid-Predicate` entry. Its syntax is that of [Solid::Predicate](/docs/api/solid/solid-predicate).

Predicates have the form:

- `DeviceClass.attribute == value`
- `DeviceClass.attribute & value`

The second form means the attribute can have a set of values, and the given value must be one of them. Which values exist depends on the device class.

For example, `OpticalDisc.availableContent & 'Audio'` means the medium is a [Solid::OpticalDisc](/docs/api/solid/solid-opticaldisc) whose [content](/docs/api/solid/solid-opticaldisc#ContentType-enum) includes audio tracks and possibly more, while `OpticalDisc.availableContent == 'Audio'` matches a disc with audio tracks and nothing else.

Predicates can be combined with `AND`, `OR` and parentheses; `IS <type>` matches devices of a type. The easiest way to write one is to create a custom action in System Settings and look at the desktop file it writes in your user folder.

### Executing actions

When the user chooses an action, the command in its `Exec=` key is run with the device as a parameter. These placeholders are replaced:

- `%f` the device's mount point, if it has one
- `%d` the device file (such as the path of a block device)
- `%i` the device's UDI

Use whichever your application's command line supports. Note that the [Desktop Entry specification](https://specifications.freedesktop.org/desktop-entry/latest/exec-variables.html) deprecates `%d` and `%i`, so they may go away.

### Installing actions

Install system-wide actions where the device notifier looks for them, with ECM's `KDEInstallDirs`:

```cmake
install(FILES someSolidAction.desktop
    DESTINATION ${KDE_INSTALL_DATADIR}/solid/actions/)
```

The action is available as soon as it is installed: the device notifier watches the folders.
