---
title: "KStatefulBrush Class"
description: "A container for a \"state-aware\" brush."
---

# KStatefulBrush Class

A container for a "state-aware" brush. [More...](#details)

- **Header:** `#include <KStatefulBrush>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ColorScheme)`  
  `target_link_libraries(mytarget PRIVATE KF6::ColorScheme)`

[List of all members, including inherited members](kstatefulbrush-members.md)

## Public Functions

- [KStatefulBrush()](#KStatefulBrush)
- [KStatefulBrush(const QBrush &, KSharedConfigPtr = KSharedConfigPtr())](#KStatefulBrush-2)
- [KStatefulBrush(KColorScheme::ColorSet, KColorScheme::BackgroundRole, KSharedConfigPtr = KSharedConfigPtr())](#KStatefulBrush-3)
- [KStatefulBrush(KColorScheme::ColorSet, KColorScheme::DecorationRole, KSharedConfigPtr = KSharedConfigPtr())](#KStatefulBrush-4)
- [KStatefulBrush(KColorScheme::ColorSet, KColorScheme::ForegroundRole, KSharedConfigPtr = KSharedConfigPtr())](#KStatefulBrush-5)
- [KStatefulBrush(const QBrush &, const QBrush &background, KSharedConfigPtr = KSharedConfigPtr())](#KStatefulBrush-6)
- [KStatefulBrush(const KStatefulBrush &)](#KStatefulBrush-1)
- [QBrush brush(QPalette::ColorGroup) const](#brush)
- [QBrush brush(const QPalette &) const](#brush-1)
- [KStatefulBrush &KStatefulBrush::operator=(const KStatefulBrush &)](#operator-eq)

## Detailed Description {#details}

[KStatefulBrush](kstatefulbrush.md) provides an easy and safe way to store a color for use in a user interface. It is "safe" both in that it will make it easy to deal with widget states in a correct manner, and that it insulates you against changes in [QPalette::ColorGroup](https://doc.qt.io/qt-6/qpalette.html#ColorGroup-enum).

Basically, a stateful brush is used to cache a particular "color" from the KDE system palette (usually, one which does not live in [QPalette](https://doc.qt.io/qt-6/qpalette.html)). When you are ready to draw using the brush, you use the current state to retrieve the appropriate brush.

Stateful brushes can also be used to apply state effects to arbitrary brushes, for example when working with a application specific user-defined color palette.

> **Note:** As of Qt 4.3, [QPalette::ColorGroup](https://doc.qt.io/qt-6/qpalette.html#ColorGroup-enum) is missing a state for disabled widgets in an inactive window. Hopefully Trolltech will fix this bug, at which point [KColorScheme](kcolorscheme-module.md) and [KStatefulBrush](kstatefulbrush.md) will be updated to recognize the new state. Using [KStatefulBrush](kstatefulbrush.md) will allow your application to inherit these changes "for free", without even recompiling.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KStatefulBrush::KStatefulBrush() {#KStatefulBrush}

Construct a "default" stateful brush. For such an instance, all overloads of [KStatefulBrush::brush](kstatefulbrush.md#brush) will return a default brush (i.e. QBrush()).

### \[explicit\] KStatefulBrush::KStatefulBrush(*const QBrush &*, *KSharedConfigPtr* = KSharedConfigPtr()) {#KStatefulBrush-2}

Construct a stateful background brush from a specified [QBrush](https://doc.qt.io/qt-6/qbrush.html) (or [QColor](https://doc.qt.io/qt-6/qcolor.html), via [QBrush](https://doc.qt.io/qt-6/qbrush.html)'s implicit constructor). The various states are determined from the base [QBrush](https://doc.qt.io/qt-6/qbrush.html) (which fills in the Active state) according to the same rules used to build stateful color schemes from the system color scheme. The state effects from the given [KConfig](../kconfigcore/kconfig.md) are used (if null, the application's state effects are used).

### \[explicit\] KStatefulBrush::KStatefulBrush(*KColorScheme::ColorSet*, *KColorScheme::BackgroundRole*, *KSharedConfigPtr* = KSharedConfigPtr()) {#KStatefulBrush-3}

Construct a stateful brush from given color set and background role, using the colors from the given [KConfig](../kconfigcore/kconfig.md) (if null, the application's colors are used).

### \[explicit\] KStatefulBrush::KStatefulBrush(*KColorScheme::ColorSet*, *KColorScheme::DecorationRole*, *KSharedConfigPtr* = KSharedConfigPtr()) {#KStatefulBrush-4}

Construct a stateful brush from given color set and decoration role, using the colors from the given [KConfig](../kconfigcore/kconfig.md) (if null, the application's colors are used).

### \[explicit\] KStatefulBrush::KStatefulBrush(*KColorScheme::ColorSet*, *KColorScheme::ForegroundRole*, *KSharedConfigPtr* = KSharedConfigPtr()) {#KStatefulBrush-5}

Construct a stateful brush from given color set and foreground role, using the colors from the given [KConfig](../kconfigcore/kconfig.md). If null, the application's color scheme is used (either the system default, or one set by [KColorSchemeManager](kcolorschememanager.md)).

### \[explicit\] KStatefulBrush::KStatefulBrush(*const QBrush &*, const QBrush &*background*, *KSharedConfigPtr* = KSharedConfigPtr()) {#KStatefulBrush-6}

Construct a stateful foreground/decoration brush from a specified [QBrush](https://doc.qt.io/qt-6/qbrush.html) (or [QColor](https://doc.qt.io/qt-6/qcolor.html), via [QBrush](https://doc.qt.io/qt-6/qbrush.html)'s implicit constructor). The various states are determined from the base [QBrush](https://doc.qt.io/qt-6/qbrush.html) (which fills in the Active state) according to the same rules used to build stateful color schemes from the system color scheme. The state effects from the given [KConfig](../kconfigcore/kconfig.md) are used (if null, the application's state effects are used).

*background* The background brush (or color) corresponding to the [KColorScheme::NormalBackground](kcolorscheme.md#BackgroundRole-enum) role and [QPalette::Active](https://doc.qt.io/qt-6/qpalette.html#ColorGroup-enum) state for this foreground/decoration color.

### KStatefulBrush::KStatefulBrush(*const KStatefulBrush &*) {#KStatefulBrush-1}

Construct a copy of another [KStatefulBrush](kstatefulbrush.md).

### QBrush KStatefulBrush::brush(*QPalette::ColorGroup*) const {#brush}

Retrieve the brush for the specified widget state. This is used when you know explicitly what state is wanted. Otherwise one of overloads is often more convenient.

### QBrush KStatefulBrush::brush(*const QPalette &*) const {#brush-1}

Retrieve the brush, using a [QPalette](https://doc.qt.io/qt-6/qpalette.html) reference to determine the correct state. Use when your painting code has easy access to the [QPalette](https://doc.qt.io/qt-6/qpalette.html) that it is supposed to be using. The state used in this instance is the [QPalette::currentColorGroup](https://doc.qt.io/qt-6/qpalette.html#currentColorGroup)().

### KStatefulBrush &KStatefulBrush::operator=(*const KStatefulBrush &*) {#operator-eq}

Standard assignment operator
