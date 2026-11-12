---
title: "FormRadioSelectorDelegate QML Type"
description: "A FormCard delegate that allows switching between multiple options."
---

# FormRadioSelectorDelegate QML Type

A [FormCard](qml-org-kde-kirigamiaddons-formcard-templates-formcard.md) delegate that allows switching between multiple options. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard
- Inherits: [AbstractFormDelegate](qml-org-kde-kirigamiaddons-formcard-abstractformdelegate.md)

## Detailed Description {#details}

This wraps a [RadioSelector](../kirigamiaddonscomponents/qml-org-kde-kirigamiaddons-components-templates-radioselector.md).

Example:

```qml
FormCard.FormRadioSelectorDelegate {
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

### actions : alias {#actions-prop}

This property holds a list of actions, each holding one of the options.

### consistentWidth : bool {#consistentWidth-prop}

This property holds whether all the items should have the same width.

### selectedIndex : int {#selectedIndex-prop}

This property holds the currently selected option.
