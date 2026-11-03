---
title: "Containment QML Type"
description: "The base class for plugins that provide backgrounds and applet grouping containers."
---

# Containment QML Type

The base class for plugins that provide backgrounds and applet grouping containers. [More...](#details)

- Import Statement: import org.kde.plasma.plasmoid

## Detailed Description {#details}

Containment objects provide the means to group applets into functional sets. They also provide the following:

- creation of focusing event
- drawing of the background image (which can be interactive)
- form factors (e.g. panel, desktop, full screen, etc)
- applet layout management

Since Containment is itself a Plasmoid (native C++ class [Plasma::Applet](../plasma/plasma-applet.md)), all the techniques used for writing the visual presentation of Plasmoids is applicable to Containments. Containments are differentiated from Plasmoids by being marked with the ServiceType of Plasma/Containment. Plugins registered with both the Applet and the Containment ServiceTypes can be loaded for use in either situation.

## Attached Property Documentation {#attached-property-documentation}

### Containment.Type : enumeration {#Type-attached-prop}

The type of the Containment.

This value is specified in the "X-Plasma-ContainmentType" JSON-metadata value of containments.

| Constant |   |
| --- | --- |
| NoContainment |   |
| Desktop | Main containments that will own a screen in a mutually exclusive fashion. |
| Panel | A desktop panel. Multiple can be present per screen. |
| Custom | A containment that is neither a desktop nor a panel but something application specific. |
| CustomPanel | A customized desktop panel. "CustomPanel" in metadata. |
| CustomEmbedded | A customized containment embedded into another applet. |

### Containment.activity : string {#activity-attached-prop}

Activity UID of this containment.

### Containment.activityName : string {#activityName-attached-prop}

Activity name of this containment.

### Containment.applets : list\<Plasmoid\> {#applets-attached-prop}

List of plasmoids in this containment.

### Containment.availableScreenRect : rect {#availableScreenRect-attached-prop}

Screen area used by the Containment by itself (free of enveloping panels).

The coordinates are relative to the containment (that is, x:0 and y:0 match the Containment's upper left corner), and independent from the screen position.

For more precise available geometry use availableScreenRegion().

### Containment.availableScreenRegion : list\<rect\> {#availableScreenRegion-attached-prop}

A list of rectangles matching the available region of this screen, panels excluded.

### Containment.containmentDisplayHints : Plasma.Types.ContainmentDisplayHints {#containmentDisplayHints-attached-prop}

### Containment.containmentType : Containment.Type {#containmentType-attached-prop}

Type of this containment.

### Containment.corona : Plasma::Corona {#corona-attached-prop}

The corona for this contaiment.

### Containment.isUiReady : bool {#isUiReady-attached-prop}

### Containment.screen : int {#screen-attached-prop}

The screen number this containment is serving as the desktop for, or -1 if none

### Containment.screenGeometry : rect {#screenGeometry-attached-prop}

Provides access to the geometry of the screen the plasmoid is in.

Can be useful to figure out what's the absolute position of the plasmoid.

### Containment.wallpaperGraphicsObject : QObject {#wallpaperGraphicsObject-attached-prop}

### Containment.wallpaperPlugin : string {#wallpaperPlugin-attached-prop}

## Method Documentation {#method-documentation}

### void addApplet(Plasma::Applet *applet*, rect *geometryHint* = rect) {#addApplet-method}

Adds an existing `applet` (plasmoid) to this Containment with the given `geometryHint`.

The hint determines the preferred location and size for the newly created plasmoid. The hint will not be respected if it's not possible to position it in the preferred location.
