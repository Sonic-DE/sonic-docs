---
title: Settings module (KCM) development
description: Create a settings module for SonicDE's System Settings.
source_url: https://develop.kde.org/docs/features/configuration/kcm/
source_authors: [Akseli Lahtinen, Alexander Lohnau, Andrey Butirsky, Carl Schwan, Claudio Cambra, Justin Zobel, Mikhail Zolotukhin, Nicolas Fella, Phu Nguyen, S Page, Thiago Sueto, Tobias Fella]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-frameworks-settings-utils (KCMUtils, KF6KCMUtilsMacros.cmake), sonic-system-settings (systemsettings, categories), sonic-tv-interface (settingsapp), sonic-accounts-integration; the example below was built against SonicDE's frameworks (KF6 6.31.0) and kcmshell6 --list shows it
---

# Settings module (KCM) development

## Introduction

Settings in SonicDE are provided by configuration modules (KCMs). Several applications load them: System Settings (`systemsettings`) on the desktop, the TV interface's settings app (`plasma-bigscreen-settings`), and `kcmshell6`, which shows one module in a window of its own. The modules' sources are spread over several repositories, such as `sonic-workspace` and `sonic-desktop-interface` (each in their `kcms` folder).

`kcmshell6 --list` lists the available modules. To open one module on its own, pass its name to one of these applications, for example `systemsettings kcm_kaccounts`, `plasma-bigscreen-settings -m kcm_kaccounts` or `kcmshell6 kcm_kaccounts`.

## A basic KCM

A KCM consists of a QML user interface and a C++ plugin with the logic. Some older KCMs use QtWidgets, but don't use that for new ones: the TV interface's settings app only loads QML modules. New modules are written in QML with [Kirigami](/docs/api/kirigami/kirigami-index).

The example is a time settings module. Its structure:

```text
...
├── CMakeLists.txt
└── src
    ├── CMakeLists.txt
    ├── timesettings.cpp
    ├── timesettings.h
    ├── kcm_time.json
    └── ui
        └── main.qml
```

## CMakeLists.txt

There are two CMake files: one in the root folder and one in `src`.

### ./CMakeLists.txt

```cmake
# SPDX-FileCopyrightText: Year Author <email@company.com>
#
# SPDX-License-Identifier: BSD-2-Clause

cmake_minimum_required(VERSION 3.16)

set(QT_MIN_VERSION "6.5.0")
set(KF6_MIN_VERSION "6.0.0")
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)

project(kcm_time)

find_package(ECM ${KF6_MIN_VERSION} REQUIRED NO_MODULE)

set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/cmake )

include(KDEInstallDirs)
include(KDECompilerSettings NO_POLICY_SCOPE)
include(KDECMakeSettings)

find_package(Qt6 ${QT_MIN_VERSION} CONFIG REQUIRED Core Quick Gui Qml)

find_package(KF6 ${KF6_MIN_VERSION} REQUIRED COMPONENTS
    Config
    CoreAddons
    KCMUtils
    I18n
)

add_subdirectory(src)
```

The root `CMakeLists.txt` declares the project and prepares the KCM for building. You only need it when you build the KCM on its own; usually a KCM is part of the project it configures, and that project must then find the libraries the KCM needs. (SonicDE itself requires Qt 6.11; the versions above are the minimum this example needs.)

### ./src/CMakeLists.txt

```cmake
# SPDX-FileCopyrightText: Year Author <email@company.com>
#
# SPDX-License-Identifier: BSD-2-Clause

kcmutils_add_qml_kcm(kcm_time)
target_sources(kcm_time PRIVATE
   timesettings.cpp
   timesettings.h
)
target_link_libraries(kcm_time PRIVATE
    Qt::Quick
    KF6::CoreAddons
    KF6::KCMUtils
    KF6::I18n
)
```

Of the packages used, [KCMUtils](/docs/api/kcmutils/kcmutils-index) (from `sonic-frameworks-settings-utils`) provides the classes for writing modules, and `Config` the [KConfig](/docs/api/kconfigcore/kconfig-index) classes. The others are used throughout this documentation.

There is no `main.cpp`: the C++ code is a plugin for the QML user interface, so you only write the class with the module's logic. `kcmutils_add_qml_kcm()` creates the plugin, bundles the `ui` folder into it, and installs it where System Settings finds it (`plasma/kcms/systemsettings` in the plugin directory, unless you pass `INSTALL_NAMESPACE`).

