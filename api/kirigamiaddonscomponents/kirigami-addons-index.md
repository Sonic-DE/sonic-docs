---
title: "Kirigami Addons"
description: "Reusable controls and visual components for Kirigami applications.."
---

# Kirigami Addons

Reusable controls and visual components for Kirigami applications..

Kirigami Addons is an additional set of visual components that work well on mobile and desktop and are guaranteed to be cross-platform.

It uses [Kirigami](../kirigami/org-kde-kirigami-qmlmodule.md) under the hood to create its components and should look native with any [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html) Controls style.

A tutorial for Kirigami Addons can be found over the [KDE Developer Platform](https://develop.kde.org/docs/getting-started/kirigami/addons-introduction).

## Using the Module {#using-the-module}

Using a Qt module's C++ API requires linking against the module library, either directly or through other dependencies. Several build tools have dedicated support for this, including [CMake](https://cmake.org/cmake/help/latest/) and [qmake](https://doc.qt.io/qt-6/resources.html#qmake).

### Building with CMake {#building-with-cmake}

To import each Kirigami Addons QML module individually:

```cpp
ecm_find_qmlmodule(org.kde.kirigamiaddons.formcard REQUIRED)
ecm_find_qmlmodule(org.kde.kirigamiaddons.delegates REQUIRED)
ecm_find_qmlmodule(org.kde.kirigamiaddons.settings REQUIRED)
ecm_find_qmlmodule(org.kde.kirigamiaddons.treeview REQUIRED)
ecm_find_qmlmodule(org.kde.kirigamiaddons.tableview REQUIRED)
ecm_find_qmlmodule(org.kde.kirigamiaddons.components REQUIRED)
ecm_find_qmlmodule(org.kde.kirigamiaddons.labs.components REQUIRED)
ecm_find_qmlmodule(org.kde.kirigamiaddons.sounds REQUIRED)
ecm_find_qmlmodule(org.kde.kirigamiaddons.actions REQUIRED)
ecm_find_qmlmodule(org.kde.kirigamiaddons.actions.labs REQUIRED)
ecm_find_qmlmodule(org.kde.kirigamiaddons.onboarding REQUIRED)
```

To import Kirigami Addons into your project using CMake:

```cpp
find_package(KF6 REQUIRED COMPONENTS KirigamiAddons)
```

## API Reference {#api-reference}

- [Kirigami Addons App C++ Classes](../kirigamiapp/kirigamiapp-module.md)
- [Kirigami Addons FormCard QML Types](../kirigamiaddonsformcard/org-kde-kirigamiaddons-formcard-qmlmodule.md)
- [Kirigami Addons Delegates QML Types](../kirigamiaddonsdelegates/org-kde-kirigamiaddons-delegates-qmlmodule.md)
- [Kirigami Addons Settings QML Types](../kirigamiaddonssettings/org-kde-kirigamiaddons-settings-qmlmodule.md)
- [Kirigami Addons TreeView QML Types](../kirigamiaddonstreeview/org-kde-kirigamiaddons-treeview-qmlmodule.md)
- [Kirigami Addons TableView QML Types](../kirigamiaddonstableview/org-kde-kirigamiaddons-tableview-qmlmodule.md)
- [Kirigami Addons Components QML Types](org-kde-kirigamiaddons-components-qmlmodule.md)
- [Kirigami Addons Components (Labs) QML Types](org-kde-kirigamiaddons-labs-components-qmlmodule.md)
- [Kirigami Addons Sounds QML Types](../kirigamiaddonssounds/org-kde-kirigamiaddons-sounds-qmlmodule.md)
- [Kirigami Addons Actions QML Types](../kirigamiaddonsactions/org-kde-kirigamiaddons-actions-qmlmodule.md)
- [Kirigami Addons Actions (Labs) QML Types](../kirigamiaddonsactions/org-kde-kirigamiaddons-actions-labs-qmlmodule.md)
- [Kirigami Addons Onboarding QML Types](../kirigamiaddonsonboarding/org-kde-kirigamiaddons-onboarding-qmlmodule.md)

## Examples {#examples}

- [Onboarding Tutorial](../kirigamiaddonsonboarding/kirigamiaddonsonboarding-onboardingtutorial-example.md)

## Licenses {#licenses}

Kirigami Addons is free software, licensed primarily under the GNU Lesser General Public License, so that it can be used by both free and proprietary software.

The project follows the [REUSE](https://reuse.software/) specification: every file carries its own `SPDX-License-Identifier`, and the full text of each license in use is available in the `LICENSES` directory of the source repository.
