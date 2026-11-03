---
title: "AbstractMaximizeComponent QML Type"
description: "A popup that covers the entire window to show a content item."
---

# AbstractMaximizeComponent QML Type

A popup that covers the entire window to show a content item. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.labs.components
- Inherits: [Popup](https://doc.qt.io/qt-6/qml-qtquick-controls-popup.html)
- Inherited By: [AlbumMaximizeComponent](qml-org-kde-kirigamiaddons-labs-components-albummaximizecomponent.md)

## Detailed Description {#details}

This component is designed to show a content item at the maximum size the application window will allow. The typical use is for showing a maximized image or other piece of media in an application, but it could be any item if desired.

The popup also has a header bar which has a writable title, an optional leading item to the left, a list of custom actions specified by the actions property and an optional footer item.

## Property Documentation {#property-documentation}

### actions : alias {#actions-prop}

List of top row actions.

Each action will be allocated a [ToolButton](https://doc.qt.io/qt-6/qml-qtquick-controls-toolbutton.html) on the top row. All actions are right aligned and appear next to the close button which is always present so does not require specifying.

### content : Item {#content-prop}

The main content item in the view.

The item will be the sized to fit the available space. If the item is larger than the available space it will be shrunk to fit.

> **Note:** If stretching the item isn't desirable the user needs to manage this, e.g. with a holding item. See [ImageMaximizeDelegate](qml-org-kde-kirigamiaddons-labs-components-imagemaximizedelegate.md) for an example.

*See also* [ImageMaximizeDelegate](qml-org-kde-kirigamiaddons-labs-components-imagemaximizedelegate.md)

### footer : Item {#footer-prop}

Item at the bottom under the content.

### leading : Item {#leading-prop}

Item to the left of the overlay title.

### subtitle : string {#subtitle-prop}

The subtitle of the overlay window.

The label will be hidden and the title centered if this is not provided.

### title : string {#title-prop}

The title of the overlay window.
