---
title: "FormDelegateSeparator QML Type"
description: "A context-aware separator."
---

# FormDelegateSeparator QML Type

A context-aware separator. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard

## Detailed Description {#details}

This is a standard [Kirigami.Separator](../kirigami/qml-org-kde-kirigami-primitives-separator.md) that can be hidden upon hovering the mouse over the [above](qml-org-kde-kirigamiaddons-formcard-formdelegateseparator.md#above-prop) or [below](qml-org-kde-kirigamiaddons-formcard-formdelegateseparator.md#below-prop) delegate, allowing for a subtle but smooth animation feedback.

Its two properties are particularly useful when it is not immediately known which delegate will fill the [above](qml-org-kde-kirigamiaddons-formcard-formdelegateseparator.md#above-prop) or [below](qml-org-kde-kirigamiaddons-formcard-formdelegateseparator.md#below-prop) position, such as delegates provided from a model or managed by a Loader.

*See also* [Kirigami.Separator](../kirigami/qml-org-kde-kirigami-primitives-separator.md)

## Property Documentation {#property-documentation}

### above : Item {#above-prop}

The delegate immediately above the separator.

### below : Item {#below-prop}

The delegate immediately below the separator.
