---
title: "ContextualHelpButton QML Type"
description: "An inline help button that shows a tooltip when clicked, made for desktop use."
---

# ContextualHelpButton QML Type

An inline help button that shows a tooltip when clicked, made for desktop use. [More...](#details)

- Inherits: [ToolButton](../plasmacomponents/qml-org-kde-plasma-components-toolbutton.md)

## Detailed Description {#details}

Use this component when you want to explain details or usage of a feature of the UI, but the explanation is too long to fit in an inline label, and too important to put in a hover tooltip and risk the user missing it.

Example usage:

```qml
import QtQuick.Layouts
import org.kde.plasma.extras as PlasmaExtras

RowLayout {
    spacing: Kirigami.Units.smallSpacing

    PlasmaComponents.CheckBox {
        text: i18ndc("your_app_name", "@option:check", "Allow screen tearing in fullscreen windows")
    }

    PlasmaExtras.ContextualHelpButton {
        toolTipText: i18ndc("your_app_name", "@info:tooltip", "With most displays, screen tearing reduces latency at the cost of some visual fidelity at high framerates. Note that not all graphics drivers support this setting.")
    }
}
```

## Property Documentation {#property-documentation}

### toolTipText : string {#toolTipText-prop}

The text to display inside the contextual help tooltip.

### toolTipVisible : bool {#toolTipVisible-prop}
