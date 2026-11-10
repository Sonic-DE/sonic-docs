---
title: Animations
description: Set how fast animations run, and choose the animation for each window and desktop event.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-win a4e76b52c5 (src/kcms/animations, src/kcms/effects/kcm.cpp, the metadata.json of each animation effect in src/plugins, src/plugins/glide, src/plugins/magiclamp, src/plugins/slide, src/plugins/scale, src/plugins/login); written from the code, not clicked through"
---

# Animations

This module, under **Appearance & Style** in [System Settings](index.md), sets how fast animations run and which animation plays when windows open, close or change state, and when you switch virtual desktops. The animations need compositing, which the [Compositor](compositor.md) module turns on.

## Global animation speed

**Global animation speed:** is a slider from **Slow** to **Instant**. Each step towards **Slow** makes animations take longer, and each step towards **Instant** makes them quicker. The last step, **Instant**, turns animations off altogether, and the animation choices below are then greyed out.

The speed also applies to applications. As the help button next to the slider says, some applications don't support it: GTK applications can't change how long their animations take, but they do turn animations off when the speed is **Instant**.

## Desktop animations

Each of these lists chooses one animation for an event, or **None** for no animation. Only one animation can play for each event.

- **Window open/close:** **Scale** (the default) makes windows grow and shrink, **Glide** makes them tilt in and out, and **Fade** fades them in and out.
- **Window maximize:** **Stretch**, the default, stretches windows when they're maximized or restored.
- **Window minimize:** **Squash** (the default) squashes windows as they're minimized, and **Magic Lamp** draws them down as if into a magic lamp.
- **Window full screen:** **Stretch**, the default, stretches windows going to and leaving full screen.
- **Peek at desktop:** what happens to the windows when you show the desktop. **Window Aperture** (the default) moves them into the screen corners, and **Eye on Screen** sucks them into the desktop.
- **Virtual desktop switching:** **Slide** (the default) slides between desktops, and **Fade** fades between them. The [Virtual Desktops](virtual-desktops.md) module has the same choice.

Effects you install from the Internet can add more choices to these lists.

Below the lists are four animations with a checkbox each, which you can turn on and off separately. They're all on by default:

- **Fading popups:** Fades popups in and out.
- **Sliding popups:** Slides panel popups in and out.
- **Login:** Fades to the desktop when you log in.
- **Logout:** Fades to the logout screen.

When the chosen animation has settings, the **Configure…** button next to it opens them. They're described below.

**More effects settings:** opens the [Desktop Effects](desktop-effects.md) module, which has the other effects. The animations on this page aren't listed there.

## Settings of the animations

Several animations have a **Duration:** setting in milliseconds. Its lowest value, **Default**, uses the animation's normal length. Whichever length you choose, the global animation speed still makes it slower or quicker.

### Scale

- **Duration:** How long the animation takes.
- **Window open scale:** The size a window starts from when it opens, compared to its real size. The default is 0.8.
- **Window close scale:** The size a window shrinks to when it closes. The default is 0.8.

### Glide

- **Duration:** How long the animation takes.
- **Window Open Animation** and **Window Close Animation** each have:
  - **Rotation edge:** The edge of the window it tilts around: **Top**, **Right**, **Bottom** or **Left**. Opening windows tilt around the top by default, and closing ones around the bottom.
  - **Rotation angle:** How far the window tilts, in degrees.
  - **Distance:** How far the window moves while it tilts.

### Magic Lamp

- **Animation duration:** How long minimizing takes.

### Slide

- **Gap between desktops**: The space between desktops while they slide past, **Horizontal:** and **Vertical:**, in pixels. The defaults are 45 and 20.
- **Slide desktop background**: Slides the wallpaper along with the windows. This is on by default; turn it off to keep the wallpaper still and slide only the windows.

### Login

- **Fade to black (fullscreen splash screens only)**: After a full-screen splash screen, fades through black instead of straight to the desktop. This is off by default.
