---
title: "Kirigami::Platform::Units Class"
description: "A set of values to define semantically sizes and durations."
---

# Kirigami::Platform::Units Class

A set of values to define semantically sizes and durations. [More...](#details)

- **Header:** `#include <Kirigami/Platform/Units>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KirigamiPlatform)`  
  `target_link_libraries(mytarget PRIVATE KF6::KirigamiPlatform)`
- **In QML:** [Units](qml-org-kde-kirigami-platform-units.md)
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kirigami-platform-units-members.md)

## Properties

- [\[read-only, since 6.2\] cornerRadius : qreal](#cornerRadius-prop)
- [\[read-only\] gridUnit : int](#gridUnit-prop)
- [\[read-only\] humanMoment : int](#humanMoment-prop)
- [\[read-only\] iconSizes : Kirigami::Platform::IconSizes\* const](#iconSizes-prop)
- [\[read-only\] largeSpacing : int](#largeSpacing-prop)
- [\[read-only\] longDuration : int](#longDuration-prop)
- [\[read-only\] mediumSpacing : int](#mediumSpacing-prop)
- [\[read-only\] shortDuration : int](#shortDuration-prop)
- [\[read-only\] smallSpacing : int](#smallSpacing-prop)
- [\[read-only\] toolTipDelay : int](#toolTipDelay-prop)
- [\[read-only\] veryLongDuration : int](#veryLongDuration-prop)
- [\[read-only\] veryShortDuration : int](#veryShortDuration-prop)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### \[read-only, since 6.2\] cornerRadius : qreal {#cornerRadius-prop}

Corner radius value shared by buttons and other rectangle elements

This property was introduced in Qt 6.2.

**Access functions:**

- `qreal` **cornerRadius**() const

**Notifier signal:**

- `void` **cornerRadiusChanged**()

### \[read-only\] gridUnit : int {#gridUnit-prop}

The fundamental unit of space that should be used for sizes, expressed in pixels.

**Access functions:**

- `int` **gridUnit**() const

**Notifier signal:**

- `void` **gridUnitChanged**()

### \[read-only\] humanMoment : int {#humanMoment-prop}

Time in milliseconds equivalent to the theoretical human moment, which can be used to determine whether how long to wait until the user should be informed of something, or can be used as the limit for how long something should wait before being automatically initiated.

Some examples:

- When the user types text in a search field, wait no longer than this duration after the user completes typing before starting the search.
- When loading data which would commonly arrive rapidly enough to not require interaction, wait this long before showing a spinner.

This might seem an arbitrary number, but given the psychological effect that three seconds seems to be what humans consider a moment (and in the case of waiting for something to happen, a moment is that time when you think "this is taking a bit long, isn't it?"), the idea is to postpone for just before such a conceptual moment. The reason for the two seconds, rather than three, is to function as a middle ground: Not long enough that the user would think that something has taken too long, for also not so fast as to happen too soon.

See [Tick, tock, tick - Hugs and life in 3 second intervals (Psychology Today)](https://www.psychologytoday.com/blog/all-about-addiction/201101/tick-tock-tick-hugs-and-life-in-3-second-intervals) (the actual paper is hidden behind an academic paywall and consequently not readily available to us, so the source will have to be the blog entry above).

> **Note:** This should \_\_not\_\_ be used as an animation duration, as it is deliberately not scaled according to the animation settings. This is specifically for determining when something has taken too long and the user should expect some kind of feedback. See [veryShortDuration](kirigami-platform-units.md#veryShortDuration-prop), [shortDuration](kirigami-platform-units.md#shortDuration-prop), [longDuration](kirigami-platform-units.md#longDuration-prop), and [veryLongDuration](kirigami-platform-units.md#veryLongDuration-prop) for animation duration choices.

**Access functions:**

- `int` **humanMoment**() const

**Notifier signal:**

- `void` **humanMomentChanged**()

### \[read-only\] iconSizes : Kirigami::Platform::IconSizes\* const {#iconSizes-prop}

**Access functions:**

- `Kirigami::Platform::IconSizes` \***iconSizes**() const

### \[read-only\] largeSpacing : int {#largeSpacing-prop}

This property holds the amount of spacing that should be used between bigger UI elements, such as a large icon and a heading in a card.

**Access functions:**

- `int` **largeSpacing**() const

**Notifier signal:**

- `void` **largeSpacingChanged**()

### \[read-only\] longDuration : int {#longDuration-prop}

units.longDuration should be used for longer, screen-covering animations, for opening and closing of dialogs and other "not too small" animations

**Access functions:**

- `int` **longDuration**() const

**Notifier signal:**

- `void` **longDurationChanged**()

### \[read-only\] mediumSpacing : int {#mediumSpacing-prop}

This property holds the amount of spacing that should be used between medium UI elements, such as buttons and text fields in a toolbar.

**Access functions:**

- `int` **mediumSpacing**() const

**Notifier signal:**

- `void` **mediumSpacingChanged**()

### \[read-only\] shortDuration : int {#shortDuration-prop}

units.shortDuration should be used for short animations, such as accentuating a UI event, hover events, etc..

**Access functions:**

- `int` **shortDuration**() const

**Notifier signal:**

- `void` **shortDurationChanged**()

### \[read-only\] smallSpacing : int {#smallSpacing-prop}

This property holds the amount of spacing that should be used between smaller UI elements, such as a small icon and a label in a button.

**Access functions:**

- `int` **smallSpacing**() const

**Notifier signal:**

- `void` **smallSpacingChanged**()

### \[read-only\] toolTipDelay : int {#toolTipDelay-prop}

time in ms by which the display of tooltips will be delayed.

**Access functions:**

- `int` **toolTipDelay**() const

**Notifier signal:**

- `void` **toolTipDelayChanged**()

### \[read-only\] veryLongDuration : int {#veryLongDuration-prop}

units.veryLongDuration should be used for specialty animations that benefit from being even longer than [longDuration](kirigami-platform-units.md#longDuration-prop).

**Access functions:**

- `int` **veryLongDuration**() const

**Notifier signal:**

- `void` **veryLongDurationChanged**()

### \[read-only\] veryShortDuration : int {#veryShortDuration-prop}

units.veryShortDuration should be used for elements that should have a hint of smoothness, but otherwise animate near instantly.

**Access functions:**

- `int` **veryShortDuration**() const

**Notifier signal:**

- `void` **veryShortDurationChanged**()
