---
title: Registering a drawing tablet
description: Describe a Wacom tablet that SonicDE doesn't recognize, so you can set it up.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-drawing-tablet c885556 (src/tabletfinder/dialog.ui, src/tabletfinder/dialog.cpp, src/tabletfinder/hwbuttondialog.ui, src/tabletfinder/hwbuttondialog.cpp, src/tabletfinder/kde_wacom_tabletfinder.desktop, src/kcmodule/kcmwacomtabletwidget.cpp, src/kcmodule/errorwidget.ui); written from the code, not clicked through"
---

# Registering a drawing tablet

SonicDE knows the details of most Wacom tablets, such as how many buttons they have. If yours isn't in its list, the [Drawing Tablet](../settings/drawing-tablet.md) module in System Settings says **No tablet device detected** and offers **Manually register a tablet device**. That opens the Wacom Tablet finder, where you describe your tablet yourself.

You can also start it from the application launcher, as **Wacom Tablet finder**, or by running `kde_wacom_tabletfinder`. It uses the `xsetwacom` tool to find tablets.

## Describing your tablet

1. Connect your tablet and click **Refresh**. **Detected Tablets:** lists what was found. Pick yours; its **Serial No.:** and **Devices:** are shown below.
2. Under **Tablet Features**, tick what your tablet has: **has TouchRing**, **has Wheel**, **has Touchstrip Left**, **has Touchstrip Right**, **has Status LEDs left** and **has Status LEDs right**.
3. Under **Button mapping**, set the **Number of available Express Keys:**, the buttons on the tablet itself. Then click **Map Hardware Buttons**. A window asks you to press each button on the tablet in turn. Move the mouse pointer inside that window, but don't click into it. When all buttons are detected, close it. The page then shows which button maps to which.
4. Under **Touch sensor**, say how the tablet handles touch:
   - **Normal tablet**, for a tablet with a pen only.
   - **Multi-device tablet, pen sensor. Touch sensor is:** for the pen part of a tablet that also has touch. Choose its touch part from the list.
   - **Multi-device tablet, touch sensor**, for the touch part.
5. Click **Save** to save the selected tablet, or **Save All** to save every tablet in the list.

The details are saved in `~/.config/tabletdblocalrc`. Log out and back in, so the tablet service picks them up. Then set up the tablet in the Drawing Tablet module.
