---
title: Search widget
description: Search for applications, files and more from a widget on a panel or the desktop.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-file-search-ui (plasmoid/main.qml, plasmoid/SearchField.qml, plasmoid/metadata.json); written from the code, not clicked through"
---

# Search widget

The **Search** widget ("Search and launch") puts a search field on a [panel](panels.md) or the desktop. It finds the same things as [KRunner](krunner.md): applications, files, settings, calculations and more, depending on which search plugins are turned on.

Add it like any other widget. In a panel, it shows as an icon: click it to open the search field. On the desktop, when there's enough room, the search field shows directly.

## Searching

- Type in the **Search…** field. Results appear below it, or above it when the widget is on a bottom panel, as you type.
- Use the Up and Down arrow keys to move through the results, and Return to open the selected one. Clicking a result opens it too.
- After you open a result, the search field is cleared and the widget closes.
- Escape clears the field. If it's already empty, Escape closes the widget.

The widget has no settings of its own. To choose what it searches, turn search plugins on or off in the [Search](../settings/search.md) settings.
