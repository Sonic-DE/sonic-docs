---
title: Create your own mouse cursor theme
description: Make custom mouse cursors and install them as a cursor theme.
source_url: https://develop.kde.org/docs/features/additional-features/cursor/
source_authors: [Andrea Marano, Carl Schwan, Kunda Ki, Magno Lomardo, Marius P, Starbeamrainbowlabs Tjovik, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-workspace d0b84fd142 (kcms/cursortheme, startkde/startplasma.cpp), sonic-silver (cursors), sonic-system-settings (categories), libXcursor 1.2.3; steps 01 to 07 were run with xcursorgen
---

# Create your own mouse cursor theme

## Requirements

You need this package:

| Package | Usage |
| --- | --- |
| xcursorgen | Required |

It is called `x11-apps/xcursorgen` on Gentoo (`emerge --ask x11-apps/xcursorgen`) and `xorg-xcursorgen` on Arch Linux (`pacman -S xorg-xcursorgen`).

## Step 00: getting started

This tutorial shows how to make your own mouse cursor. Cursors made this way are X11 cursors (the Xcursor format), which is what SonicDE uses; they work with other X11 desktops too.

Check that you have the [requirements](#requirements) with `which xcursorgen`. If it prints `xcursorgen not found`, install the package. If it prints a path such as `/usr/bin/xcursorgen`, you're ready.

**Now let's make your first cursor!**

## Step 01: the image file

First you need an image for the cursor. Start with an empty PNG file.

Cursor images are square: width and height are the same. Make them at least 16×16 pixels; you can also make several sizes and bundle them into one cursor file.

Keep the **transparency (alpha channel)** when you save the file, or the cursor gets a square background.

> **Image sizes:** look at other cursor themes to see common sizes. SonicDE's Silver cursors, for example, are drawn for a nominal size of 24 pixels and generated at scales from 50% to 300%. In the end, the sizes are up to you.

When the file exists, draw your cursor now or later, but save the file.

Give it a name that says what it is for, in the form `filename.png`. Here the cursor is the default cursor, so call it `default.png`.

> **Note:** Repeat this step for every cursor you want to make or change. There is no required naming scheme, but descriptive names make the symlink step later much easier.

## Step 02: the hotspot

The *hotspot* is the point of the cursor where the click happens: the position in the image that the system takes as the cursor's position.

To find the right pixel for the hotspot, use a graphics program that shows exact pixel positions. [Krita](https://krita.org) does this well, but others work just as well.

The origin (0,0) is the **top-left corner** of the image. X grows to the right, Y downwards.

So an X offset of 10 pixels puts the hotspot 10 pixels right of the top-left corner, and a Y offset of 5 pixels puts it 5 pixels down.

> **Important:** if the cursor has several sizes, find the hotspot for each of them.

## Step 03: the .cursor file

With the image and its hotspot, write a `.cursor` file. It tells `xcursorgen` how to generate the cursor.

Each line of a `.cursor` file has the form `(size) (hotspot-x) (hotspot-y) (filename) (frame-time)`:

| Field | Description | Static cursors | Animated cursors |
| --- | --- | --- | --- |
| size | The size of the image. | Required | Required |
| hotspot-x | The x coordinate of the hotspot in the image. | Required | Required |
| hotspot-y | The y coordinate of the hotspot in the image. | Required | Required |
| filename | The image file for this cursor. | Required | Required |
| frame-time | How long this frame of an animated cursor is shown, in milliseconds. | Optional | Required |

Any program that can save a file with a custom extension can write it. Here we use the `echo` command in a terminal:

```shell
echo "32 10 5 default.png" > default.cursor
```

This creates `default.cursor` with the content `32 10 5 default.png` in the current directory. In detail:

- *32* is the **size**: a 32×32 pixel image.
- *10* is **hotspot-x**: 10 pixels to the right.
- *5* is **hotspot-y**: 5 pixels down.
- *default.png* is the **image file**, with its extension.
- *>* makes `echo` write its output to the file that follows.
- *default.cursor* is the file that receives the output.

Your `.cursor` file for this cursor is ready.

### Animated cursors

For an animated cursor, such as the `wait` cursor, make one PNG for each frame of the animation (`filename_#.png`) and list them all in `filename.cursor`, one per line, with the frame time:

```text
32 16 16 wait_1.png 50
32 16 16 wait_2.png 50
```

### Several sizes

To give a cursor several sizes, write one line per size, each with its own PNG:

```text
32 10 5 default-32.png
64 20 10 default-64.png
```

## Step 04: running xcursorgen

Now generate the cursor with `xcursorgen`.

In a terminal, go to the folder with your cursor images. `xcursorgen` is used like this: `xcursorgen config-file output-file`

| Parameter | Description |
| --- | --- |
| config-file | The cursor's configuration file. |
| output-file | The name of the cursor file to generate. |

For example:

```shell
xcursorgen default.cursor default
```

This reads `default.cursor` and generates the cursor file `default` (Xcursor data) in the current folder.

> **Note:** repeat steps 01 to 04 for every cursor you want to make.

## Step 05: the theme folder

To use your cursors, put them in the folder structure of a cursor theme.

Create a folder named after your cursor theme; here it is `KoolKursors`:

```shell
mkdir KoolKursors
```

Change into it:

```shell
cd KoolKursors
```

and create a `cursors` folder inside it:

```shell
mkdir cursors
```

The `cursors` folder holds all the cursor files and the symlinks they need (see the next step).

Move all the cursors you made in [step 04](#step-04-running-xcursorgen) into `cursors`; here that is at least the `default` cursor.

## Step 06: the symlinks

The cursor changes with what you point at or do: over a text field it becomes a text cursor, over a link usually a hand.

For your cursors to be used for these states, the `cursors/` folder needs files with specific names, one for each state. The X11 names are listed in `/usr/include/X11/cursorfont.h` (from libX11's development files; `XC_left_ptr` is the cursor named `left_ptr`):

```text
X_cursor arrow based_arrow_down based_arrow_up boat bogosity bottom_left_corner
bottom_right_corner bottom_side bottom_tee box_spiral center_ptr circle clock
coffee_mug cross cross_reverse crosshair diamond_cross dot dotbox double_arrow
draft_large draft_small draped_box exchange fleur gobbler gumby hand1 hand2 heart
icon iron_cross left_ptr left_side left_tee leftbutton ll_angle lr_angle man
middlebutton mouse pencil pirate plus question_arrow right_ptr right_side right_tee
rightbutton rtl_logo sailboat sb_down_arrow sb_h_double_arrow sb_left_arrow
sb_right_arrow sb_up_arrow sb_v_double_arrow shuttle sizing spider spraycan star
target tcross top_left_arrow top_left_corner top_right_corner top_side top_tee trek
ul_angle umbrella ur_angle watch xterm
```

Many states usually share one cursor file. Since each state only needs a file with its name, use [symlinks](https://en.wikipedia.org/wiki/Symbolic_link#POSIX_and_Unix-like_operating_systems).

Create a symlink with `ln -s file-path symlink-path`:

| Parameter | Description |
| --- | --- |
| file-path | The path, relative to the current folder, of the file to link to. |
| symlink-path | The path, relative to the current folder, of the symlink to create. |

For example, to use the `default` cursor as the normal pointer (pointing up and left, as for right-handed use), create a `left_ptr` symlink in `KoolKursors/cursors`:

```shell
ln -s default left_ptr
```

Your `cursors` folder now has two files:

- `default`: the cursor generated by `xcursorgen`
- `left_ptr`: the symlink you just created

> **Note:** script this step if you have a complete list of cursor names and their aliases. Incomplete lists of aliases can make it frustrating.

## Step 07: the index.theme file

`index.theme` describes the theme. The minimal version is:

```ini
[Icon Theme]
Name=KoolKursors
```

You can add more, for example a comment, or another theme to inherit cursors from.

The theme's folder name is its identifier: settings store it, and `Inherits=` refers to themes by it. `Name=` is only the title shown in System Settings, so it can differ from the folder name; SonicDE's own `silver_cursors_light` theme, for example, has `Name=Silver Light`.

Put `index.theme` in the theme folder, with this content:

```ini
[Icon Theme]
Name=KoolKursors
Comment=My very own cursor theme
Inherits=silver_cursors_light
```

With `Inherits=silver_cursors_light`, any cursor your theme doesn't provide comes from SonicDE's Silver Light cursors.

> **Translations:** add translated texts with language tags such as `[de]`, `[fr]` or `[pt_BR]`, each on its own line:
>
> ```ini
> [Icon Theme]
> Name=KoolKursors
> Inherits=silver_cursors_light
> Comment=My very own cursor theme.
> Comment[pt_BR]=Meu próprio tema de cursor.
> ```

## Step 08: installing the theme

With the cursors, symlinks and `index.theme` in place, copy the whole `KoolKursors` folder to a folder where cursor themes are found, for example with the Ecco file manager.

Cursor themes are found by libXcursor, in the folders of its search path:

- for just you: `~/.icons/`, which every libXcursor searches, and `~/.local/share/icons/` where your libXcursor searches it;
- system-wide: `/usr/share/icons/`.

If the environment variable `XCURSOR_PATH` is set, it replaces the default list; SonicDE sets it when installed outside `/usr`, starting with `~/.local/share/icons:~/.icons`. Otherwise the default list depends on how your system's libXcursor was built (Gentoo's libXcursor 1.2.3, for example, searches `~/.icons` but not `~/.local/share/icons`).

## Step 09: applying your cursor theme

In SonicDE, select it in System Settings → Colors & Themes → Pointers → KoolKursors → Apply.

Done! Enjoy your new `KoolKursors` theme. :)

## Other resources

- [X.org xcursorgen documentation](https://www.x.org/releases/current/doc/man/man1/xcursorgen.1.xhtml)
- [xcursorgen on the Arch Wiki](https://wiki.archlinux.org/title/Xcursorgen)
