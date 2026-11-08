---
title: Testing loose binding on your video card
description: Help find out whether a faster way of drawing windows works on your video card, and report what you find.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-win 4cf630dd38 (src/options.cpp, src/compositor_x11.cpp, src/opengl/glplatform.cpp, src/backends/x11/standalone/x11_standalone_glx_backend.cpp); commands run on an AMD Radeon RX 9060 XT, logging out with the setting changed not run"
---

# Testing loose binding on your video card

We'd like results from as many video cards as possible, including reports where nothing went wrong.

When a window changes, [SonicWin](../applications/sonicwin.md) normally binds its image to the graphics card again, which is called *strict binding*. *Loose binding* skips that step. On one AMD Radeon card it lowered the total processor use of an animation by 6-7%, but it could show old window contents on other hardware. Intel's driver had loose binding turned off in 2014 for causing problems. That's why it's only on by default for AMD cards with `gfx1200` or `gfx1201` in the renderer string, and other cards need testing first.

This only changes one setting, and you can undo it at any time. You'll need to log out and back in a few times, and to [open a console](open-a-console.md) to run the commands.

## 1. Check that this test applies to you

Log in to your usual X11 session with [compositing](../settings/compositor.md) on, then run:

```bash
qdbus6 org.kde.KWin /KWin supportInformation | grep -E '^(Vendor|Vendor Release|OpenGL (vendor|renderer|version) string|OpenGL platform interface|Driver|GPU class|Linux kernel version|Number of Screens|glStrictBinding):'
```

Keep the output for your report. You can take part if it includes both of these lines:

```text
OpenGL platform interface: GLX
glStrictBinding: true
```

If it says `glStrictBinding: false`, your setup already uses loose binding, so there's nothing to test.

## 2. Measure processor use with the normal setting

Start something that keeps changing, such as a video in a window, and keep the window the same size throughout. Close other busy applications, then run this and leave the desktop alone for 30 seconds:

```bash
top -b -d 30 -n 2 -p "$(pgrep -x sonic-win)" | grep sonic-w | tail -1
```

The ninth column is SonicWin's processor use, as a percentage of one core. Run it three times and note each number.

## 3. Turn on loose binding

First note your video card for the report. Run:

```bash
glxinfo -B | grep 'renderer string'
```

`glxinfo` comes with your distribution's Mesa utilities package. It prints a line like this:

```text
OpenGL renderer string: AMD Radeon RX 9060 XT (radeonsi, gfx1200, ACO, DRM 3.64, 7.2.13-gentoo-dist-bin)
```

The report needs the card's name, the driver and the chip. On an AMD card those are the first three parts, so here that's `AMD Radeon RX 9060 XT, radeonsi, gfx1200`. Other cards print a different line: copy it from after `OpenGL renderer string:` up to the first version number.

Then turn on loose binding:

```bash
kwriteconfig6 --file kwinrc --group Compositing --key GLStrictBinding --type bool false
```

Log out and back in. Don't use `sonic-win --replace` for this, because replacing a running SonicWin can leave every window blank.

Run the command from step 1 again, and check that it now says `glStrictBinding: false`.

## 4. Test it

Measure processor use as in step 2, with the same video and window size. Then use your desktop normally for a while, and try each of these:

- Play a video, then scroll quickly in a terminal.
- Resize, maximize and minimize windows.
- Type, and hover over buttons, in a few applications.
- Open menus and tooltips, and look at any blurred or see-through panels.
- Open Overview and the task switcher, and check that the thumbnails are up to date.
- Take a screenshot, and check that it matches the screen.
- Run a game or a video fullscreen.

Look for windows that don't update until you click or move them, old contents, flickering, stuttering, corrupted images or crashes. If you see a problem, note whether it goes away after step 5, because that shows the setting caused it.

## 5. Go back to the normal setting

```bash
kwriteconfig6 --file kwinrc --group Compositing --key GLStrictBinding --delete
```

Log out and back in. If your desktop is too broken to use, switch to a text console with Ctrl+Alt+F3, log in, run the same command, and then restart your session.

## 6. Report your results

[Open an issue](https://github.com/Sonic-DE/sonic-win/issues) titled `Loose binding test: ` followed by the video card you noted in step 3, and copy in this template:

```markdown
**Result:** works / has problems

**Output of the command in step 1:**
(paste here, taken before turning on loose binding)

**SonicWin processor use, three runs each:**
- Normal setting:
- Loose binding:

**What was running during the measurements:**
(for example: a 1080p video in an 800x600 window)

**Problems seen:**
(what you did, what happened, and whether it went away after going back to the normal setting; or "none")

**How long you used it for:**
```
