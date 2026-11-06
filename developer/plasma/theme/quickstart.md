---
title: Creating a desktop theme quickstart
description: A quick guide to creating your first desktop theme.
source_url: https://develop.kde.org/docs/plasma/theme/quickstart/
source_authors: [Benjamin Flesch, Carl Schwan, Chris Holland, Dolphin von Chips, Johannes Zarl-Zierl, Kunda Ki, Mikhail Zolotukhin, Niccolò Venerandi, Nicolas Fella, Robert Kucsora, Taro Tanaka, Thiago Sueto, nobkd nobkd, obno sim]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-svg (ImageSet caches, tools), sonic-interface-libraries desktoptheme, sonicshell"
---

# Creating a desktop theme quickstart


One of Plasma's features is the ability to theme desktop elements using Scalable
Vector Graphics (SVGs). This means there is no need for theme authors to know
C++ or any other programming language to create a great looking theme. They
need only use common graphics tools like Krita,
Inkscape, GIMP, etc. Depending on your prowess with such tools, a great
looking desktop theme can be created in under an hour.

A [video tutorial](https://www.youtube.com/playlist?list=PLX3_anRd8Mp7ibLDlSEJHNzSBaTslFp-x) is available to learn how to edit desktop themes.

## Creating a desktop theme in 7 Easy Steps

### Step 1: Using an existing theme {#existing-theme}

Copy and rename an existing desktop theme folder. The new folder name should
be the name of the theme. Themes provided by your distribution are stored in `/usr/share/plasma/desktoptheme/`,
while user-installed themes go in `~/.local/share/plasma/desktoptheme/`.
You can also find [desktop themes on the KDE Store](https://store.kde.org/browse/cat/104/order/latest/). Edit the `metadata.json` file
in the theme folder to match your theme name.

See [Theme Metadata](details.md#theme-metadata">}}) if you need help.

> **Important:** Prior to KDE Frameworks 6, themes used a `metadata.desktop` file instead of `metadata.json`.

```bash
# Create theme directory in home if it doesn't exist
mkdir -p ~/.local/share/plasma/desktoptheme
# Copy default theme to home directory so we can modify it
cp -r /usr/share/plasma/desktoptheme/default ~/.local/share/plasma/desktoptheme/
# Rename theme
cd ~/.local/share/plasma/desktoptheme
mv ./default ./mytheme
# Edit the relevant fields in the metadata.json
# with your theme information and credits.
# Remove any translation names or descriptions
# (entries like Name[fr] or Description[zh_CN]).
```

> **Note:** The `default/` theme has all the default SVGs. `breeze-light/` and `breeze-dark/` only have a `colors` file and a pair of metadata files, and inherit everything else from the `default/` theme. SonicDE's `silver-light/` and `silver-dark/` themes add their own SVGs on top of `default/`.

### Step 2: Open a file {#open}

Open the SVG file associated with the Plasma element you would like to theme
(panel background, clock, etc.) in an SVG editor (e.g. Inkscape).

See [Theme Location, Structure and Definition](details.md#structure) to understand how desktop themes are organized, and the [Theme Elements Reference]({{< ref "theme-elements.md">}}) to understand what each SVG file does.

### Step 3: Edit each element {#edit}

Each SVG file may have several elements (objects with element ID = `left`,
`right`, `top`, `topright`, `center`, `ClockFace`, etc.). Modify existing elements OR delete
and create replacement elements. Elements can be any SVG primitive or object group.

See [SVG Elements and Inkscape](svg.md) to understand how to edit desktop theme SVG elements.

> **Hint:** You can embed raster images as SVG elements if you creatively prefer raster editors
> like Krita, GIMP, etc. Remember to _embed_ each image instead of _linking_ (Inkscape:
> Effects -> Images -> Embed All Images).

### Step 4: Use an Inkscape extension {#extension}

To make renaming of the theme elements easier, it is possible to use an [Inkscape
extension provided by
KSvg](https://github.com/Sonic-DE/sonic-frameworks-svg/tree/master/src/tools/inkscape%20extensions). See [Inkscape Extensions](svg.md#inkscape-extensions) for how to install it.

### Step 5: Review element IDs {#review}

Make sure that the element ID for each new element is correctly set.

> **Hint:** In Inkscape you can check the element ID for each element by right-clicking on the
> element and choosing Object Properties.

### Step 6: Edit hint elements {#hints}

Add or remove any element containing a hint ID you desire. It doesn't matter how the element looks,
just that elements with IDs matching the hint elements either exist or
don't exist. See [Background SVG Format](background-svg.md) for a
description of available hint elements.

### Step 7: Save the SVG file. {#save}

Repeat steps 3 - 6 for any other Plasma element for which you would like to
create a new theme.

## Testing the Theme

* If you have not already done so, copy your new theme folder to `~/.local/share/plasma/desktoptheme`.

* Choose the theme in System Settings -> Appearance -> Desktop Style, run `plasma-apply-desktoptheme mytheme`, or edit your `~/.config/plasmarc` to point to the new theme. This may require restarting the shell.

* Carefully check the appearance of all new theme elements.

* If you created separate themes that do not require compositing/desktop effects (SVGs in the `opaque/` folder), remember
to test your theme with compositing turned off (this can be toggled with the keyboard shortcut `Alt+Shift+F12`). See [Opaque Folder](elements.md#opaque-folder) for details.

When you update the theme, you need to battle with the theme caches. To make sure
you are running the latest version of your theme after updating its files, clear the cache:

```
rm ~/.cache/plasma_theme_*.kcache ~/.cache/ksvg-elements*
```

Then restart the shell. The easiest way to do so is by opening KRunner with `Alt + Space` and running:

```
sonicshell --replace
```

## Theme Colors

* You can provide a color scheme that will allow text, selected backgrounds and
other items to blend well with your theme by supplying a `colors` file in your theme folder.
See the `colors` file in the `default` theme for an example.

* If the `colors` file is omitted, the current system colors are used.

> **Important:** Theme SVGs are only colorized if they use the `current-color-scheme` stylesheet. See [System and accent colors](colors.md).

## Hints and Tips

* Even a **pixel or two out of place** can make a difference over hours of use. It may not
be obvious at first glance but the user may intuitively pick up that something is "just
not right" and give up using your theme.

* In Inkscape, turn off **stroke scaling** when elements are resized. Inkscape may default
to scaling the stroke of an element when changing its size. This may show up in the rendered
desktop theme as thin, barely-there lines that you can't seem to get rid of.

* If you prefer raster editors like Krita and GIMP, create your theme in these
programs first, then import them into Inkscape (drag and drop of the files works fine). If
you're working on a background with multiple elements, like `widgets/panel-background.svg` or `widgets/background.svg`, crop the raster image into the different elements (top, bottom, right,
etc.) and save as separate files before importing into Inkscape.

* Don't forget to **embed imported raster images**. By default Inkscape will import these
as linked images that will not show up on the desktop (to embed the images, go to Effects ->
Images -> Embed All Images).

* Remember that the border elements of backgrounds (`top`, `right`, `bottom`, `left`) are tiled if the
`hint-stretch-borders` element is *not* present in the SVG.

* Remember that the center element of backgrounds are stretched if the `hint-tile-center`
element is *not* present in the SVG.

* When testing the theme, if it looks like portions of a multi-element SVG are missing
(missing borders, etc.), check the SVG again to **make sure the element IDs are correct**.

* Do not use more advanced SVG features since they will not be rendered properly. If you
want to add blur or something similar, consider pre-rendering to PNG, and then importing the
PNG into the final SVG file.

* Perform this quick sanity check for background SVGs to help troubleshoot annoying lines
and gaps between elements:

  * `topleft`, `top` and `topright` elements should have the same height
  * `topright`, `right` and `bottomright` elements should have the same width
  * `bottomleft`, `bottom` and `bottomright` elements should have the same height
  * `topleft`, `left` and `bottomleft` elements should have the same width
