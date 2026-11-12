---
title: "RadioSelector QML Type"
description: "A Component that allows switching between multiple options."
---

# RadioSelector QML Type

A Component that allows switching between multiple options. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.components
- Inherits: [RadioSelector](qml-org-kde-kirigamiaddons-components-templates-radioselector.md)

## Detailed Description {#details}

Example:

```qml
Components.RadioSelector {
  consistentWidth: false
  actions: [
      Kirigami.Action {
          text: i18nc("@option:radio", "Week")
          icon.name: "view-calendar-week-symbolic"
      },
      Kirigami.Action {
          text: i18nc("@option:radio", "3 Days")
          icon.name: "view-calendar-upcoming-days-symbolic"
      },
      Kirigami.Action {
          text: i18nc("@option:radio", "1 Day")
          icon.name: "view-calendar-day-symbolic"
      }
  ]
}
```
