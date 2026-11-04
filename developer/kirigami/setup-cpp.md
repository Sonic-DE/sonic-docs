---
title: Setup with C++
description: Create your first Kirigami application with C++.
source_url: https://develop.kde.org/docs/getting-started/kirigami/setup-cpp/
source_authors: [Adrian Chaves, Alexander Robb, Andrew Shark, Antti Savolainen, Carl Schwan, Chris Holland, Claudio Cambra, Cristian Le, Felipe Kinoshita, Jamie Phillips, Jonah Brüchert, Josep M. Ferrer, Marie Stadlbauer, Mikhail Zolotukhin, Nicolas Fella, Onuralp SEZER, Parth Dhiman, Phu Nguyen, Thiago Sueto, Thomas A, Tobias Fella, chakli ch]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-frameworks-quick-ui (Kirigami, templates/kirigami6, tabletmodewatcher.cpp), sonic-frameworks-internationalization (KLocalization::setupLocalizedContext), sonic-frameworks-quick-desktop-style, sonic-silver-icons; the example was built against SonicDE's frameworks without warnings and loaded offscreen without QML errors
---

# Setup with C++

## Installing Kirigami

Kirigami is part of SonicDE (`sonic-frameworks-quick-ui`). You need a C++ compiler, CMake, Qt 6's development files and SonicDE's frameworks with their development files. Either install SonicDE from your distribution (on Gentoo and Arch Linux the packages include the headers), or build and install it with sonicde-builder as described in [Building Sonic-DE](../building.md).

Create a folder for the tutorial, for example `~/src/kirigami-tutorial`, and put the tutorial's source files in it.

## Project structure

Tools can create these files for us, but we write them by hand, to understand the parts that make up the application.

The project folder, `kirigami-tutorial/`, looks like this:

```text
kirigami-tutorial/
├── CMakeLists.txt
├── org.kde.tutorial.desktop
└── src/
    ├── CMakeLists.txt
    ├── main.cpp
    └── Main.qml
```

Inside it we create a `src/` folder and a `CMakeLists.txt`. It is good practice to keep the main C++ files in `src/`. `Main.qml` goes there too, since it is built into the program.

> **Tip:** Create this structure quickly with:
>
> ```bash
> mkdir -p kirigami-tutorial/src
> touch kirigami-tutorial/{CMakeLists.txt,org.kde.tutorial.desktop}
> touch kirigami-tutorial/src/{CMakeLists.txt,main.cpp,Main.qml}
> ```

### Main.qml

```qml
// Includes relevant modules used by the QML
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

// Provides basic features needed for all kirigami applications
Kirigami.ApplicationWindow {
    // Unique identifier to reference this object
    id: root

    width: 400
    height: 300

    // Window title
    // i18nc() makes a string translatable
    // and provides additional context for the translators
    title: i18nc("@title:window", "Hello World")

    // Set the first page that will be loaded when the app opens
    // This can also be set to an id of a Kirigami.Page
    pageStack.initialPage: Kirigami.Page {
        Controls.Label {
            // Center label horizontally and vertically within parent object
            anchors.centerIn: parent
            text: i18n("Hello World!")
        }
    }
}
```

This is the application's user interface.

