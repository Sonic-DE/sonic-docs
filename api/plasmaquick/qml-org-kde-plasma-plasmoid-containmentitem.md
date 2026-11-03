---
title: "ContainmentItem QML Type"
description: "This class is exposed to containments QML as the attached property Plasmoid."
---

# ContainmentItem QML Type

This class is exposed to containments QML as the attached property Plasmoid. [More...](#details)

- Import Statement: import org.kde.plasma.plasmoid
- Inherits: [PlasmoidItem](qml-org-kde-plasma-plasmoid-plasmoiditem.md)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### loading : bool {#loading-prop}

True if the UI is still loading, for instance a desktop which doesn't have its wallpaper yet

### wallpaper : WallpaperItem {#wallpaper-prop}

## Method Documentation {#method-documentation}

### QPointF adjustToAvailableScreenRegion(int *x*, int *y*, int *w*, int *h*) {#adjustToAvailableScreenRegion-method}

Given a geometry, it adjusts it moving it completely inside of the boundaries of availableScreenRegion Returns the toLeft point of the rectangle

### QtObject containmentItemAt(int *x*, int *y*) {#containmentItemAt-method}

Search for a containment at those coordinates. the coordinates are passed as local coordinates of \*this\* containment

### AppletQuickItem itemFor(var *applet*) {#itemFor-method}

Returns the corresponding [PlasmoidItem](qml-org-kde-plasma-plasmoid-plasmoiditem.md) of one of its applets

### void processMimeData(QMimeData *data*, int *x*, int *y*, var *dropJob*) {#processMimeData-method}

Process the mime data arrived to a particular coordinate, either with a drag and drop or paste with middle mouse button

### void processMimeData(QtObject *data*, int *x*, int *y*, var *dropJob*) {#processMimeData-method-1}

Process the mime data arrived to a particular coordinate, either with a drag and drop or paste with middle mouse button
