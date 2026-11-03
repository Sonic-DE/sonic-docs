---
title: "DisplayHint QML Type (Singleton)"
description: "Hints for implementations using Actions indicating preferences about how to display the action."
---

# DisplayHint QML Type (Singleton)

Hints for implementations using Actions indicating preferences about how to display the action. [More...](#details)

- Import Statement: import org.kde.kirigami.layouts

> **Note:** **Note:** This type is a QML singleton. There is only one instance of this type in the QML engine.

## Detailed Description {#details}

This is a singleton type.

Possible hint values are:

- NoPreference: Indicates there is no specific preference.
- IconOnly: Only display an icon for this Action
- KeepVisible: Try to keep the action visible even when space constrained. Mutually exclusive with AlwaysHide, KeepVisible has priority.
- AlwaysHide: If possible, hide the action in an overflow menu or similar location. Mutually exclusive with KeepVisible, KeepVisible has priority.
- HideChildIndicator: When this action has children, do not display any indicator (like a menu arrow) for this action.

## Method Documentation {#method-documentation}

### bool displayHintSet(DisplayHints *values*, Hint *hint*) {#displayHintSet-method}

Helper function to check if a certain display hint has been set.

This function is mostly convenience to enforce certain behaviour of the various display hints, primarily the mutual exclusivity of KeepVisible and AlwaysHide.

`values` The display hints to check.

`hint` The display hint to check if it is set.

Return `true` if the hint was set for this action, false if not.

### bool displayHintSet(QtObject *object*, Hint *hint*) {#displayHintSet-method-1}

Check if a certain display hint has been set on an object.

This overloads [displayHintSet](qml-org-kde-kirigami-layouts-displayhint.md#displayHintSet-method)(DisplayHints, Hint) to accept a [QObject](https://doc.qt.io/qt-6/qobject.html) instance. This object is checked to see if it has a displayHint property and if so, if that property has `hint` set.

`object` The object to check.

`hint` The hint to check for.

Returns `false` if object is null, object has no displayHint property or the hint was not set. `true` if it has the property and the hint is set.
