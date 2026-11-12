---
title: Colors
description: Choose, edit and create color schemes and set the accent color.
source_url: https://invent.kde.org/plasma/plasma-workspace/-/blob/master/doc/kcontrol/colors/index.docbook
source_authors: [Matthew Woehlke, Natalie Clarius]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-workspace (kcms/colors, kcms/colors/editor), sonic-silver (colors), sonic-workspace-addons (kdeds/kameleon), sonic-power-management (applets/brightness); read from code, not clicked through"
---

# Colors

## Scheme management

This module manages the color schemes on your machine. It shows a preview of each scheme. Only one scheme is active at once, but you may edit schemes. Hover over an item in the grid to reveal its remove button. System schemes and the active scheme can't be removed. A removed scheme is only marked for removal until you click **Apply**; until then, **Don’t delete this color scheme** brings it back.

SonicDE comes with these color schemes from Silver:

- **Silver Light:** The default scheme, used by the light [Silver global themes](global-theme.md#the-silver-themes).
- **Silver Dark:** Used by the dark Silver global themes.
- **Sonic Colorful Dark**
- **Opal Fruits Light (Silver)** and **Opal Fruits Dark (Silver)**

The see-through title bars and toolbars of the Silver look aren't part of the color scheme. They're set in [Transparency](transparency.md), along with the transparency of panels, pop-ups and menus.

You can filter the list with the search field, and the box next to it shows **All schemes**, **Light schemes** or **Dark schemes**.

With an Internet connection, **Get New…** lets you browse and retrieve user-created schemes. **Install from File…** installs `*.colors` schemes you've downloaded or otherwise obtained.

## Accent color

The accent color highlights focused or selected elements, and is also used for other interface elements such as sliders and folder icons. You have three options:

- **Accent color from color scheme:** Leaves the color of highlighted elements up to the color scheme.
- **Accent color from wallpaper:** Automatically extracts a matching color from your desktop background.
- **Custom accent color:** Choose from predefined colors or pick your own.

### Keyboard lights

The lights of a color-lit keyboard can follow the accent color. This works with keyboards whose colored lights the system can control directly, as on many laptops, and with keyboards running QMK firmware that support VIA. It's off by default. When such a keyboard is found, the [Brightness & Color](../desktop/brightness-and-color.md) widget in the system tray shows **Keyboard Color** with a **Follow accent color** switch to turn it on. When it's on, the keyboard takes the current accent color and changes whenever the accent color does. Turning it off sets the lights back to white.

## Editing or creating schemes

Hover over a scheme and press **Edit Color Scheme…** to open a dialog with the tabs **Options**, **Colors** and **Disabled**, plus **Inactive** while **Apply effects to inactive windows** is on. When you have a scheme you like, you can save it under a different name or overwrite it.

### Options

This tab changes how the color scheme is used, as well as some options that change it without assigning colors.

- **Apply effects to inactive windows:** Applies [state effects](#disabled-and-inactive) to inactive windows, set on the **Inactive** tab. This can help identify active and inactive windows, but some people find the repainting distracting. These effects don't need compositing, but only work in applications that support them.
- **Use different colors for inactive selections:** Draws the selection in elements without input focus in a different color. This can help you see which element has focus, especially in applications that display several lists at once.
- **Shade sorted column in lists:** Multi-column lists use a slightly different color for the column being sorted.
- **Tint all colors with accent color:** Blends some of the accent color into all colors. **Tint strength** controls how much.
- **Make window titlebars accent-colored:** Tints the titlebar and header of windows with the accent color. Active windows get a strong highlight, and inactive windows a fainter one.
- **Contrast**, under **Frames and Outlines:** Sets the contrast of frames, separators and outlines. A lower value gives softer edges, and a higher value makes them stand out more. Values below 15% may look awkward in some applications and color schemes, and the tab warns about that.

### Colors

This tab changes the colors in the active scheme. To change a color, click its swatch in the list and select a new one. Save your scheme when you're done.

**Common Colors**, shown first, isn't really a set in the sense below. It presents a number of roles in a way that makes it easier to edit the scheme as a whole. When creating a scheme you'll usually change these first, and use the other sets to tweak specific colors.

Common Colors makes roles from all sets available. For example, “View Background” is shorthand for the Normal Background role of the View set. Setting a color that doesn't refer to a specific set changes it in *all* sets. The exception is Inactive Text, which changes all sets except Selection, and there's a separate Selection Inactive Text for that. Some roles only appear when you select the appropriate set. When one of the text or decoration roles from Inactive Text to Hover Decoration has different colors in different sets, Common Colors shows **Varies** instead of a swatch; click it to pick one color for all of them.

#### Color sets

The scheme is broken into sets based on the type of interface element:

- **View:** Information elements, such as lists, trees and text input boxes.
- **Window:** Window elements that aren't buttons or views.
- **Button:** Buttons and similar elements.
- **Selection:** Selected text and items.
- **Tooltip:** Tooltips, “What's This” tips and similar elements.
- **Complementary:** Areas of applications with an alternative color scheme, usually with a dark background for light schemes. Examples are the logout interface, the lock screen and the fullscreen mode of some applications.

Each set has the same roles, and all colors are associated with a set.

#### Color roles

As well as Normal Text and Normal Background, the roles are:

- **Alternate Background:** Used to subtly change the background to help associate items, mostly for alternating rows in lists.
- **Link Text:** Used for hyperlinks, or to indicate something that may be visited.
- **Visited Text:** Used for something that has been visited, or to indicate something old.
- **Active Text:** Used for an active element or to attract attention, such as alerts and notifications, and for hovered hyperlinks.
- **Inactive Text:** Used for unobtrusive text, such as comments, subtitles and unimportant information.
- **Negative Text:** Used for errors, failure notices and warnings that an action may be dangerous.
- **Neutral Text:** Used to draw attention when another role isn't appropriate, such as warnings, or to indicate secure or encrypted content.
- **Positive Text:** Used for success notices and to indicate trusted content.

There are also two decoration roles for drawing lines or shading, which aren't meant for text:

- **Focus Decoration:** Indicates the item with input focus.
- **Hover Decoration:** Used for mouse-over effects, such as illuminating buttons.

Except for Inactive Text, each text role has a corresponding background role. Other than Normal and Alternate Background, these aren't chosen by you, but determined automatically from Normal Background and the text color. You can preview them by selecting a set other than Common Colors.

The choice of role is left to the developer, and these are guidelines for typical use.

#### Window manager colors

The window manager has its own roles, only available through Common Colors:

- **Active Titlebar:** Used to draw the title bar background, borders or decorations of the active window. Not all window decorations use it the same way.
- **Active Titlebar Text:** Used to draw the title bar text when Active Titlebar is the background.
- **Active Titlebar Secondary:** A second title bar color, which some window decorations use alongside Active Titlebar.

The **Inactive Titlebar**, **Inactive Titlebar Text** and **Inactive Titlebar Secondary** roles are the same, but for inactive windows.

These title bar roles aren't shown for schemes that have their own header colors, which include all the Silver schemes, because the header colors are used instead.

### Disabled and Inactive

The effects on the **Disabled** tab apply to interface elements in the disabled state. The **Inactive** tab has the same effects for inactive windows, and is only there while **Apply effects to inactive windows** is on. Usually inactive elements have reduced contrast and slightly reduced intensity, while disabled ones have strongly reduced contrast and are often notably darker or lighter.

Three types of effect apply to each state, and the two states are independent. **Intensity** and **Color** control the overall color, while **Contrast** deals with foreground colors relative to the background.

#### Intensity

This lightens or darkens the overall color. The middle of the slider produces no change.

- **Shade:** Makes everything lighter or darker in a controlled manner. Each tick changes the intensity by an absolute amount.
- **Darken:** Changes the intensity to a percentage of the initial value. Halfway between middle and maximum gives half the original intensity, and the minimum gives twice.
- **Lighten:** The opposite of darken, working with “distance from white”. The minimum is twice as far from white as the original, and halfway between middle and maximum is halfway between the original color and white.

#### Color

This also changes the overall color, but isn't limited to intensity.

- **Desaturate:** Changes the relative chroma. The middle produces no change, the maximum gives a gray of the same perceived intensity, and lower settings give a more vibrant color.
- **Fade:** Blends the original color into a reference color. The minimum produces no change, and the maximum gives the reference color.
- **Tint:** Similar to Fade, except that hue and chroma change more quickly while intensity changes more slowly.

#### Contrast

These are similar to the color effects, except they apply to the text with the background as the reference color, and Desaturate isn't available. Fade produces text that fades out more quickly but keeps its color longer. Tint produces text that matches the background's color more quickly, but keeps its contrast in intensity for longer. The minimum produces no change, and the maximum makes the text disappear into the background.