If you know some JavaScript, much of QML will look familiar (though it has its own peculiarities). [Qt's documentation](https://doc.qt.io/qt-6/qtqml-index.html) has extensive material on the language if you want to try things yourself. In these tutorials we spend most of our time on QML code, using Kirigami to get the most out of it.

First we [import](https://doc.qt.io/qt-6/qtqml-syntax-imports.html) some important modules:

- [QtQuick](https://doc.qt.io/qt-6/qtquick-index.html), the standard library of QML applications.
- [Qt Quick Controls](https://doc.qt.io/qt-6/qtquickcontrols-index.html), standard controls that make applications interactive.
- [Qt Quick Layouts](https://doc.qt.io/qt-6/qtquicklayouts-index.html), tools for placing components in the window.
- [Kirigami](/docs/api/kirigami/kirigami-index), components for applications that work on devices of different shapes and sizes.

> **Note:** Importing Qt Quick Controls and Kirigami into separate namespaces with `as` is good practice: components with the same name can't conflict. You will see other names for Qt Quick Controls, such as "QQC" or "QQC2"; this tutorial uses "Controls" for clarity.

Then comes the root element, [Kirigami.ApplicationWindow](/docs/api/kirigami/qml-org-kde-kirigami-applicationwindow), which provides basic features every Kirigami application needs. This window holds our *pages*, the main sections of the user interface.

We set the window's `id` to `root`. IDs let us refer to a particular component, even when there are several of the same type.

We also set the window's [title](https://doc.qt.io/qt-6/qml-qtquick-window.html#title-prop) to "Hello World", wrapped in `i18nc()`, which takes a context and the string.

> **Note:** The `i18n()` functions make your application translatable: they return the string in the user's language, if your application has been translated into it. An English user sees the window title "Hello World", a Spanish user "Hola Mundo".
>
> `i18nc()` adds a context for the translators. Here it says the string is a window title, with `@title:window` before "Hello World". See [KI18n](/docs/api/ki18n/ki18n-index) for more on writing good contexts.

Then we set the first page of the page stack. Most Kirigami applications are organized as a stack of pages, each holding the components for one task. For now we keep it to one page. [pageStack](/docs/api/kirigami/qml-org-kde-kirigami-abstractapplicationwindow#pageStack-prop) is a page stack provided by [Kirigami.ApplicationWindow](/docs/api/kirigami/qml-org-kde-kirigami-applicationwindow), initially empty; `pageStack.initialPage: Kirigami.Page {...}` makes a [Kirigami.Page](/docs/api/kirigami/qml-org-kde-kirigami-page) the first page shown when the application starts. It holds all our content.

Finally, the page contains a [Controls.Label](https://doc.qt.io/qt-6/qml-qtquick-controls-label.html) that shows text. `anchors.centerIn: parent` centers it horizontally and vertically in its parent, here the [Kirigami.Page](/docs/api/kirigami/qml-org-kde-kirigami-page). Last, we set its text: `text: i18n("Hello World!")`.

### org.kde.tutorial.desktop

The main purpose of [desktop entry files](https://specifications.freedesktop.org/desktop-entry-spec/latest/) is to show your application in the application launcher. SonicDE's task manager also uses the file to match your windows to the application's icon and name: Qt sets the desktop file name (`QGuiApplication::setDesktopFileName()`, see `main.cpp` below) on each window.

The file name follows a [reverse-DNS scheme](https://en.wikipedia.org/wiki/Reverse_domain_name_notation) with the `.desktop` extension, such as `org.kde.tutorial.desktop`:

```ini
[Desktop Entry]
Name=Kirigami Tutorial
Exec=kirigami-hello
Icon=kde
Type=Application
Terminal=false
Categories=Utility
```

(The original file also has translations of `Name`; see [Desktop file](../additional/desktop-file.md) for the keys.)

### CMakeLists.txt

CMake, the build system used here, reads `CMakeLists.txt` files. `kirigami-tutorial/CMakeLists.txt` describes some of the application's properties and the dependencies needed to build it.

```cmake
cmake_minimum_required(VERSION 3.20)
project(kirigami-tutorial)

find_package(ECM 6.0.0 REQUIRED NO_MODULE)
set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH})

include(KDEInstallDirs)
include(KDECMakeSettings)
include(KDECompilerSettings NO_POLICY_SCOPE)
include(ECMFindQmlModule)
include(ECMQmlModule)

find_package(Qt6 REQUIRED COMPONENTS
    Core
    Quick
    Test
    Gui
    QuickControls2
    Widgets
)

find_package(KF6 REQUIRED COMPONENTS
    Kirigami
    I18n
    CoreAddons
    QQC2DesktopStyle
    IconThemes
)

ecm_find_qmlmodule(org.kde.kirigami REQUIRED)

add_subdirectory(src)

install(PROGRAMS org.kde.tutorial.desktop DESTINATION ${KDE_INSTALL_APPDIR})

feature_summary(WHAT ALL INCLUDE_QUIET_PACKAGES FATAL_ON_MISSING_REQUIRED_PACKAGES)
```

The `CMakeLists.txt` defines how the project is built. Most of it sets up the project; [Understanding CMakeLists](understanding-cmakelists.md) explains it line by line.

The important thing: C++ build dependencies on Qt and SonicDE's frameworks are declared with [find_package()](https://cmake.org/cmake/help/latest/command/find_package.html), and QML run-time dependencies with `ecm_find_qmlmodule()`. Add to these lines when you use more components. (SonicDE's frameworks keep the `KF6` package names; `QQC2DesktopStyle` is `sonic-frameworks-quick-desktop-style`.)

`add_subdirectory(src)` points CMake to `kirigami-tutorial/src/`, where the source code is.

`install()` says where to install the desktop file.

Now `kirigami-tutorial/src/CMakeLists.txt`:

```cmake
add_executable(kirigami-hello)

ecm_add_qml_module(kirigami-hello
    URI
    org.kde.tutorial
)

target_sources(kirigami-hello
    PRIVATE
    main.cpp
)

ecm_target_qml_sources(kirigami-hello
    SOURCES
    Main.qml
)

target_link_libraries(kirigami-hello
    PRIVATE
    Qt6::Quick
    Qt6::Qml
    Qt6::Gui
    Qt6::QuickControls2
    Qt6::Widgets
    KF6::I18n
    KF6::I18nQml
    KF6::CoreAddons
    KF6::IconThemes
)

install(TARGETS kirigami-hello ${KDE_INSTALL_TARGETS_DEFAULT_ARGS})
```

It has five steps:

1. create an executable;
2. turn it into a QML module that accepts QML files;
3. add the C++ and QML files;
4. link the libraries it needs;
5. install it.

When you add QML files, add them to the existing `ecm_target_qml_sources()` call. C++ files that use [QML_ELEMENT](https://doc.qt.io/qt-6/qtqml-cppintegration-definetypes.html), which comes later in the tutorial, are added with `target_sources()`.

With CMake taken care of, let's look at the files we will mostly work with.

### main.cpp

`kirigami-tutorial/src/main.cpp` holds the application's "business logic". C++ is flexible and fast, though more involved than some other languages.

It is also the application's entry point: it sets up and starts both the logic and the user interface.

```cpp
#include <QApplication>
#include <QQmlApplicationEngine>
#include <QtQml>
#include <QUrl>
#include <QQuickStyle>
#include <KLocalizedQmlContext>
#include <KLocalizedString>
#include <KIconTheme>

int main(int argc, char *argv[])
{
    KIconTheme::initTheme();
    QApplication app(argc, argv);
    KLocalizedString::setApplicationDomain("tutorial");
    QApplication::setOrganizationName(QStringLiteral("KDE"));
    QApplication::setOrganizationDomain(QStringLiteral("kde.org"));
    QApplication::setApplicationName(QStringLiteral("Kirigami Tutorial"));
    QApplication::setDesktopFileName(QStringLiteral("org.kde.tutorial"));

    if (qEnvironmentVariableIsEmpty("QT_QUICK_CONTROLS_STYLE")) {
        QQuickStyle::setStyle(QStringLiteral("org.kde.desktop"));
    }

    QQmlApplicationEngine engine;

    KLocalization::setupLocalizedContext(&engine);
    engine.loadFromModule("org.kde.tutorial", "Main");

    if (engine.rootObjects().isEmpty()) {
        return -1;
    }

    return app.exec();
}
```

We don't need the details of `main.cpp` yet; its role grows once the application gets more functionality. [Figuring out main.cpp](main-cpp.md) explains it. To see ways to improve the C++ code, such as [KAboutData](/docs/api/kcoreaddons/kaboutdata) for translatable application metadata, see the [KXmlGui tutorial](../kxmlgui/index.md).

A few SonicDE specifics:

- The program doesn't set a widget style: on SonicDE the platform theme applies the user's style (Silver by default), as SonicDE's own Kirigami application template does.
- `org.kde.desktop` is the Qt Quick Controls style that follows that desktop style (`sonic-frameworks-quick-desktop-style`).
- `KLocalization::setupLocalizedContext()` (from `KF6::I18nQml`) makes the `i18n()` functions available in QML. Older code uses `KLocalizedContext`, which is deprecated since 6.8.

For now, the line that interests us is:

```cpp
engine.loadFromModule("org.kde.tutorial", "Main");
```

The first argument is the URI set in `kirigami-tutorial/src/CMakeLists.txt`, the second the name of the QML type to load (`Main`, from the file `Main.qml`, which must start with an uppercase letter).

> **The old way:** You may see another way of loading QML files in real code:
>
> ```cpp
> engine.load(QUrl(QStringLiteral("qrc:/qt/qml/org/kde/tutorial/qml/Main.qml")));
> ```
>
> This [Qt resource URI](https://doc.qt.io/qt-6/resources.html) has the form `<resource prefix><import URI><optional QML folder><file>`: the resource prefix is `/qt/qml` in Qt 6 (`/` in Qt 5), the import URI `/org/kde/tutorial` matches `org.kde.tutorial`, the optional folder `/qml` is needed if the QML files are in a `qml/` folder, and last comes the file. It is more verbose and has disadvantages, so prefer `loadFromModule()`.

## Building and installing the application

In the project's root folder, run:

```bash
cmake -B build/ --install-prefix ~/.local
cmake --build build/
cmake --install build/
```

The program is installed to `~/.local/bin` and its desktop file to `~/.local/share/applications`.

## Running the application

Run the program:

```bash
kirigami-hello
```

Voilà! Your first Kirigami application appears.

To run it in mobile mode, set `QT_QUICK_CONTROLS_MOBILE=1`:

```bash
QT_QUICK_CONTROLS_MOBILE=1 kirigami-hello
```

To uninstall a project you built and installed with CMake:

```bash
cmake --build build/ --target uninstall
```

> **Note:** To create a new project's files, you can start from Kirigami's application template, `templates/kirigami6` in `sonic-frameworks-quick-ui`, which tools such as KAppTemplate and KDevelop use. Such generated projects also contain [AppStream](https://www.freedesktop.org/software/appstream/docs/sect-Metadata-Application.html) metadata and a desktop file. Thanks to CMake, IDEs such as KDevelop and [Qt Creator](https://www.qt.io/product/development-tools) work with this project with little effort.
