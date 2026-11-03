---
title: "OverlaySheet QML Type"
description: "An overlay sheet that covers the current Page content."
---

# OverlaySheet QML Type

An overlay sheet that covers the current Page content. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [Popup](https://doc.qt.io/qt-6/qml-qtquick-controls-popup.html)

## Detailed Description {#details}

[OverlaySheet](qml-org-kde-kirigami-overlaysheet.md) is used for auxiliary display of narrow, read-only, scrollable content. For more details, see [ https://develop.kde.org/hig/displaying_content/#page-vs-dialog-vs-overlaysheet ](https://develop.kde.org/hig/displaying_content/#page-vs-dialog-vs-overlaysheet).

Can be dismissed with a touch swipe when scrolled to the top or bottom.

> **Note:** [OverlaySheet](qml-org-kde-kirigami-overlaysheet.md) needs a single child item defined. Do not override its `contentItem`.

Example usage:

```qml
Kirigami.OverlaySheet {
   ColumnLayout { ... }
}
Kirigami.OverlaySheet {
   ListView { ... }
}
```

## Property Documentation {#property-documentation}

### footer : Item {#footer-prop}

An optional item which will be used as the sheet's footer, and always kept on screen.

default: `null`

### header : Item {#header-prop}

This property holds an optional item which will be used as the sheet's header, and will always be displayed.

default: `null`

### showCloseButton : bool {#showCloseButton-prop}

This property sets the visibility of the close button in the top-right corner.

default: Only shown in desktop mode

### title : string {#title-prop}

A title to be displayed in the header of this Sheet.

default: empty string, and no header text will be displayed
