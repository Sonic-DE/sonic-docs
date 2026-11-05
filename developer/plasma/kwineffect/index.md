---
title: SonicWin effects
description: How to write a QML effect for SonicWin.
source_url: https://develop.kde.org/docs/plasma/kwineffect/
source_authors: [Carl Schwan, Joshua Wug, Vlad Zahorodnii]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "org.kde.kwin registrations in sonic-win/src/scripting/scripting.cpp, the effect package structure, examples/quick-effect; test effects loaded through D-Bus on sonic-win under Xvfb with OpenGL compositing and captured from that display, showing the delegate, Text, WindowThumbnail in a WindowModel grid and the color from main.xml; gesture handlers load without activating. Not exercised: input, the shortcut and screen edge triggers, SceneView.screen.name on screen (off-screen in the test), and the configuration dialog."
---

# SonicWin effects

This page shows how to write a QML effect for SonicWin. Scripted effects written in JavaScript are also possible; the [API page](../kwin/api.md#global-in-scripted-effects) lists what they can use.

## Project structure

```text
package
├── contents
│   └── ui
│       └── main.qml
└── metadata.json
```

The top-level directory holds two things: `metadata.json`, with the name of the effect, the API it uses, the author and so on, and `contents`, with the QML code, configuration files and assets.

```json
{
    "KPackageStructure": "KWin/Effect",
    "KPlugin": {
        "Authors": [
            {
                "Email": "user@example.com",
                "Name": "Name"
            }
        ],
        "Category": "Appearance",
        "Description": "Yo",
        "EnabledByDefault": false,
        "Id": "hello-world",
        "License": "MIT",
        "Name": "Hello World"
    },
    "X-KDE-Ordering": 60,
    "X-Plasma-API": "declarativescript"
}
```

`ui/main.qml` is the entry point, and every effect must have it.

To install the effect and make it visible in the Desktop Effects settings, run:

```bash
kpackagetool6 --type KWin/Effect --install package/
```

SonicWin has an example effect you can copy in [`examples/quick-effect`](https://github.com/Sonic-DE/sonic-win/tree/master/examples/quick-effect). It also has a `CMakeLists.txt`, an alternative way to install the effect, with `cmake --install builddir`.

> **Note:** `org.kde.kwin` also has `PinchGestureHandler` and `SwipeGestureHandler`, which `examples/quick-effect` uses. SonicWin doesn't recognize gestures on X11, so they load but never activate. Give your effect another way to start, such as a shortcut or screen edge.

## Hello world

This effect shows a hello world message on the screen:

```qml
import QtQuick
import org.kde.kwin

SceneEffect {
    id: effect

    delegate: Rectangle {
        color: "blue"

        Text {
            anchors.centerIn: parent
            color: "white"
            text: "Hello world!"
        }
    }

    ScreenEdgeHandler {
        enabled: true
        edge: ScreenEdgeHandler.TopEdge
        onActivated: effect.visible = !effect.visible
    }

    ShortcutHandler {
        name: "Toggle Hello World Effect"
        text: "Toggle Hello World Effect"
        sequence: "Meta+H"
        onActivated: effect.visible = !effect.visible
    }
}
```

`import QtQuick` provides basic components such as `Rectangle`, and `import org.kde.kwin` the ones specific to SonicWin.

`SceneEffect` is a special type that every declarative effect must use. Its `delegate` property sets the content for every screen: here, a blue rectangle with a label in the center.

`ShortcutHandler` registers global shortcuts. `name` is the shortcut's key, used to store it in the configuration, and `text` is a readable description shown in the Shortcuts settings.

`ScreenEdgeHandler` reserves a screen edge. When the pointer hits that edge, the `activated` signal is emitted.

`effect.visible = !effect.visible` toggles the effect. When `visible` is true, the effect is active and on the screen. Set it to true to show the effect.

If you press `Meta+H` or move the pointer to the top edge of the screen, you'll see a blue screen with the message. There are no windows visible any more: it is up to the effect to decide what is displayed.

## Displaying windows

Effects usually need to display windows. This shows the active window:

```qml
    delegate: Rectangle {
        color: "blue"

        WindowThumbnail {
            anchors.centerIn: parent
            client: Workspace.activeWindow
        }
    }
```

`WindowThumbnail` comes from the `org.kde.kwin` module. Its `client` property sets which window it displays.

## Input

Input involves no special APIs: `TapHandler`, `MouseArea`, `Keys` and the rest of Qt Quick should just work. For example, this arranges windows in a grid and closes a window when it is middle-clicked:

```qml
    delegate: Rectangle {
        color: "pink"

        GridView {
            id: grid
            anchors.fill: parent
            cellWidth: 300
            cellHeight: 300

            model: WindowModel {}
            delegate: WindowThumbnail {
                required property var model
                client: model.window
                width: grid.cellWidth
                height: grid.cellHeight

                TapHandler {
                    acceptedButtons: Qt.MiddleButton
                    onTapped: client.closeWindow()
                }
            }
        }
    }
```

`WindowModel`, from the `org.kde.kwin` module, lists all windows. It can be passed to views, `Repeater` and so on.

## Delegates are per screen

Delegates are instantiated once per screen:

```qml
    delegate: Rectangle {
        color: "yellow"

        Text {
            anchors.centerIn: parent
            color: "black"
            text: SceneView.screen.name
        }
    }
```

On a setup with several outputs, each is filled with yellow with its name in the center. If you need to know which output a delegate is on, use the `SceneView.screen` attached property.

## Configuration

Say we want the background color of our effect to be configurable. First, add `contents/config/main.xml`:

```text
package/
├── contents
│   ├── config
│   │   └── main.xml
│   └── ui
│       └── main.qml
└── metadata.json
```

It lists all options:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<kcfg xmlns="http://www.kde.org/standards/kcfg/1.0"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://www.kde.org/standards/kcfg/1.0
                          http://www.kde.org/standards/kcfg/1.0/kcfg.xsd" >
    <kcfgfile name=""/>
    <group name="">
        <entry name="BackgroundColor" type="Color">
            <default>#ff00ff</default>
        </entry>
    </group>
</kcfg>
```

Here there is one option, `BackgroundColor`, of type `Color`. [Using KConfig XT](../../configuration/kconfig-xt.md) describes the other entry types.

Next, use the option. `effect.configuration` is a map of all the options in `main.xml`.

```qml
    delegate: Rectangle {
        color: effect.configuration.BackgroundColor

        Text {
            anchors.centerIn: parent
            color: "white"
            text: "Hello world!"
        }
    }
```

To get a configure button next to the effect in the Desktop Effects settings, the effect also needs `contents/ui/config.ui`:

```text
package/
├── contents
│   ├── config
│   │   └── main.xml
│   └── ui
│       ├── config.ui
│       └── main.qml
└── metadata.json
```

It is a regular Qt Designer file. The only special thing is that controls representing options are named `kcfg_` followed by the option name, such as `kcfg_BackgroundColor`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<ui version="4.0">
 <class>QuickEffectConfig</class>
 <widget class="QWidget" name="QuickEffectConfig">
  <property name="geometry">
   <rect>
    <x>0</x>
    <y>0</y>
    <width>455</width>
    <height>177</height>
   </rect>
  </property>
  <layout class="QFormLayout" name="formLayout">
   <item row="0" column="0">
    <widget class="QLabel" name="label">
     <property name="text">
      <string>Background color:</string>
     </property>
    </widget>
   </item>
   <item row="0" column="1">
    <widget class="KColorButton" name="kcfg_BackgroundColor">
     <property name="flat">
      <bool>false</bool>
     </property>
    </widget>
   </item>
  </layout>
 </widget>
 <customwidgets>
  <customwidget>
   <class>KColorButton</class>
   <extends>QPushButton</extends>
   <header>kcolorbutton.h</header>
  </customwidget>
 </customwidgets>
 <resources/>
 <connections/>
</ui>
```

Finally, add this line to `metadata.json`:

```json
"X-KDE-ConfigModule": "kcm_kwin4_genericscripted"
```

The effect is then shown as configurable, and the color can be changed in System Settings.

## Sharing your effect

The preferred way to distribute effects is the [KDE Store](https://store.kde.org), which SonicDE uses for downloads. JavaScript and QML effects both go in the "KWin Effects" category.

## Documentation and other resources

- The [SonicWin scripting API](../kwin/api.md)
- The [examples in the sonic-win repository](https://github.com/Sonic-DE/sonic-win/tree/master/examples)

## Window heap

To arrange windows the way the overview effect does, you can use the `WindowHeap` component from the `org.kde.kwin_x11.private.effects` module. It is private and has no stable API yet, so use it at your own risk, or copy the relevant code. Its source is in [`src/plugins/private`](https://github.com/Sonic-DE/sonic-win/tree/master/src/plugins/private).

## More examples

The desktop cube effect in `sonic-workspace-addons` uses the same QML effect API with Qt Quick 3D. Its source is in [`kwin/effects/cube`](https://github.com/Sonic-DE/sonic-workspace-addons/tree/master/kwin/effects/cube).
