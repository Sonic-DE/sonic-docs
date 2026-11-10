---
title: Window Behavior
description: Configure window focus, mouse actions, snapping and placement.
source_url: https://invent.kde.org/plasma/kwin-x11/-/blob/master/doc/windowbehaviour-x11/index.docbook
source_authors: [Mike McBride, Jost Schenck, Natalie Clarius]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-win a4e76b52c5 (src/kcms/options); read from code, not clicked through"
---

# Window Behavior

This module has several tabs. **Focus** sets how windows gain or lose focus. **Titlebar Actions** and **Window Actions** set how titlebars and windows react to mouse clicks. **Movement** sets how windows move. **Advanced** covers specialized options such as window shading and where new windows are placed.

These settings only apply if you use SonicWin, the desktop's window manager.

## Focus

The focus is the window you're currently working on, often called the active window.

Focus doesn't necessarily mean the window is at the front, which is called being raised. Both are configured here, independently.

### Window activation policy

There are six ways of deciding which window has focus:

- **Click to focus:** A window becomes active when you click into it. This is common on other operating systems and probably what you want.
- **Click to focus (mouse precedence):** Mostly the same, except that if the system has to choose an active window, because the current one was closed for example, it prefers the one under the mouse.
- **Focus follows mouse:** Moving the pointer over a normal window activates it. New windows, such as KRunner opened with Alt+F2, receive focus without you pointing at them. Windows that happen to appear under the mouse don't gain focus. Focus stealing prevention works as usual. Think of it as click to focus without having to click. Other window managers sometimes call this “sloppy focus”.
- **Focus follows mouse (mouse precedence):** Mostly the same as Focus follows mouse, except that if the system has to choose an active window, it prefers the one under the mouse. Choose this for hover-controlled focus.
- **Focus under mouse:** The window under the pointer becomes active. If the mouse isn't over a window, the last window under it keeps focus. New windows such as KRunner don't receive focus, so you must move the mouse over them to type.
- **Focus strictly under mouse:** Similar, but even stricter. Only the window under the pointer is active. If the pointer isn't over a window, no window has focus. New windows don't receive focus here either.

> [!NOTE]
> Focus under mouse and Focus strictly under mouse stop certain features from working properly, such as focus stealing prevention and the Alt+Tab task switcher.

### Delay focus by

The delay before the window under the pointer automatically receives focus.

### Focus stealing prevention

How hard the window manager tries to prevent new windows from unexpectedly taking focus.

- **None:** Prevention is off and new windows always become active.
- **Low:** Prevention is on. If a window doesn't support the underlying mechanism and it's unclear whether to activate it, it's activated. This can give worse or better results than Medium, depending on the applications.
- **Medium:** Prevention is on.
- **High:** New windows only become active if no window is active, or if they belong to the active application. This probably isn't usable without a mouse focus policy.
- **Extreme:** You must explicitly activate all windows.

Windows prevented from stealing focus are marked as demanding attention, which by default highlights their task manager entry.

### Raising windows

You can also control when windows are brought to the front. Make sure at least one of these is on, or windows won't be raised at all.

- **Click raises active window:** Brings a window to the front when you click it. This is on by default with click to focus.
- **Raise on hover, delayed by:** Brings a window to the front when the pointer has been over it for a set time. This is only available with a hover focus policy.

> [!TIP]
> A very short delay causes rapid changing of windows, which can be distracting. Most people like 100 to 300 ms, which is responsive but lets you slide over the corners of a window without bringing it to the front.

### Multiscreen behavior

**Separate screen focus** limits focus operations to the active screen. For example, when you close a window, the next window to receive focus is on the active screen, even if a more recently used one is on another screen. This only appears when more than one screen is connected.

## Titlebar Actions

This tab sets what happens when you click on window titlebars.

### Double-click and mouse wheel

**Double-click** can do one of these:

- **Maximize:** Resizes the window to fill the screen.
- **Vertically maximize:** Resizes it to the height of the screen.
- **Horizontally maximize:** Resizes it to the width of the screen.
- **Minimize:** Hides it, and you can restore it with the task manager or task switcher.
- **Shade:** Reduces it to just the titlebar. Double-clicking the titlebar again restores it.
- **Lower:** Moves it below the other windows.
- **Close:** Closes it.
- **Show on all desktops:** Makes it visible on all virtual desktops.
- **Do nothing.**

**Mouse wheel** can trigger an action that depends on the direction you scroll:

- **Raise/lower:** Up moves the window on top of others, and down moves it below.
- **Shade/unshade:** Up collapses it to its titlebar, and down restores it.
- **Maximize/restore:** Up maximizes it, and down restores its previous size.
- **Keep above/below:** Up keeps it on top, and down keeps it covered.
- **Move to previous/next desktop:** Up moves it to the previous virtual desktop, and down to the next.
- **Change opacity:** Up makes it less transparent, and down more.
- **Do nothing.**

