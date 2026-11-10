---
title: Input Method Panel
description: Control your input method, such as Fcitx or IBus, from a panel widget.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-desktop-interface (applets/kimpanel/qml/main.qml, ContextMenu.qml, ConfigAppearance.qml, main.xml, backend/ibus, layout-templates/org.kde.plasma.desktop.defaultPanel); sonic-silver (layout-templates/org.kde.silver.plasma.desktop.bottomPanel); written from the code, not clicked through"
---

# Input Method Panel

An input method lets you type languages that need more than the keys on your keyboard, such as Chinese, Japanese or Korean: you type, and choose the characters you want from a list of candidates. Input method frameworks such as Fcitx and IBus do the work. The **Input Method Panel** widget shows their status and controls in a [panel](panels.md), and draws the list of candidates while you type.

If your system language usually needs an input method, for example Chinese, Japanese, Korean, Hindi, Thai or Vietnamese, the default panel already has this widget. Otherwise, add it to a panel yourself. It does nothing until an input method framework is installed and running.

## Using it

The widget shows the icons that your input method provides, for example the current input method or language and the input mode.

- Click an icon to use it. Icons that have choices open a menu.
- Right-click an icon for more:
  - **Hide** followed by the icon's name: Removes that icon from the panel. **Show** brings hidden icons back; it appears in this menu once an icon is hidden.
  - **Configure Input Method:** Opens your input method's own settings.
  - **Reload Config:** Makes the input method read its settings again.
  - **Exit Input Method:** Stops the input method.

## Settings

Right-click the widget and open its settings. The **Appearance** page has:

- **Input method list:** Whether the list of candidates is **Vertical** or **Horizontal**. The default is horizontal.
- **Font:** **Use custom:** draws the candidate list in a font of your choice instead of the default font. **Choose Font…** picks the font.
- **Panel icon size:** **Small**, the default, or **Scale with Panel height** (**Scale with Panel width** on a vertical panel), which makes the icons as big as the panel allows.
