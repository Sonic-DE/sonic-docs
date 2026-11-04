---
title: C++ API
description: Compiling desktop widgets that use C++ with CMake.
source_url: https://develop.kde.org/docs/plasma/widget/c-api/
source_authors: [Alexander Hau, Alexander Lohnau, Carl Schwan, Chris Holland, Christoph Dreier, Claudius Ellsel, David Edmundson, Florian Ruechel, Fushan Wen, Johannes Zarl-Zierl, Joshua Goins, Kunda Ki, Marco Martin, Mariusz Libera, Michael Pyne, Mikhail Zolotukhin, Nate Graham, Nicolas Fella, Parth Dhiman, Paul Brown, Plata Hill, Raresh Rus, Rony Bou Moujahed, Thiago Sueto, Tino Lorenz, Tobias Fella, Yaron Shahrabani, Zren (Chris Holland), ivan tkachenko, yaniss khima]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "PlasmaMacros.cmake, templates/cpp-plasmoid6 and PluginLoader in sonic-interface-libraries; mediaframe, grouping, kicker and systemtray applets; both examples built against the built libraries and loaded in plasmawindowed under Xvfb"
---

# C++ API

Most widgets need only QML. If yours needs models backed by C++ libraries, file I/O or other things QML can't do, you can compile it. Most of SonicDE's own widgets are built this way.

A compiled widget is a plugin with its QML embedded, installed to `plasma/applets` in Qt's plugin directory.

> **Warning:** A compiled widget can't be installed from a package with `kpackagetool6`, so it can't be offered as a plain download on the store. Distribute it through your distribution's packaging instead.

## Compiling with CMake

