---
title: Transparency and the unified header
description: How a desktop style follows the transparency set in the Transparency settings, how popup headings and window decorations form one see-through header, and how widget styles follow the menu transparency.
checked_against: "sonic-frameworks-svg (ImageSetPrivate::readDesktopThemeOpacity), sonic-interface-libraries (default and Silver desktop themes), sonic-workspace (kcms/transparency), sonic-silver and sonic-breeze (kstyle/breezestyle.cpp), sonic-win (DecorationBridge), sonic-frameworks-color-scheme (src/ktoolsarea.h, src/ktoolsarea.cpp), Qt 6.11.3"
---

# Transparency and the unified header

## Following the transparency settings {#follow}

The Desktop section of **System Settings → Colors & Themes → Transparency** sets how
see-through panels, pop-ups, tooltips and desktop widgets are. It works like [accent colors](colors.md): one desktop-wide setting,
applied to every desktop style that asks for it. Styles that don't ask keep their own transparency.

A style asks for it with one line in its `colors` file, next to `FollowAccentColor`:

```ini
[General]
FollowAccentColor=true
FollowDesktopThemeOpacity=true
```

The settings live in `kdeglobals`:

```ini
[DesktopThemeOpacity]
Enabled=true
Panels=70
Popups=85
Tooltips=85
Widgets=80
```

Values are percent. A missing key uses the default shown here. With `Enabled=false` (the default), or in a
style without `FollowDesktopThemeOpacity=true`, nothing changes.

## Marking the see-through parts {#classes}

SonicDE adds one CSS rule per surface to the stylesheet it puts into every theme SVG, next to the
`.ColorScheme-…` color rules:

| Class | Surface | Files |
| --- | --- | --- |
| `SonicOpacity-Panel` | panels | `widgets/panel-background` |
| `SonicOpacity-Popup` | pop-ups | `dialogs/background` |
| `SonicOpacity-Tooltip` | tooltips | `widgets/tooltip` |
| `SonicOpacity-Widget` | desktop widgets | the `blurred-*` prefix of `widgets/background` |

Give the class to each see-through fill, next to its color class, and put the style's own opacity in
the **`opacity` attribute**:

```xml
<rect id="rect4138" style="fill:currentColor" opacity="0.85"
      class="ColorScheme-Background SonicOpacity-Popup" width="32" height="32" />
```

- Never put that opacity inside `style=""`. An inline style wins over the generated rule, so the setting
  would have no effect. Measured with Qt 6.11.3: `opacity="0.75"` with a 0.25 rule draws at 0.25;
  `style="opacity:0.75"` with the same rule stays at 0.75.
- The file needs the `<style id="current-color-scheme">` element (see [System and accent
  colors](colors.md)); the rules are only added to files that have it.
- Tag the plain files and the `translucent/` ones. The desktop shell uses `translucent/` when the blur
  effect is on, the plain files when compositing is on without blur, and `opaque/` without compositing.
  Leave `opaque/` alone.
- Only tag the fills. Edge highlights, shadows (`shadow-*`), masks (`mask-*`) and hints keep their values.
- Without the setting, the attribute is used and the style looks exactly as before.

The default and Silver themes in sonic-interface-libraries show the full set.

## The unified header {#header}

### Pop-up headings

A pop-up's header and footer, such as the search bar and the buttons along the bottom of the
application launcher, are drawn from `widgets/plasmoidheading`, on top of the pop-up's background. To
keep them as see-through as the rest of the pop-up, the heading draws **no fill**, only its separator
lines (`ColorScheme-Frame`): give the fill paths `opacity="0"` and keep the elements, so the frame sizes
and margins stay the same. Any fill there would stack on the pop-up's own and look more solid.

### Window decorations

The titlebar and the toolbars and menu bars under it can be one see-through surface, the tools area.
Its settings are shared desktop-wide in the `[ToolsArea]` group of `kdeglobals`, set in the Titlebars
section of **Transparency**, and read through `KToolsArea` in sonic-frameworks-color-scheme by
the decoration, the app style and the Qt Quick platform integration.

