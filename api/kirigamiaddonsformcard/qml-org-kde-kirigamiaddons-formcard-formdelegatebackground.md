---
title: "FormDelegateBackground QML Type"
description: "A background for Form delegates."
---

# FormDelegateBackground QML Type

A background for Form delegates. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard

## Detailed Description {#details}

This is a simple background that provides opacity feedback to the user when the control has focus or is currently being pressed, for example.

This is used in [AbstractFormDelegate](qml-org-kde-kirigamiaddons-formcard-abstractformdelegate.md) so that new delegates provide this feedback by default, and can be easily overriden with an Item.

*See also* [AbstractFormDelegate](qml-org-kde-kirigamiaddons-formcard-abstractformdelegate.md)

## Property Documentation {#property-documentation}

### \[required\] control : Control {#control-prop}

The control to which the background will be assigned.