The [`cpp-plasmoid6` template](https://github.com/Sonic-DE/sonic-interface-libraries/tree/master/templates/cpp-plasmoid6) is a complete starting point. The steps below build the same kind of widget.

```text
plasma-widgetname/
├── CMakeLists.txt
├── metadata.json
├── qml/
│   └── main.qml
├── widgetitem.cpp
└── widgetitem.h
```

The CMake function `plasma_add_applet()` creates the plugin and embeds the QML. Its first argument is the widget's ID, which is also the name of the plugin file.

`GENERATE_APPLET_CLASS` generates the plugin class, which is all you need unless you want [your own applet class](#your-own-applet-class). The macro turns the ID into the QML module `plasma.applet.<id>`.

`CMakeLists.txt`:

```cmake
cmake_minimum_required(VERSION 3.16)

project(plasma-widgetname)

find_package(ECM 6.0.0 REQUIRED NO_MODULE)
set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH})

include(KDEInstallDirs)
include(KDECMakeSettings)
include(KDECompilerSettings NO_POLICY_SCOPE)

find_package(Qt6 REQUIRED COMPONENTS Core Qml Quick)
find_package(KF6 REQUIRED COMPONENTS I18n Config)
find_package(Plasma REQUIRED)

add_definitions(-DTRANSLATION_DOMAIN=\"plasma_applet_org.example.widgetname\")

plasma_add_applet(org.example.widgetname
    QML_SOURCES
        qml/main.qml
    CPP_SOURCES
        widgetitem.cpp
    GENERATE_APPLET_CLASS
)

target_link_libraries(org.example.widgetname PRIVATE
    Qt::Core
    Qt::Qml
    Qt::Quick
    KF6::I18n
)
```

`KF6 Config` is listed because `Plasma::Plasma` links to it without finding it.

`metadata.json` is embedded in the plugin. Leave out `KPlugin.Id`: the ID comes from the plugin's file name, and the loader warns if the key is present.

```json
{
    "KPlugin": {
        "Name": "widgetname",
        "Version": "1.0"
    },
    "X-Plasma-API-Minimum-Version": "6.0",
    "KPackageStructure": "Plasma/Applet"
}
```

## Adding a QML type

Let's add a `WidgetItem` type with a `number` property, and a `randomize()` function that sets it to a random number.

`qml/main.qml` imports the widget's own module:

```qml
import QtQuick
import org.kde.plasma.components as PlasmaComponents
import org.kde.plasma.plasmoid

import plasma.applet.org.example.widgetname

PlasmoidItem {
    id: widget

    WidgetItem {
        id: widgetItem
        number: 123
    }

    fullRepresentation: PlasmaComponents.Button {
        text: widgetItem.number
        onClicked: widgetItem.randomize()
    }
}
```

`QML_ELEMENT` registers the class in that module, so there is no plugin class or `qmldir` to write. The `number` property isn't read-only, so it has a `WRITE` setter and a `NOTIFY` signal to tell the interface when it changes. `randomize()` needs [`Q_INVOKABLE`](https://doc.qt.io/qt-6/qtqml-cppintegration-exposecppattributes.html), or QML couldn't call it.

`widgetitem.h`:

```cpp
#pragma once

#include <QObject>
#include <QtQml/qqmlregistration.h>

class WidgetItem : public QObject
{
    Q_OBJECT
    QML_ELEMENT

    Q_PROPERTY(int number READ number WRITE setNumber NOTIFY numberChanged)

public:
    explicit WidgetItem(QObject *parent = nullptr);

    int number() const;
    void setNumber(int number);

    Q_INVOKABLE void randomize();

Q_SIGNALS:
    void numberChanged();

private:
    int m_number = 0;
};
```

The setter doesn't emit the signal unless the value actually changes. [`qDebug()`](https://doc.qt.io/qt-6/qdebug.html#basic-use) logs to the terminal, which helps during development.

`widgetitem.cpp`:

```cpp
#include "widgetitem.h"

#include <QDebug>
#include <QRandomGenerator>

WidgetItem::WidgetItem(QObject *parent)
    : QObject(parent)
{
}

int WidgetItem::number() const
{
    return m_number;
}

void WidgetItem::setNumber(int number)
{
    if (number != m_number) {
        m_number = number;
        qDebug() << "setNumber" << m_number;
        Q_EMIT numberChanged();
    }
}

void WidgetItem::randomize()
{
    setNumber(QRandomGenerator::global()->bounded(10001));
}
```

## Building and testing

The plugin has to be somewhere Qt looks for plugins, so install it to the same prefix as SonicDE. Then run it as described on the [testing page](testing.md):

```bash
cmake -B build -DCMAKE_INSTALL_PREFIX=/usr
cmake --build build
sudo cmake --install build
plasmawindowed org.example.widgetname
```

> **Warning:** Don't reuse the ID of a widget you installed as a package with `kpackagetool6`. When a package and a plugin have the same ID, the loader combines them, and the package in your home directory supplies the widget's files.

## Your own applet class

To give QML access to C++ on the widget object itself, subclass `Plasma::Applet`. Properties and invokable functions of the subclass are available through the `Plasmoid` attached property. This is how the system tray hands its model to QML, as `Plasmoid.systemTrayModel`.

Remove `GENERATE_APPLET_CLASS` from `plasma_add_applet()`, add the new file to `CPP_SOURCES`, and link to `Plasma::Plasma`.

`widgetapplet.h`:

```cpp
#pragma once

#include <Plasma/Applet>

class WidgetApplet : public Plasma::Applet
{
    Q_OBJECT
    Q_PROPERTY(QString greeting READ greeting CONSTANT)

public:
    WidgetApplet(QObject *parent, const KPluginMetaData &data, const QVariantList &args);

    QString greeting() const;
};
```

`widgetapplet.cpp`:

```cpp
#include "widgetapplet.h"

#include <KLocalizedString>
#include <KPluginFactory>

WidgetApplet::WidgetApplet(QObject *parent, const KPluginMetaData &data, const QVariantList &args)
    : Plasma::Applet(parent, data, args)
{
}

QString WidgetApplet::greeting() const
{
    return i18n("Hello from C++");
}

K_PLUGIN_CLASS_WITH_JSON(WidgetApplet, "metadata.json")

#include "widgetapplet.moc"
```

QML then reads `Plasmoid.greeting`.

For a real example, see [`systemtray.h`](https://github.com/Sonic-DE/sonic-workspace/blob/master/applets/systemtray/systemtray.h) and [`systemtray.cpp`](https://github.com/Sonic-DE/sonic-workspace/blob/master/applets/systemtray/systemtray.cpp).

## Examples

SonicDE's widgets are good references.

- [Media Frame](https://github.com/Sonic-DE/sonic-workspace-addons/tree/master/applets/mediaframe) is a fairly simple one: one C++ class, imported as `plasma.applet.org.kde.plasma.mediaframe`.
- The [Application Menu](https://github.com/Sonic-DE/sonic-desktop-interface/tree/master/applets/kicker) and [Application Launcher](https://github.com/Sonic-DE/sonic-desktop-interface/tree/master/applets/kickoff) share a separate QML module from [`sonic-workspace/applets/kicker`](https://github.com/Sonic-DE/sonic-workspace/tree/master/applets/kicker), built with `ecm_add_qml_module()`.

```qml
import org.kde.plasma.private.kicker as Kicker
```

> **Note:** A `.private` module can be imported by any widget, but its API can change with any update. Using someone else's private module may break your widget.

## Containments

A containment is a widget that holds other widgets. Use `GENERATE_CONTAINMENT_CLASS`, or subclass `Plasma::Containment`, to write one.

- The [Grouping widget](https://github.com/Sonic-DE/sonic-workspace-addons/tree/master/applets/grouping) shows one child widget at a time, using tabs.
- The [system tray](https://github.com/Sonic-DE/sonic-workspace/tree/master/applets/systemtray) can show several compact representations at a time, but only one full representation in its popup.
- The panel ([`containments/panel`](https://github.com/Sonic-DE/sonic-desktop-interface/tree/master/containments/panel) and [`desktoppackage/contents/views/Panel.qml`](https://github.com/Sonic-DE/sonic-desktop-interface/blob/master/desktoppackage/contents/views/Panel.qml)) can show compact and full representations next to each other, and is the most complicated of the three to read.

## Translating C++ strings

To translate messages in your C++ code, use `KF6::I18n` and define the translation domain in `CMakeLists.txt`, as the example above does. The [translations page](translations-i18n.md) explains how the domain is used.

```cmake
find_package(KF6 REQUIRED COMPONENTS I18n Config)

add_definitions(-DTRANSLATION_DOMAIN=\"plasma_applet_org.example.widgetname\")

target_link_libraries(org.example.widgetname PRIVATE
    KF6::I18n
)
```
