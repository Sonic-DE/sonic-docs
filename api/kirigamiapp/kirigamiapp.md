---
title: "KirigamiApp Class"
description: "Helper to set up the process to properly run a Kirigami app. This class is deprecated since 1.11. We strongly advise against using it in new code."
---

# KirigamiApp Class

Helper to set up the process to properly run a Kirigami app. **This class is deprecated since 1.11. We strongly advise against using it in new code.** [More...](#details)

- **Header:** `#include <KirigamiApp>`
- **CMake:** `find_package(KF6KirigamiAddons REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE KirigamiApp)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)
- **Status:** Deprecated since 1.11

[List of all members, including inherited members](kirigamiapp-members.md)

## Public Types

- [\[alias\] KirigamiApp::App](#App-typedef)

## Public Functions

- [KirigamiApp()](#KirigamiApp)
- [bool start(QAnyStringView uri, QAnyStringView typeName, QQmlApplicationEngine \*engine)](#start)

**This class is deprecated since 1.11. We strongly advise against using it in new code.**

## Detailed Description {#details}

Kirigami apps are generally Qt apps using Kirigami. While that stands, there's certain things we need to do to ensure proper integration with the OS and that the different KDE Frameworks are engaged in making the app work smoothly.

Your normal main function should look something like

```cpp
int main(int argc, char *argv[])
{
    KirigamiApp::App app(argc, argv);
    KirigamiApp kapp;

    // Set up KAboutData

    // QCommandLineParser creation and processing

    if (!kapp.start("org.kde.myapp", u"Main", new QQmlApplicationEngine)) {
        return -1;
    }
    return app.exec();
}
```

Use [KirigamiAppDefaults::apply](kirigamiappdefaults.md#apply)() instead.

## Member Type Documentation {#member-type-documentation}

### \[alias\] KirigamiApp::App {#App-typedef}

Chooses either `QGuiApplication` or `QApplication` for you.

Allows the system to choose the one you'll want without really having to decide. Kirigami apps should generally not need QApplication (only for certain specific cases), but we keep using it in most apps to support qqc2-desktop-style which depends on QStyle. Except for on Android where we normally run with qqc2-breeze-style by default, which is QWidgets-free.

## Member Function Documentation {#member-function-documentation}

### KirigamiApp::KirigamiApp() {#KirigamiApp}

Constructor.

Call right after initialising the Q\*Application

### bool KirigamiApp::start(QAnyStringView *uri*, QAnyStringView *typeName*, QQmlApplicationEngine \**engine*) {#start}

Sets up the app's QQmlApplicationEngine, enables the translation context and loads the QML type `typeName` from the module specified by `uri`.
