---
title: "SimpleKCM QML Type"
description: "This component is intended to be used as root item for KCMs with arbitrary content."
---

# SimpleKCM QML Type

This component is intended to be used as root item for KCMs with arbitrary content. [More...](#details)

- Import Statement: import org.kde.kcmutils
- Inherits: [ScrollablePage](../kirigami/qml-org-kde-kirigami-scrollablepage.md)

## Detailed Description {#details}

Often a Kirigami.[FormLayout](../kirigami/qml-org-kde-kirigami-layouts-formlayout.md) is used as main element.

It is possible to specify a header and footer component.

```qml
import org.kde.kcmutils as KCMUtils
import org.kde.kirigami as Kirigami

KCMUtils.SimpleKCM {
    Kirigami.FormLayout {
       TextField {
          Kirigami.FormData.label: "Label:"
       }
       TextField {
          Kirigami.FormData.label: "Label:"
       }
    }
    footer: Item {...}
}
```

## Property Documentation {#property-documentation}

### \[default: false\] headerPaddingEnabled : bool {#headerPaddingEnabled-prop}

Whether the contents of the header will have automatic padding around it.

Should be disabled when using an [InlineMessage](../kirigami/qml-org-kde-kirigami-inlinemessage.md) or custom content item in the header that's intended to touch the window edges.

### \[read-only\] margins : int {#margins-prop}
