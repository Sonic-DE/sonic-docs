---
title: "Solid::Battery Class"
description: "This device interface is available on batteries."
---

# Solid::Battery Class

This device interface is available on batteries. [More...](#details)

- **Header:** `#include <Solid/Battery>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Solid)`  
  `target_link_libraries(mytarget PRIVATE KF6::Solid)`
- **Inherits:** [Solid::DeviceInterface](solid-deviceinterface.md)

[List of all members, including inherited members](solid-battery-members.md)

## Public Types

- [enum Battery::BatteryType](#BatteryType-enum)
- [enum Battery::ChargeState](#ChargeState-enum)
- [enum Battery::Technology](#Technology-enum)

## Properties

- [\[read-only\] capacity : int](#capacity-prop)
- [\[read-only\] chargePercent : int](#chargePercent-prop)
- [\[read-only\] chargeState : ChargeState](#chargeState-prop)
- [\[read-only\] cycleCount : int](#cycleCount-prop)
- [\[read-only\] energy : double](#energy-prop)
- [\[read-only\] energyFull : double](#energyFull-prop)
- [\[read-only\] energyFullDesign : double](#energyFullDesign-prop)
- [\[read-only\] energyRate : double](#energyRate-prop)
- [\[read-only\] powerSupply : bool](#powerSupply-prop)
- [\[read-only\] present : bool](#present-prop)
- [\[read-only\] rechargeable : const bool](#rechargeable-prop)
- [\[read-only\] remainingTime : qlonglong](#remainingTime-prop)
- [\[read-only\] serial : const QString](#serial-prop)
- [\[read-only\] technology : const Technology](#technology-prop)
- [\[read-only\] temperature : double](#temperature-prop)
- [\[read-only\] timeToEmpty : qlonglong](#timeToEmpty-prop)
- [\[read-only\] timeToFull : qlonglong](#timeToFull-prop)
- [\[read-only\] type : const BatteryType](#type-prop)
- [\[read-only\] voltage : double](#voltage-prop)

## Public Functions

- [int capacity() const](#capacity)
- [int chargePercent() const](#chargePercent)
- [Solid::Battery::ChargeState chargeState() const](#chargeState)
- [int cycleCount() const](#cycleCount) (since 6.9)
- [double energy() const](#energy)
- [double energyFull() const](#energyFull)
- [double energyFullDesign() const](#energyFullDesign)
- [double energyRate() const](#energyRate)
- [bool isPowerSupply() const](#isPowerSupply)
- [bool isPresent() const](#isPresent)
- [bool isRechargeable() const](#isRechargeable)
- [qlonglong remainingTime() const](#remainingTime)
- [QString serial() const](#serial)
- [Solid::Battery::Technology technology() const](#technology)
- [double temperature() const](#temperature)
- [qlonglong timeToEmpty() const](#timeToEmpty)
- [qlonglong timeToFull() const](#timeToFull)
- [Solid::Battery::BatteryType type() const](#type)
- [double voltage() const](#voltage)

## Signals

- [void capacityChanged(int value, const QString &udi)](#capacityChanged)
- [void chargePercentChanged(int value, const QString &udi)](#chargePercentChanged)
- [void chargeStateChanged(int newState, const QString &udi = QString())](#chargeStateChanged)
- [void cycleCountChanged(int value, const QString &udi)](#cycleCountChanged) (since 6.9)
- [void energyChanged(double energy, const QString &udi)](#energyChanged)
- [void energyFullChanged(double energy, const QString &udi)](#energyFullChanged)
- [void energyFullDesignChanged(double energy, const QString &udi)](#energyFullDesignChanged)
- [void energyRateChanged(double energyRate, const QString &udi)](#energyRateChanged)
- [void powerSupplyStateChanged(bool newState, const QString &udi)](#powerSupplyStateChanged)
- [void presentStateChanged(bool newState, const QString &udi)](#presentStateChanged)
- [void remainingTimeChanged(qlonglong time, const QString &udi)](#remainingTimeChanged)
- [void temperatureChanged(double temperature, const QString &udi)](#temperatureChanged)
- [void timeToEmptyChanged(qlonglong time, const QString &udi)](#timeToEmptyChanged)
- [void timeToFullChanged(qlonglong time, const QString &udi)](#timeToFullChanged)
- [void voltageChanged(double voltage, const QString &udi)](#voltageChanged)

## Static Public Members

- [Solid::DeviceInterface::Type deviceInterfaceType()](#deviceInterfaceType)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum Battery::BatteryType {#BatteryType-enum}

This enum type defines the type of the device holding the battery

| Constant | Value | Description |
| --- | --- | --- |
| `Solid::Battery::PdaBattery` | `1` | A battery in a Personal Digital Assistant |
| `Solid::Battery::UpsBattery` | `2` | A battery in an Uninterruptible Power Supply |
| `Solid::Battery::PrimaryBattery` | `3` | A primary battery for the system (for example laptop battery) |
| `Solid::Battery::MouseBattery` | `4` | A battery in a mouse |
| `Solid::Battery::KeyboardBattery` | `5` | A battery in a keyboard |
| `Solid::Battery::KeyboardMouseBattery` | `6` | A battery in a combined keyboard and mouse |
| `Solid::Battery::CameraBattery` | `7` | A battery in a camera |
| `Solid::Battery::PhoneBattery` | `8` | A battery in a phone |
| `Solid::Battery::MonitorBattery` | `9` | A battery in a monitor |
| `Solid::Battery::GamingInputBattery` | `10` | A battery in a gaming input device (for example a wireless game pad) |
| `Solid::Battery::BluetoothBattery (since Qt 5.54)` | `11` | A generic Bluetooth device battery (if its type isn't known, a Bluetooth mouse would normally show up as a MouseBattery) |
| `Solid::Battery::TabletBattery (since Qt 5.88)` | `12` | A battery in a graphics tablet or pen |
| `Solid::Battery::HeadphoneBattery (since Qt 6.0)` | `13` | A battery in a headphone |
| `Solid::Battery::HeadsetBattery (since Qt 6.0)` | `14` | A battery in a headset |
| `Solid::Battery::TouchpadBattery (since Qt 6.0)` | `15` | A battery in a touchpad. This is how the Dualsense Wireless Controller is categorized |
| `Solid::Battery::WearableBattery (since Qt 6.21)` | `16` | A battery for a wearable device, watch... |
| `Solid::Battery::UnknownBattery` | `0` | A battery in an unknown device |

### enum Battery::ChargeState {#ChargeState-enum}

This enum type defines charge state of a battery

| Constant | Value | Description |
| --- | --- | --- |
| `Solid::Battery::NoCharge` | `0` | Battery charge is stable, not charging or discharging or the state is Unknown |
| `Solid::Battery::Charging` | `1` | Battery is charging |
| `Solid::Battery::Discharging` | `2` | Battery is discharging |
| `Solid::Battery::FullyCharged` | `3` | The battery is fully charged; a battery not necessarily charges up to 100% |

### enum Battery::Technology {#Technology-enum}

Technology used in the battery

| Constant | Value | Description |
| --- | --- | --- |
| `Solid::Battery::UnknownTechnology` | `0` | Unknown |
| `Solid::Battery::LithiumIon` | `1` | Lithium ion |
| `Solid::Battery::LithiumPolymer` | `2` | Lithium polymer |
| `Solid::Battery::LithiumIronPhosphate` | `3` | Lithium iron phosphate |
| `Solid::Battery::LeadAcid` | `4` | Lead acid |
| `Solid::Battery::NickelCadmium` | `5` | Nickel cadmium |
| `Solid::Battery::NickelMetalHydride` | `6` | Nickel metal hydride |

## Property Documentation {#property-documentation}

### \[read-only\] capacity : int {#capacity-prop}

**Access functions:**

- `int` **[capacity](solid-battery.md#capacity)**() const

**Notifier signal:**

- `void` **[capacityChanged](solid-battery.md#capacityChanged)**(`int` *value*, const `QString` &*udi*)

### \[read-only\] chargePercent : int {#chargePercent-prop}

**Access functions:**

- `int` **[chargePercent](solid-battery.md#chargePercent)**() const

**Notifier signal:**

- `void` **[chargePercentChanged](solid-battery.md#chargePercentChanged)**(`int` *value*, const `QString` &*udi*)

### \[read-only\] chargeState : ChargeState {#chargeState-prop}

**Access functions:**

- `Solid::Battery::ChargeState` **[chargeState](solid-battery.md#chargeState)**() const

**Notifier signal:**

- `void` **[chargeStateChanged](solid-battery.md#chargeStateChanged)**(`int` *newState*, const `QString` &*udi* = QString())

### \[read-only\] cycleCount : int {#cycleCount-prop}

**Access functions:**

- `int` **[cycleCount](solid-battery.md#cycleCount)**() const

**Notifier signal:**

- `void` **[cycleCountChanged](solid-battery.md#cycleCountChanged)**(`int` *value*, const `QString` &*udi*)

### \[read-only\] energy : double {#energy-prop}

**Access functions:**

- `double` **[energy](solid-battery.md#energy)**() const

**Notifier signal:**

- `void` **[energyChanged](solid-battery.md#energyChanged)**(`double` *energy*, const `QString` &*udi*)

### \[read-only\] energyFull : double {#energyFull-prop}

**Access functions:**

- `double` **[energyFull](solid-battery.md#energyFull)**() const

**Notifier signal:**

- `void` **[energyFullChanged](solid-battery.md#energyFullChanged)**(`double` *energy*, const `QString` &*udi*)

### \[read-only\] energyFullDesign : double {#energyFullDesign-prop}

**Access functions:**

- `double` **[energyFullDesign](solid-battery.md#energyFullDesign)**() const

**Notifier signal:**

- `void` **[energyFullDesignChanged](solid-battery.md#energyFullDesignChanged)**(`double` *energy*, const `QString` &*udi*)

### \[read-only\] energyRate : double {#energyRate-prop}

**Access functions:**

- `double` **[energyRate](solid-battery.md#energyRate)**() const

**Notifier signal:**

- `void` **[energyRateChanged](solid-battery.md#energyRateChanged)**(`double` *energyRate*, const `QString` &*udi*)

### \[read-only\] powerSupply : bool {#powerSupply-prop}

**Access functions:**

- `bool` **[isPowerSupply](solid-battery.md#isPowerSupply)**() const

**Notifier signal:**

- `void` **[powerSupplyStateChanged](solid-battery.md#powerSupplyStateChanged)**(`bool` *newState*, const `QString` &*udi*)

### \[read-only\] present : bool {#present-prop}

**Access functions:**

- `bool` **[isPresent](solid-battery.md#isPresent)**() const

**Notifier signal:**

- `void` **[presentStateChanged](solid-battery.md#presentStateChanged)**(`bool` *newState*, const `QString` &*udi*)

### \[read-only\] rechargeable : const bool {#rechargeable-prop}

**Access functions:**

- `bool` **[isRechargeable](solid-battery.md#isRechargeable)**() const

### \[read-only\] remainingTime : qlonglong {#remainingTime-prop}

**Access functions:**

- `qlonglong` **[remainingTime](solid-battery.md#remainingTime)**() const

**Notifier signal:**

- `void` **[remainingTimeChanged](solid-battery.md#remainingTimeChanged)**(`qlonglong` *time*, const `QString` &*udi*)

### \[read-only\] serial : const QString {#serial-prop}

**Access functions:**

- `QString` **[serial](solid-battery.md#serial)**() const

### \[read-only\] technology : const Technology {#technology-prop}

**Access functions:**

- `Solid::Battery::Technology` **[technology](solid-battery.md#technology)**() const

### \[read-only\] temperature : double {#temperature-prop}

**Access functions:**

- `double` **[temperature](solid-battery.md#temperature)**() const

**Notifier signal:**

- `void` **[temperatureChanged](solid-battery.md#temperatureChanged)**(`double` *temperature*, const `QString` &*udi*)

### \[read-only\] timeToEmpty : qlonglong {#timeToEmpty-prop}

**Access functions:**

- `qlonglong` **[timeToEmpty](solid-battery.md#timeToEmpty)**() const

**Notifier signal:**

- `void` **[timeToEmptyChanged](solid-battery.md#timeToEmptyChanged)**(`qlonglong` *time*, const `QString` &*udi*)

### \[read-only\] timeToFull : qlonglong {#timeToFull-prop}

**Access functions:**

- `qlonglong` **[timeToFull](solid-battery.md#timeToFull)**() const

**Notifier signal:**

- `void` **[timeToFullChanged](solid-battery.md#timeToFullChanged)**(`qlonglong` *time*, const `QString` &*udi*)

### \[read-only\] type : const BatteryType {#type-prop}

**Access functions:**

- `Solid::Battery::BatteryType` **[type](solid-battery.md#type)**() const

### \[read-only\] voltage : double {#voltage-prop}

**Access functions:**

- `double` **[voltage](solid-battery.md#voltage)**() const

**Notifier signal:**

- `void` **[voltageChanged](solid-battery.md#voltageChanged)**(`double` *voltage*, const `QString` &*udi*)

## Member Function Documentation {#member-function-documentation}

### int Battery::capacity() const {#capacity}

Returns the battery capacity normalised to percent, meaning how much energy can it hold compared to what it is designed to.

The capacity of the battery will reduce with age. A capacity value less than 75% is usually a sign that you should renew your battery.

> **Note:** Getter function for property [capacity](solid-battery.md#capacity-prop).

### \[signal\] void Battery::capacityChanged(int *value*, const QString &*udi*) {#capacityChanged}

This signal is emitted when the capacity of this battery has changed.

Returns the new capacity `value` of the battery with the given `udi`.

> **Note:** Notifier signal for property [capacity](solid-battery.md#capacity-prop).

### int Battery::chargePercent() const {#chargePercent}

Returns the current charge level of the battery normalised to percent, or -1 if the charge level is unknown.

> **Note:** Getter function for property [chargePercent](solid-battery.md#chargePercent-prop).

### \[signal\] void Battery::chargePercentChanged(int *value*, const QString &*udi*) {#chargePercentChanged}

This signal is emitted when the charge percent value of this battery has changed.

Returns the new charge percent `value` of the battery with the given `udi`.

> **Note:** Notifier signal for property [chargePercent](solid-battery.md#chargePercent-prop).

### Solid::Battery::ChargeState Battery::chargeState() const {#chargeState}

Retrieves the current charge state of the battery.

It can be in a stable state (no charge), charging or discharging.

> **Note:** Getter function for property [chargeState](solid-battery.md#chargeState-prop).

*See also* [Solid::Battery::ChargeState](solid-index.md)

### \[signal\] void Battery::chargeStateChanged(int *newState*, const QString &*udi* = QString()) {#chargeStateChanged}

This signal is emitted when the charge state of this battery has changed.

Returns the new charge state `newState` of the battery with the given `udi`.

> **Note:** Notifier signal for property [chargeState](solid-battery.md#chargeState-prop).

### \[since 6.9\] int Battery::cycleCount() const {#cycleCount}

Returns the number of charge cycles this battery has experienced so far, or -1 if this information is unavailable.

> **Note:** Getter function for property [cycleCount](solid-battery.md#cycleCount-prop).

This function was introduced in Qt 6.9.

### \[signal, since 6.9\] void Battery::cycleCountChanged(int *value*, const QString &*udi*) {#cycleCountChanged}

This signal is emitted when the number of charge cycles of the battery has changed.

Returns the new `value` for the charge cycles of the battery with the given `udi`.

> **Note:** Notifier signal for property [cycleCount](solid-battery.md#cycleCount-prop).

This function was introduced in Qt 6.9.

### \[static\] Solid::DeviceInterface::Type Battery::deviceInterfaceType() {#deviceInterfaceType}

Returns the [Solid::DeviceInterface::Type](solid-deviceinterface.md#Type-enum) of the Battery device interface.

*See also* [Solid::DeviceInterface::Type](solid-index.md)

### double Battery::energy() const {#energy}

Returns the amount of energy (measured in Wh) currently available in the power source.

> **Note:** Getter function for property [energy](solid-battery.md#energy-prop).

### \[signal\] void Battery::energyChanged(double *energy*, const QString &*udi*) {#energyChanged}

This signal is emitted when the energy value of this battery has changed.

Returns the new `energy` value for the battery with the given `udi`.

> **Note:** Notifier signal for property [energy](solid-battery.md#energy-prop).

### double Battery::energyFull() const {#energyFull}

Returns the amount of energy (measured in Wh) the battery has when it is full.

> **Note:** Getter function for property [energyFull](solid-battery.md#energyFull-prop).

### \[signal\] void Battery::energyFullChanged(double *energy*, const QString &*udi*) {#energyFullChanged}

This signal is emitted when the energy full value of this battery has changed.

Returns the new full `energy` value of the battery with the given `udi`.

> **Note:** Notifier signal for property [energyFull](solid-battery.md#energyFull-prop).

### double Battery::energyFullDesign() const {#energyFullDesign}

Returns the amount of energy (measured in Wh) the battery should have by design when it is full.

> **Note:** Getter function for property [energyFullDesign](solid-battery.md#energyFullDesign-prop).

### \[signal\] void Battery::energyFullDesignChanged(double *energy*, const QString &*udi*) {#energyFullDesignChanged}

This signal is emitted when the energy full design value of this battery has changed.

Returns the new `energy` full design value of the battery with the given `udi`.

> **Note:** Notifier signal for property [energyFullDesign](solid-battery.md#energyFullDesign-prop).

### double Battery::energyRate() const {#energyRate}

Amount of energy being drained from the source, measured in W.

If positive, the source is being discharged, if negative it's being charged.

> **Note:** Getter function for property [energyRate](solid-battery.md#energyRate-prop).

### \[signal\] void Battery::energyRateChanged(double *energyRate*, const QString &*udi*) {#energyRateChanged}

This signal is emitted when the energy rate value of this battery has changed.

If positive, the source is being discharged, if negative it's being charged.

Returns the new `energy` rate value of the battery with the given `udi`.

> **Note:** Notifier signal for property [energyRate](solid-battery.md#energyRate-prop).

### bool Battery::isPowerSupply() const {#isPowerSupply}

Indicates if the battery is powering the machine.

> **Note:** Getter function for property [powerSupply](solid-battery.md#powerSupply-prop).

### bool Battery::isPresent() const {#isPresent}

Returns whether this battery is currently present in its bay.

> **Note:** Getter function for property [present](solid-battery.md#present-prop).

### bool Battery::isRechargeable() const {#isRechargeable}

Indicates if the battery is rechargeable.

> **Note:** Getter function for property [rechargeable](solid-battery.md#rechargeable-prop).

### \[signal\] void Battery::powerSupplyStateChanged(bool *newState*, const QString &*udi*) {#powerSupplyStateChanged}

This signal is emitted when the power supply state of the battery changes.

Returns the `newState` for the power supply of the battery with the given `udi`.

> **Note:** Notifier signal for property [powerSupply](solid-battery.md#powerSupply-prop).

### \[signal\] void Battery::presentStateChanged(bool *newState*, const QString &*udi*) {#presentStateChanged}

This signal is emitted if the battery gets plugged in/out of the battery bay.

Returns the `newState` of the battery with the given `udi`.

> **Note:** Notifier signal for property [present](solid-battery.md#present-prop).

### qlonglong Battery::remainingTime() const {#remainingTime}

Retrieves the current estimated remaining time (in seconds) of the system batteries

> **Note:** Getter function for property [remainingTime](solid-battery.md#remainingTime-prop).

### \[signal\] void Battery::remainingTimeChanged(qlonglong *time*, const QString &*udi*) {#remainingTimeChanged}

This signal is emitted when the estimated battery remaining time changes.

Returns the new battery remaining `time` for the battery with the given `udi`.

> **Note:** Notifier signal for property [remainingTime](solid-battery.md#remainingTime-prop).

### QString Battery::serial() const {#serial}

The serial number of the battery

> **Note:** Getter function for property [serial](solid-battery.md#serial-prop).

### Solid::Battery::Technology Battery::technology() const {#technology}

Returns the technology used to manufacture the battery.

> **Note:** Getter function for property [technology](solid-battery.md#technology-prop).

*See also* [Solid::Battery::Technology](solid-index.md)

### double Battery::temperature() const {#temperature}

The temperature of the battery in degrees Celsius.

> **Note:** Getter function for property [temperature](solid-battery.md#temperature-prop).

### \[signal\] void Battery::temperatureChanged(double *temperature*, const QString &*udi*) {#temperatureChanged}

This signal is emitted when the battery temperature has changed.

Returns the new `temperature` of the battery in degrees Celsius.

> **Note:** Notifier signal for property [temperature](solid-battery.md#temperature-prop).

### qlonglong Battery::timeToEmpty() const {#timeToEmpty}

Time (in seconds) until the battery is empty.

> **Note:** Getter function for property [timeToEmpty](solid-battery.md#timeToEmpty-prop).

### \[signal\] void Battery::timeToEmptyChanged(qlonglong *time*, const QString &*udi*) {#timeToEmptyChanged}

This signal is emitted when the time until the battery is empty has changed.

Returns the new remaining `time` until empty of the battery with the given `udi`.

> **Note:** Notifier signal for property [timeToEmpty](solid-battery.md#timeToEmpty-prop).

### qlonglong Battery::timeToFull() const {#timeToFull}

Time (in seconds) until the battery is full.

> **Note:** Getter function for property [timeToFull](solid-battery.md#timeToFull-prop).

### \[signal\] void Battery::timeToFullChanged(qlonglong *time*, const QString &*udi*) {#timeToFullChanged}

This signal is emitted when the time until the battery is full has changed.

Returns the new remaining `time` until full of the battery with the given `udi`.

> **Note:** Notifier signal for property [timeToFull](solid-battery.md#timeToFull-prop).

### Solid::Battery::BatteryType Battery::type() const {#type}

Returns the type of device holding this battery.

> **Note:** Getter function for property [type](solid-battery.md#type-prop).

*See also* [Solid::Battery::BatteryType](solid-index.md)

### double Battery::voltage() const {#voltage}

Voltage in the Cell or being recorded by the meter.

> **Note:** Getter function for property [voltage](solid-battery.md#voltage-prop).

### \[signal\] void Battery::voltageChanged(double *voltage*, const QString &*udi*) {#voltageChanged}

This signal is emitted when the voltage in the cell has changed.

Returns the new `voltage` of the cell for the battery with the given `udi`.

> **Note:** Notifier signal for property [voltage](solid-battery.md#voltage-prop).
