---
title: "KirigamiAppDefaults Namespace"
description: "Contains a function to apply useful default Qt options for Kirigami apps."
---

# KirigamiAppDefaults Namespace

Contains a function to apply useful default Qt options for Kirigami apps. [More...](#details)

- **Header:** `#include <KirigamiAppDefaults>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KirigamiAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::KirigamiAddons)`

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### void KirigamiAppDefaults::apply(QGuiApplication \**app*) {#apply}

Helper to apply suitable defaults for an app using Kirigami

Kirigami apps are generally Qt apps using Kirigami. Qt's defaults and fallbacks on different platforms don't fit these apps very well. This function sets up the default style to Breeze, sets up support for color schemes, sets the Breeze icon theme, sets a font size and configures logging and crash handling.

Your normal main function should look something like

```cpp
int main(int argc, char *argv[])
{
    QApplication app(argc, argv);
    KirigamiAppDefaults::apply(&app);

    // Set up KAboutData

    // QCommandLineParser creation and processing

    QQmlApplicationEngine engine;
    KLocalization::setupLocalizedContext(&engine);
    if (!KirigamiAppDefaults::load("org.kde.myapp", u"Main", &engine)) {
        return EXIT_FAILURE;
    }
    return app.exec();
}
```

### bool KirigamiAppDefaults::load(QAnyStringView *uri*, QAnyStringView *typeName*, QQmlApplicationEngine \**engine*) {#load}

Loads the QML module and displays its loading errors if startup fails.

On desktop platforms, the errors are shown in a native message box. On Android, a Qt Quick dialog is used so this helper does not require Qt Widgets.

Returns `true` when the requested module or fallback error UI loaded successfully.
