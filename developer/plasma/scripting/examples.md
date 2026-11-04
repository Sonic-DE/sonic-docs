---
title: Scripting examples
description: Some examples of desktop scripts.
source_url: https://develop.kde.org/docs/plasma/scripting/examples/
source_authors: [Alexander Lohnau, Carl Schwan, Chris Holland, Felipe Peter, Marius P, Mikhail Zolotukhin, Phu Nguyen, Plata Hill, Thiago Sueto, Torstein Wilhelmsen Sandvik, Yifan Zhu, Zren (Chris Holland)]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "scripts run through evaluateScript on a sonicshell on a private Xvfb and D-Bus; layout templates in sonic-desktop-interface"
---

# Scripting examples

## Print the configuration of all widgets

```js
function logWidget(widget) {
    print(widget.type + ":\n");

    // slice() clones the array, which changes with the current group
    for (const group of widget.configGroups.slice()) {
        print("\t" + group + ":\n");
        widget.currentConfigGroup = [group];

        for (const key of widget.configKeys) {
            print("\t\t" + key + ": " + widget.readConfig(key) + "\n");
        }
    }
}

for (const containment of desktops().concat(panels())) {
    print(containment.type + "\n");
    containment.widgets().forEach(logWidget);
}
```

`print()` doesn't add a line break.

## Print the configuration of one kind of widget

`widgets()` takes an optional widget ID. This example uses `logWidget()` from the previous example.

```js
for (const containment of desktops().concat(panels())) {
    containment.widgets("org.kde.plasma.keyboardlayout").forEach(logWidget);
}
```

## Add a widget to the system tray

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

## Change a setting of one kind of widget

```js
function setWidgetConfig(type, group, key, value) {
    for (const containment of desktops().concat(panels())) {
        for (const widget of containment.widgets(type)) {
            widget.currentConfigGroup = [group];
            print(widget.type + " (id: " + widget.id + ") [" + group + "] " + key
                + ": " + widget.readConfig(key) + " => " + value + "\n");
            widget.writeConfig(key, value);
        }
    }
}

setWidgetConfig("org.kde.plasma.digitalclock", "Appearance", "showDate", "true");
```

## Create a panel

The entries in the desktop's "Add Panel" menu each run a script from a [layout template](templates.md). This is `org.kde.plasma.desktop.appmenubar/contents/layout.js` from [`sonic-desktop-interface/layout-templates`](https://github.com/Sonic-DE/sonic-desktop-interface/tree/master/layout-templates):

```js
var panel = new Panel
panel.location = "top";
panel.height = Math.round(gridUnit * 1.5);

panel.addWidget("org.kde.plasma.appmenu");
```
