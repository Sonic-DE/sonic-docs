---
title: Introduction to Kirigami Addons
description: Get acquainted with Kirigami Addons components.
source_url: https://develop.kde.org/docs/getting-started/kirigami/addons-introduction/
source_authors: [Erwin Kaats, Melissa Autumn, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-quick-ui-addons (FormCard, examples/FormCardTutorial, README), sonic-frameworks-cmake-modules; the project built standalone against SonicDE's frameworks and run"
---

# Introduction to Kirigami Addons

Kirigami Addons is an additional set of visual components that work well on mobile and desktop and are meant to be cross-platform. It uses Kirigami under the hood to create its components. SonicDE ships it as `sonic-frameworks-quick-ui-addons`.

Here you set up a new Kirigami Addons project and meet a few useful components.

These components use the localization facilities of KDE Frameworks, so before using them we set up a small project that makes the `i18n()` functions available to QML with [KLocalization::setupLocalizedContext()](/docs/api/ki18nqml/klocalization#setupLocalizedContext).

## Setting up your project

The initial project structure looks like this:

```bash
addonsexample/
├── CMakeLists.txt
├── main.cpp
└── Main.qml
```

> **Tip:** You can quickly create this file structure with:
>
> ```bash
> mkdir addonsexample
> touch addonsexample/{CMakeLists.txt,main.cpp,Main.qml}
> ```

We start with a very standard `CMakeLists.txt`:

```cmake
cmake_minimum_required(VERSION 3.20)

project(FormCardTutorial)

find_package(ECM 6.0.0 REQUIRED NO_MODULE)
set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH})

include(KDEInstallDirs)
include(KDECompilerSettings NO_POLICY_SCOPE)
include(KDECMakeSettings)
include(ECMQmlModule)

find_package(Qt6 REQUIRED COMPONENTS
    Widgets        # For QApplication
    Quick          # For QML
    QuickControls2 # For QQuickStyle
)
find_package(KF6 REQUIRED COMPONENTS
    CoreAddons # For KAboutData
    I18n       # For KLocalization
)

add_executable(addonsexample)

target_sources(addonsexample PRIVATE main.cpp)

ecm_add_qml_module(addonsexample
    URI org.kde.addonsexample
)

ecm_target_qml_sources(addonsexample SOURCES
    Main.qml
)

target_link_libraries(addonsexample PRIVATE
    Qt::Widgets
    Qt::Quick
    Qt::QuickControls2
    KF6::CoreAddons
    KF6::I18n
    KF6::I18nQml
)

install(TARGETS addonsexample DESTINATION ${KDE_INSTALL_BINDIR})
```

The version in `find_package(ECM 6.0.0 ...)` matters: without it, ECM's QML module commands fall back to their Qt 5 code path in a project like this one, which looks for Qt only afterwards, and configuring fails.

The interesting part is `main.cpp`:

```cpp
#include <QtQml>
#include <QApplication>
#include <QQmlApplicationEngine>
#include <QIcon>
#include <QQuickStyle>
#include <KAboutData>
#include <KLocalizedQmlContext>
#include <KLocalizedString>

int main(int argCount, char* argVector[])
{
    QApplication app(argCount, argVector);
    KLocalizedString::setApplicationDomain("org.kde.addonsexample");

    KAboutData aboutData(
        QStringLiteral("addonsexample"),
        i18nc("@title:window", "Addons Example"),
        QStringLiteral("1.0"),
        i18nc("@info", "This program shows how to use Kirigami Addons"),
        KAboutLicense::GPL_V3,
        QStringLiteral("(C) 2023"),
        i18nc("@info", "Optional text shown in the About"),
        QStringLiteral("https://example.com/addonsexample/"),
        QStringLiteral("https://example.com/addonsexample/bugs/"));

    aboutData.addAuthor(i18nc("@info:credit", "John Doe"),
                        i18nc("@info:credit", "Maintainer"));

    KAboutData::setApplicationData(aboutData);

    if (qEnvironmentVariableIsEmpty("QT_QUICK_CONTROLS_STYLE")) {
        QQuickStyle::setStyle(QStringLiteral("org.kde.desktop"));
    }
    QApplication::setWindowIcon(QIcon::fromTheme(QStringLiteral("start-here-sonicde")));

    QQmlApplicationEngine engine;
    KLocalization::setupLocalizedContext(&engine);
    engine.loadFromModule("org.kde.addonsexample", "Main");

    if (engine.rootObjects().isEmpty()) {
        return -1;
    }

    return app.exec();
}
```

If you have read the [KXmlGui tutorial](../kxmlgui/index.md) or the [Kirigami About page](about-page.md), much of this will look familiar.

We create our application and use [KAboutData](/docs/api/kcoreaddons/kaboutdata)'s constructor to add its metadata, add ourselves as an author, and call [setApplicationData()](/docs/api/kcoreaddons/kaboutdata#setApplicationData) to finish the process. For later, we also set an application icon from the system theme.

We then create our QML engine and call [KLocalization::setupLocalizedContext()](/docs/api/ki18nqml/klocalization#setupLocalizedContext), which integrates translated strings into it.

Finally, we load our QML from the `org.kde.addonsexample` module defined in CMake, so all that's left is our initial QML file.

## FormCard and FormButtonDelegate

The idea for our application is a small Kirigami Addons gallery of our own, showing several components, one per page. The main page holds a simple list of buttons in a [ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html), each opening a separate page.

Initially, our `Main.qml` should look like this:

```qml
import QtQuick
import QtQuick.Layouts

import org.kde.kirigami as Kirigami
import org.kde.kirigamiaddons.formcard as FormCard

Kirigami.ApplicationWindow {
    id: root
    width: 600
    height: 700

    pageStack.initialPage: Kirigami.ScrollablePage {
        ColumnLayout {
            // Our code will go here
        }
    }
}
```

We use the handy [pageStack](page-row-and-page-stack.md) to set the initial page to a [Kirigami.ScrollablePage](/docs/api/kirigami/qml-org-kde-kirigami-scrollablepage).

We could use a [FormLayout](form-layouts.md) together with [Qt Quick Controls components](controls.md) to reach our goal, but here we introduce [FormCard](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formcard).

The main purpose of a FormCard is to be a container for other components, in a color different from the background, much like a [Kirigami.Card](/docs/api/kirigami/qml-org-kde-kirigami-card), but for settings windows. You can have several FormCards in your application to indicate different sections. They are grouped with a [ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html), which also gives them their width.

Importing `org.kde.kirigamiaddons.formcard` makes all FormCard components available to your QML file.

Our main page has a single section, so we add a single FormCard:

```qml
import QtQuick
import QtQuick.Layouts

import org.kde.kirigami as Kirigami
import org.kde.kirigamiaddons.formcard as FormCard

Kirigami.ApplicationWindow {
    id: root
    width: 600
    height: 700

    pageStack.initialPage: Kirigami.ScrollablePage {
        ColumnLayout {
            FormCard.FormCard {
                // Our buttons will go here
            }
        }
    }
}
```

The great thing about FormCard is that it lays things out for you: the order of its components is enough to set their position in the FormCard. No [Layout attached properties](https://doc.qt.io/qt-6/qml-qtquick-layouts-layout.html) are needed, and you aren't expected to use [anchors](https://doc.qt.io/qt-6/qtquick-positioning-anchors.html) or [positioners](https://doc.qt.io/qt-6/qtquick-positioning-layouts.html).

We can simply add a few [FormButtonDelegate](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formbuttondelegate) buttons to our FormCard:

```qml
import QtQuick
import QtQuick.Layouts

import org.kde.kirigami as Kirigami
import org.kde.kirigamiaddons.formcard as FormCard

Kirigami.ApplicationWindow {
    id: root
    width: 600
    height: 700

    pageStack.initialPage: Kirigami.ScrollablePage {
        ColumnLayout {
            FormCard.FormCard {
                FormCard.FormButtonDelegate {
                    id: aboutSonicDEButton
                    icon.name: "start-here-sonicde"
                    text: i18n("About SonicDE Page")
                }
                FormCard.FormButtonDelegate {
                    id: aboutPageButton
                    icon.name: "applications-utilities"
                    text: i18n("About Addons Example")
                }
                FormCard.FormButtonDelegate {
                    id: settingsButton
                    icon.name: "settings-configure"
                    text: i18n("Single Settings Page")
                }
            }
        }
    }
}
```

That's it! The buttons don't do anything yet, but we are now set up to play with our [About pages](addons-about.md).

Build and run it like so:

```bash
cmake -B build/ --install-prefix ~/.local
cmake --build build/
cmake --install build/
addonsexample
```
