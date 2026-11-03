---
title: "CategorizedSettings QML Type"
description: "A container for setting actions showing them in a list view and displaying the actual page next to it. This type is deprecated. We strongly advise against using it in new code."
---

# CategorizedSettings QML Type

A container for setting actions showing them in a list view and displaying the actual page next to it. **This type is deprecated. We strongly advise against using it in new code.** [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.settings
- Inherits: [PageRow](../kirigami/qml-org-kde-kirigami-pagerow.md)
- Status: Deprecated

**This type is deprecated. We strongly advise against using it in new code.**

## Detailed Description {#details}

To open a setting page, you should use PageRow::pushDialogLayers.

Since 1.3.0, use ConfigurationsView instead.

## Property Documentation {#property-documentation}

### actions : list\<Kirigami.PagePoolAction\> {#actions-prop}

The list of pages for the settings.

### defaultPage : string {#defaultPage-prop}

The default page that will be shown when opened.

This only applies when the categorized settings object is wide enough to show multiple pages.

*See also* [actions](qml-org-kde-kirigamiaddons-settings-categorizedsettings.md#actions-prop)
