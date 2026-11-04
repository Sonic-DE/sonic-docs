---
title: Desktop widget tutorial
description: Learn how to create a SonicDE desktop widget.
source_url: https://develop.kde.org/docs/plasma/widget/
source_authors: [Alexander Hau, Alexander Lohnau, Carl Schwan, Chris Holland, Christoph Dreier, Claudius Ellsel, David Edmundson, Florian Ruechel, Fushan Wen, Johannes Zarl-Zierl, Joshua Goins, Kunda Ki, Marco Martin, Mariusz Libera, Michael Pyne, Mikhail Zolotukhin, Nate Graham, Nicolas Fella, Parth Dhiman, Paul Brown, Plata Hill, Raresh Rus, Rony Bou Moujahed, Thiago Sueto, Tino Lorenz, Tobias Fella, Yaron Shahrabani, Zren (Chris Holland), ivan tkachenko, yaniss khima]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "the widgets installed by the SonicDE build (share/plasma/plasmoids and lib64/plugins/plasma/applets), sonic-desktop-interface and sonic-workspace-addons applets"
---

# Desktop widget tutorial

- [Setup](setup.md): create a new widget from scratch.
- [Testing](testing.md): quickly test a widget.

## Default widgets

### Learn by example

You can learn by example by reading SonicDE's default widgets. Most of them are compiled into plugins, in `plasma/applets/` in the Qt plugin directory, so read their source code: [sonic-desktop-interface](https://github.com/Sonic-DE/sonic-desktop-interface/tree/master/applets) and [sonic-workspace-addons](https://github.com/Sonic-DE/sonic-workspace-addons/tree/master/applets) have most of them.

A few widgets are plain packages in `/usr/share/plasma/plasmoids/`, such as `org.kde.plasma.systemmonitor`. Widgets you download are installed the same way, in `~/.local/share/plasma/plasmoids/`.

To fork a widget that is a plain package, copy its folder to `~/.local/share/plasma/plasmoids/` and rename it. Then change the `Id` in its `metadata.json` file to match the new folder name, change the `Name` so you can tell it apart from the widget you forked, and delete the translated lines such as `Name[fr]`.

Finally, run `plasmawindowed` with the new `Id` to quickly test the fork.

```bash
mkdir -p ~/.local/share/plasma/plasmoids
cp -r /usr/share/plasma/plasmoids/org.kde.plasma.systemmonitor/ ~/.local/share/plasma/plasmoids/com.example.mymonitor
cd ~/.local/share/plasma/plasmoids/com.example.mymonitor
sed -i 's/org.kde.plasma.systemmonitor/com.example.mymonitor/' ./metadata.json
sed -i '/^\s*"Name\[/ d' ./metadata.json
sed -i '/^\s*"Description\[/ d' ./metadata.json
plasmawindowed com.example.mymonitor
```

Fix any trailing comma errors these commands leave in `metadata.json`: there must be no trailing comma after the last entry of an object.
