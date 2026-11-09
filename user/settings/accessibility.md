---
title: Accessibility
description: Zoom, system bell, keyboard filters, screen reader and other accessibility options.
source_url: https://invent.kde.org/plasma/plasma-desktop/-/blob/master/doc/kcontrol/kcmaccess/index.docbook
source_authors: [Mike McBride]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-desktop-interface fad996458a (kcms/access), xkeyboard-config compat/mousekeys; read from code, not clicked through"
---

# Accessibility

This module helps people who have difficulty seeing the screen, hearing audible cues or using a keyboard. Its pages are listed in the module's own sidebar.

## Zoom & Magnifier

The zoom and magnifier tools enlarge parts of the screen, like a digital magnifying glass. **Zoom** switches between **Full screen**, **Magnify region** and **Disabled**.

### Full screen

- **Show pixel grid at zoom level:** Above this level, a thin grid is drawn around each pixel, so you can see exactly where one ends and the next begins.
- **Pointer appearance:** **Scale**, **Keep** or **Hide** the mouse pointer when zooming.
- **Pointer tracking:**
  - **Proportional:** The zoom area moves in sync with the pointer.
  - **Centered:** The pointer stays centered on-screen, except near screen edges.
  - **Centered (Strict):** The pointer stays centered on-screen, even near screen edges.
  - **Push:** The pointer pushes the zoom area at screen edges.
  - **Disabled:** The zoom area doesn't follow the pointer.
- **Sharpen screen content while zoomed in:** Tries to scale the shape of text and icons at extreme zoom levels. This improves contrast at the cost of font accuracy, by avoiding blur or pixelation.
- **Enable focus tracking:** The magnified area follows the focused part of the interface, even if your mouse isn't moving.
- **Enable text caret tracking:** The magnified area follows the text cursor, which helps when you're typing far from where your mouse is resting.

### Magnify region

**Width** and **Height** set the size of the magnified area.

### Common options

**Zoom factor** adjusts how much the screen enlarges with each step. **Configure Shortcuts…** sets the shortcuts that control zoom.

The module also shows **Scroll gesture modifier keys**, but zoom scroll gestures aren't available on X11.

## System Bell

- **Audible bell:** **Enable** turns the system bell on or off. **Custom sound** plays an audio file of your choice instead.
- **Visual bell:** For people who have difficulty hearing the bell, or who have a silent computer, this gives a visual signal when the bell would sound. Choose **Invert screen colors**, or **Flash screen** with a color. **Duration** sets how long it lasts.

## Modifier Keys

- **Sticky keys:** Modifier keys like Ctrl, Shift, Alt and Meta act as though they stick in place, so you don't need to hold them down when typing a shortcut. For example, Ctrl+Alt+Del can be done with Ctrl, then Alt, then Del.
- **Lock sticky keys:** Pressing a modifier key twice keeps it active until you press it again. For example, press Shift twice, then F, and you get Shift+F. Type P and you get Shift+P. Press Shift again to release it. Without this option, the second letter would be typed without Shift.
- **Disable when two keys are held down:** Turns sticky keys off if you press two keys together.
- **Ring system bell when modifier keys are used.**
- **Feedback:** **Ring system bell when locking keys are used**, for Caps Lock, Num Lock and Scroll Lock, and **Show notification when modifier or locking keys are used**. **Configure Notifications…** edits these notifications.

## Keyboard Filters

- **Slow keys:** A key has to be held for the set **Delay** before it's accepted, which prevents accidental keystrokes. You can ring the system bell when a key is pressed, accepted or rejected.
- **Bounce keys:** Ignores rapid, repeated presses of the same key within the set **Delay**, which prevents accidental multiple keystrokes. **Ring system bell when rejected** gives an audible signal.

## Mouse Navigation

**Use number pad to move pointer** makes the number pad work like a mouse. This may be useful on a device without another pointing device, or if you have no other use for the number pad.

The keys move in the direction you'd expect, including diagonally. The 5 key clicks a pointer button. You change which button with the / key (left), the \* key (middle) and the - key (right). The + key double-clicks the selected button. The 0 key holds it down for dragging, and the . key releases it.

- **Acceleration delay:** The time between the first key press and the first repeated movement.
- **Repeat interval:** The time between repeated movements.
- **Acceleration time:** The time before the pointer reaches its maximum speed.
- **Maximum speed:** The fastest the pointer can move, in pixels per second.
- **Pointer acceleration:** How much acceleration is applied.

## Dwell Clicker

This clicks for you when you hold the mouse pointer still, for people who find pressing mouse buttons hard. **Click when pointer remains still** turns it on. **Motion Threshold**, **Delay Time**, **Dwell Time** and **Dwell Color** set how still the pointer has to be, how long it waits and the color of the ring that shows the click coming. See [Dwell clicking](../accessibility/dwell-clicking.md) for how to use it and choose the type of click.

## Activation Shortcuts

**Activation shortcuts** turns on keyboard gestures for these features:

- Press Shift 5 times to enable Sticky Keys.
- Hold Shift for 8 seconds to enable Slow Keys.

**Disable sticky and slow keys after** turns them off after a period of inactivity.

**When a shortcut is used** you can have it **Display a confirmation dialog**, **Ring the system bell** or **Show a notification**. **Configure Notifications…** edits the notifications.

## Screen Reader

Screen reading uses the Orca screen reader, and this page tells you if it isn't installed. You also need `speech-dispatcher` and a text-to-speech synthesizer such as `espeak`. Test that sound works using the command `spd-say hello` in a terminal.

Check **Enable Screen Reader**, then log out and start your desktop session again. **Launch Orca Screen Reader Configuration…** opens Orca's own settings.

To use the desktop itself, make sure the application menu has a keyboard shortcut, Alt+F1 for example. When you press it, the menu should open and be read as you navigate it with the arrow keys.

## Color Blindness Correction

This helps people with color vision deficiencies tell colors apart on the screen. It shifts problematic colors into parts of the spectrum you can see more clearly, which restores contrast that would otherwise be lost, such as green for success and red for error. It works at the window manager level, so it applies to everything on the screen.

- **Problematic colors:** Choose **Red & purple (Protanopia)**, **Green & purple (Deuteranopia)**, **Yellow, green & purple (Tritanopia)** or **All (grayscale mode)**.
- **Intensity:** Adjusts the strength of the shift from mild to intense. Color vision is a spectrum, so you can fine-tune this to your own.
- **Adjusted colors:** Swatches let you check the result.

> [!NOTE]
> These filters are for accessibility, not color-accurate work like photo editing or digital painting, because the colors on the screen no longer match those of the files you're viewing.

## Invert

This flips the colors of the screen, turning white to black, blue to orange, and so on. It's handled by the window manager as a post-processing effect.

For people with light sensitivity or certain types of low vision, a bright screen can be painful or make text blurry. Inverting turns bright backgrounds dark and dark text light, which reduces the light from the monitor while keeping the contrast needed to read. It can also act as a universal dark mode for software that doesn't have one.

**Enable** turns on the effect, and **Configure Shortcuts…** sets the shortcuts that toggle inverting display and window colors.

## Shake Pointer

This helps you find a lost pointer, which is easy to lose on multiple monitors, a high-resolution display or a dark wallpaper. When you shake the mouse rapidly back and forth, the pointer grows. It returns to its normal size when you stop.

**Shake pointer to find it** turns this on, and **Magnification** sets how large it gets, between **Normal** and **Large**.
