---
title: "Solid::Processor Class"
description: "This device interface is available on processors."
---

# Solid::Processor Class

This device interface is available on processors. [More...](#details)

- **Header:** `#include <Solid/Processor>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Solid)`  
  `target_link_libraries(mytarget PRIVATE KF6::Solid)`
- **Inherits:** [Solid::DeviceInterface](solid-deviceinterface.md)

[List of all members, including inherited members](solid-processor-members.md)

## Public Types

- [enum Processor::InstructionSet](#InstructionSet-enum)

## Properties

- [\[read-only\] canChangeFrequency : bool](#canChangeFrequency-prop)
- [\[read-only\] instructionSets : InstructionSets](#instructionSets-prop)
- [\[read-only\] maxSpeed : qulonglong](#maxSpeed-prop)
- [\[read-only\] number : int](#number-prop)

## Public Functions

- [bool canChangeFrequency() const](#canChangeFrequency)
- [Solid::Processor::InstructionSets instructionSets() const](#instructionSets)
- [int maxSpeed() const](#maxSpeed)
- [int number() const](#number)

## Static Public Members

- [Solid::DeviceInterface::Type deviceInterfaceType()](#deviceInterfaceType)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum Processor::InstructionSet {#InstructionSet-enum}

**flags Processor::InstructionSets**

This enum contains the list of architecture extensions you can query.

| Constant |   |
| --- | --- |
| `Solid::Processor::NoExtensions` | `0x0` |
| `Solid::Processor::IntelMmx` | `0x1` |
| `Solid::Processor::IntelSse` | `0x2` |
| `Solid::Processor::IntelSse2` | `0x4` |
| `Solid::Processor::IntelSse3` | `0x8` |
| `Solid::Processor::IntelSsse3` | `0x80` |
| `Solid::Processor::IntelSse4` | `0x10` |
| `Solid::Processor::IntelSse41` | `0x10` |
| `Solid::Processor::IntelSse42` | `0x100` |
| `Solid::Processor::Amd3DNow` | `0x20` |
| `Solid::Processor::AltiVec` | `0x40` |

The `InstructionSets` type is a typedef for `QFlags<InstructionSet>. `It stores an OR combination of `InstructionSet` values.

## Property Documentation {#property-documentation}

### \[read-only\] canChangeFrequency : bool {#canChangeFrequency-prop}

**Access functions:**

- `bool` **[canChangeFrequency](solid-processor.md#canChangeFrequency)**() const

### \[read-only\] instructionSets : InstructionSets {#instructionSets-prop}

**Access functions:**

- `Solid::Processor::InstructionSets` **[instructionSets](solid-processor.md#instructionSets)**() const

### \[read-only\] maxSpeed : qulonglong {#maxSpeed-prop}

**Access functions:**

- `int` **[maxSpeed](solid-processor.md#maxSpeed)**() const

### \[read-only\] number : int {#number-prop}

**Access functions:**

- `int` **[number](solid-processor.md#number)**() const

## Member Function Documentation {#member-function-documentation}

### bool Processor::canChangeFrequency() const {#canChangeFrequency}

Returns whether the processor can change the CPU frequency.

> **Note:** Getter function for property [canChangeFrequency](solid-processor.md#canChangeFrequency-prop).

### \[static\] Solid::DeviceInterface::Type Processor::deviceInterfaceType() {#deviceInterfaceType}

Returns the [Solid::DeviceInterface::Type](solid-deviceinterface.md#Type-enum) of the Processor device interface.

*See also* [Solid::DeviceInterface::Type](solid-index.md)

### Solid::Processor::InstructionSets Processor::instructionSets() const {#instructionSets}

Returns the instructions set extensions supported by the CPU.

> **Note:** Getter function for property [instructionSets](solid-processor.md#instructionSets-prop).

*See also* [Solid::Processor::InstructionSet](solid-index.md)

### int Processor::maxSpeed() const {#maxSpeed}

Returns the maximum speed of the processor in MHz, or 0 if the device can't be queried for this information.

> **Note:** Getter function for property [maxSpeed](solid-processor.md#maxSpeed-prop).

### int Processor::number() const {#number}

Returns the internal processor number in the system, starting from zero.

> **Note:** Getter function for property [number](solid-processor.md#number-prop).