## timesettings.h

```cpp
/**
 * SPDX-FileCopyrightText: Year Author <author@domain.com>
 * SPDX-License-Identifier: GPL-2.0-or-later
 */

#pragma once

#include <KQuickConfigModule>

class TimeSettings : public KQuickConfigModule
{
    Q_OBJECT
    public:
        TimeSettings(QObject *parent, const KPluginMetaData &data);
};
```

This declares the module's class. [KQuickConfigModule](/docs/api/kcmutilsquick/kquickconfigmodule) is the base class of every QML module. Its API reference has the details; [Using KConfig XT](kconfig-xt.md) shows how to connect a module to its settings with `KQuickManagedConfigModule`.

## timesettings.cpp

```cpp
/**
 * SPDX-FileCopyrightText: Year Author <author@domain.com>
 * SPDX-License-Identifier: GPL-2.0-or-later
 */

#include "timesettings.h"

#include <KPluginFactory>

K_PLUGIN_CLASS_WITH_JSON(TimeSettings, "kcm_time.json")

TimeSettings::TimeSettings(QObject *parent, const KPluginMetaData &data)
    : KQuickConfigModule(parent, data)
{
    setButtons(Help | Apply | Default);
}

#include "timesettings.moc"
```

This is where the code that actually changes things goes. Functions you expose here can be called from the QML user interface. The plugin is installed with the other modules, and System Settings loads it when the module is opened.

The constructor connects the class to the module's metadata (`K_PLUGIN_CLASS_WITH_JSON`) and chooses the buttons the window shows.

## kcm_time.json

```json
{
    "KPlugin": {
        "Description": "Configure Time",
        "FormFactors": [
            "desktop",
            "handset",
            "tablet",
            "mediacenter"
        ],
        "Icon": "preferences-system-time",
        "Name": "Time"
    },
    "X-KDE-Keywords": "Time,Date,Clock",
    "X-KDE-System-Settings-Parent-Category": "personalization"
}
```

This file is the module's metadata (shown here without its translations):

- `Name` is the module's name in the settings application.
- `Description` is a short, one-sentence description.
- `FormFactors` lists the kinds of devices the module is shown on; the TV interface's settings app, for example, only shows modules for the current platform.
- `X-KDE-System-Settings-Parent-Category` is the System Settings category the module appears in (the categories are defined in `sonic-system-settings/categories`).
- `X-KDE-Keywords` are keywords for searching for the module.

## ui/main.qml

```qml
/**
 * SPDX-FileCopyrightText: Year Author <author@domain.com>
 * SPDX-License-Identifier: GPL-2.0-or-later
 */


import QtQuick
import QtQuick.Controls as Controls

import org.kde.kirigami as Kirigami
import org.kde.kcmutils as KCMUtils

KCMUtils.SimpleKCM {
    Controls.Label {
        text: i18n("Time settings example")
    }
}
```

This is a very simple module page: a [SimpleKCM](/docs/api/kcmutilsqml/qml-org-kde-kcmutils-simplekcm) as the root, with a label in it.

Other layouts use other root types:

- [ScrollViewKCM](/docs/api/kcmutilsqml/qml-org-kde-kcmutils-scrollviewkcm) for content that scrolls vertically, such as a ListView.
- [GridViewKCM](/docs/api/kcmutilsqml/qml-org-kde-kcmutils-gridviewkcm) for selectable items in a grid.
- [SimpleKCM](/docs/api/kcmutilsqml/qml-org-kde-kcmutils-simplekcm) for everything else.

> **Note:** A module can have several pages, opened and closed as needed. To push another page onto the page stack:
>
> ```js
> kcm.push("AnotherPage.qml")
> ```
>
> `AnotherPage.qml` must have one of the root types above. To remove the last page from the stack:
>
> ```js
> kcm.pop()
> ```

## Run it

Now build and install the module. This example installs it to `~/sonic/usr`, a location of its own, so it doesn't interfere with your system:

```bash
# Configure the project in a build/ folder outside the sources
cmake -B build/ -DCMAKE_INSTALL_PREFIX=~/sonic/usr
# Compile it in build/
cmake --build build/
# Install the result into ~/sonic/usr
cmake --install build/
```

To use a module installed there, load the environment the build generated (`build/prefix.sh`, which adds `~/sonic/usr` to the plugin and QML paths), then run it:

```bash
source build/prefix.sh
kcmshell6 kcm_time
```
