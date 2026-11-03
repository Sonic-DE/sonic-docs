---
title: "AbstractKCM QML Type"
description: "This component is intended to be used as root item for KCMs with arbitrary content. This type was introduced in Qt 6.0."
---

# AbstractKCM QML Type

This component is intended to be used as root item for KCMs with arbitrary content. This type was introduced in Qt 6.0. [More...](#details)

- Import Statement: import org.kde.kcmutils
- Since: Qt 6.0
- Inherited By: [GridViewKCM](qml-org-kde-kcmutils-gridviewkcm.md) and [ScrollViewKCM](qml-org-kde-kcmutils-scrollviewkcm.md)

## Detailed Description {#details}

Unlike [SimpleKCM](qml-org-kde-kcmutils-simplekcm.md) this does NOT provide a scrollable view, the developer will have to manage their own scrollviews.

Most of the times [SimpleKCM](qml-org-kde-kcmutils-simplekcm.md) should be used instead.

```qml
import QtQuick
import QtQuick.Controls as QQC2
import QtQuick.Layouts
import org.kde.kcmutils as KCMUtils

KCMUtils.AbstractKCM {
    RowLayout {
        QQC2.ScrollView { }
        QQC2.ScrollView { }
    }
    footer: QQC2.ToolBar { }
}
```

## Property Documentation {#property-documentation}

### \[default: true\] footerPaddingEnabled : bool {#footerPaddingEnabled-prop}

Whether the contents of the footer will have automatic padding around it.

Should be disabled when using an InlineMessage or custom content item in the footer that's intended to touch the window edges.

### forceFooterSeparator : bool {#forceFooterSeparator-prop}

\*

Whether to always draw a separator line between main content and footer. \* \* [AbstractKCM](qml-org-kde-kcmutils-abstractkcm.md) usually does not draw a separator line above the footer. Enable \* this to draw a separator line; this is generally recommended if you have \* a custom footer, in plaricular in a [ScrollViewKCM](qml-org-kde-kcmutils-scrollviewkcm.md) or [GridViewKCM](qml-org-kde-kcmutils-gridviewkcm.md).

### forceHeaderSeparator : bool {#forceHeaderSeparator-prop}

\*

Whether to always draw a separator line between header and main content. \* \* Usually, a separator will only be inserted if extra content is added to \* the header, as it would be redundant with the header that Kirigami.PageRow \* draws, and if [framedView](qml-org-kde-kcmutils-abstractkcm.md#framedView-prop) is false as otherwise the view provides the \* separator. Enable this to have [AbstractKCM](qml-org-kde-kcmutils-abstractkcm.md) always draw a separator line.

### \[default: true\] framedView : bool {#framedView-prop}

Whether to use this component as the base of a "framed" KCM with an inner scrollview that draws its own frame.

### \[default: true\] headerPaddingEnabled : bool {#headerPaddingEnabled-prop}

Whether the contents of the header will have automatic padding around it.

Should be disabled when using an InlineMessage or custom content item in the header that's intended to touch the window edges.

### \[read-only\] margins : int {#margins-prop}

### sidebarMode : bool {#sidebarMode-prop}
