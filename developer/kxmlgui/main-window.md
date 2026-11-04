---
title: Creating the main window
description: The most important part of an application, its main window.
source_url: https://develop.kde.org/docs/getting-started/kxmlgui/main_window/
source_authors: [Alexander Lohnau, Andrew Shark, Arpan Patelia, Carl Schwan, Claudio Cambra, Frederik Schwarzer, Mikhail Zolotukhin, Nicolas Fella, Thiago Sueto, Tobias Fella]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-frameworks-xml-gui (KXmlGuiWindow), sonic-frameworks-text-widgets (KTextEdit); the code was built against SonicDE's frameworks
---

# Creating the main window

## Summary

This step continues the [Hello World project](hello-world.md) and introduces the [KXmlGuiWindow](/docs/api/kxmlgui/kxmlguiwindow) class.

In the previous step, the program showed a dialog. Now we start building a working application with a full main window.

## KXmlGuiWindow

[KXmlGuiWindow](/docs/api/kxmlgui/kxmlguiwindow) provides a complete main window with menu bar, toolbars, status bar and a central area for one large widget. The Help menu, for example, is already defined. Most applications built on SonicDE's libraries derive from it, because it lets you define menu and toolbar layouts in XML files (that technology is [KXmlGui](/docs/api/kxmlgui/kxmlgui-index)). We won't use that yet; the next step does.

To use [KXmlGuiWindow](/docs/api/kxmlgui/kxmlguiwindow), subclass it. Create two files, `mainwindow.cpp` and `mainwindow.h`, for the code.

### mainwindow.h

```cpp
#ifndef MAINWINDOW_H
#define MAINWINDOW_H

#include <KXmlGuiWindow>

class KTextEdit;

class MainWindow : public KXmlGuiWindow
{
public:
    explicit MainWindow(QWidget *parent = nullptr);

private:
    KTextEdit *textArea;
};

#endif // MAINWINDOW_H
```

First we [subclass](https://en.wikipedia.org/wiki/Inheritance_%28object-oriented_programming%29#Subclasses_and_superclasses) [KXmlGuiWindow](/docs/api/kxmlgui/kxmlguiwindow) with `class MainWindow : public KXmlGuiWindow`, then declare the [constructor](https://en.wikipedia.org/wiki/Constructor_(object-oriented_programming)), `MainWindow(QWidget *parent = nullptr);`.

Finally we declare a pointer to the object that makes up most of the program and turns it into a text editor: a [KTextEdit](/docs/api/ktextwidgets/ktextedit), a rich text editing widget with extras such as hiding the mouse cursor while typing and spell checking.

### mainwindow.cpp

```cpp
#include <KTextEdit>
#include "mainwindow.h"

MainWindow::MainWindow(QWidget *parent) : KXmlGuiWindow(parent)
{
    textArea = new KTextEdit();
    setCentralWidget(textArea);
    setupGUI();
}
```

First, include the header with the class declaration.

In the constructor we create the [KTextEdit](/docs/api/ktextwidgets/ktextedit) `textArea`. Because it is a [QWidget](https://doc.qt.io/qt-6/qwidget.html) and our window is a [QMainWindow](https://doc.qt.io/qt-6/qmainwindow.html) (KXmlGuiWindow derives from it), we can call [QMainWindow::setCentralWidget()](https://doc.qt.io/qt-6/qmainwindow.html#setCentralWidget) to make `textArea` fill the central area of the window.

Finally, [KXmlGuiWindow::setupGUI()](/docs/api/kxmlgui/kxmlguiwindow#setupGUI) does a lot behind the scenes and creates the default menus (Settings, Help).

### Back to main.cpp

To show the window, add a few lines to `main.cpp`:

```cpp
#include <QApplication>
#include <QCommandLineParser>
#include <KAboutData>
#include <KLocalizedString>
#include "mainwindow.h"

int main (int argc, char *argv[])
{
    using namespace Qt::Literals::StringLiterals;

    QApplication app(argc, argv);
    KLocalizedString::setApplicationDomain("mainwindow");

    KAboutData aboutData(
        u"mainwindow"_s,
        i18n("Main Window"),
        u"1.0"_s,
        i18n("A simple text area"),
        KAboutLicense::GPL,
        i18n("(c) 2024"),
        i18n("Educational application..."),
        u"https://example.com/mainwindow/"_s,
        u"https://example.com/mainwindow/bugs/"_s);

    aboutData.addAuthor(
        i18n("John Doe"),
        i18n("Tutorial learner"),
        u"john.doe@example.com"_s,
        u"https://john-doe.example.com"_s,
        u"johndoe"_s);

    KAboutData::setApplicationData(aboutData);

    QCommandLineParser parser;
    aboutData.setupCommandLine(&parser);
    parser.process(app);
    aboutData.processCommandLine(&parser);

    MainWindow *window = new MainWindow();
    window->show();

    return app.exec();
}
```

We include the new header `mainwindow.h`, create a `MainWindow` near the end of `main()`, and show it (new windows are hidden by default).

## CMake

Add `mainwindow.cpp` to the sources, add the `XmlGui` and `TextWidgets` frameworks, and replace `helloworld` with `mainwindow`.

### CMakeLists.txt

```cmake
cmake_minimum_required(VERSION 3.20)

project(mainwindow)

set(QT_MIN_VERSION "6.6.0")
set(KF_MIN_VERSION "6.0.0")

find_package(ECM ${KF_MIN_VERSION} REQUIRED NO_MODULE)
set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

include(KDEInstallDirs)
include(KDECMakeSettings)
include(KDECompilerSettings NO_POLICY_SCOPE)
include(FeatureSummary)

find_package(Qt6 ${QT_MIN_VERSION} CONFIG REQUIRED COMPONENTS
    Core    # QCommandLineParser, QStringLiteral
    Widgets # QApplication
)

find_package(KF6 ${KF_MIN_VERSION} REQUIRED COMPONENTS
    CoreAddons      # KAboutData
    I18n            # KLocalizedString
    XmlGui          # KXmlGuiWindow
    TextWidgets     # KTextEdit
)

add_executable(mainwindow)

target_sources(mainwindow
    PRIVATE
    main.cpp
    mainwindow.cpp
)

target_link_libraries(mainwindow
    Qt6::Widgets
    KF6::CoreAddons
    KF6::I18n
    KF6::XmlGui
    KF6::TextWidgets
)

install(TARGETS mainwindow ${KDE_INSTALL_TARGETS_DEFAULT_ARGS})

feature_summary(WHAT ALL INCLUDE_QUIET_PACKAGES FATAL_ON_MISSING_REQUIRED_PACKAGES)
```

## Running the application

Build and install it as in [Hello World](hello-world.md#building-and-running), then run:

```bash
mainwindow
```

Next: [Using actions](using-actions.md).
