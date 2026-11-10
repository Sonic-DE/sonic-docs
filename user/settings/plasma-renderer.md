---
title: Plasma Renderer
description: Advanced settings for how the desktop draws its Qt Quick interface.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-desktop-interface (kcms/qtquicksettings/kcmqtquicksettingswidget.ui, renderer.kcfg, kcmqtquicksettings.cpp); written from the code, not clicked through"
---

# Plasma Renderer

The Plasma Renderer module adjusts how the desktop's Qt Quick interface, such as Sonic Shell's panels and widgets, is drawn. These are troubleshooting settings: as the module warns, changing them can break your desktop. Only change them if you know what you're doing, for example to work around a graphics driver problem.

The module isn't listed in the System Settings sidebar. Open it with `kcmshell6 kcm_qtquicksettings`.

- **Rendering Backend:** What draws the interface: **Automatic**, **Open GL**, **Software** or **Vulkan**. The default is **Automatic**. **Software** doesn't use the graphics card, which can help when the driver has problems, but it's slower.
- **GL Core Profile:** **Force** makes the interface use an OpenGL core profile. It's off by default.
- **Render Loop:** How drawing is scheduled: **Automatic**, **Basic** or **Threaded**. The default is **Automatic**. **Basic** draws everything on the main thread, which can help with some drivers.

The settings are saved in `~/.config/kdeglobals`, in the `QtQuickRendererSettings` group.
