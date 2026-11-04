---
title: Figuring out main.cpp
description: Understanding the central file of our backend code.
source_url: https://develop.kde.org/docs/getting-started/kirigami/advanced-maincpp/
source_authors: [Carl Schwan, Chris Holland, Claudio Cambra, Mikhail Zolotukhin, Thiago Sueto, Yelsin Sepulveda]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "the tutorial's main.cpp as built and run against SonicDE's frameworks; KIconTheme::initTheme (sonic-frameworks-icon-themes), sonic-qt-theme-bridge platform theme key, sonic-frameworks-quick-desktop-style README, KLocalization; Qt 6.11 documentation"
---

# Figuring out main.cpp

## The role of main.cpp

QML is used for the front end of Kirigami applications, while the back end is usually written in C++, thanks to the language's speed and flexibility. The previous pages covered QML in depth; to make applications that do more than pure QML can, we need to understand our back-end C++ code.

Here we go over the `main.cpp` file we created in [Setup with C++](setup-cpp.md), to better understand what happens in the central C++ file of our application. It is a basic `main.cpp`, but the features we go over stay essential whatever kind of application you create.

## What it does

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

First we include a number of [header files](https://www.learncpp.com/cpp-tutorial/header-files/) so we can use their functions: Qt headers that handle application logic and let us load QML files, and KDE Frameworks headers for icons and translations.

Before anything else, we call [KIconTheme::initTheme()](/docs/api/kiconthemes/kicontheme#initTheme). It must be called before the application object is created. Under SonicDE, the platform theme already handles icons and colors, and the call does nothing more. In other environments, it applies the icon theme the user configured (Silver by default) through KIconThemes and makes the application's colors follow the system color scheme, so the application still looks right there.

We then create a [QApplication](https://doc.qt.io/qt-6/qapplication.html) instance called `app`. Passing [argc and argv](https://www.learncpp.com/cpp-tutorial/command-line-arguments/) to the constructor is required. We use QApplication rather than [QGuiApplication](https://doc.qt.io/qt-6/qguiapplication.html) because the `org.kde.desktop` Qt Quick Controls style needs it: that style draws controls with the widget style, and isn't used with a QGuiApplication.

[KLocalizedString::setApplicationDomain()](/docs/api/ki18n/klocalizedstring#setApplicationDomain) sets the translation domain, the name of the catalog the application's translations are loaded from.

We also set some metadata about the application: the [organization](https://doc.qt.io/qt-6/qcoreapplication.html#organizationName-prop) that created it, its [domain](https://doc.qt.io/qt-6/qcoreapplication.html#organizationDomain-prop), the [name of the application](https://doc.qt.io/qt-6/qcoreapplication.html#applicationName-prop), and the [desktop file name](https://doc.qt.io/qt-6/qguiapplication.html#desktopFileName-prop) that matches our `org.kde.tutorial.desktop` file. The first three are properties of [QCoreApplication](https://doc.qt.io/qt-6/qcoreapplication.html), which QApplication inherits from and which provides the [event loop](https://doc.qt.io/qt-6/qcoreapplication.html#exec) for applications with or without a GUI (so this metadata would still be set if we ran our program without the GUI).

We don't set a widget style: on SonicDE the platform theme applies the user's style (Silver by default). For Qt Quick Controls, we set the `org.kde.desktop` style with [QQuickStyle::setStyle()](https://doc.qt.io/qt-6/qquickstyle.html#setStyle), unless the user chose a style with the `QT_QUICK_CONTROLS_STYLE` environment variable. This style, from `sonic-frameworks-quick-desktop-style`, makes the controls in the window, such as buttons and checkboxes, follow the desktop style.

The [QQmlApplicationEngine](https://doc.qt.io/qt-6/qqmlapplicationengine.html) lets us load an application from a QML file. [KLocalization::setupLocalizedContext()](/docs/api/ki18nqml/klocalization#setupLocalizedContext) makes the `i18n()` functions available to the engine's QML code. Then, with `engine.loadFromModule("org.kde.tutorial", "Main");`, we load our QML from the import URI defined in CMake.

Next, we check that the engine loaded the QML file correctly by making sure the engine's [rootObjects()](https://doc.qt.io/qt-6/qqmlapplicationengine.html#rootObjects) list isn't empty. We can then run our application with [app.exec()](https://doc.qt.io/qt-6/qcoreapplication.html#exec).
