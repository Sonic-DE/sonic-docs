---
title: "KToolBar Class"
description: "Floatable toolbar with auto resize."
---

# KToolBar Class

Floatable toolbar with auto resize. [More...](#details)

- **Header:** `#include <KToolBar>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS XmlGui)`  
  `target_link_libraries(mytarget PRIVATE KF6::XmlGui)`
- **Inherits:** [QToolBar](https://doc.qt.io/qt-6/qtoolbar.html)

[List of all members, including inherited members](ktoolbar-members.md)

## Public Functions

- [KToolBar(QWidget \*parent, bool isMainToolBar = false, bool readConfig = true)](#KToolBar)
- [KToolBar(const QString &objectName, QWidget \*parent, bool readConfig = true)](#KToolBar-1)
- [KToolBar(const QString &objectName, QMainWindow \*parentWindow, Qt::ToolBarArea area, bool newLine = false, bool isMainToolBar = false, bool readConfig = true)](#KToolBar-2)
- [~KToolBar()](#dtor.KToolBar)
- [void addXMLGUIClient(KXMLGUIClient \*client)](#addXMLGUIClient)
- [void applySettings(const KConfigGroup &cg)](#applySettings)
- [bool eventFilter(QObject \*watched, QEvent \*event)](#eventFilter)
- [int iconSizeDefault() const](#iconSizeDefault)
- [void loadState(const QDomElement &element)](#loadState)
- [KMainWindow \*mainWindow() const](#mainWindow)
- [void removeXMLGUIClient(KXMLGUIClient \*client)](#removeXMLGUIClient)
- [void saveSettings(KConfigGroup &cg)](#saveSettings)
- [void saveState(QDomElement &element) const](#saveState)
- [void setIconDimensions(int size)](#setIconDimensions)

## Static Public Members

- [void emitToolbarStyleChanged()](#emitToolbarStyleChanged)
- [void setToolBarsEditable(bool editable)](#setToolBarsEditable)
- [void setToolBarsLocked(bool locked)](#setToolBarsLocked)
- [bool toolBarsEditable()](#toolBarsEditable)
- [bool toolBarsLocked()](#toolBarsLocked)

## Detailed Description {#details}

A KDE-style toolbar.

[KToolBar](ktoolbar.md) can be used as a standalone widget, but [KMainWindow](kmainwindow.md) provides easy factories and management of one or more toolbars.

[KToolBar](ktoolbar.md) uses a global config group to load toolbar settings on construction. It will reread this config group on a KApplication::appearanceChanged() signal.

[KToolBar](ktoolbar.md) respects Kiosk settings (see the [KAuthorized](../kconfigcore/kauthorized.md) namespace in the [KConfig](../kconfigcore/kconfig.md) framework). In particular, system administrators can prevent users from moving toolbars with the "movable\_toolbars" action, and from showing or hiding toolbars with the "options\_show\_toolbar" action. For example, to disable both, add the following the application or global configuration:

```cpp
[KDE Action Restrictions][$i]
movable_toolbars=false
options_show_toolbar=false
```

If you can't depend on [KXmlGui](kxmlgui-module.md) but still want to integrate better with KDE, you can use [QToolBar](https://doc.qt.io/qt-6/qtoolbar.html) and:

- Set ToolButtonStyle to [Qt::ToolButtonFollowStyle](https://doc.qt.io/qt-6/qt.html#ToolButtonStyle-enum), this will make [QToolBar](https://doc.qt.io/qt-6/qtoolbar.html) use the settings for "Main Toolbar".
- Additionally set QToolBar::setProperty("otherToolbar", true) to use settings for "Other toolbars"; settings from "Other toolbars" will only work on widget styles derived from KStyle.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KToolBar::KToolBar(QWidget \**parent*, bool *isMainToolBar* = false, bool *readConfig* = true) {#KToolBar}

Constructor.

This constructor takes care of adding the toolbar to the mainwindow, if `parent` is a [QMainWindow](https://doc.qt.io/qt-6/qmainwindow.html).

Normally KDE applications do not call this directly, they either call [KMainWindow::toolBar](kmainwindow.md#toolBar)(), or they use XML-GUI and specify toolbars using XML.

`parent` The standard toolbar parent (usually a [KMainWindow](kmainwindow.md)).

`isMainToolBar` True for the "main toolbar", false for other toolbars. Different settings apply.

`readConfig` Whether to apply the configuration (global and application-specific)

### \[explicit\] KToolBar::KToolBar(const QString &*objectName*, QWidget \**parent*, bool *readConfig* = true) {#KToolBar-1}

Constructor.

This constructor takes care of adding the toolbar to the mainwindow, if `parent` is a [QMainWindow](https://doc.qt.io/qt-6/qmainwindow.html).

Normally KDE applications do not call this directly, they either call [KMainWindow::toolBar](kmainwindow.md#toolBar)(), or they use XML-GUI and specify toolbars using XML.

`objectName` The [QObject](https://doc.qt.io/qt-6/qobject.html) name of this toolbar, required so that [QMainWindow](https://doc.qt.io/qt-6/qmainwindow.html) can save and load the toolbar position, and so that [KToolBar](ktoolbar.md) can find out if it's the main toolbar.

`parent` The standard toolbar parent (usually a [KMainWindow](kmainwindow.md)).

`readConfig` Whether to apply the configuration (global and application-specific).

### KToolBar::KToolBar(const QString &*objectName*, QMainWindow \**parentWindow*, Qt::ToolBarArea *area*, bool *newLine* = false, bool *isMainToolBar* = false, bool *readConfig* = true) {#KToolBar-2}

Alternate constructor with additional arguments, e.g. to choose in which area the toolbar should be auto-added. This is rarely used in KDE. When using XMLGUI you can specify this as an xml attribute instead.

`objectName` The [QObject](https://doc.qt.io/qt-6/qobject.html) name of this toolbar, required so that [QMainWindow](https://doc.qt.io/qt-6/qmainwindow.html) can save and load the toolbar position.

`parentWindow` The window that should be the parent of this toolbar.

`area` The position of the toolbar. Usually [Qt::TopToolBarArea](https://doc.qt.io/qt-6/qt.html#ToolBarArea-enum).

`newLine` If true, start a new line in the dock for this toolbar.

`isMainToolBar` True for the "main toolbar", false for other toolbars. Different settings apply. `readConfig` whether to apply the configuration (global and application-specific)

### \[override virtual noexcept\] KToolBar::~KToolBar() {#dtor.KToolBar}

Destroys the toolbar.

### void KToolBar::addXMLGUIClient(KXMLGUIClient \**client*) {#addXMLGUIClient}

Adds an XML gui `client` that uses this toolbar.

### void KToolBar::applySettings(const KConfigGroup &*cg*) {#applySettings}

Read the toolbar settings from group `cg` and apply them.

### \[static\] void KToolBar::emitToolbarStyleChanged() {#emitToolbarStyleChanged}

Emits a D-Bus signal to tell all toolbars in all applications that the user settings have changed.

### \[override virtual\] bool KToolBar::eventFilter(QObject \**watched*, QEvent \**event*) {#eventFilter}

Reimplements: [QObject::eventFilter(QObject \*watched, QEvent \*event)](https://doc.qt.io/qt-6/qobject.html#eventFilter).

Filters then returns the specified `event` for a given `watched` object.

Reimplemented to support context menu activation on disabled tool buttons.

### int KToolBar::iconSizeDefault() const {#iconSizeDefault}

Returns the default size for this type of toolbar.

### void KToolBar::loadState(const QDomElement &*element*) {#loadState}

Load state from an XML `element`, called by [KXMLGUIBuilder](kxmlguibuilder.md).

### KMainWindow \*KToolBar::mainWindow() const {#mainWindow}

Returns the main window that this toolbar is docked with.

### void KToolBar::removeXMLGUIClient(KXMLGUIClient \**client*) {#removeXMLGUIClient}

Removes an XML gui `client` that uses this toolbar.

### void KToolBar::saveSettings(KConfigGroup &*cg*) {#saveSettings}

Save the toolbar settings to group `cg`.

### void KToolBar::saveState(QDomElement &*element*) const {#saveState}

Save state into an XML `element`, called by [KXMLGUIBuilder](kxmlguibuilder.md).

### void KToolBar::setIconDimensions(int *size*) {#setIconDimensions}

Convenience function to set icon `size`.

### \[static\] void KToolBar::setToolBarsEditable(bool *editable*) {#setToolBarsEditable}

Makes all toolbars `editable` via drag & drop of actions.

This is called by [KEditToolBar](kedittoolbar.md) and should generally be set to disabled whenever [KEditToolBar](kedittoolbar.md) is not active.

*See also* [toolBarsEditable](ktoolbar.md#toolBarsEditable)()

### \[static\] void KToolBar::setToolBarsLocked(bool *locked*) {#setToolBarsLocked}

Makes all toolbars `locked` (that is, disallow/allow moving of the toolbars).

*See also* [toolBarsLocked](ktoolbar.md#toolBarsLocked)()

### \[static\] bool KToolBar::toolBarsEditable() {#toolBarsEditable}

Returns whether the toolbars are currently editable (drag & drop of actions).

*See also* [setToolBarsEditable](ktoolbar.md#setToolBarsEditable)()

### \[static\] bool KToolBar::toolBarsLocked() {#toolBarsLocked}

Returns whether the toolbars are locked (that is, disallow moving of the toolbars).

*See also* [setToolBarsLocked](ktoolbar.md#setToolBarsLocked)()
