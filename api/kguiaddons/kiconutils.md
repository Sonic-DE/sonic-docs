---
title: "KIconUtils Namespace"
description: "Provides utility functions for icons."
---

# KIconUtils Namespace

Provides utility functions for icons. [More...](#details)

- Header: KIconUtils
- CMake: find\_package(KF6 REQUIRED COMPONENTS GuiAddons) target\_link\_libraries(mytarget PRIVATE KF6::GuiAddons)

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### QIcon KIconUtils::addOverlay(const QIcon &*icon*, const QIcon &*overlay*, Qt::Corner *position*) {#addOverlay}

Adds the `overlay` over the `icon` in the specified `position`

The `overlay` icon is scaled down approx. to 1/3 or 1/4 (depending on the icon size) and placed in one of the corners of the base icon.

### QIcon KIconUtils::addOverlays(const QIcon &*icon*, const QHash\<Qt::Corner, QIcon\> &*overlays*) {#addOverlays}

Adds `overlays` over the `icon`

The `overlays` is a [QHash](https://doc.qt.io/qt-6/qhash.html#qhash) of [Qt::Corner](https://doc.qt.io/qt-6/qt.html#Corner-enum) and [QIcon](https://doc.qt.io/qt-6/qicon.html). The [Qt::Corner](https://doc.qt.io/qt-6/qt.html#Corner-enum) value decides where the overlay icon will be painted, the [QIcon](https://doc.qt.io/qt-6/qicon.html) value is the overlay icon to be painted.

The overlay icon is scaled down to 1/3 or 1/4 (depending on the icon size) and placed in one of the corners of the base icon.

### QIcon KIconUtils::addOverlays(const QIcon &*icon*, const QStringList &*overlays*) {#addOverlays-1}

Adds up to four overlays over the `icon`.

The `overlays` is a [QStringList](https://doc.qt.io/qt-6/qstringlist.html) of icon names (e.g. the emblems that are drawn on icons in Dolphin and KFileWidget, e.g. symlink, un-mounted device ...etc).

Overlays are added in this order:

- first icon is used to paint an overlay on the bottom-right corner
- second icon on the bottom-left corner
- third icon on the top-left corner
- fourth icon on the top-right corner

Each overlay icon is scaled down to 1/3 or 1/4 (depending on the icon size).

### QIcon KIconUtils::addOverlays(const QString &*iconName*, const QStringList &*overlays*) {#addOverlays-2}

Adds up to four overlays on the icon constructed from `iconName`.

The `overlays` is a [QStringList](https://doc.qt.io/qt-6/qstringlist.html) of icon names (e.g. the emblems that are drawn on icons in Dolphin and KFileWidget, e.g. symlink, un-mounted device ...etc).

Overlays are added in this order:

- first icon is used to paint an overlay on the bottom-right corner
- second icon on the bottom-left corner
- third icon on the top-left corner
- fourth icon on the top-right corner

Each overlay icon is scaled down to 1/3 or 1/4 (depending on the icon size).

All [QIcon](https://doc.qt.io/qt-6/qicon.html) objects are constructed using [QIcon::fromTheme](https://doc.qt.io/qt-6/qicon.html#fromTheme)().
