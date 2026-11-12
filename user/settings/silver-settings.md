---
title: Silver Settings
description: Fine-tune SonicDE's Silver application style and window decoration, and use and share Silver presets.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-silver (kstyle/config/main.cpp, kstyle/config/ui/breezestyleconfig.ui, kstyle/breeze.kcfg, kdecoration/config/breezeconfigwidget.cpp, kdecoration/config/loadpreset.cpp, kdecoration/config/ui/*.ui, kdecoration/config/presets/, libbreezecommon/autotests/presettoolsareatest.cpp); written from the code, not clicked through"
---

# Silver Settings

Silver is SonicDE's own look, and its default. **Silver Settings** collects everything you can adjust about it in one window, with two pages:

- **Silver: Application Style** changes how buttons, scroll bars, menus and other controls are drawn in applications.
- **Silver: Window Decoration** changes the titlebar, its buttons, and the borders, shadows and corners of windows.

There are three ways to open these settings:

- Start **Silver Settings** from the application launcher.
- In [Application Style](application-style.md), click **Configure Style…** on the Silver preview. This opens the application style page only.
- In [Window Decorations](window-decorations.md), click the edit button on the Silver preview. This opens the window decoration page only.

Click **Apply** to use your changes, or **Defaults** to go back to Silver's standard settings.

## Application style

### General

- **Enable extended resize handles:** Makes the handles between resizable parts of a window, such as the panels of a file manager, easier to grab.
- **Draw focus indicator in lists:** Marks the item that has the keyboard focus in a list.
- **Draw slider tick marks:** Shows the scale marks along sliders.
- **Keyboard accelerators visibility:** When the underlined letters in menus and buttons show: **Always hide**, **Show when Alt key is pressed** (the default) or **Always show**.
- **Centre tabbar tabs:** Centers the tabs in a tab bar instead of starting them at the left.
- **Windows' drag mode:** Where you can grab a window to move it: **Drag windows from titlebar only**, **Drag windows from titlebar, menubar and toolbars** (the default) or **Drag windows from all empty areas**.
- **Show button gradient effect:** Draws buttons with a slight gradient. Off by default.
- **Draw toolbar item separators:** Shows the separator lines between groups of toolbar buttons.
- **Corner radius:** How round the corners of frames and buttons are. **Derive from Silver window corner radius** (the default) uses the same radius as your windows; **Custom** lets you set your own.

### Frames

- **Draw frame around dockable panels:** Draws a frame around panels you can move around inside a window.
- **Draw frame around side panels:** Draws a frame around side panels, such as the Places panel in [Ecco](../applications/ecco.md).
- **Draw a thin line to indicate focus in menus and menubars:** Marks the focused item in menus and menu bars with a thin line.

### Scrollbars

- **Scrollbar top/bottom margins:** The space at the ends of a scroll bar.
- **Draw scrollbar separator:** Draws a line between a scroll bar and the content. Off by default.
- **Arrow buttons:** **Top arrow button type:** and **Bottom arrow button type:** choose **No Buttons**, **One Button** or **Two Buttons** at each end of a scroll bar. **Space between arrow and groove:** or **Space between arrows and groove:** sets the gap between the arrows and the track. **Auto-hide arrows** shows the arrows only while the pointer is over the scroll bar; it's offered when both ends have **One Button**, and is on by default.
- **Groove/Slider:** **Slider thickness when mouse is over:** and **Slider thickness when mouse is not over:** (as a percentage of the first) set how wide the slider is. **Slider side padding:** and **Slider minimum height:** set the space beside the slider and its smallest length.

### Transparency

