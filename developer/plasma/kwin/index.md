---
title: SonicWin scripting tutorial
description: Learn how to manipulate windows with SonicWin scripts.
source_url: https://develop.kde.org/docs/plasma/kwin/
source_authors: [Alexander Lohnau, Carl Schwan, Chris Holland, Denis Štogl, Emil Sonnenschein, Hynek Schlindenbuch, Ian Canino, Jade Lovelace, Kunda Ki, Marius Bosler, Marius P, Mikhail Zolotukhin, Sebastian Kügler, Shalok Shalom, Thiago Sueto, Vlad Zahorodnii, Zren (Chris Holland)]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "src/scripting and kcms in sonic-win; the tutorial script packaged, installed with kpackagetool6, enabled through kwinrc and exercised on sonic-win on a private Xvfb and D-Bus, reporting through callDBus. The output of print() was not seen in that setup, so the journal command is unconfirmed; the configuration dialog was not opened."
---

# SonicWin scripting tutorial

SonicWin, the SonicDE window manager, can be controlled with scripts. Many of its interfaces keep the name `KWin`, which it inherited, so that existing scripts keep working.

## Quick start: the console

The easiest way to test scripts is the interactive console. Open it by typing `wm console` in KRunner, or from the terminal:

```bash
plasma-interactiveconsole --kwin
```

The console sends a script to the window manager, which loads and runs it. Output isn't shown in the console window; see [Output](#output).

Scripts run from the console last only as long as the window manager is running. In a new session, the script has to be sent again.

## Packaging scripts

To have SonicWin load a script every time a session starts, package it. Scripts use the [KPackage](/docs/api/kpackage/kpackage-index) format.

### Package structure

```text
myscript
├── contents
│   └── code
│       └── main.js
└── metadata.json
```

`contents/code/main.js`, or `contents/ui/main.qml` if you write your script in QML, holds the main code. The top-level folder may contain any number of additional files, such as a readme.

### Metadata

`metadata.json` provides general information about the script. `Id` is the name of the folder the script is installed to. `X-Plasma-API` is `javascript`, or `declarativescript` for QML.

```json
{
    "KPlugin": {
        "Name": "My Script",
        "Description": "Description of the script",
        "Icon": "preferences-system-windows",
        "Authors": [
            {
                "Email": "username@example.org",
                "Name": "Firstname Lastname"
            }
        ],
        "Id": "myscript",
        "Version": "1.0",
        "License": "GPLv3",
        "Website": "https://example.org/myscript"
    },
    "X-Plasma-API": "javascript",
    "X-Plasma-MainScript": "code/main.js",
    "KPackageStructure": "KWin/Script"
}
```

### Installation

Installed scripts are listed in System Settings, on the page for SonicWin scripts. A package can be installed from there, or with `kpackagetool6`:

```bash
kpackagetool6 --type=KWin/Script -i ~/Code/myscript/
```

Then enable it, on the settings page or with `kwriteconfig6`:

```bash
kwriteconfig6 --file kwinrc --group Plugins --key myscriptEnabled true
qdbus org.kde.KWin /KWin reconfigure
```

A script can't provide a shell script to perform additional steps when it is installed.

## Where can I find example scripts?

