---
title: Effect settings
description: The settings of the desktop effects that have them, such as Blur, Dim Inactive, Overview and Wobbly Windows.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-win a4e76b52c5 (src/plugins: blur, diminactive, mouseclick, mousemark, overview, thumbnailaside, trackmouse, translucency, wobblywindows; their *_config.ui, *.kcfg and effect sources), sonic-workspace-addons (kwin/effects/cube); written from the code, not clicked through"
---

# Effect settings

In the [Desktop Effects](desktop-effects.md) module, an effect with settings has a **Configure…** button to the right of it. The button only works while the effect is checked. This page describes those settings. The settings of the animations, such as Glide and Slide, are on the [Animations](animations.md) page.

## Blur

Blur blurs the background behind see-through windows that ask for it, and behind see-through window decorations. It's on by default. To make other windows see-through and blurred, see [Forcing transparency and blur](../tutorials/transparency-and-blur.md).

The settings come in two groups with the same three sliders, each running from **Light** to **Strong**:

- **Blur windows** is for every window apart from menus.
- **Blur menus** is for menus. Its checkbox decides whether menus are blurred at all: when it's off, no menu is blurred, even one that asks for it. When it's on, menus made see-through by the [Translucency](#translucency) effect are blurred too. It's off by default.

The sliders are:

- **Blur strength:** How much the background is blurred. For windows the default is the strongest setting.
- **Noise strength:** Adds a fine grain on top of the blur, which hides the visible bands that smooth color changes can show. All the way to **Light** turns it off.
- **Saturation strength:** How colorful the blurred background is. The default, one step from **Light**, keeps its colors as they are. Each step towards **Strong** makes them more vivid, and the lowest step makes them a little paler.

## Dim Inactive

Dim Inactive darkens every window except the active one, so it's easy to see where you're typing.

- **Strength:** How much the inactive windows are darkened, as a percentage. The default is 25%.
- **Dim:** Which other windows are darkened as well:
  - **Docks and panels**, off by default.
  - **Desktop**, off by default.
  - **Keep above windows**, off by default.
  - **By window group**: Doesn't dim windows that belong to the same application group as the active window, such as its dialogs. This is on by default.
  - **Fullscreen windows**, on by default.

## Mouse Click Animation

Mouse Click Animation draws rings around the pointer when you press a mouse button, which is useful for screen recordings and presentations. Turn it on and off with Meta+\*.

**Basic Settings**:

- **Left Mouse Button Color:**, **Middle Mouse Button Color:** and **Right Mouse Button Color:** The color of the rings for each button. The defaults are red, green and blue.

**Advanced Settings**:

- **Rings**:
  - **Line Width:** The thickness of the rings, in pixels.
  - **Ring Duration:** How long the rings stay visible, in milliseconds. The default is 300.
  - **Ring Radius:** The size of the rings, in pixels. The default is 20.
  - **Ring Count:** How many rings are drawn for each click. The default is 2.
- **Text**:
  - **Show Text:** Also shows the name of the button you pressed. This is on by default.
  - **Font:** The font of that text.

## Mouse Mark

Mouse Mark lets you draw on the screen with the mouse, for example to point something out during a presentation.

**Appearance**:

- **Width:** The thickness of the lines, in pixels. The default is 3.
- **Color:** The color of the lines. The default is red.

**Draw with the mouse by holding modifier keys and moving the mouse**:

- **Free draw modifier keys:** The keys to hold while you move the mouse to draw freely. Choose any of **Alt**, **Ctrl**, **Shift** and **Meta**. The default is Shift+Meta.
- **Arrow draw modifier keys:** The keys to hold to draw an arrow from where you start to where you stop. The default is Ctrl+Shift+Meta.

Shift+Meta+F11 clears all the marks, and Shift+Meta+F12 clears the last one. You can change these keys in the [Shortcuts](shortcuts.md) module.

## Overview

Overview shows all your windows and virtual desktops at once, and lets you search. Grid View, part of the same effect, shows every virtual desktop side by side. Overview is on by default.

- **Ignore minimized windows:** Leaves minimized windows out. This is off by default.
- **Organize windows in the Grid View:** Arranges the windows on each desktop in Grid View so they don't overlap. When it's off, they keep their real positions. This is on by default.
- **Search results include filtered windows:** When you type in Overview, the windows whose names match stay on show, and search results for applications and files appear only when no window matches. When it's off, typing shows the search results straight away. This is on by default.

The shortcuts list below them sets the keys:

- **Toggle Overview**, Meta+W by default.
- **Toggle Grid View**, Meta+G by default.
- **Cycle through Overview and Grid View** and **Cycle through Grid View and Overview**, with no keys by default.

You can also open Overview from a [screen edge](screen-edges.md).

## Thumbnail Aside

Thumbnail Aside shows a live thumbnail of a window at the edge of the screen, so you can keep an eye on it while you work in another. Meta+Ctrl+T adds the active window's thumbnail, or removes it.

**Appearance**:

- **Maximum width:** The widest a thumbnail can be, in pixels. The default is 200.
- **Spacing:** The space between thumbnails, in pixels. The default is 10.
- **Opacity:** How opaque the thumbnails are, as a percentage. The default is 50%.

## Track Mouse

Track Mouse draws rings around the mouse pointer so you can find it on the screen.

**Trigger effect with:** has two ways to show it, and both work:

- **Keyboard shortcut:** Press the shortcut you set here to show the rings, and press it again to hide them. There's none by default.
- **Modifier keys:** Hold the chosen keys, any of **Alt**, **Ctrl**, **Shift** and **Meta**, and move the mouse to show the rings. They stay while you hold the keys. The default is Ctrl+Meta.

## Translucency

Translucency makes some kinds of window see-through. It's off by default. Each slider runs from **Transparent** to **Opaque**.

**General Translucency Settings** has a slider for each kind: **Menus:**, **Combobox popups:** (the lists that open from drop-down boxes), **Dialogs:**, **Moving windows:** (windows while you move or resize them) and **Inactive windows:**. All are fully opaque by default, except **Moving windows:**, which is 80% opaque.

**Set menu translucency independently** greys out the single **Menus:** slider and uses three sliders instead: **Dropdown menus:**, **Popup menus:** and **Torn-off menus:**. It's off by default.

To blur behind see-through menus, turn on **Blur menus** in the [Blur](#blur) settings.

## Wobbly Windows

Wobbly Windows makes windows wobble like jelly when you move them.

- **Wobbliness**: How much the windows wobble, from **Less** to **More**.
- **Wobble when moving**, on by default.
- **Wobble when resizing**, on by default.

**Advanced** has finer settings, which apply instead of **Wobbliness** when you check **Enable advanced mode**:

- **Stiffness:** How strongly a window springs back into shape.
- **Drag:** How much of its movement a window keeps as it wobbles. Higher values make the wobbling last longer.
- **Move factor:** How fast the parts of the window move as they wobble.

## Cube

The Cube effect comes with the SonicDE add-ons package. It arranges your virtual desktops on the sides of a cube that you can turn. It's off by default, and listed under Window Management.

Meta+C opens and closes the cube. Turn it with the left and right arrow keys, and press Return or Space, or click a side, to go to that desktop. Escape closes it.

The cube needs at least three virtual desktops. With fewer, it says so and offers an **Add Virtual Desktop** button.

Its settings:

- **Cube face displacement:** How far apart the sides of the cube are, from **Less** to **More**.
- **Distance:** How far away the cube is, from **Closer** to **Farther**.
- **Mouse:** **Invert X** and **Invert Y** reverse the direction the cube turns when you drag it.
- **Background:** What's behind the cube: a **Plain color:**, dark grey by default, or a **Skybox:** image you choose.
