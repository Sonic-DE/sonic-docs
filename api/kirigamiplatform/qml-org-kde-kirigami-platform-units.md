---
title: "Units QML Type (Singleton)"
description: "A set of values to define semantically sizes and durations."
---

# Units QML Type (Singleton)

A set of values to define semantically sizes and durations. [More...](#details)

- Import Statement: import org.kde.kirigami.platform
- In C++: [Units](kirigami-platform-units.md)

> **Note:** **Note:** This type is a QML singleton. There is only one instance of this type in the QML engine.

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### \[read-only, since 6.2\] cornerRadius : real {#cornerRadius-prop}

Corner radius value shared by buttons and other rectangle elements.

This property was introduced in Qt 6.2.

### \[read-only\] gridUnit : int {#gridUnit-prop}

The fundamental unit of space that should be used for sizes, expressed in pixels.

### \[read-only\] humanMoment : int {#humanMoment-prop}

Time in milliseconds equivalent to the theoretical human moment, which can be used to determine whether how long to wait until the user should be informed of something, or can be used as the limit for how long something should wait before being automatically initiated.

Some examples:

- When the user types text in a search field, wait no longer than this duration after the user completes typing before starting the search.
- When loading data which would commonly arrive rapidly enough to not require interaction, wait this long before showing a spinner.

This might seem an arbitrary number, but given the psychological effect that three seconds seems to be what humans consider a moment (and in the case of waiting for something to happen, a moment is that time when you think "this is taking a bit long, isn't it?"), the idea is to postpone for just before such a conceptual moment. The reason for the two seconds, rather than three, is to function as a middle ground: Not long enough that the user would think that something has taken too long, for also not so fast as to happen too soon.

See [Tick, tock, tick - Hugs and life in 3 second intervals (Psychology Today)](https://www.psychologytoday.com/blog/all-about-addiction/201101/tick-tock-tick-hugs-and-life-in-3-second-intervals) (the actual paper is hidden behind an academic paywall and consequently not readily available to us, so the source will have to be the blog entry above).

> **Note:** This should \_\_not\_\_ be used as an animation duration, as it is deliberately not scaled according to the animation settings. This is specifically for determining when something has taken too long and the user should expect some kind of feedback. See [veryShortDuration](qml-org-kde-kirigami-platform-units.md#veryShortDuration-prop), [shortDuration](qml-org-kde-kirigami-platform-units.md#shortDuration-prop), [longDuration](qml-org-kde-kirigami-platform-units.md#longDuration-prop), and [veryLongDuration](qml-org-kde-kirigami-platform-units.md#veryLongDuration-prop) for animation duration choices.

### iconSizes group {#iconSizes-prop}

**iconSizes.enormous : int**

**iconSizes.huge : int**

**iconSizes.large : int**

**iconSizes.medium : int**

**iconSizes.sizeForLabels : int**

**iconSizes.small : int**

**iconSizes.smallMedium : int**

The units.iconSizes group provides access to platform-dependent icon sizing.

The icon sizes provided are normalized for different DPI, so icons will scale depending on the DPI.

- sizeForLabels (the largest icon size that fits within fontMetrics.height)
- small
- smallMedium
- medium
- large
- huge
- enormous

### \[read-only\] largeSpacing : int {#largeSpacing-prop}

This property holds the amount of spacing that should be used between bigger UI elements, such as a large icon and a heading in a card.

### \[read-only\] longDuration : int {#longDuration-prop}

units.longDuration should be used for longer, screen-covering animations, for opening and closing of dialogs and other "not too small" animations

### \[read-only\] mediumSpacing : int {#mediumSpacing-prop}

This property holds the amount of spacing that should be used between medium UI elements, such as buttons and text fields in a toolbar.

### \[read-only\] shortDuration : int {#shortDuration-prop}

units.shortDuration should be used for short animations, such as accentuating a UI event, hover events, etc..

### \[read-only\] smallSpacing : int {#smallSpacing-prop}

This property holds the amount of spacing that should be used between smaller UI elements, such as a small icon and a label in a button.

### \[read-only\] toolTipDelay : int {#toolTipDelay-prop}

time in ms by which the display of tooltips will be delayed.

### \[read-only\] veryLongDuration : int {#veryLongDuration-prop}

units.veryLongDuration should be used for specialty animations that benefit from being even longer than [longDuration](qml-org-kde-kirigami-platform-units.md#longDuration-prop).

### \[read-only\] veryShortDuration : int {#veryShortDuration-prop}

units.veryShortDuration should be used for elements that should have a hint of smoothness, but otherwise animate near instantly.
