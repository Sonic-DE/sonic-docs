---
title: Testing
description: How to quickly test a desktop widget.
source_url: https://develop.kde.org/docs/plasma/widget/testing/
source_authors: [Alexander Hau, Alexander Lohnau, Carl Schwan, Chris Holland, Christoph Dreier, Claudius Ellsel, David Edmundson, Florian Ruechel, Fushan Wen, Johannes Zarl-Zierl, Joshua Goins, Kunda Ki, Marco Martin, Mariusz Libera, Michael Pyne, Mikhail Zolotukhin, Nate Graham, Nicolas Fella, Parth Dhiman, Paul Brown, Plata Hill, Raresh Rus, Rony Bou Moujahed, Thiago Sueto, Tino Lorenz, Tobias Fella, Yaron Shahrabani, Zren (Chris Holland), ivan tkachenko, yaniss khima]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "plasmawindowed and plasmoidviewer (sonic-theme-sdk) options and runs on Xvfb, kwriteconfig6, sonicshell"
---

# Testing

## plasmawindowed

There are three ways to test a widget.

1. `plasmawindowed` can be used if the widget is installed to `~/.local/share/plasma/plasmoids`. It remembers changes you make to the configuration, as it is the same command used for "windowed widgets". It has limited features for displaying the widget, but it comes with the desktop.
2. `plasmoidviewer`, explained further down, can display a widget as a desktop widget or a panel widget. It can also test a widget that isn't installed yet. It comes with [sonic-theme-sdk](https://github.com/Sonic-DE/sonic-theme-sdk).
3. Install the widget and add it to your panel, restarting the shell each time with `sonicshell --replace`. This takes a few seconds for the panel to load, so it is best kept for a final test.

```bash
plasmawindowed --help
```

To test the Application Launcher widget:

```bash
plasmawindowed org.kde.plasma.kickoff
```

## plasmoidviewer

```bash
plasmoidviewer --help
```

You can test an installed widget by its plugin id:

```bash
plasmoidviewer -a org.kde.plasma.kickoff
```

Or run a widget from a folder. This is particularly useful for development, as you can skip the install step:

```bash
plasmoidviewer -a ~/Code/plasmoid-helloworld/package
```

## Test as a desktop widget

`--location=desktop` is for the desktop wallpaper, not desktop widgets. Desktop widgets use `--location=floating`.

```bash
plasmoidviewer -a package --location=floating --formfactor=planar
plasmoidviewer -a package # floating+planar is the default
```

## Test as a horizontal panel widget

If we set `plasmoidviewer`'s form factor to `horizontal` and its location to `topedge` or `bottomedge`, we can test a widget in a panel.

```bash
plasmoidviewer -a package -l topedge -f horizontal
```

## Testing DPI scaling

Setting the `QT_SCALE_FACTOR=2` environment variable doubles the scale, just for the `plasmoidviewer` window. This is great for testing whether your code supports a HiDPI screen.

At a very high scale, the default `plasmoidviewer` window will probably be too small to show the widget, so set the size and position of the window. The window goes maximized if you set a size larger than your screen has available.

```bash
QT_SCALE_FACTOR=2 plasmoidviewer -a package
QT_SCALE_FACTOR=2 plasmoidviewer -a package -l topedge -f horizontal -x 0 -y 0 -s 1920x1080
```

## Enable logging

If QML's `console.log()` output is hidden, you can show it with an environment variable:

```bash
QT_LOGGING_RULES="qml.debug=true" plasmawindowed org.kde.plasma.kickoff
QT_LOGGING_RULES="qml.debug=true" plasmoidviewer -a org.kde.plasma.kickoff
QT_LOGGING_RULES="qml.debug=true" sonicshell --replace
```

It is much easier to always have it shown for the current user, including in the system log (`journalctl -b0 -f`). To do so, set `[Rules] qml.debug=true` in `~/.config/QtProject/qtlogging.ini`, for example with `kwriteconfig6`:

```bash
kwriteconfig6 --file ~/.config/QtProject/qtlogging.ini --group "Rules" --key "qml.debug" "true"
```

```ini
# ~/.config/QtProject/qtlogging.ini
[Rules]
qml.debug=true
```

`plasmoidviewer` and `sonicshell` log through Sonic Logging, which writes to `~/.local/state/sonic/<program>.log` and also shows the lines in the terminal when you run the program from one. So if you redirect a program's output to a file or a pipe, look in that log instead.

You should now see output when you add `console.log()` statements to your widget. You can place them in any function, like the `Component.onCompleted` signal handler:

```qml
import QtQuick
import org.kde.plasma.plasmoid

PlasmoidItem {
    Component.onCompleted: {
        console.log("Hello World")
    }
}
```

Or in an `onPropertyChanged` signal handler. The following example prints a log message when you click the button:

```qml
import QtQuick
import QtQuick.Layouts
import org.kde.plasma.components as PlasmaComponents
import org.kde.plasma.plasmoid

PlasmoidItem {
    id: widget
    preferredRepresentation: fullRepresentation

    property int num: 1
    onNumChanged: console.log("num", num)

    fullRepresentation: PlasmaComponents.Button {
        Layout.minimumWidth: implicitWidth
        text: i18n("Add 1")
        onClicked: widget.num += 1
    }
}
```
