---
title: Gamma
description: Correct your monitor's gamma so images look the way they should.
source_url: https://invent.kde.org/graphics/kgamma/-/blob/master/doc/index.docbook
source_authors: [Michael v. Ostheim]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-gamma 386cfe3 (kcmkgamma); read from code, not clicked through"
---

# Gamma

This module is a tool for monitor gamma correction. With proper gamma settings, your display, such as websites and images, looks the same on your monitor as on other monitors.

It changes the gamma correction of the X server, but that's not all you need. For good results you also have to set the correct brightness, contrast and color balance on your monitor. This can be difficult, and you may have to repeat every step several times. Perfect results need very good and expensive hardware. If your X server can't do gamma correction, the module tells you so.

Use the four sliders to set the gamma correction as a single value with **Gamma**, or separately for **Red**, **Green** and **Blue**. The X server's default gamma is 1.00. The test pictures help you find the right settings.

**Save settings system wide** keeps them for all users and graphical environments on this machine, and restores them at the next X server start. This needs administrator access.

Without that option, the settings go in your personal configuration. They're restored at your next login and temporarily replace the system settings, which aren't removed and are restored at the next X server start.

With several screens, select the one to change from the box. **Sync screens** sets them all to the same values, and has no effect with a single screen.

## Using the test pictures

**Select test picture** offers six test pictures.

### Gray Scale

You should see:

- A grayscale with 20 different sections
- The darkest section pure black
- The lightest section pure white
- No hint of any color in the gray tones

If you can't see all 20 sections, use your monitor's contrast setting or the **Gamma** slider. If black isn't pure black, try darkening the monitor, and if white isn't pure white, try lightening it. If you see any colors in the gray tones, change your monitor's color balance or use the **Red**, **Green** and **Blue** sliders.

### RGB Scale

You should see three strips, each with 16 sections of red, green or blue tones. The darkest sections should be pure black, and the brightest pure red, green or blue. If you can't see all the sections of a strip, try lightening or darkening that color.

### CMY Scale

You should see three strips, each with 11 sections of cyan, magenta or yellow tones. The brightest sections should be pure white, and the darkest pure cyan, magenta or yellow.

- If you can't see all the cyan sections, try lightening or darkening red.
- If you can't see all the magenta sections, try lightening or darkening green.
- If you can't see all the yellow sections, try lightening or darkening blue.

### Advanced test pictures

These three pictures show what your monitor can do at three points of the gray spectrum. If you can't see all the details, don't worry, or buy better hardware.

- **Dark Gray:** You should see 10 different rectangles of dark gray in a black box, in 1% steps from black.
- **Mid Gray:** You should see 11 gray rectangles in a 50% gray box, all except the middle one, in steps from 45% to 55% gray.
- **Light Gray:** You should see 10 different rectangles of light gray in a white box, in 1% steps from white.