SonicWin ships a few scripts and scripted effects, in [`src/plugins`](https://github.com/Sonic-DE/sonic-win/tree/master/src/plugins). `minimizeall`, `synchronizeskipswitcher` and `desktopchangeosd` are scripts, and each has a `package` folder. They are installed in `/usr/share/kwin-x11/scripts/`.

Scripts you install go in `~/.local/share/kwin/scripts/`. List them with:

```bash
kpackagetool6 --type=KWin/Script --list
```

## Scripting basics

You need some idea of JavaScript to follow this tutorial. The [desktop scripting pages](../scripting/index.md) are a quick introduction to scripting SonicDE.

Scripts are written in JavaScript (`javascript`) or [QML](https://doc.qt.io/qt-6/qtqml-index.html) (`declarativescript`). You should know the basic concepts of [signals and properties](https://doc.qt.io/qt-6/signalsandslots.html).

The [API documentation](api.md) lists the available objects and functions.

### Output

`print(...)` prints the given arguments. `console.log()` does the same, and is preferred in QML scripts.

The output of scripts goes to the journal:

```bash
journalctl -f QT_CATEGORY=js QT_CATEGORY=kwin_scripting
```

Debug messages from the scripting system need `QT_LOGGING_RULES="kwin_*.debug=true"` in the window manager's environment.

### Workspace and options

Scripts can access two global properties. `workspace` is the interface to the core of the window manager, and `options` gives access to its current configuration.

### Windows

Most methods of `workspace` that work on windows return or take a `Window`. This prints the caption of every window the window manager manages:

```js
for (const window of workspace.windowList()) {
    print(window.caption);
}
```

This prints the ID of each new window:

```js
workspace.windowAdded.connect((window) => {
    print(window.internalId);
});
```

To see what is passed to the functions you connect, check the [API documentation](api.md).

## Configuration

Scripts can have a user configuration. To enable this, add this line to `metadata.json`:

```json
"X-KDE-ConfigModule": "kcm_kwin4_genericscripted"
```

### Declaration

Settings are defined in the file `contents/config/main.xml`. The [widget configuration page](../widget/configuration.md) has an example.

### Graphical interface

A configuration dialog is provided by the file `contents/ui/config.ui`. Such a package has this structure:

```text
myscript
├── contents
│   ├── code
│   │   └── main.js
│   ├── config
│   │   └── main.xml
│   └── ui
│       └── config.ui
└── metadata.json
```

`.ui` files are most easily edited with Qt Designer.

The object name of each element that provides a setting must be `kcfg_keyName`, where `keyName` is the `name` attribute of the entry in the XML file.

The dialog opens from the configuration button on the scripts settings page.

### Reading configuration values

Values are stored in `~/.config/kwinrc`, in the group `[Script-myscript]`. Read them with this global function, available in JavaScript and QML:

- `readConfig(key, defaultValue)`: reads a value. `key` is the `name` attribute of the entry in the XML file, and `defaultValue` is optional, returned if the key doesn't exist.

## Your first useful script

This script is based on a suggestion by Eike Hein: remove keep-above from a window while it is maximized, and put it back when the window is restored. It covers most of the important parts of scripting while doing something useful.

### The basic outline

For every window set to keep above, the window shouldn't be above all others when it is maximized. So:

1. Create an array of windows whose keep-above state has been removed.
2. When a window is maximized, if it is keep above, remove that and remember the window.
3. When a window is restored, if it is in the array, set keep above again.

### The basic framework

First, create the array:

```js
const keepAboveMaximized = [];
```

Next we need to know whenever a window gets maximized. Each window has a signal for this, `maximizedChanged`, so we connect to it on all current windows and on each new one. The window's `maximizeMode` property is `0` when restored, `1` when maximized vertically, `2` horizontally and `3` fully.

```js
function watchWindow(window) {
    window.maximizedChanged.connect(() => {
        if (window.maximizeMode === 3) {
            print(window.caption + " is fully maximized");
        } else {
            print(window.caption + " is not maximized");
        }
    });
}

workspace.windowList().forEach(watchWindow);
workspace.windowAdded.connect(watchWindow);
```

Try it in the console and play with your windows. Right- and middle-clicking the maximize button changes the horizontal and vertical state.

### Checking keep above

Now we check whether the maximized window is keep above. If so, we remove that and remember the window, so that it can be reset on restore. For readability the code moves into its own function:

```js
function manageKeepAbove(window) {
    if (window.maximizeMode === 3) {
        if (window.keepAbove) {
            keepAboveMaximized.push(window);
            window.keepAbove = false;
        }
    }
}
```

`keepAbove` is a boolean, and removing it is a simple assignment.

### Restoring it all

Finally, when the window isn't fully maximized, we check whether it is in the array, and if so set keep above again. This is the entire script:

```js
const keepAboveMaximized = [];

function manageKeepAbove(window) {
    if (window.maximizeMode === 3) {
        // maximized
        if (window.keepAbove) {
            keepAboveMaximized.push(window);
            window.keepAbove = false;
        }
    } else {
        // no longer maximized
        const found = keepAboveMaximized.indexOf(window);
        if (found !== -1) {
            window.keepAbove = true;
            keepAboveMaximized.splice(found, 1);
        }
    }
}

function watchWindow(window) {
    window.maximizedChanged.connect(() => manageKeepAbove(window));
}

workspace.windowList().forEach(watchWindow);
workspace.windowAdded.connect(watchWindow);
```

### What next?

You could restrict the script to some window classes, such as video players. It's up to you.

## Publishing

If you've created something nice, consider sharing it! Make a zip file of the package folder and upload it to the [KDE Store](https://store.kde.org), which SonicDE uses for downloads, under the category for KWin scripts. People can then install it with "Get New Scripts…" in System Settings.
