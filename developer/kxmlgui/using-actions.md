---
title: Using actions
description: Add actions to the menus and toolbars.
source_url: https://develop.kde.org/docs/getting-started/kxmlgui/using_actions/
source_authors: [Alexander Lohnau, Andrew Shark, Arpan Patelia, Bharadwaj Raju, Carl Schwan, Claudio Cambra, Frederik Schwarzer, Mikhail Zolotukhin, Mladen Mirilović, Mouad Benali, Nicolas Fella, Snehit Sah, Thiago Sueto, Tobias Fella]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-frameworks-xml-gui (KActionCollection, KXMLGUIClient, kxmlguiclient.cpp), sonic-frameworks-settings-ui (KStandardAction), sonic-frameworks-cmake-modules (KDE_INSTALL_KXMLGUIDIR), sonic-silver-icons; the code was built against SonicDE's frameworks
---

# Using actions

## Introduction

This step introduces *actions*: a single way of offering the user something to do in your program.

For example, to let the user of our [main window](main-window.md) clear the text area with a toolbar button, a File menu entry or a keyboard shortcut, one [QAction](https://doc.qt.io/qt-6/qaction.html) does it all.

## QActions

A [QAction](https://doc.qt.io/qt-6/qaction.html) holds everything about an action: its text, icon and shortcuts. Through [signals and slots](https://doc.qt.io/qt-6/signalsandslots.html), a function elsewhere in your program runs whenever the action is triggered (for example when its menu entry is clicked).

QActions are mostly used in [QMenus](https://doc.qt.io/qt-6/qmenu.html) in a [QMenuBar](https://doc.qt.io/qt-6/qmenubar.html), in a [QToolBar](https://doc.qt.io/qt-6/qtoolbar.html), or in a context menu.

## The code

### main.cpp

We will install the user interface's `.rc` file for the component `texteditor`, so change the names in `main.cpp` accordingly. The `.rc` file is explained at the end of this step.

```c++
    // ...
    KLocalizedString::setApplicationDomain("texteditor");

    KAboutData aboutData(
            u"texteditor"_s,
    // ...
```

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
    void setupActions();
};

#endif // MAINWINDOW_H
```

Only a function `void setupActions()` was added; it sets up the actions.

### mainwindow.cpp

```cpp
#include <QApplication>
#include <QAction>
#include <KTextEdit>
#include <KLocalizedString>
#include <KActionCollection>
#include <KStandardAction>
#include "mainwindow.h"

MainWindow::MainWindow(QWidget *parent) : KXmlGuiWindow(parent)
{
    textArea = new KTextEdit();
    setCentralWidget(textArea);
    setupActions();
}

void MainWindow::setupActions()
{
    using namespace Qt::Literals::StringLiterals;

    QAction *clearAction = new QAction(this);
    clearAction->setText(i18n("&Clear"));
    clearAction->setIcon(QIcon::fromTheme(u"document-new-symbolic"_s));
    actionCollection()->addAction(u"clear"_s, clearAction);
    actionCollection()->setDefaultShortcut(clearAction, Qt::CTRL | Qt::Key_L);
    connect(clearAction, &QAction::triggered, textArea, &KTextEdit::clear);

    KStandardAction::quit(qApp, &QCoreApplication::quit, actionCollection());

    setupGUI(Default, u"texteditorui.rc"_s);
}
```

## Explanation

This builds on the [KXmlGuiWindow](/docs/api/kxmlgui/kxmlguiwindow) code of the [main window](main-window.md). Most changes are in `mainwindow.cpp`. An important one is that the constructor now calls `setupActions()` instead of `setupGUI()`: `setupActions()` creates the actions and then calls `setupGUI()` itself.

### Creating the QAction

First include the [QAction](https://doc.qt.io/qt-6/qaction.html) header and create one:

```c++
#include <QAction>
...
QAction *clearAction = new QAction(this);
```

### Setting its properties

Now set the action's properties. [QAction::setText()](https://doc.qt.io/qt-6/qaction.html#text-prop) sets the text shown in the menu, and with the [icon](https://doc.qt.io/qt-6/qaction.html#icon-prop) in the toolbar, depending on the widget style (beside or below the icon) and settings (whether to show text at all).

```c++
clearAction->setText(i18n("&Clear"));
```

The text goes through `i18n()`, so it can be translated, as described in [Hello World](hello-world.md#about-data-and-internationalization) (see also [KI18n](/docs/api/ki18n/ki18n-index)).

The ampersand (&) marks the letter that is the action's keyboard accelerator. When the user opens a menu and presses Alt, that letter is underlined: here the user presses Alt+C to clear the text area while the File menu is open.

The ampersand also helps translation: in languages that don't use the Latin alphabet, such as Japanese (where "copy" is コピー), it tells translators whether to add the Latin letter in parentheses, so users keep the same accelerator key whatever the translation.

### Icon

An action shown in a toolbar should have an icon, which may also appear next to it in menus, depending on the widget style. [QIcon::fromTheme()](https://doc.qt.io/qt-6/qicon.html#fromTheme) gets the icon `document-new-symbolic` from the user's icon theme (SonicDE's Silver theme has it), and [QAction::setIcon()](https://doc.qt.io/qt-6/qaction.html#icon-prop) gives it to `clearAction`:

```c++
clearAction->setIcon(QIcon::fromTheme(u"document-new-symbolic"_s));
```

### Adding it to the collection

For [KXmlGui](/docs/api/kxmlgui/kxmlgui-index) (explained below) to use the action, it must be in the application's action collection.

Our [KXmlGuiWindow](/docs/api/kxmlgui/kxmlguiwindow) implements the [KXMLGUIClient](/docs/api/kxmlgui/kxmlguiclient) interface, so [KXMLGUIClient::actionCollection()](/docs/api/kxmlgui/kxmlguiclient#actionCollection) returns its actions as a [KActionCollection](/docs/api/kxmlgui/kactioncollection), with convenience functions such as [KActionCollection::addAction()](/docs/api/kxmlgui/kactioncollection#addAction):

```c++
actionCollection()->addAction(u"clear"_s, clearAction);
```

This adds `clearAction` to the collection under the name `clear`. KXmlGui uses the name to refer to the action, so it is internal and never translated.

### Keyboard shortcuts

[KActionCollection::setDefaultShortcut()](/docs/api/kxmlgui/kactioncollection#setDefaultShortcut) gives the action a default shortcut, Ctrl+L:

```c++
actionCollection()->setDefaultShortcut(clearAction, Qt::CTRL | Qt::Key_L);
```

The keys are listed in Qt's [Qt::Key](https://doc.qt.io/qt-6/qt.html#Key-enum) enum. Combine modifier and key with `|`.

### Connecting the action

The action is set up; now connect it to something useful. Here it clears the text area, so we connect it to the `clear()` slot of the [KTextEdit](/docs/api/ktextwidgets/ktextedit):

```c++
connect(clearAction, &QAction::triggered, textArea, &KTextEdit::clear);
```

[QObject::connect()](https://doc.qt.io/qt-6/qobject.html#connect) is Qt's most useful magic. The first argument is the object that sends the signal, `clearAction`; the second is the signal, `triggered()`; the third is the object that receives it, `textArea`; and the last is the slot that is called, `clear()`. Read it as "when this signal fires, run that slot".

Qt's documentation on [signals and slots](https://doc.qt.io/qt-6/signalsandslots.html) explains more. Signals and slots are essential in Qt applications; understanding them is highly recommended.

### KStandardAction

For actions that appear in almost every application, such as Quit, Save and Open, [KStandardAction](/docs/api/kconfigwidgets/kstandardaction) (from `sonic-frameworks-settings-ui`, the `ConfigWidgets` component) provides ready-made actions.

They are very simple to use. Include `<KStandardAction>`, then give it what the action should do and the action collection to add it to:

```c++
KStandardAction::quit(qApp, &QCoreApplication::quit, actionCollection());
```

This calls [QCoreApplication::quit()](https://doc.qt.io/qt-6/qcoreapplication.html#quit) when the action is triggered. `qApp` is a pointer to the application object created in `main()`.

The result is an action with the right icon, text and shortcut, which is even added to the File menu automatically.

### Adding the action to menus and toolbars

The "Clear" action exists now, but isn't in any menu or toolbar yet. We use KXmlGui for that, which also makes toolbars movable for you.

### Your own help menu

The Help menu is standardized to make life easier for developers and users. To make your own, see "Using your own about-application dialog box" in the [KHelpMenu](/docs/api/kxmlgui/khelpmenu) documentation.

### XMLGUI

`setupGUI()` of [KXmlGuiWindow](/docs/api/kxmlgui/kxmlguiwindow) builds the user interface with the [KXmlGui](/docs/api/kxmlgui/kxmlgui-index) system, from an XML description of the interface.

The XML file is named `appnameui.rc`, where `appname` is the component name set in [KAboutData](/docs/api/kcoreaddons/kaboutdata), here `texteditor`. So our file is `texteditorui.rc`, in the same folder as the other files. Where it is installed is up to CMake.

#### appnameui.rc files

The interface is described in XML, so the file must follow strict rules. This tutorial doesn't go into depth.

#### texteditorui.rc

```xml
<?xml version="1.0" encoding="UTF-8"?>
<gui name="texteditor"
     version="1"
     xmlns="https://www.kde.org/standards/kxmlgui/1.0"
     xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
     xsi:schemaLocation="https://www.kde.org/standards/kxmlgui/1.0
                         https://www.kde.org/standards/kxmlgui/1.0/kxmlgui.xsd">
  <MenuBar>
    <Menu name="file" >
      <Action name="clear" />
    </Menu>
    <Menu >
      <text>A&amp;nother Menu</text>
      <Action name="clear" />
    </Menu>
  </MenuBar>

  <ToolBar name="mainToolBar" >
    <text>Main Toolbar</text>
    <Action name="clear" />
  </ToolBar>
</gui>
```

The `<ToolBar>` tag describes a toolbar, the bar of icons usually at the top of the window. This one has the unique name `mainToolBar` and, with `<text>`, the name "Main Toolbar" shown to users. The `<Action>` tag adds the `clear` action; its `name` is the name given to the action collection with `KActionCollection::addAction()` in `mainwindow.cpp`.

The action can also be in the menu bar: here it is added to the `File` menu of the `MenuBar` the same way, and to a second menu.

If you change the `.rc` file after installing it, increase the `version` attribute of the `<gui>` tag, so the user's saved copy is updated. It must be an integer: a decimal value doesn't work, and you get no warning.

> **Warning:** The version attribute must always be an integer.

How the code and the `.rc` file work together: menus are created automatically and should have a `<text>` child unless they are standard menus. Actions must be created in code and added to `actionCollection()` with the same name as in the `.rc` file. Actions can be hidden or disabled; menus can't.

## CMake

Finally, `texteditorui.rc` must be installed where it can be found; it can't stay in the source folder. **So the project now has to be installed**, unlike in the previous steps.

### CMakeLists.txt

```cmake
cmake_minimum_required(VERSION 3.20)

project(texteditor)

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
    Widgets # QApplication, QAction
)

find_package(KF6 ${KF_MIN_VERSION} REQUIRED COMPONENTS
    CoreAddons      # KAboutData
    I18n            # KLocalizedString
    XmlGui          # KXmlGuiWindow, KActionCollection
    TextWidgets     # KTextEdit
    ConfigWidgets   # KStandardActions
)

add_executable(texteditor)

target_sources(texteditor
    PRIVATE
    main.cpp
    mainwindow.cpp
)

target_link_libraries(texteditor
    Qt6::Widgets
    KF6::CoreAddons
    KF6::I18n
    KF6::XmlGui
    KF6::TextWidgets
    KF6::ConfigWidgets
)

install(TARGETS texteditor ${KDE_INSTALL_TARGETS_DEFAULT_ARGS})
install(FILES texteditorui.rc DESTINATION ${KDE_INSTALL_KXMLGUIDIR}/texteditor)
```

This is almost the same as the [previous](main-window.md#cmakeliststxt) file, plus the `ConfigWidgets` framework for KStandardAction and two lines at the end that say where to install: the `texteditor` program goes where programs go (`${KDE_INSTALL_TARGETS_DEFAULT_ARGS}`), and `texteditorui.rc` into the component's folder in `${KDE_INSTALL_KXMLGUIDIR}`.

## Running the application

Build and install it as in [Hello World](hello-world.md#building-and-running), then run:

```bash
texteditor
```

In Hello World we installed with `--install-prefix`:

```bash
cmake -B build/ --install-prefix ~/.local
cmake --build build/ --parallel
cmake --install build/
```

That creates a `/usr`-like layout in `~/.local`: the program goes to `~/.local/bin/texteditor` and the `.rc` file to `~/.local/share/kxmlgui5/texteditor/texteditorui.rc` (`KDE_INSTALL_KXMLGUIDIR` is the `kxmlgui5` data folder).

Next: [Saving and loading](saving-and-loading.md).
