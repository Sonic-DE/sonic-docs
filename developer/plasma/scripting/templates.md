---
title: Layout templates
description: Reuse scripts through named packages, and add entries to the Add Panel menu.
source_url: https://develop.kde.org/docs/plasma/scripting/templates/
source_authors: [Alexander Lohnau, Carl Schwan, Chris Holland, Felipe Peter, Marius P, Mikhail Zolotukhin, Phu Nguyen, Plata Hill, Thiago Sueto, Torstein Wilhelmsen Sandvik, Yifan Zhu, Zren (Chris Holland)]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "loadTemplate and ShellCorona in sonic-workspace, the layouttemplate package structure, templates in sonic-desktop-interface and sonic-silver; a test template loaded on a sonicshell on a private Xvfb and D-Bus"
---

# Layout templates

Templates are named packages that contain scripts. They let common functionality be reused, and they fill in parts of the user interface, such as the entries in the "Add Panel" menu.

A template package contains:

- `metadata.json`: describes the template
- `contents/layout.js`: the script

Templates are stored in:

- `/usr/share/plasma/layout-templates/`
- `~/.local/share/plasma/layout-templates/`

Install one with:

```bash
kpackagetool6 --type=Plasma/LayoutTemplate -i /path/to/package
```

`metadata.json` has the usual [KPluginMetaData](/docs/api/kcoreaddons/kpluginmetadata) entries, such as `Name` and `Id`, and `KPackageStructure` must be `Plasma/LayoutTemplate`. `X-Plasma-Shell` names the shell the template is for, and `X-Plasma-ContainmentCategories` says what kind of layout it is. `X-SonicDE-HiddenWhilePlaced`, a list of widget `Id`s, leaves the template out of the Add Panel menu while any of those widgets is placed anywhere; see [Where a widget can be placed](../widget/setup.md#where-a-widget-can-be-placed).

```json
{
    "KPlugin": {
        "Id": "org.example.mypanel",
        "Name": "My Panel",
        "Description": "A panel with a clock"
    },
    "X-Plasma-ContainmentCategories": [
        "panel"
    ],
    "X-Plasma-Shell": "sonicshell",
    "KPackageStructure": "Plasma/LayoutTemplate"
}
```

A template's script can read two global variables, `templateName` and `templateComment`. They hold the `Name` and `Description` from the file above, translated if a translation is available.

```js
print(templateName + ": " + templateComment + "\n");

const panel = new Panel;
panel.location = "top";
panel.addWidget("org.kde.plasma.digitalclock");
```

Other scripts can run a panel template with `loadTemplate()`, which returns whether it found the template:

```js
loadTemplate("org.example.mypanel");
```

## Creating panels

A good example is `org.kde.plasma.desktop.defaultPanel`, which ships in [`sonic-desktop-interface/layout-templates`](https://github.com/Sonic-DE/sonic-desktop-interface/tree/master/layout-templates) and holds the layout of the default panel. Because it is marked as a panel template, it shows up in the "Add Panel" menu, where it creates that panel, with its widgets and configuration.

The Silver look has templates of its own in [`sonic-silver/layout-templates`](https://github.com/Sonic-DE/sonic-silver/tree/master/layout-templates).
