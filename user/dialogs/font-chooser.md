---
title: Choosing a font
description: Pick a font, its style and size, and its OpenType features, in the Select Font window.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-widgets-addons (src/kfontchooserwidget.ui, kfontchooser.cpp, kfontchooser.h, kfontchooserdialog.cpp); written from the code, not clicked through"
---

# Choosing a font

When you choose a font, for example in the [Fonts](../settings/fonts.md) module of System Settings, the **Select Font** window opens. [Terminal](../applications/terminal.md) uses the same font lists in its own font window, and only offers monospaced fonts there.

- **Font:** The list of installed fonts. Check **Show only monospaced fonts** to list only fonts whose letters are all the same width, as programmers and terminals use. Some windows only offer monospaced fonts, and then the checkbox isn't shown.
- **Font style:** The styles the font comes in, such as **Normal**, **Italic** or **Bold**.
- **Size:** The size in points. Pick one from the list or type your own.
- **Comma separated list of font features (e.g., liga, calt):** Turns on OpenType features that the font offers, by their four-letter tags. For example, `liga` turns on ligatures, where letter pairs such as "fi" are drawn as one shape, and `calt` turns on letters that change shape depending on their neighbours. Which features a font has depends on the font.
- **Sample:** Shows text in the font as it's set now. You can edit it, to see how particular letters or symbols look.

Some windows change several fonts at once, such as **Adjust All Fonts…** in the [Fonts](../settings/fonts.md) module. Then **Font**, **Font style** and **Size** each have a checkbox: only the parts you check are changed, and the others stay as each font had them.

To install new fonts, use the [Font Management](../settings/font-management.md) module.
