---
title: Desktop scripting
description: Control the SonicDE desktop shell with JavaScript.
source_url: https://develop.kde.org/docs/plasma/scripting/
source_authors: [Alexander Lohnau, Carl Schwan, Chris Holland, Felipe Peter, Marius P, Mikhail Zolotukhin, Phu Nguyen, Plata Hill, Thiago Sueto, Torstein Wilhelmsen Sandvik, Yifan Zhu, Zren (Chris Holland)]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "ShellCorona and shell/scripting in sonic-workspace, interactiveconsole, the plasma-desktop runner; scripts run through evaluateScript on a sonicshell on a private Xvfb and D-Bus"
---

# Desktop scripting

You can control the SonicDE desktop shell with JavaScript. Scripts have access to desktops, panels, activities, widgets and other parts of the shell's configuration. They run in a [QJSEngine](https://doc.qt.io/qt-6/qjsengine.html).

These pages describe the [API](api.md), give [examples](examples.md), explain [layout templates](templates.md) and list common [configuration keys](keys.md).

## An example

This script adds a widget to the system tray of every panel:

```js
const widgetName = "org.kde.plasma.printmanager";

panels().forEach((panel) => {
    panel.widgets("org.kde.plasma.systemtray").forEach((tray) => {
        tray.currentConfigGroup = ["General"];
        const extraItems = tray.readConfig("extraItems").split(",");
        if (!extraItems.includes(widgetName)) {
            extraItems.push(widgetName);
            tray.writeConfig("extraItems", extraItems);
            tray.reloadConfig();
        }
    });
});
```

## Running scripts

Scripts can run in four ways.

### On first run

When `sonicshell` starts without an existing configuration, it runs a layout script to create the desktop. It looks in the current global theme for `contents/layouts/org.sonicde.desktop-layout.js`, and otherwise in the shell package for `contents/layout.js`. A global theme can also provide `contents/layouts/org.sonicde.desktop-prelayout.js`, which runs first.

The themes in [`sonic-silver/look-and-feel`](https://github.com/Sonic-DE/sonic-silver/tree/master/look-and-feel) are examples of this.

### On update

When `sonicshell` starts, it looks for `.js` scripts in the `contents/updates` directory of the shell package, for example:

```text
/usr/share/plasma/shells/org.sonicde.desktop/contents/updates/unlock_widgets.js
```

Each script runs once. The ones that have run are recorded in the `[Updates]` group of `~/.config/sonicshellrc`, so removing that file runs them all again.

```ini
[Updates]
performed=/usr/share/plasma/shells/org.sonicde.desktop/contents/updates/unlock_widgets.js
```

For security reasons, update scripts in your home directory aren't run.

SonicDE's own update scripts are in [`desktoppackage/contents/updates`](https://github.com/Sonic-DE/sonic-desktop-interface/tree/master/desktoppackage/contents/updates).

### Interactively

The interactive console is a window for writing and running scripts. Open it by typing `desktop console` in KRunner, or with this command:

```bash
plasma-interactiveconsole --plasma
```

Enter a script in the window and its output appears in the lower half. `Ctrl+E` runs the script, and scripts can be saved to and loaded from disk.

To open a script file straight away, add its path: `desktop console /path/to/file.js` in KRunner, or `plasma-interactiveconsole --plasma /path/to/file.js` in a terminal.

### From the terminal

The shell runs a script through its D-Bus method `evaluateScript`, and returns what the script prints:

```bash
qdbus org.sonicde.sonicshell /SonicShell org.sonicde.SonicShell.evaluateScript "$(cat /path/to/file.js)"
```

`qdbus` is in Qt's tool directory; some distributions install it in the `PATH` as `qdbus6`. See [the D-Bus introduction](../../dbus/introduction.md#qdbus).

If the script fails, the call returns an error, and anything it printed before that is lost.

## Default widget settings from a global theme

A global theme can contain scripts that change the default configuration of widgets, so that distributions and system integrators can set up the desktop differently.

The API is the same as for layout scripts, with two more global variables:

- `applet`: the widget. For a containment, `applet` and `containment` are the same.
- `containment`: the containment the widget is in.

The scripts are in the `contents/plasmoidsetupscripts` folder of the global theme, named after the widget's ID. To show the battery percentage by default, as the Silver themes do, the file is `contents/plasmoidsetupscripts/org.kde.plasma.battery.js`:

```js
applet.currentConfigGroup = ["General"];
applet.writeConfig("showPercentage", true);
applet.reloadConfig();
```
