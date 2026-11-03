---
title: "KLed Class"
description: "An LED widget."
---

# KLed Class

An LED widget. [More...](#details)

- **Header:** `#include <KLed>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kled-members.md)

## Public Types

- [enum KLed::Look](#Look-enum)
- [enum KLed::Shape](#Shape-enum)
- [enum KLed::State](#State-enum)

## Properties

- [color : QColor](#color-prop)
- [darkFactor : int](#darkFactor-prop)
- [look : Look](#look-prop)
- [shape : Shape](#shape-prop)
- [state : State](#state-prop)

## Public Functions

- [KLed(QWidget \*parent = nullptr)](#KLed)
- [KLed(const QColor &color, QWidget \*parent = nullptr)](#KLed-1)
- [KLed(const QColor &color, KLed::State state, KLed::Look look, KLed::Shape shape, QWidget \*parent = nullptr)](#KLed-2)
- [QColor color() const](#color)
- [int darkFactor() const](#darkFactor)
- [KLed::Look look() const](#look)
- [void setColor(const QColor &color)](#setColor)
- [void setDarkFactor(int darkFactor)](#setDarkFactor)
- [void setLook(KLed::Look look)](#setLook)
- [void setShape(KLed::Shape shape)](#setShape)
- [void setState(KLed::State state)](#setState)
- [KLed::Shape shape() const](#shape)
- [KLed::State state() const](#state)

## Public Slots

- [void off()](#off)
- [void on()](#on)
- [void toggle()](#toggle)

## Detailed Description {#details}

Displays a round or rectangular light emitting diode.

It is configurable to arbitrary colors, the two on/off states and three styles (or "looks");

It may display itself in a performant flat view, a round view with light spot or a round view sunken in the screen.

## Member Type Documentation {#member-type-documentation}

### enum KLed::Look {#Look-enum}

Displays a flat, round or sunken LED.

LED look.

| Constant |   |
| --- | --- |
| `KLed::Flat` | `0` |
| `KLed::Raised` | `1` |
| `KLed::Sunken` | `2` |

### enum KLed::Shape {#Shape-enum}

Shades of the lamp.

LED shape

| Constant |   |
| --- | --- |
| `KLed::Rectangular` | `0` |
| `KLed::Circular` | `1` |

### enum KLed::State {#State-enum}

Status of the light is on/off.

LED on/off.

| Constant |   |
| --- | --- |
| `KLed::Off` | `0` |
| `KLed::On` | `1` |

## Property Documentation {#property-documentation}

### color : QColor {#color-prop}

**Access functions:**

- `QColor` **[color](kled.md#color)**() const
- `void` **[setColor](kled.md#setColor)**(const `QColor` &*color*)

### darkFactor : int {#darkFactor-prop}

**Access functions:**

- `int` **[darkFactor](kled.md#darkFactor)**() const
- `void` **[setDarkFactor](kled.md#setDarkFactor)**(`int` *darkFactor*)

### look : Look {#look-prop}

**Access functions:**

- `KLed::Look` **[look](kled.md#look)**() const
- `void` **[setLook](kled.md#setLook)**(`KLed::Look` *look*)

### shape : Shape {#shape-prop}

**Access functions:**

- `KLed::Shape` **[shape](kled.md#shape)**() const
- `void` **[setShape](kled.md#setShape)**(`KLed::Shape` *shape*)

### state : State {#state-prop}

**Access functions:**

- `KLed::State` **[state](kled.md#state)**() const
- `void` **[setState](kled.md#setState)**(`KLed::State` *state*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KLed::KLed(QWidget \**parent* = nullptr) {#KLed}

Constructs a green, round LED widget which will initially be turned on.

`parent` The parent widget.

### \[explicit\] KLed::KLed(const QColor &*color*, QWidget \**parent* = nullptr) {#KLed-1}

Constructs a round LED widget with the supplied color which will initially be turned on.

`color` Initial color of the LED.

`parent` The parent widget.

### KLed::KLed(const QColor &*color*, KLed::State *state*, KLed::Look *look*, KLed::Shape *shape*, QWidget \**parent* = nullptr) {#KLed-2}

Constructor with the color, state and look.

Differs from above only in the parameters, which configure all settings.

`color` Initial color of the LED.

`state` Sets the State.

`look` Sets the Look.

`shape` Sets the Shape (rectangular or circular).

`parent` The parent widget.

### QColor KLed::color() const {#color}

Returns the current color of the widget.

> **Note:** Getter function for property [color](kled.md#color-prop).

*See also* [setColor](kled.md#setColor)()

### int KLed::darkFactor() const {#darkFactor}

Returns the factor to darken the LED.

> **Note:** Getter function for property [darkFactor](kled.md#darkFactor-prop).

*See also* [setDarkFactor](kled.md#setDarkFactor)()

### KLed::Look KLed::look() const {#look}

Returns the current look of the widget.

> **Note:** Getter function for property [look](kled.md#look-prop).

*See also* [setLook](kled.md#setLook)(), [Look](kled.md#Look-enum)

### \[slot\] void KLed::off() {#off}

Sets the state of the widget to Off.

*See also* [on](kled.md#on)(), [toggle](kled.md#toggle)(), [setState](kled.md#setState)()

### \[slot\] void KLed::on() {#on}

Sets the state of the widget to On.

*See also* [off](kled.md#off)(), [toggle](kled.md#toggle)(), [setState](kled.md#setState)()

### void KLed::setColor(const QColor &*color*) {#setColor}

Set the color of the widget.

The LED is shown with `color` when in the [KLed::On](kled.md#State-enum) state or with the darken color in [KLed::Off](kled.md#State-enum) state.

The widget calls the [update](https://doc.qt.io/qt-6/qwidget.html#update)() method, so it will be updated when entering the main event loop.

`color` New color of the LED.

> **Note:** Setter function for property [color](kled.md#color-prop).

*See also* [color](kled.md#color)(), [darkFactor](kled.md#darkFactor)()

### void KLed::setDarkFactor(int *darkFactor*) {#setDarkFactor}

Sets the factor to darken the LED in [KLed::Off](kled.md#State-enum) state.

The `darkFactor` should be greater than 100, otherwise the LED becomes lighter in [KLed::Off](kled.md#State-enum) state.

Defaults to 300.

`darkFactor` Sets the factor to darken the LED.

> **Note:** Setter function for property [darkFactor](kled.md#darkFactor-prop).

*See also* [darkFactor](kled.md#darkFactor)(), [setColor](kled.md#setColor)

### void KLed::setLook(KLed::Look *look*) {#setLook}

Sets the look of the widget.

The look may be Flat, Raised or Sunken.

The widget calls the [update](https://doc.qt.io/qt-6/qwidget.html#update)() method, so it will be updated when entering the main event loop.

`look` New look of the LED.

> **Note:** Setter function for property [look](kled.md#look-prop).

*See also* [look](kled.md#look)(), [Look](kled.md#Look-enum)

### void KLed::setShape(KLed::Shape *shape*) {#setShape}

Set the shape of the LED.

`shape` The LED shape.

Set LED shape.

> **Note:** Setter function for property [shape](kled.md#shape-prop).

*See also* [shape](kled.md#shape)()

### void KLed::setState(KLed::State *state*) {#setState}

Sets the state of the widget to On or Off.

`state` The LED state: on or off.

> **Note:** Setter function for property [state](kled.md#state-prop).

*See also* [state](kled.md#state)(), [on](kled.md#on)(), [off](kled.md#off)(), [toggle](kled.md#toggle)()

### KLed::Shape KLed::shape() const {#shape}

Returns the current shape of the widget.

> **Note:** Getter function for property [shape](kled.md#shape-prop).

*See also* [setShape](kled.md#setShape)(), [Shape](kled.md#Shape-enum)

### KLed::State KLed::state() const {#state}

Returns the current state of the widget (on/off).

> **Note:** Getter function for property [state](kled.md#state-prop).

*See also* [setState](kled.md#setState)(), [State](kled.md#State-enum)

### \[slot\] void KLed::toggle() {#toggle}

Toggles the state of the led from Off to On or vice versa.