A window decoration that draws a see-through titlebar from these settings says so in its plugin
metadata:

```json
{
    "KPlugin": { "Name": "Silver" },
    "X-SonicDE-ToolsArea": true
}
```

When SonicWin loads a decoration without it, it turns the tools area off (`Enabled=false`) and records
that it did (`DisabledByDecoration=true`), so toolbars don't stay see-through under a solid titlebar.
When it loads a decoration with the marker, it turns a tools area it turned off back on. A tools area
the user turned off stays off.

### Reading the settings in code {#ktoolsarea}

Read the tools area through [`KToolsArea`](/docs/api/kcolorscheme/ktoolsarea) (`#include <KToolsArea>`,
`KF6::ColorScheme`), not by reading `[ToolsArea]` yourself, so that the decoration, the app style, the
platform theme and the settings pages always agree:

```cpp
const KSharedConfigPtr kdeglobals = KSharedConfig::openConfig(QStringLiteral("kdeglobals"));
const KToolsArea::Settings settings = KToolsArea::settings(kdeglobals, QCoreApplication::applicationName());
if (settings.enabled) {
    const KToolsArea::Colors colors = KToolsArea::colors(kdeglobals, settings);
    // colors.palette's Window colour carries the opacity when colors.headerColors and
    // settings.applyOpacityToHeader are set
}
```

- `settings(scheme, name)` returns the `[ToolsArea]` keys (`Enabled`, `ActiveOpacity`, `InactiveOpacity`,
  `ApplyOpacityToHeader`, `MatchApplicationColor`, `BlurBehind`, `OpaqueWhenMaximized`, `SeparatorColor`,
  `HideTitleBar`), with the first enabled exception whose `Pattern` matches `name` applied on top. Pass
  the application name or the window class; an empty name skips the exceptions. Opacities are percent.
- Exceptions are the `[ToolsArea][Application <n>]` groups, a regular expression in `Pattern` plus any of
  the keys above. Built-in default exceptions come first and can only be switched off, with
  `[ToolsArea][Default Application <n>]` `Enabled=false`. `exceptions()` and `writeExceptions()` read and
  write them.
- `colors(scheme, settings)` gives the palette to draw with: the scheme's Header colours (or the Window
  colours without a Header set), the opacity as the Window colour's alpha when header colours apply and `ApplyOpacityToHeader` is on, a
  `translucent` flag, and the separator colour (`SeparatorColor`, or one mixed from the Window and
  WindowText colours).
- `writeSettings()` writes the keys and sets `Enabled=true`. A writer then sends
  `KGlobalSettings.notifyChange` itself; readers reload on it. `snapshot()` returns every `[ToolsArea]`
  entry as text, to tell whether anything changed.
- `followDecoration(scheme, supported)` is what SonicWin calls with the `X-SonicDE-ToolsArea` marker, as
  described above. `migrateFromSilver()` moves the settings the Silver theme kept in `silverrc` before
  the tools area existed, once.

## Menus {#menus}

How see-through menus are is one desktop-wide value, `[Menus] Opacity` in `kdeglobals` (percent, 100 by
default), set in the Menus section of **Transparency**. A widget style that draws see-through menus
reads it through `KToolsArea` and reloads on `KGlobalSettings.notifyChange`, as the Silver and Breeze
styles do in `loadConfiguration()`:

```cpp
const KSharedConfigPtr kdeglobals = KSharedConfig::openConfig(QStringLiteral("kdeglobals"));
kdeglobals->reparseConfiguration();
KToolsArea::migrateMenuOpacity(kdeglobals);
const int menuOpacity = KToolsArea::menuOpacity(kdeglobals);
```

- `menuOpacity(scheme)` returns the value, clamped to 0–100.
- `writeMenuOpacity(scheme, opacity)` writes it with KConfig's Notify flag.
- `migrateMenuOpacity(scheme)` runs once, while `[Menus]` has no `Opacity` key: it moves `MenuOpacity`
  from Silver's `silverrc` (`[Style]`), or else Breeze's `breezerc`, and deletes it from both.
