---
title: Aurorae window decorations
description: How to create window decorations with SVGs.
source_url: https://develop.kde.org/docs/plasma/aurorae/
source_authors: [Carl Schwan, Johannes Zarl-Zierl, Thiago Sueto, tusooa the west wind]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "the KWin/Aurorae package structure and decorationbridge in sonic-win. The engine is not in SonicDE's sources: option names were spot-checked against strings in the installed org.kde.kwin.aurorae plugin (kde-plasma/aurorae 6.7.3); defaults and behavior come from the KDE page. No theme was run."
---

# Aurorae window decorations

Aurorae is a theme engine for window decorations: the frames around windows that typically contain the title and buttons for closing, minimizing and so on. It renders the decoration and buttons from SVG or QML, with a simple configuration file for the details. Decorations can also be written in C++ with the [KDecoration API](https://github.com/Sonic-DE/sonic-decoration). This page describes how to create a theme with SVGs.

SonicWin loads Aurorae as a decoration plugin, `org.kde.kwin.aurorae`, which isn't part of SonicDE's own repositories. It comes from the separate `aurorae` package, which SonicWin uses as a runtime dependency.

An easy way to start is to modify an existing theme. You can find many in the [KDE Store](https://store.kde.org/browse?cat=114&ord=latest).

## Package structure

An Aurorae theme is one folder containing:

- SVG files for the decoration and buttons
- a KConfig rc file for the theme details
- a `metadata.desktop` file with information about the theme

```text
ExampleDecoration
├── metadata.desktop
├── ExampleDecorationrc
├── decoration.svg
├── close.svg
├── maximize.svg
├── minimize.svg
└── ...
```

Each SVG file needs certain element IDs to work as part of a decoration. In a vector graphics editor like [Inkscape](https://inkscape.org/), you can set them by selecting an object, opening the Object Properties pane and changing the ID and Label fields. You can also use colors from the [system color scheme](../theme/colors.md).

Themes installed for the whole system are in `/usr/share/aurorae/themes/`, and those for one user in `~/.local/share/aurorae/themes/`. If you copy your folder to the user folder, it can be selected in System Settings. Make sure the theme name matches for the folder, the configuration file and the metadata file, as described below.

## Window frame

The window frame is in the file `decoration.svg`. It has to contain all the elements of a [desktop theme background](../theme/background-svg.md). Styles for special states, such as inactive windows, can optionally be in the same file.

Each state consists of one element for each side of the window, with the side as a suffix in the ID: `left`, `right`, `top`, `bottom`, `topleft`, `topright`, `bottomleft`, `bottomright`, `center`.

### Basic decoration

The base decoration elements use the prefix `decoration`, as in `decoration-top`.

### Inactive windows

A different style for inactive windows uses the prefix `decoration-inactive`. If it isn't provided, inactive windows look like active ones.

### Opacity

A special decoration for opaque mode, when compositing isn't active, can be provided. The prefix is `decoration-opaque` for active windows and `decoration-opaque-inactive` for inactive ones. If it isn't provided, the engine falls back to the translucent version.

### Blur

For transparent decorations to get a blur effect, provide an element named `mask` that specifies the region to blur. It should use the same padding as the active and inactive decorations. Without a mask element, blur is disabled for the theme.

### Inner borders

Aurorae supports inner borders, a border at the margin to the window. You could add them directly in the decoration element, but inner borders are preferred because they support the configurable border sizes.

For inner borders, `decoration.svg` can include two additional frames: `innerborder` and `innerborder-inactive`. If the inactive element isn't present, the active one is used for inactive windows.

These frames must include the border elements. Only those are visible, not the center element. For performance, the center element should be a simple rectangle, and to support decorations behind windows it should be completely translucent.

Inner borders aren't shown for maximized windows. If a maximized window should show one, add it directly to the `maximized` element.

### Maximized windows

To better support maximized windows there is a special frame, `decoration-maximized`, with the versions `decoration-maximized-inactive`, `decoration-maximized-opaque` and `decoration-maximized-opaque-inactive`. If they aren't provided, the engine falls back to the normal decoration.

In all cases only the center element is used, so there is no need to specify borders. In a window with translucent widgets, the center element is stretched to the size of the complete window. To support Fitts' Law, all `TitleEdge` settings are set to 0, so the buttons are directly next to the screen edges.

## Buttons

Each button needs an SVG file. If a theme has no file for a button type, the engine doesn't include that button, and the decoration will miss it. There is no fallback to a default theme. Each button has to provide the `center` element, and borders aren't supported.

### Button types

- `close` (`X`): closes the window
- `minimize` (`I`): minimizes the window
- `maximize` (`A`): maximizes the window; replaced by `restore` when maximized
- `restore`: restores the window from the maximized state
- `alldesktops` (`S`): shows the window on all desktops
- `keepabove` (`F`): keeps the window above others
- `keepbelow` (`B`): keeps the window below others
- `shade` (`L`): shades the window
- `help` (`H`): shows help information
- (`M`): the window menu ("Move to Desktop" and so on). This button isn't provided as an SVG file, but it can be used in the configuration.
- `appmenu` (`N`): the application menu ("File", "Edit" and so on). It can be provided as an SVG file, and otherwise falls back to the window's icon.

Each file is named after the button type, so the close button is `close.svg`. The letter in brackets is the button's name in the configuration (see below).

### Button states

Each button can have different states, and a theme can style active and inactive windows differently. These element prefixes are available:

- `active`: normal button for active windows
- `inactive`: normal button for inactive windows
- `hover`: hover state for active windows
- `hover-inactive`: hover state for inactive windows
- `pressed`: pressed button
- `pressed-inactive`: pressed button for inactive windows
- `deactivated`: the button can't be clicked, for example because the window can't be closed
- `deactivated-inactive`: the same for inactive windows

At least the `active` element has to be provided. The others are optional, and `active` is the fallback for all of them. If the theme provides `inactive`, it is the fallback for inactive states: if a theme has a `hover` element but none for `inactive`, the inactive window has no hover effect. The same is true of `pressed` and `deactivated`.

`alldesktops`, `keepabove`, `keepbelow` and `shade` are toggle buttons. When clicked, they stay in the `pressed` (or `pressed-inactive`) state, and clicking again changes them back.

All of these elements go in one SVG file for each button type.

## Configuration

The configuration file is named after the plugin name in the metadata file, with the suffix `rc`. It is a KConfig file.

These options go in a `[General]` group:

- `TitleAlignment`: horizontal alignment of the window title (default: `Left`)
- `TitleVerticalAlignment`: vertical alignment of the window title (default: `Center`)
- `Animation`: animation duration in ms when hovering a button and on an active or inactive change (default: `0`)
- `ActiveTextColor`: title text color of active windows (default: `0,0,0,255`)
- `InactiveTextColor`: title text color of inactive windows (default: `0,0,0,255`)
- `UseTextShadow`: draw a shadow behind the title text (default: `false`)
- `ActiveTextShadowColor`: shadow text color of active windows (default: `255,255,255,255`)
- `InactiveTextShadowColor`: shadow text color of inactive windows (default: `255,255,255,255`)
- `TextShadowOffsetX`: offset of the shadow in the x direction (default: `0`)
- `TextShadowOffsetY`: offset of the shadow in the y direction (default: `0`)
- `HaloActive`: draw a halo behind the title of active windows (default: `false`)
- `HaloInactive`: draw a halo behind the title of inactive windows (default: `false`)
- `LeftButtons`: buttons in the left button group (default: `MS`)
- `RightButtons`: buttons in the right button group (default: `HIAX`)
- `Shadow`: the decoration provides shadows (default: `true`)
- `DecorationPosition`: decoration on top (`0`), left (`1`), right (`2`) or bottom (`3`) (default: `0`)

If `Shadow` is enabled, `Padding` values have to be added to the layout configuration (see below).

## Layout

These diagrams show which value influences which part of the decoration.

Window:

```text
 ___________________________________________________________________
|                 PaddingTop                                        |
|  _______________________________________________________________  |
| |              TitleEdgeTop                                     | |
| |_______________________________________________________________| |
| | TitleEdgeLeft |   [title]                    | TitleEdgeRight | |
| |_______________|______________________________|________________| |
| |              TitleEdgeBottom                                  | |
| |_______________________________________________________________| |
| | |                                                           | | |
|PaddingLeft                                            PaddingRight|
| | |                                                           | | |
| |BorderLeft                                          BorderRight| |
| |_|___________________________________________________________|_| |
| |              BorderBottom                                     | |
| |_______________________________________________________________| |
|                PaddingBottom                                      |
|___________________________________________________________________|
```

Title:

```text
 __________________________________________________________________________
| ButtonMarginTop             |             |              ButtonMarginTop |
|_____________________________|             |______________________________|
| [Buttons] | TitleBorderLeft | TitleHeight | TitleBorderRight | [Buttons] |
|___________|_________________|_____________|__________________|___________|
```

Buttons:

```text
 _____________________________________________________________________________________________
| button | spacing | button | spacing | explicit spacer | spacing | ...    | spacing | button |
|________|_________|________|_________|_________________|_________|________|_________|________|
```

These options go in a `[Layout]` group:

- `BorderLeft`, `BorderRight`, `BorderBottom` (default: `5`), `BorderTop` (default: `0`)
- `TitleEdgeTop`, `TitleEdgeBottom`, `TitleEdgeLeft`, `TitleEdgeRight` (default: `5`)
- `TitleEdgeTopMaximized`, `TitleEdgeBottomMaximized`, `TitleEdgeLeftMaximized`, `TitleEdgeRightMaximized` (default: `0`)
- `TitleBorderLeft`, `TitleBorderRight` (default: `5`)
- `TitleHeight` (default: `20`)
- `ButtonWidth` (default: `20`)
- `ButtonWidthMinimize`, `ButtonWidthMaximizeRestore`, `ButtonWidthClose`, `ButtonWidthAlldesktops`, `ButtonWidthKeepabove`, `ButtonWidthKeepbelow`, `ButtonWidthShade`, `ButtonWidthHelp`, `ButtonWidthMenu` (default: `20`)
- `ButtonHeight` (default: `20`)
- `ButtonSpacing` (default: `5`)
- `ButtonMarginTop` (default: `0`)
- `ExplicitButtonSpacer` (default: `10`)
- `PaddingTop`, `PaddingBottom`, `PaddingRight`, `PaddingLeft` (default: `0`)

`Border<Direction>` is only needed if the decoration isn't in that direction: `BorderTop`, for example, only for decorations on the left, right or bottom. `Padding<Direction>` values can be used to provide shadows. The `ButtonWidth<Action>` values are optional, and fall back to `ButtonWidth`.

If the decoration is on a side other than the top, options that exist only for the top apply to that side. With `DecorationPosition=1` (left), `ButtonMarginTop` means `ButtonMarginLeft`, while the `TitleEdge` options stay as they are, being defined for all four sides. A shaded window always has its decoration on top, so the layout is transformed to be painted there again.

The user can change the border and button sizes in the settings. The defaults are the values in the configuration file. The border size influences the right, left and bottom borders, and the button size influences the size of all buttons and the title height.

The buttons have to be scalable to support this, and the borders may extend into the center element if the border size changes.

## Metadata

The theme must contain a `metadata.desktop` file with information such as the name, author and license. It starts with a `[Desktop Entry]` group heading and has these entries:

- `Name`: the name displayed in theme selection
- `Comment`: a comment on the theme
- `X-KDE-PluginInfo-Name`: an ID for the theme, which should be identical to the folder name
- `X-KDE-PluginInfo-Author`: the author's name, used in the about dialog
- `X-KDE-PluginInfo-Email`: the author's email address, used in the about dialog
- `X-KDE-PluginInfo-Website`: the theme's website
- `X-KDE-PluginInfo-Version`: the version, such as 1.0
- `X-KDE-PluginInfo-License`: the license, such as GPLv3

## Publishing

If you've created something nice, consider sharing it! Make a zip file of the package folder and upload it to the [KDE Store](https://store.kde.org/browse/), which SonicDE uses for downloads, under the Window Decorations category. People can then install your theme with "Get New Window Decorations…" in System Settings.
