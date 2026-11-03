---
title: "RadioSelector QML Type"
description: "A Component that allows switching between multiple options."
---

# RadioSelector QML Type

A Component that allows switching between multiple options. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.components
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

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

## Property Documentation {#property-documentation}

### actions : list\<Action\> {#actions-prop}

This property holds a list of actions, each holding one of the options.

### \[default: false\] consistentWidth : bool {#consistentWidth-prop}

This property holds whether all the items should have the same width.

### selectedIndex : int {#selectedIndex-prop}

This property holds the currently selected option.

By default, it's the first actions or -1 if no actions is set.
