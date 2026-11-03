---
title: "IconDialog QML Type"
description: "Icon GUI utilities."
---

# IconDialog QML Type

Icon GUI utilities. [More...](#details)

- Import Statement: import org.kde.iconthemes

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### customLocation : string {#customLocation-prop}

Use a custom location, only local directory paths are allowed

### iconName : string {#iconName-prop}

The name or path of the icon the user has selected

### iconSize : int {#iconSize-prop}

The desired size of icons

### modality : enumeration {#modality-prop}

Window modality, default is Qt.NonModal

### title : string {#title-prop}

The title to use for the dialog

### user : bool {#user-prop}

Begin with the "user icons" instead of "system icons"

### visible : string {#visible-prop}

Whether the dialog is currently visible, setting this property to true is the same as calling show()

## Method Documentation {#method-documentation}

### void close() {#close-method}

### void open() {#open-method}
