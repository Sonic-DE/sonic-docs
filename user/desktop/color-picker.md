---
title: Color Picker
description: Capture the color of anything on your screen and copy it in the format you need.
source_url: https://userbase.kde.org/Plasma/ColorPicker
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-workspace-addons (applets/colorpicker/main.xml, qml/); read from code, not clicked through"
---

# Color Picker

![The Color Picker widget](images/color-picker.png)

Use this widget to capture the color of something on your screen.

When you work in a graphics editor, there is usually a tool for picking a color from the image you have open. But if you're working in a browser and want to know about a color on a web page, you need the Color Picker widget.

> **Tip:** See [Installing widgets](installing-widgets.md) for how to add it, if it's not in your **Add Widgets** list.

Like all widgets, you can make it bigger or smaller, though it doesn't shrink below the size of its icons.

## Picking a color

To choose a color, click the upper icon, which shows a small dropper (its tooltip says **Pick color**). Crosshairs appear on the screen. Move them with your mouse or touchpad until they center on the color you want, then click the left mouse button.

The color you clicked appears in the lower circle icon as a visible patch, and is added to the top of the widget's history. The history keeps the last nine colors. By default, the color is also copied to the clipboard straight away, in the default format.

Picking needs desktop effects. If compositing is turned off, the dropper icon is disabled, and an empty history says **Color picking unavailable when compositing is disabled** and offers **Configure Compositing**, which opens the [Compositor](../settings/compositor.md) module.

You can also add colors without picking them from the screen:

- Drag a color code, such as `#bac4bd`, onto the widget to save it.
- Drag an image file onto the widget to save the image's average color.
- Right-click the widget and choose **Open Color Dialog** to choose a color in a color dialog.

## Using the history

Click the color circle, or right-click the widget and choose **View History**, to see the colors you picked.

![Recently captured colors](images/color-picker-history.png)

- **Left-click** a color to copy it in the default format. The color's label briefly says **Copied!**
- **Right-click** a color to see it in every format, under **Copy to Clipboard**. Click one to copy it in that format.
- The **Delete** button that appears when you hover over a color removes it from the history. The Delete key does the same for the selected color.
- Drag a color into another application to drop it there.

Middle-clicking the color circle copies the most recent color in the default format, without opening the history. To remove every color at once, right-click the widget and choose **Clear History**.

![Formats of captured colors](images/color-picker-format.png)

The formats on offer are decimal values (`186, 196, 189`), `rgb(…)`, `rgba(…)`, hexadecimal in upper or lower case with or without the leading `#`, Qt's `Qt.rgba(…)` and a LaTeX `\definecolor` line.

For example, say you want to pick a color on the screen to use in an image editor. Pick the color, then click the color circle, right-click the color and choose the HTML format `#bac4bd`. Then switch to your image editor, click its foreground color tool, and paste the color into the dialog. The application you use may need a different format. In the worst case, you can type the numbers yourself when it gives you a separate field for each decimal value of red, green and blue (RGB), here 186, 196, 189.

## Settings

Right-click the widget and choose **Configure Color Picker...** to change these:

- **Default color format:** The format used when a picked color is copied automatically, when you left-click a color in the history and when you middle-click the color circle. The default is hexadecimal in capitals, `#RRGGBB`.
- **Automatically copy color to clipboard:** Copies each color you pick, in the default format. On by default.
- **When pressing the keyboard shortcut:** What the widget's keyboard shortcut does: **Pick a color** (the default) or **Show history**. Set the shortcut itself on the **Keyboard Shortcuts** page of the same window.
- **Preview count:** How many recent colors the widget shows in a panel, from 0 to 9. The default is 1.
