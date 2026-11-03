---
title: "KEditToolBar Class"
description: "A dialog used to customize or configure toolbars."
---

# KEditToolBar Class

A dialog used to customize or configure toolbars. [More...](#details)

- **Header:** `#include <KEditToolBar>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS XmlGui)`  
  `target_link_libraries(mytarget PRIVATE KF6::XmlGui)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](kedittoolbar-members.md)

## Public Functions

- [KEditToolBar(KActionCollection \*collection, QWidget \*parent = nullptr)](#KEditToolBar)
- [KEditToolBar(KXMLGUIFactory \*factory, QWidget \*parent = nullptr)](#KEditToolBar-1)
- [~KEditToolBar()](#dtor.KEditToolBar)
- [void setDefaultToolBar(const QString &toolBarName)](#setDefaultToolBar)
- [void setResourceFile(const QString &file, bool global = true)](#setResourceFile)

## Signals

- [void newToolBarConfig()](#newToolBarConfig)

## Static Public Members

- [void setGlobalDefaultToolBar(const QString &toolBarName)](#setGlobalDefaultToolBar) (since 6.0)

## Detailed Description {#details}

This dialog only works if your application uses the XML UI framework for creating menus and toolbars. It depends on the XML files to describe the toolbar layouts and it requires the actions to determine which buttons are active.

Typically you do not need to use it directly as [KXmlGuiWindow::setupGUI](kxmlguiwindow.md#setupGUI) takes care of it.

If you use [KXMLGUIClient::plugActionList](kxmlguiclient.md#plugActionList)() you need to overload [KXmlGuiWindow::saveNewToolbarConfig](kxmlguiwindow.md#saveNewToolbarConfig)() to plug actions again:

```cpp
void MyClass::saveNewToolbarConfig()
{
    KXmlGuiWindow::saveNewToolbarConfig();
    plugActionList( "list1", list1Actions );
    plugActionList( "list2", list2Actions );
}
```

When created, [KEditToolBar](kedittoolbar.md) takes a [KXMLGUIFactory](kxmlguifactory.md) object, and uses it to find all of the action collections and XML files (there is one of each for the mainwindow, but there could be more, when adding other XMLGUI clients like KParts or plugins). The editor aims to be semi-intelligent about where it assigns any modifications. In other words, it will not write out part specific changes to your application's main XML file.

[KXmlGuiWindow](kxmlguiwindow.md) and KParts::MainWindow take care of creating [KEditToolBar](kedittoolbar.md) correctly and connecting to its [newToolBarConfig](kedittoolbar.md#newToolBarConfig) slot, but if you really really want to do it yourself, see the [KXmlGuiWindow::configureToolbars](kxmlguiwindow.md#configureToolbars)() and [KXmlGuiWindow::saveNewToolbarConfig](kxmlguiwindow.md#saveNewToolbarConfig)() code.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KEditToolBar::KEditToolBar(KActionCollection \**collection*, QWidget \**parent* = nullptr) {#KEditToolBar}

Old constructor for apps that do not use components.

This constructor is somewhat deprecated, since it doesn't work with any KXMLGuiClient being added to the mainwindow. You really want to use the other constructor.

You **must** pass along your collection of actions (some of which appear in your toolbars).

`collection` The collection of actions to work on.

`parent` The parent of the dialog.

### \[explicit\] KEditToolBar::KEditToolBar(KXMLGUIFactory \**factory*, QWidget \**parent* = nullptr) {#KEditToolBar-1}

Main constructor.

The main parameter, `factory`, is a pointer to the XML GUI factory object for your application. It contains a list of all of the GUI clients (along with the action collections and xml files) and the toolbar editor uses that.

Use this like so:

```cpp
KEditToolBar edit(factory());
if (edit.exec())
// ...
```

`factory` Your application's factory object.

`parent` The usual parent for the dialog.

### \[override virtual noexcept\] KEditToolBar::~KEditToolBar() {#dtor.KEditToolBar}

Destructor.

### \[signal\] void KEditToolBar::newToolBarConfig() {#newToolBarConfig}

Emitted when 'Apply' or 'Ok' is clicked or toolbars were reset.

Connect to it to plug action lists and to call applyMainWindowSettings (see sample code in the documentation for this class).

### void KEditToolBar::setDefaultToolBar(const QString &*toolBarName*) {#setDefaultToolBar}

Sets `toolBarName` as the default toolbar that will be selected when the dialog is shown.

If not set, or QString() is passed in, the global default tool bar name will be used.

*See also* [setGlobalDefaultToolBar](kedittoolbar.md#setGlobalDefaultToolBar)

### \[static, since 6.0\] void KEditToolBar::setGlobalDefaultToolBar(const QString &*toolBarName*) {#setGlobalDefaultToolBar}

Sets `toolBarName` as the default toolbar which will be auto-selected for all [KEditToolBar](kedittoolbar.md) instances.

Can be overridden on a per-dialog basis by calling [setDefaultToolBar](kedittoolbar.md#setDefaultToolBar)( const [QString](https://doc.qt.io/qt-6/qstring.html)& ) on the dialog.

This function was introduced in Qt 6.0.

### void KEditToolBar::setResourceFile(const QString &*file*, bool *global* = true) {#setResourceFile}

Sets a new resource `file` and whether the global resource file should be used.

The name (absolute or relative) of your application's UI resource `file` is assumed to be share/apps/appname/appnameui.rc, but it can be overridden by calling this method.

The `global` parameter controls whether or not the global resource file is used. If this is `true`, then you may edit all of the actions in your toolbars – global ones and local one. If it is `false`, then you may edit only your application's entries. The only time you should set this to false is if your application does not use the global resource file at all (very rare).

`file` The application's local resource file.

`global` If `true`, then the global resource file will also be parsed.
