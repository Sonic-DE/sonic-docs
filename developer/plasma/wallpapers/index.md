---
title: Wallpapers
description: Set a custom accent color for a wallpaper.
source_url: https://develop.kde.org/docs/wallpapers/
source_authors: [Carl Schwan]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "MediaProxy::getAccentColorFromMetaData in sonic-workspace/wallpapers/image and the wallpaper package structure. Read from code; no wallpaper was applied."
---

# Wallpapers

SonicDE can select an accent color automatically from the colors of the current wallpaper. A wallpaper can also specify one, for more artistic control.

## Setting a custom accent color

Add the `X-KDE-PlasmaImageWallpaper-AccentColor` property to your wallpaper's `metadata.json` to set the accent color applied when the user enables the "Accent color from wallpaper" option. This sets it to red:

```json
{
    "KPlugin": {
        "Id": "TestTest",
        "License": "CC-BY-SA-4.0",
        "Name": "CustomAccentColor"
    },
    "X-KDE-PlasmaImageWallpaper-AccentColor": "red"
}
```

You can also use a hex color code instead of a color name:

```json
{
    "KPlugin": {
        "Id": "TestTest",
        "License": "CC-BY-SA-4.0",
        "Name": "CustomAccentColor"
    },
    "X-KDE-PlasmaImageWallpaper-AccentColor": "#FF0000"
}
```

## Light versus dark

The same accent color doesn't always look right with both light and dark themes, so you can set one for each. Use `Light` and `Dark` under the property. If the color scheme is light, or there is no `Dark` entry, the `Light` color is used.

```json
{
    "KPlugin": {
        "Id": "TestTest",
        "License": "CC-BY-SA-4.0",
        "Name": "CustomAccentColor"
    },
    "X-KDE-PlasmaImageWallpaper-AccentColor": {
        "Light": "red",
        "Dark": "cyan"
    }
}
```
