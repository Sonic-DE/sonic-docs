---
title: "Solid::GenericInterface Class"
description: "Generic interface to deal with a device."
---

# Solid::GenericInterface Class

Generic interface to deal with a device. [More...](#details)

- **Header:** `#include <Solid/GenericInterface>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Solid)`  
  `target_link_libraries(mytarget PRIVATE KF6::Solid)`
- **Inherits:** [Solid::DeviceInterface](solid-deviceinterface.md)

[List of all members, including inherited members](solid-genericinterface-members.md)

## Public Types

- [enum GenericInterface::PropertyChange](#PropertyChange-enum)

## Public Functions

- [QMap\<QString, QVariant\> allProperties() const](#allProperties)
- [QVariant property(const QString &key) const](#property)
- [bool propertyExists(const QString &key) const](#propertyExists)

## Signals

- [void conditionRaised(const QString &condition, const QString &reason)](#conditionRaised)
- [void propertyChanged(const QMap\<QString, int\> &changes)](#propertyChanged)

## Static Public Members

- [Solid::DeviceInterface::Type deviceInterfaceType()](#deviceInterfaceType)

## Detailed Description {#details}

It exposes a set of properties and is organized as a key/value set.

> **Warning:** Using this class could expose some backend specific details and lead to non portable code. Use it at your own risk, or during transitional phases when the provided device interfaces don't provide the necessary methods.

## Member Type Documentation {#member-type-documentation}

### enum GenericInterface::PropertyChange {#PropertyChange-enum}

This enum type defines the type of change that can occur to a [GenericInterface](solid-genericinterface.md) property.

| Constant | Value | Description |
| --- | --- | --- |
| `Solid::GenericInterface::PropertyModified` | `0` | A property value has changed in the device |
| `Solid::GenericInterface::PropertyAdded` | `1` | A new property has been added to the device |
| `Solid::GenericInterface::PropertyRemoved` | `2` | A property has been removed from the device |

## Member Function Documentation {#member-function-documentation}

### QMap\<QString, QVariant\> GenericInterface::allProperties() const {#allProperties}

Returns a key/value map of all the known properties for the device.

> **Warning:** Using this method could expose some backend specific details and lead to non portable code. Use it at your own risk, or during transitional phases when the provided device interfaces don't provide the necessary methods.

### \[signal\] void GenericInterface::conditionRaised(const QString &*condition*, const QString &*reason*) {#conditionRaised}

This signal is emitted when an event occurred in the device. For example when a button is pressed.

Returns the name for the `condition` of the event and the `reason` for the condition to have been raised.

### \[static\] Solid::DeviceInterface::Type GenericInterface::deviceInterfaceType() {#deviceInterfaceType}

Returns the [Solid::DeviceInterface::Type](solid-deviceinterface.md#Type-enum) of the [GenericInterface](solid-genericinterface.md) device interface.

*See also* [Solid::DeviceInterface::Type](solid-index.md)

### QVariant GenericInterface::property(const QString &*key*) const {#property}

Returns the property `key` of the device, or QVariant() if the property is unknown.

> **Warning:** Using this method could expose some backend specific details and lead to non portable code. Use it at your own risk, or during transitional phases when the provided device interfaces don't provide the necessary methods.

### \[signal\] void GenericInterface::propertyChanged(const QMap\<QString, int\> &*changes*) {#propertyChanged}

This signal is emitted when a property is changed in the device.

Returns the map describing the property `changes` that occurred in the device, keys are property names, and values describe the kind of change done on the device property (added/removed/modified), one of Solid::Device::PropertyChange.

### bool GenericInterface::propertyExists(const QString &*key*) const {#propertyExists}

Returns whether a property `key` exists in the device.

> **Warning:** Using this method could expose some backend specific details and lead to non portable code. Use it at your own risk, or during transitional phases when the provided device interfaces don't provide the necessary methods.
