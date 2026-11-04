---
title: Understanding CMakeLists
description: Getting to grips with how CMakeLists.txt files work.
source_url: https://develop.kde.org/docs/getting-started/kirigami/advanced-understanding_cmakelists/
source_authors: [Carl Schwan, Chris Holland, Claudio Cambra, Mark Penner, Mikhail Zolotukhin, Nicolas Fella, Tammes Burghard, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-cmake-modules (KDEInstallDirs6, KDECMakeSettings, KDECompilerSettings, ECMQmlModule), CMake FeatureSummary, and the tutorial's CMake files as built against SonicDE's frameworks"
---

# Understanding CMakeLists

## CMake

In the introductory tutorial we used [CMake](https://cmake.org/) as the build system for our application, but we only looked closely at one of our `CMakeLists.txt` files. Here we go over how they work in a bit more detail.

CMake is useful because it automates much of what needs to be done before compilation.

## The root CMakeLists.txt

You might remember this `CMakeLists.txt` file from the [first tutorial](setup-cpp.md):

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

The first line, `cmake_minimum_required()`, sets the minimum version of CMake the project needs.

After that, `project(kirigami-tutorial)` defines the name of the project.

Then comes a section that includes a number of necessary CMake and KDE settings from extra-cmake-modules (ECM, shipped by SonicDE as [sonic-frameworks-cmake-modules](https://github.com/Sonic-DE/sonic-frameworks-cmake-modules)). They provide a set of useful utilities:

- [KDEInstallDirs](https://github.com/Sonic-DE/sonic-frameworks-cmake-modules/blob/master/kde-modules/KDEInstallDirs6.cmake) provides convenience variables such as `${KDE_INSTALL_TARGETS_DEFAULT_ARGS}`, `${KDE_INSTALL_QMLDIR}`, `${KDE_INSTALL_BINDIR}` and `${KDE_INSTALL_LIBDIR}`.
- [KDECMakeSettings](https://github.com/Sonic-DE/sonic-frameworks-cmake-modules/blob/master/kde-modules/KDECMakeSettings.cmake) provides things like `CMAKE_AUTORCC ON`, an `uninstall` target that can be used with `cmake --build build/ --target uninstall`, and `ENABLE_CLAZY`.
- [KDECompilerSettings](https://github.com/Sonic-DE/sonic-frameworks-cmake-modules/blob/master/kde-modules/KDECompilerSettings.cmake) provides a minimum C++ standard, compiler flags such as `-pedantic`, and best-practice macros like `-DQT_NO_CAST_FROM_ASCII`, which requires explicit conversions such as `QStringLiteral()`.
- [ECMFindQmlModule](https://github.com/Sonic-DE/sonic-frameworks-cmake-modules/blob/master/modules/ECMFindQmlModule.cmake) provides a way to make sure a QML dependency needed at runtime is found at build time.
- [ECMQmlModule](https://github.com/Sonic-DE/sonic-frameworks-cmake-modules/blob/master/modules/ECMQmlModule.cmake) provides CMake commands like `ecm_add_qml_module()` and `ecm_target_qml_sources()`.

The next section is important, because it specifies the dependencies we bring in at build time. Let's look at the first:

```cmake
find_package(Qt6 REQUIRED COMPONENTS
    Core
    Quick
    Test
    Gui
    QuickControls2
    Widgets
)
```

- [find_package()](https://cmake.org/cmake/help/latest/command/find_package.html) finds and loads the external library and its components.
- `REQUIRED` tells CMake to exit with an error if the package can't be found.
- `COMPONENTS` precedes the specific components of the framework we include.
- Each word after `COMPONENTS` is a specific component of the library.

> **Note:** To add another SonicDE framework to your application, add its component to the `KF6` list. Each class page of the [API reference](/docs/api) gives the lines it needs under **CMake**; for example, [KAboutData](/docs/api/kcoreaddons/kaboutdata) lists the `CoreAddons` component and `KF6::CoreAddons`. The Kirigami framework's CMake package is `KF6Kirigami`, which with ECM becomes:
>
> ```cmake
> find_package(KF6 COMPONENTS Kirigami)
> ```
>
> Pay close attention to the components you include: leaving out one used in your code stops the application from compiling.

The install line tells CMake to install the desktop file in `${KDE_INSTALL_APPDIR}`, which is `share/applications` under the installation prefix, usually `/usr/share/applications`:

```cmake
install(PROGRAMS org.kde.tutorial.desktop DESTINATION ${KDE_INSTALL_APPDIR})
```

The final line makes CMake print which packages it found, and makes configuring fail immediately if a required package is missing:

```cmake
feature_summary(WHAT ALL INCLUDE_QUIET_PACKAGES FATAL_ON_MISSING_REQUIRED_PACKAGES)
```

And above that, `add_subdirectory(src)` points CMake to the `src/` directory, where it finds another `CMakeLists.txt` file.

## src/CMakeLists.txt

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

While the first file handled metadata and finding libraries, this one handles dependencies and installing the application. It has the following CMake calls:

- [add_executable()](https://cmake.org/cmake/help/latest/command/add_executable.html) creates the executable target we use to run our project.
- `ecm_add_qml_module()` creates a QML module target, accessible through the "org.kde.tutorial" import.
- [target_sources()](https://cmake.org/cmake/help/latest/command/target_sources.html) adds C++ source files to the executable target.
- `ecm_target_qml_sources()` adds QML files to the module.
- [target_link_libraries()](https://cmake.org/cmake/help/latest/command/target_link_libraries.html) links the C++ libraries used in our code to our executable. Kirigami isn't included here because we only use its QML module.
- [install()](https://cmake.org/cmake/help/latest/command/install.html) installs the executable to the system.

The documentation for the two ECM commands is in [ECMQmlModule](https://github.com/Sonic-DE/sonic-frameworks-cmake-modules/blob/master/modules/ECMQmlModule.cmake).

The call to `ecm_add_qml_module()` turns the traditional C++ executable target into one that can accept QML files and C++ code accessible from QML, which is called [using the executable as backing target for a QML module](https://doc.qt.io/qt-6/qt-add-qml-module.html#executable-as-a-qml-module). The QML files then run directly as part of the application, which is often what applications do.

You can also use `ecm_add_qml_module()` to create a separate QML module that doesn't use the executable as backing target. In that case you create a library target with [add_library()](https://cmake.org/cmake/help/latest/command/add_library.html) and link it to an existing executable target with `target_link_libraries()`. Besides installing the library with `install()`, you need to finalize the QML module with `ecm_finalize_qml_module()` so that it generates two files, `qmldir` and `qmltypes`. Qt Quick applications use these files to find separate QML modules.

Creating a separate QML module is shown in [Using separate files](separate-files.md).

These commands are additions from ECM that make [Qt's declarative QML module registration](https://doc.qt.io/qt-6/cmake-build-qml-application.html) (the [replacement for Qt resource files](https://doc.qt.io/qt-6/resources.html)) easier to use.

> **Note:** These libraries must match the components found in the root `CMakeLists.txt` file; otherwise those components aren't included and the application won't compile.

## src/components/CMakeLists.txt

The page about [splitting your code into separate files](separate-files.md#preparing-cmake-for-the-new-files) introduced a new CMake file for a separate QML module:

```cmake
add_library(kirigami-hello-components)

ecm_add_qml_module(kirigami-hello-components
    URI "org.kde.tutorial.components"
    GENERATE_PLUGIN_SOURCE
)

ecm_target_qml_sources(kirigami-hello-components
    SOURCES
    AddDialog.qml
    KountdownDelegate.qml
)

ecm_finalize_qml_module(kirigami-hello-components)

install(TARGETS kirigami-hello-components ${KDE_INSTALL_TARGETS_DEFAULT_ARGS})
```

For CMake to read this file, `src/CMakeLists.txt` needs a call to `add_subdirectory()` pointing to it.

We create a new target called `kirigami-hello-components` and then turn it into a QML module with `ecm_add_qml_module()`, under the import name `org.kde.tutorial.components`, and add the relevant QML files.

The call to [add_library()](https://cmake.org/cmake/help/latest/command/add_library.html) generates the new `kirigami-hello-components` target. This target has its own source files and QML files, links its own libraries and so on, and once it is compiled it needs to be linked to the executable created in `src/CMakeLists.txt`. This is done by adding the target name to the libraries linked to the executable in `target_link_libraries()`.

The call to `ecm_add_qml_module()` lets the library accept QML files as before, but this time we need `GENERATE_PLUGIN_SOURCE`. When the executable is the backing target (as with `kirigami-hello`), no plugin code is needed, since the module is built into the executable; separate QML modules like `kirigami-hello-components` need the plugin code.

Upstream Qt's [qt_add_qml_module()](https://doc.qt.io/qt-6/qt-add-qml-module.html#targets-and-plugin-targets) generates a plugin together with the QML module by default, but ECM's `ecm_add_qml_module()` doesn't, for backwards compatibility.

Separate QML modules also need to be finalized. Mainly, this means CMake generates two files, [qmldir and qmltypes](https://doc.qt.io/qt-6/qtqml-modules-qmldir.html), which describe our QML modules and export their symbols. They matter when the application is installed, so that the executable can find the QML files of each module, and they are added to the target automatically.

You can then install the target as before.

Next time you add more QML files, remember to include them in this file. C++ files that use the [QML_ELEMENT](https://doc.qt.io/qt-6/qtqml-cppintegration-definetypes.html) macro, which we will see much later in the tutorial, can also be added here with `target_sources()`. You can separate your code logically by creating more QML modules with different imports as needed.

This setup is useful for developing most Kirigami applications.
