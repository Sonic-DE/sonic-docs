---
title: "Representation QML Type"
description: "Item to be used as root item for representations (full and compact) of plasmoids."
---

# Representation QML Type

Item to be used as root item for representations (full and compact) of plasmoids. [More...](#details)

- Import Statement: import org.kde.plasma.extras
- Inherits: [Page](../plasmacomponents/qml-org-kde-plasma-components-page.md)

## Detailed Description {#details}

It's a [QtQuickControls2](https://doc.qt.io/qt-6/qtquickcontrols2-module.html) Page, and like that one, has an header, a contentItem and a Footer It may go over the plasmoid edges (both on desktop and popups) with the properties applyHorizontalPadding and applyVerticalPadding. When the contentItem is a [ScrollView](https://doc.qt.io/qt-6/qml-qtquick-controls-scrollview.html) or a Scrollarea, the plasmoid margins will be automatically removed.

This code will create a full representation with a listview that will automatically fill the whole area without margins from the plasmoid popup borders

```qml
Plasmoid.Representation: PlasmaExtras.Representation {
    header: PlasmaExtras.BasicPlasmoidHeading {}
    contentItem: PlasmaComponent.ScrollView {
        ListView {
            // ...
        }
    }
}
```

## Property Documentation {#property-documentation}

### collapseMarginsHint : bool {#collapseMarginsHint-prop}

If true, the representation will remove any borders its container may have put and will be collapsed above its borders