> [!TIP]
> Shaded windows can unshade automatically when you put the mouse over their titlebar. See [Window unshading](#window-unshading). This is a great way to reclaim screen space when you're copying between lots of windows.

### Titlebar and frame actions

This sets what happens when you single-click a window's titlebar or frame. You can choose different actions for each mouse button, depending on whether the window is **Active** or **Inactive**.

- **Raise:** Brings the window to the top of the stack.
- **Lower:** Moves it to the bottom of the stack, out of the way.
- **Toggle raise and lower:** Raises windows that aren't on top, and lowers those that are.
- **Minimize**, **Shade** and **Close**, as above.
- **Show actions menu:** Opens a menu of window commands, such as Move to Desktop, Move to Screen, Maximize, Minimize and Close.
- **Do nothing.**

For an **Inactive** window there are three more choices, which also make it the active window:

- **Activate and raise:** Activates the window and brings it to the top.
- **Activate and lower:** Activates the window and moves it to the bottom of the stack.
- **Activate:** Activates the window without changing where it is in the stack.

**Maximize window by double clicking its frame** does just that.

### Maximize button actions

This sets what each mouse button does on the maximize button: **Maximize**, **Vertically maximize** or **Horizontally maximize**.

## Window Actions

### Inactive inner window

This sets what happens when you click an inactive window with any of the three mouse buttons, or use the mouse wheel.

For the buttons:

- **Activate, raise and pass click:** Makes the window active, raises it and passes the click to the application.
- **Activate and pass click:** Makes it active and passes the click on.
- **Activate:** Makes it active, without passing the click on.
- **Activate and raise:** Makes it active and raises it, without passing the click on.

**Activate, pass click and raise on release** doesn't work on X11.

**Mouse wheel:**

- **Scroll:** Just scrolls the content.
- **Activate and scroll:** Makes the window active and scrolls.
- **Activate, raise and scroll:** Makes it active, raises it and scrolls.

### Inner window, titlebar and frame

This sets extra actions when clicking a window with a modifier key pressed. **Modifier key** can be **Meta**, the default, or **Alt**. You can choose different actions for left, middle and right clicks and the mouse wheel.

For the buttons:

- **Move:** Lets you drag the window around.
- **Activate, raise and move:** Makes it active, raises it and lets you drag it.
- **Toggle raise and lower**, **Raise**, **Lower** and **Minimize**, as above.
- **Resize:** Lets you change the size of the window.
- **Decrease opacity:** Makes it more transparent.
- **Increase opacity:** Makes it less transparent.
- **Do nothing.**

The mouse wheel has the same choices as the [titlebar mouse wheel](#double-click-and-mouse-wheel).

## Movement

This page sets the snap zones, which are like a magnetic field along the side of the screen and each window, making windows snap alongside when moved near.

- **Screen edge snap zone:** Moving a window within this distance of a screen edge makes it snap to the edge.
- **Window snap zone:** Moving a window near another makes it snap to its edge, as if they were magnetized.
- **Center snap zone:** The strength of the field that makes windows snap to the center of the screen.
- **Snap windows, Only when overlapping:** Windows only snap if they overlap, by the set amount or less, not if they're just near each other.

> [!TIP]
> [Screen Edges](screen-edges.md) lets you tile windows to half or a quarter of the screen, or maximize them, when you drag them near the screen edges.

## Advanced

### Window unshading

**On titlebar hover after** automatically unshades a shaded window when the pointer has been over its titlebar for some time. Use the spin box to set the delay.

### Window placement

The placement policy sets where a new window appears. With several monitors, it's always on the active screen, the one with the pointer or focused window, unless the window remembers its previous position.

- **Minimal Overlapping:** Overlaps existing windows as little as possible.
- **Maximized:** Tries to maximize all new windows.
- **Random:** Uses random locations.
- **Centered:** Uses the center of the screen.
- **In Top-Left Corner:** Puts the window's top left corner in the top left corner of the screen.
- **Under mouse:** Centers new windows under the pointer.

**Allow apps to remember the positions of their own windows, if they support it** opens windows where they previously were, instead of following the policy above. This includes the screen, so windows may open on a screen other than the active one.

> [!TIP]
> To make some windows appear on specific positions, screens or virtual desktops, use [Window Rules](window-rules.md).

### Virtual Desktop behavior

Sometimes opening an application activates an existing window instead of opening a new one. **When activating a window on a different Virtual Desktop** sets what happens if that window is on another desktop:

- **Switch to that Virtual Desktop:** The active desktop follows the window.
- **Bring window to current Virtual Desktop:** The window jumps to the active desktop, so the desktop only changes when you navigate there yourself.
- **Do nothing:** The window stays on its desktop and the current desktop doesn't change.