How see-through menus are is set in [Transparency](transparency.md#menus), shared with the Breeze style.

## Window decoration

The **Presets...** button at the top right is described in [Presets](#presets) below.

### Buttons

- **Shape:** The shape of the titlebar buttons: **Full-height Rectangle**, **Full-height Rounded Rectangle**, **Integrated Rounded Rectangle**, **Integrated Rounded Rectangle, grouped**, **Circle**, **Square** or **Rounded Square**.
- **Icons:** The style of the symbols on the buttons: **Use system icon theme**, or one of Silver's own sets: **Silver**, **SuessigSilver**, **Oxygen/Breeze**, **Klasse**, **Traditional**, **Metro**, **Fluent**, **Ark**, **Arkopal**, **Arkopal (Left Panel)** and **Kisweet**.
- **Icon size:** From **8 - Tiny** to **48 - Humongous**. There's a separate size for when you use the system icon theme.
- **Bold icons:** For Silver's own icon sets: **Bold**, **Fine**, **Bold on HiDPI only**, **Bold active window** or **Bold active, HiDPI**.
- **Force-colourize icons:** For the system icon theme: colors its icons to match the buttons.
- **Button Behaviour...** opens a dialog for how buttons react when you hover over and press them, for the active and inactive window, with separate settings for the close button, and **Unison hovering**.
- **Button Colours...** opens a dialog for the colors of each button and its symbol.
- **Button Size && Spacing...** opens a dialog for the size of the buttons, the spacing between them, the margins at either end, and the button corner radius.

### Titlebar

- **Titlebar Spacing...** opens a dialog for the titlebar's top, bottom, left and right margins, separate top and bottom margins for maximized windows, and the title alignment: **Left**, **Centre**, **Centre (Full Width)** or **Right**.
- **On active window:** **Draw titlebar background gradient**, **Draw separator under titlebar**, **Make title bold** and **Underline title**.

The titlebar's transparency and blur are set in [Transparency](transparency.md#titlebars), because they're shared by every window decoration and also apply to applications drawn with Qt Quick.

Silver can show an application's menus in the titlebar, in the colours of its **Application menu** button. That's also set under **Configure Titlebar…**, with **Application menu button style**.

### Window

- **Shadows:** **Shadow Style...** opens a dialog for the shadow's **Size:** (**None**, **Small**, **Medium**, **Large** or **Very Large**), strength and **Colour:**.
- **Borders:** **Use titlebar colour for all window borders**, and **Draw border on maximized windows**, which keeps the border on maximized windows. Off by default. To resize a maximized window from its edges, borders must be turned on as well.
- **Corners:** **Corner Radius:** sets how round window corners are. **Round all corners when no borders (clips window content)** also rounds the bottom corners when windows have no borders, by cutting off the corners of the window's content.
- **Thin window outline:** **Window Outline Style...** opens a dialog for a thin line around windows, separately for the active and inactive window: **None**, **Shadow colour**, **Contrast**, **Accent colour**, **Contrast blended with accent colour**, **Custom colour** or **Contrast blended with custom colour**, each with its own opacity, and the outline thickness. **Colourize with highlighted button's colour** takes the outline's color from the titlebar button you're pointing at.

### Animations

**Enable animations** turns the decoration's animations on and off; it's on by default. **Animations speed:** goes from **Slower** to **Faster**.

### Window-Specific Overrides

Different settings for particular windows. **Default overrides (can be enabled/disabled only):** lists the overrides Silver comes with; you can only switch these on and off. **User-specified overrides:** are your own.

Each override matches windows by **Window Class Name** or **Window Title** with a regular expression; **Detect Window Properties...** lets you click a window to fill these in. It can then set a different **Preset:**, **Border size:**, and whether to hide the titlebar: **Never**, **Always**, **On maximized windows**, **On any maximization**, **On windows kept behind**, or **On any maximization or windows kept behind**. Under **Application Style Options**, a regular expression for the **Application name** makes the Silver application style inside that application follow the override too.

## Presets

A preset is a complete set of Silver window decoration settings with a name. **Presets...** opens the list of presets:

- **Load** applies the selected preset.
- **Add...** saves your current settings as a new preset, under **Name of new Preset:**.
- **Remove** deletes the selected preset.
- **Export To File...** saves the selected preset as a `.klpw` file, to back it up or share it.
- **Import From File...** adds presets from `.klpw` files. A file made for a different version of Silver asks before importing. The **Download Silver Preset files** link leads to presets other people have shared.

Silver comes with these presets: **Silver**, **Glassy Silver**, **SuessigSilver**, **Silver-Aurorae**, **Breeze Original**, **Chroma**, **ClassiK v3**, **ClassikStyles**, **Defenestrated 7**, **Defenestrated 8**, **Defenestrated 10**, **Defenestrated 11**, **Eaten Fruits**, **Garden Ornaments**, **KLCXP**, **Opal Fruits** and **Plastik**.

Loading a preset also sets the shared titlebar transparency settings in [Transparency](transparency.md#titlebars), such as the opacity and blur, and saving a preset records them. Silver doesn't keep its own copy of these settings: if you used them in Silver's settings before, they were moved over to the shared settings automatically.

### From the command line

`silver-settings` can also work with presets without opening the window:

- `silver-settings --import-preset <file>` (or `-i`) imports a `.klpw` preset file.
- `silver-settings --load-windeco-preset <name>` (or `-w`) loads the window decoration preset with that name.
- `--force-import-invalid-version` (or `-f`) imports a preset file made for a different version of Silver.
