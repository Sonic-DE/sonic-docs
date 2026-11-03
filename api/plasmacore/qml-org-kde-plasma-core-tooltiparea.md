---
title: "ToolTipArea QML Type"
description: "An Item managing a Plasma-themed tooltip."
---

# ToolTipArea QML Type

An Item managing a Plasma-themed tooltip. [More...](#details)

- Import Statement: import org.kde.plasma.core
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

It is rendered in its own window. You can either specify icon, [mainText](qml-org-kde-plasma-core-tooltiparea.md#mainText-prop) and [subText](qml-org-kde-plasma-core-tooltiparea.md#subText-prop), or a custom Component that will be put inside the tooltip. By default the tooltip will be rendered when hovering over the parent item.

The item inside the [ToolTipArea](qml-org-kde-plasma-core-tooltiparea.md) is loaded on demand and will be destroyed when the tooltip is being hidden.

Example usage:

```qml
import org.kde.plasma.core as PlasmaCore
import org.kde.kirigami 2.20 as Kirigami

Kirigami.Icon {
    PlasmaCore.ToolTipArea {
        mainText: i18n("Tooltip Title")
        subText: i18n("Some explanation.")
        icon: "plasma"
        // alternatively, you can specify your own component
        // to be loaded when the tooltip shows
        mainItem: YourCustomItem { }
    }
}
```

## Property Documentation {#property-documentation}

### active : bool {#active-prop}

Property that controls if a tooltips will show on mouse over. The default is true.

### containsMouse : bool {#containsMouse-prop}

Returns whether the mouse is inside the item

### hideOnClick : bool {#hideOnClick-prop}

If set to true (default), any click within the tooltiparea will hide the toolip. This is generally the correct behavior for typical tooltips with usage hints. Set it to false to keep the thumbnail open even when the tooltiparea is clicked, which may be appropriate for complex tooltipareas with interior controls and tooltips with specific information or interactive controls.

### icon : var {#icon-prop}

An icon for this tooltip, accepted values are an icon name, a [QIcon](https://doc.qt.io/qt-6/qicon.html), [QImage](https://doc.qt.io/qt-6/qimage.html) or [QPixmap](https://doc.qt.io/qt-6/qpixmap.html)

### image : var {#image-prop}

TODO: single property for images? An image for this tooltip, accepted values are an icon name, a [QIcon](https://doc.qt.io/qt-6/qicon.html), [QImage](https://doc.qt.io/qt-6/qimage.html) or [QPixmap](https://doc.qt.io/qt-6/qpixmap.html)

### interactive : bool {#interactive-prop}

If interactive is false (default), the tooltip will automatically hide itself as soon as the mouse leaves the tooltiparea, if is true, if the mouse leaves tooltiparea and goes over the tooltip itself, the tooltip won't hide, so it will be possible to interact with tooltip contents.

### location : Plasma::Types::Location {#location-prop}

Plasma Location of the dialog window. Useful if this dialog is a popup for a panel

### mainItem : Item {#mainItem-prop}

The item shown inside the tooltip.

### mainText : string {#mainText-prop}

The main text of this tooltip

### subText : string {#subText-prop}

The description of this tooltip

### textFormat : enumeration {#textFormat-prop}

How to handle the text format of the tooltip subtext:

- Text.AutoText (default)
- Text.PlainText
- Text.StyledText
- Text.RichText

> **Note:** in the default implementation the main text is always plain text

### timeout : int {#timeout-prop}

Timeout in milliseconds after which the tooltip will hide itself. Set this value to -1 to never hide the tooltip automatically.

## Signal Documentation {#signal-documentation}

### aboutToShow() {#aboutToShow-signal}

Emitted just before the tooltip dialog is shown.

> **Note:** The corresponding handler is `onAboutToShow`.

### toolTipVisibleChanged(bool *toolTipVisible*) {#toolTipVisibleChanged-signal}

Emitted when the tooltip's visibility changes.

> **Note:** The corresponding handler is `onToolTipVisibleChanged`.

## Method Documentation {#method-documentation}

### void hideImmediately() {#hideImmediately-method}

Hides the tooltip immediately, in comparison to [hideToolTip](qml-org-kde-plasma-core-tooltiparea.md#hideToolTip-method).

### void hideToolTip() {#hideToolTip-method}

Hides the tooltip after a grace period if shown. Does not affect whether the tooltip area is active.

### void showToolTip() {#showToolTip-method}

Shows the tooltip.
