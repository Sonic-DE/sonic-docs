---
title: "SizeGroup QML Type"
description: "SizeGroup is a utility object that makes groups of items request the same size."
---

# SizeGroup QML Type

[SizeGroup](qml-org-kde-kirigami-layouts-sizegroup.md) is a utility object that makes groups of items request the same size. [More...](#details)

- Import Statement: import org.kde.kirigami.layouts

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### items : list\<Item\> {#items-prop}

Which items this [SizeGroup](qml-org-kde-kirigami-layouts-sizegroup.md) should adjust

### mode : enumeration {#mode-prop}

Which dimensions this [SizeGroup](qml-org-kde-kirigami-layouts-sizegroup.md) should adjust.

Possible values are:

- None: [SizeGroup](qml-org-kde-kirigami-layouts-sizegroup.md) does nothing
- Width: [SizeGroup](qml-org-kde-kirigami-layouts-sizegroup.md) syncs item widths
- Height: [SizeGroup](qml-org-kde-kirigami-layouts-sizegroup.md) syncs item heights
- Both: [SizeGroup](qml-org-kde-kirigami-layouts-sizegroup.md) syncs both item widths and heights

## Method Documentation {#method-documentation}

### void relayout() {#relayout-method}

Forces the [SizeGroup](qml-org-kde-kirigami-layouts-sizegroup.md) to relayout items.

Normally this is never needed as the [SizeGroup](qml-org-kde-kirigami-layouts-sizegroup.md) automatically relayout items as they're added and their sizes change.
