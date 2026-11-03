---
title: "KXmlGuiWindow Class"
description: "KMainWindow with convenience functions and integration with XmlGui files."
---

# KXmlGuiWindow Class

[KMainWindow](kmainwindow.md) with convenience functions and integration with XmlGui files. [More...](#details)

- **Header:** `#include <KXmlGuiWindow>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS XmlGui)`  
  `target_link_libraries(mytarget PRIVATE KF6::XmlGui)`
- **Inherits:** [KMainWindow](kmainwindow.md), [KXMLGUIBuilder](kxmlguibuilder.md), and [KXMLGUIClient](kxmlguiclient.md)

[List of all members, including inherited members](kxmlguiwindow-members.md)

## Public Types

- [enum KXmlGuiWindow::StandardWindowOption](#StandardWindowOption-enum)

## Properties

- [\[read-only\] autoSaveGroup : QString](#autoSaveGroup-prop)
- [\[read-only\] autoSaveSettings : bool](#autoSaveSettings-prop)
- [\[read-only\] hasMenuBar : bool](#hasMenuBar-prop)
- [standardToolBarMenuEnabled : bool](#standardToolBarMenuEnabled-prop)

## Public Functions

- [KXmlGuiWindow(QWidget \*parent = nullptr, Qt::WindowFlags flags = WindowFlags())](#KXmlGuiWindow)
- [~KXmlGuiWindow()](#dtor.KXmlGuiWindow)
- [void createGUI(const QString &xmlfile = QString())](#createGUI)
- [void createStandardStatusBarAction()](#createStandardStatusBarAction)
- [void finalizeGUI(bool force)](#finalizeGUI)
- [KXMLGUIFactory \*guiFactory()](#guiFactory)
- [bool isCommandBarEnabled() const](#isCommandBarEnabled)
- [bool isHelpMenuEnabled() const](#isHelpMenuEnabled)
- [bool isStandardToolBarMenuEnabled() const](#isStandardToolBarMenuEnabled)
- [void setCommandBarEnabled(bool showCommandBar)](#setCommandBarEnabled)
- [void setHelpMenuEnabled(bool showHelpMenu = true)](#setHelpMenuEnabled)
- [void setStandardToolBarMenuEnabled(bool showToolBarMenu)](#setStandardToolBarMenuEnabled)
- [void setupGUI(KXmlGuiWindow::StandardWindowOptions options = Default, const QString &xmlfile = QString())](#setupGUI)
- [void setupGUI(const QSize &defaultSize, KXmlGuiWindow::StandardWindowOptions options = Default, const QString &xmlfile = QString())](#setupGUI-1)
- [QAction \*toolBarMenuAction()](#toolBarMenuAction)
- [QStringList toolBarNames() const](#toolBarNames) (since 6.10)

## Public Slots

- [void configureToolbars()](#configureToolbars)
- [bool isToolBarVisible(const QString &name)](#isToolBarVisible) (since 6.10)
- [void saveNewToolbarConfig()](#saveNewToolbarConfig)
- [void setToolBarVisible(const QString &name, bool visible)](#setToolBarVisible) (since 6.10)
- [void slotStateChanged(const QString &newstate)](#slotStateChanged)
- [void slotStateChanged(const QString &newstate, bool reverse)](#slotStateChanged-1)

## Protected Functions

- [void checkAmbiguousShortcuts()](#checkAmbiguousShortcuts)
- [bool event(QEvent \*event)](#event)

## Detailed Description {#details}

This class includes several convenience `<action>Enabled()` functions to toggle the presence of functionality in your main window, including a [KCommandBar](../kconfigwidgets/kcommandbar.md) instance.

The [StandardWindowOptions](kxmlguiwindow.md#StandardWindowOption-enum) enum can be used to pass additional options to describe the main window behavior/appearance. Use it in conjunction with [setupGUI](kxmlguiwindow.md#setupGUI)() to load an appnameui.rc file to manage the main window's actions.

[setCommandBarEnabled](kxmlguiwindow.md#setCommandBarEnabled)() is set by default.

A minimal example can be created with [QMainWindow::setCentralWidget](https://doc.qt.io/qt-6/qmainwindow.html#setCentralWidget)() and [setupGUI](kxmlguiwindow.md#setupGUI)():

```cpp
MainWindow::MainWindow(QWidget *parent) : KXmlGuiWindow(parent) {
  textArea = new KTextEdit();
  setCentralWidget(textArea);
  setupGUI(Default);
}
```

With this, a ready-made main window with menubar and statusbar is created, as well as two default menus, Settings and Help.

Management of QActions is made trivial in combination with [KActionCollection](kactioncollection.md) and [KStandardAction](../kconfigwidgets/kstandardaction.md).

```cpp
void MainWindow::setupActions() {
  QAction *clearAction = new QAction(this);
  clearAction->setText(i18n("&Clear"));
  clearAction->setIcon(QIcon::fromTheme("document-new"));
  KActionCollection::setDefaultShortcut(clearAction, Qt::CTRL + Qt::Key_W);
  actionCollection()->addAction("clear", clearAction);
  connect(clearAction, &QAction::triggered, textArea, &KTextEdit::clear);
  KStandardAction::quit(qApp, &QCoreApplication::quit, actionCollection());
  setupGUI(Default, "texteditorui.rc");
}
```

See https://develop.kde.org/docs/use/kxmlgui/ for a tutorial on how to create a simple text editor using [KXmlGuiWindow](kxmlguiwindow.md).

See https://develop.kde.org/docs/use/session-managment for more information on session management.

*See also* [KMainWindow](kmainwindow.md), [KActionCollection](kactioncollection.md), [KStandardAction](../kconfigwidgets/kstandardaction.md), [setupGUI](kxmlguiwindow.md#setupGUI)(), [createGUI](kxmlguiwindow.md#createGUI)(), [setCommandBarEnabled](kxmlguiwindow.md#setCommandBarEnabled)()

## Member Type Documentation {#member-type-documentation}

### enum KXmlGuiWindow::StandardWindowOption {#StandardWindowOption-enum}

**flags KXmlGuiWindow::StandardWindowOptions**

Use these options for the first argument of [setupGUI](kxmlguiwindow.md#setupGUI)().

| Constant | Value | Description |
| --- | --- | --- |
| `KXmlGuiWindow::ToolBar` | `1` | Adds action(s) to show/hide the toolbar(s) and adds a menu action to configure the toolbar(s). |
| `KXmlGuiWindow::Keys` | `2` | Adds an action in the 'Settings' menu to open the configure keyboard shortcuts dialog. |
| `KXmlGuiWindow::StatusBar` | `4` | Adds an action to show/hide the statusbar in the 'Settings' menu. Note that setting this value will create a statusbar if one doesn't already exist. |
| `KXmlGuiWindow::Save` | `8` | Autosaves (and loads) the toolbar/menubar/statusbar settings and window size using the default name. Like [KMainWindow::setAutoSaveSettings](kmainwindow.md#setAutoSaveSettings)(), enabling this causes the application to save state data upon close in a [KConfig](../kconfigcore/kconfig.md)-managed configuration file. Typically you want to let the default window size be determined by the widgets' size hints. Make sure that [setupGUI](kxmlguiwindow.md#setupGUI)() is called after all the widgets are created (including [QMainWindow::setCentralWidget](https://doc.qt.io/qt-6/qmainwindow.html#setCentralWidget)()) so that the default size is managed properly. |
| `KXmlGuiWindow::Create` | `16` | Calls [createGUI](kxmlguiwindow.md#createGUI)() once ToolBar, Keys and Statusbar have been taken care of. |
| `KXmlGuiWindow::Default` | `ToolBar | Keys | StatusBar | Save | Create` | Sets all of the above options as true. > **Note:** In the case of KXmlGuiWindow::Create, when using KParts::MainWindow, remove this flag from the [setupGUI](kxmlguiwindow.md#setupGUI)() call, since you'll be using [createGUI](kxmlguiwindow.md#createGUI)(part) instead: ```cpp setupGUI(ToolBar | Keys | StatusBar | Save); ``` |

The `StandardWindowOptions` type is a typedef for `QFlags<StandardWindowOption>. `It stores an OR combination of `StandardWindowOption` values.

*See also* [setupGUI](kxmlguiwindow.md#setupGUI)(), [setStandardToolBarMenuEnabled](kxmlguiwindow.md#setStandardToolBarMenuEnabled)(), [isStandardToolBarMenuEnabled](kxmlguiwindow.md#isStandardToolBarMenuEnabled)(), [createStandardStatusBarAction](kxmlguiwindow.md#createStandardStatusBarAction)(), [KMainWindow::setAutoSaveSettings](kmainwindow.md#setAutoSaveSettings)(), [KConfig](../kconfigcore/kconfig-index.md), [createGUI](kxmlguiwindow.md#createGUI)()

## Property Documentation {#property-documentation}

### \[read-only\] autoSaveGroup : QString {#autoSaveGroup-prop}

**Access functions:**

- `QString` **[autoSaveGroup](kmainwindow.md#autoSaveGroup)**() const

### \[read-only\] autoSaveSettings : bool {#autoSaveSettings-prop}

**Access functions:**

- `bool` **[autoSaveSettings](kmainwindow.md#autoSaveSettings)**() const

### \[read-only\] hasMenuBar : bool {#hasMenuBar-prop}

**Access functions:**

- `bool` **[hasMenuBar](kmainwindow.md#hasMenuBar)**()

### standardToolBarMenuEnabled : bool {#standardToolBarMenuEnabled-prop}

**Access functions:**

- `bool` **[isStandardToolBarMenuEnabled](kxmlguiwindow.md#isStandardToolBarMenuEnabled)**() const
- `void` **[setStandardToolBarMenuEnabled](kxmlguiwindow.md#setStandardToolBarMenuEnabled)**(`bool` *showToolBarMenu*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KXmlGuiWindow::KXmlGuiWindow(QWidget \**parent* = nullptr, Qt::WindowFlags *flags* = Qt::WindowFlags()) {#KXmlGuiWindow}

Construct a main window.

Note that by default a [KXmlGuiWindow](kxmlguiwindow.md) is created with the [Qt::WA\_DeleteOnClose](https://doc.qt.io/qt-6/qt.html#WidgetAttribute-enum) attribute set, i.e. it is automatically destroyed when the window is closed. If you do not want this behavior, call:

```cpp
window->setAttribute(Qt::WA_DeleteOnClose, false);
```

KXmlGuiWindows must be created on the heap with 'new', like:

```cpp
KXmlGuiWindow *kmw = new KXmlGuiWindow(...);
kmw->setObjectName(...);
```

> **Note:** For session management and window management to work properly, all main windows in the application should have a different name. Otherwise, the base class [KMainWindow](kmainwindow.md) will create a unique name, but it's recommended to explicitly pass a window name that will also describe the type of the window. If there can be several windows of the same type, append '\#' (hash) to the name, and [KMainWindow](kmainwindow.md) will replace it with numbers to make the names unique. For example, for a mail client which has one main window showing the mails and folders, and which can also have one or more windows for composing mails, the name for the folders window should be e.g. "mainwindow" and for the composer windows "composer\#".

`parent` The widget parent. This is usually `nullptr`, but it may also be the window group leader. In that case, the [KXmlGuiWindow](kxmlguiwindow.md) becomes a secondary window.

`flags` Specify the window flags. The default is none.

*See also* [KMainWindow::KMainWindow](kmainwindow.md)

### \[override virtual noexcept\] KXmlGuiWindow::~KXmlGuiWindow() {#dtor.KXmlGuiWindow}

Destructor.

Will also destroy the toolbars and menubar if needed.

### \[protected\] void KXmlGuiWindow::checkAmbiguousShortcuts() {#checkAmbiguousShortcuts}

Checks if there are actions using the same shortcut.

This is called automatically from [createGUI](kxmlguiwindow.md#createGUI)().

### \[virtual slot\] void KXmlGuiWindow::configureToolbars() {#configureToolbars}

Show a standard configure toolbar dialog.

This slot can be connected directly to the action to configure the toolbar.

Example code:

```cpp
KStandardAction::configureToolbars(this, &KXmlGuiWindow::configureToolbars, actionCollection);
```

### void KXmlGuiWindow::createGUI(const QString &*xmlfile* = QString()) {#createGUI}

Generates the interface based on a local XML file.

This is the function that generates UI elements such as the main menu, toolbar (if any) and statusbar. This is called by [setupGUI](kxmlguiwindow.md#setupGUI)(Create) as well.

Typically, in a regular application, you would use [setupGUI](kxmlguiwindow.md#setupGUI)() instead, as it sets up the toolbar/shortcut edit actions, among other things.

If `xmlfile` is an empty string, this method will try to construct a local XML filename like appnameui.rc where 'appname' is your app's name. Typically that app name is what [KXMLGUIClient::componentName](kxmlguiclient.md#componentName)() returns. If that file does not exist, then the XML UI code will use only the global (standard) XML file for its layout purposes.

`xmlfile` The path (relative or absolute) to the local xmlfile.

*See also* [setupGUI](kxmlguiwindow.md#setupGUI)()

### void KXmlGuiWindow::createStandardStatusBarAction() {#createStandardStatusBarAction}

Creates a toggle under the 'Settings' menu to show/hide the statusbar.

Calling this method will create a statusbar if one doesn't already exist.

If an application maintains the action on its own (i.e. never calls this function), a connection needs to be made to let [KMainWindow](kmainwindow.md) know when the hidden/shown status of the statusbar has changed. For example:

```cpp
connect(action, &QAction::triggered,
        kmainwindow, &KMainWindow::setSettingsDirty);
```

Otherwise the status might not be saved by [KMainWindow](kmainwindow.md).

> **Note:** This function only makes sense before calling [createGUI](kxmlguiwindow.md#createGUI)() or when using [setupGUI](kxmlguiwindow.md#setupGUI)() without [StandardWindowOption::StatusBar](kxmlguiwindow.md#StandardWindowOption-enum).

*See also* [createGUI](kxmlguiwindow.md#createGUI)(), [setupGUI](kxmlguiwindow.md#setupGUI)(), [StandardWindowOption](kxmlguiwindow.md#StandardWindowOption-enum), [KStandardAction::showStatusbar](../kconfigwidgets/kstandardaction.md#showStatusbar)(), [setStandardToolBarMenuEnabled](kxmlguiwindow.md#setStandardToolBarMenuEnabled)(), [QMainWindow::setStatusBar](https://doc.qt.io/qt-6/qmainwindow.html#setStatusBar)(), [QMainWindow::statusBar](https://doc.qt.io/qt-6/qmainwindow.html#statusBar)()

### \[override virtual protected\] bool KXmlGuiWindow::event(QEvent \**event*) {#event}

Reimplements: [KMainWindow::event(QEvent \*event)](kmainwindow.md#event).

Reimplemented to return the `event` [QEvent::Polish](https://doc.qt.io/qt-6/qevent.html#Type-enum) in order to adjust the object name if needed, once all constructor code for the main window has run.

Also reimplemented to catch when a [QDockWidget](https://doc.qt.io/qt-6/qdockwidget.html) is added or removed.

### void KXmlGuiWindow::finalizeGUI(bool *force*) {#finalizeGUI}

### \[virtual\] KXMLGUIFactory \*KXmlGuiWindow::guiFactory() {#guiFactory}

### bool KXmlGuiWindow::isCommandBarEnabled() const {#isCommandBarEnabled}

Whether a [KCommandBar](../kconfigwidgets/kcommandbar.md) was set.

Returns `true` by default, `false` if [setCommandBarEnabled](kxmlguiwindow.md#setCommandBarEnabled)(false) was set.

*See also* [setCommandBarEnabled](kxmlguiwindow.md#setCommandBarEnabled)()

### bool KXmlGuiWindow::isHelpMenuEnabled() const {#isHelpMenuEnabled}

Returns `true` if the help menu is enabled, `false` if [setHelpMenuEnabled](kxmlguiwindow.md#setHelpMenuEnabled)(false) was set.

*See also* [setHelpMenuEnabled](kxmlguiwindow.md#setHelpMenuEnabled)()

### bool KXmlGuiWindow::isStandardToolBarMenuEnabled() const {#isStandardToolBarMenuEnabled}

Returns whether [setStandardToolBarMenuEnabled](kxmlguiwindow.md#setStandardToolBarMenuEnabled)() was set.

> **Note:** This function only makes sense if [createGUI](kxmlguiwindow.md#createGUI)() was used. This function returns true only if [setStandardToolBarMenuEnabled](kxmlguiwindow.md#setStandardToolBarMenuEnabled)() was set and will return false even if [StandardWindowOption::ToolBar](kxmlguiwindow.md#StandardWindowOption-enum) was used.

Returns `true` if [setStandardToolBarMenuEnabled](kxmlguiwindow.md#setStandardToolBarMenuEnabled)() was set, `false` otherwise.

> **Note:** Getter function for property [standardToolBarMenuEnabled](kxmlguiwindow.md#standardToolBarMenuEnabled-prop).

*See also* [createGUI](kxmlguiwindow.md#createGUI)(), [setupGUI](kxmlguiwindow.md#setupGUI)(), [setStandardToolBarMenuEnabled](kxmlguiwindow.md#setStandardToolBarMenuEnabled)(), [StandardWindowOption](kxmlguiwindow.md#StandardWindowOption-enum)

### \[slot, since 6.10\] bool KXmlGuiWindow::isToolBarVisible(const QString &*name*) {#isToolBarVisible}

Checks the visual state of a given toolbar. If an invalid name is given, the method will always return false.

This does not utilize [KMainWindow::toolBar](kmainwindow.md#toolBar)(), as that method would create a new toolbar in the case of an invalid name, which is not something that should be freely accessable via the dbus.

`name` The internal name of the toolbar.

Returns whether the toolbar with the specified name is currently visible

This function was introduced in Qt 6.10.

*See also* [toolBarNames](kxmlguiwindow.md#toolBarNames)(), [setToolBarVisible](kxmlguiwindow.md#setToolBarVisible)(), [KMainWindow::toolBar](kmainwindow.md#toolBar)()

### \[virtual protected slot\] void KXmlGuiWindow::saveNewToolbarConfig() {#saveNewToolbarConfig}

Completes the rebuild of the GUI after [KEditToolBar](kedittoolbar.md) changed the toolbar layout. The default implementation invokes [applyMainWindowSettings](kmainwindow.md#applyMainWindowSettings)(). Reimplement this method in your subclass when other actions need to be plugged in manually again.

*See also* [configureToolbars](kxmlguiwindow.md#configureToolbars)(), [KEditToolBar::newToolBarConfig](kedittoolbar.md#newToolBarConfig)()

### void KXmlGuiWindow::setCommandBarEnabled(bool *showCommandBar*) {#setCommandBarEnabled}

Enable a [KCommandBar](../kconfigwidgets/kcommandbar.md) to list and quickly execute actions.

A [KXmlGuiWindow](kxmlguiwindow.md) by default automatically creates a [KCommandBar](../kconfigwidgets/kcommandbar.md), but it is inaccessible unless [createGUI](kxmlguiwindow.md#createGUI)() or [setupGUI](kxmlguiwindow.md#setupGUI)(Create) is used.

It provides a HUD-like menu that lists all QActions in your application and can be activated via Ctrl+Atl+i or via an action in the 'Help' menu.

If you need more than a global set of QActions listed for your application, use [KCommandBar](../kconfigwidgets/kcommandbar.md) directly instead.

`showCommandBar` Whether to show the command bar. `true` by default.

*See also* [KCommandBar](../kconfigwidgets/kcommandbar.md), [KCommandBar::setActions](../kconfigwidgets/kcommandbar.md#setActions)(), [isCommandBarEnabled](kxmlguiwindow.md#isCommandBarEnabled)()

### void KXmlGuiWindow::setHelpMenuEnabled(bool *showHelpMenu* = true) {#setHelpMenuEnabled}

Creates a standard help menu when calling [createGUI](kxmlguiwindow.md#createGUI)() or [setupGUI](kxmlguiwindow.md#setupGUI)().

`showHelpMenu` Whether to create a Help Menu. `true` by default.

*See also* [isHelpMenuEnabled](kxmlguiwindow.md#isHelpMenuEnabled)()

### void KXmlGuiWindow::setStandardToolBarMenuEnabled(bool *showToolBarMenu*) {#setStandardToolBarMenuEnabled}

Creates a toggle under the 'Settings' menu to show/hide the available toolbars.

The standard toolbar menu toggles the visibility of one or multiple toolbars.

If there is only one toolbar configured, a simple 'Show \<toolbar name\>' menu item is shown; if more than one toolbar is configured, a "Shown Toolbars" menu is created instead, with 'Show \<toolbar1 name\>', 'Show \<toolbar2 name\>' ... sub-menu actions.

If your application uses a non-default XmlGui resource file, then you can specify the exact position of the menu/menu item by adding a `<Merge` name="StandardToolBarMenuHandler"\> line to the settings menu section of your resource file ( usually appname.rc ).

`showToolBarMenu` Whether to show the standard toolbar menu. `false` by default.

> **Note:** This function only makes sense before calling [createGUI](kxmlguiwindow.md#createGUI)(). Using [setupGUI](kxmlguiwindow.md#setupGUI)([ToolBar](kxmlguiwindow.md#StandardWindowOption-enum)) overrides this function.

> **Note:** Setter function for property [standardToolBarMenuEnabled](kxmlguiwindow.md#standardToolBarMenuEnabled-prop).

*See also* [isStandardToolBarMenuEnabled](kxmlguiwindow.md#isStandardToolBarMenuEnabled)(), [createGUI](kxmlguiwindow.md#createGUI)(), [setupGUI](kxmlguiwindow.md#setupGUI)(), KToggleBarAction, [StandardWindowOption](kxmlguiwindow.md#StandardWindowOption-enum), [KMainWindow::toolBar](kmainwindow.md#toolBar)(), [KMainWindow::toolBars](kmainwindow.md#toolBars)(), [QMainWindow::addToolBar](https://doc.qt.io/qt-6/qmainwindow.html#addToolBar)(), [QMainWindow::removeToolBar](https://doc.qt.io/qt-6/qmainwindow.html#removeToolBar)(), [createStandardStatusBarAction](kxmlguiwindow.md#createStandardStatusBarAction)()

### \[slot, since 6.10\] void KXmlGuiWindow::setToolBarVisible(const QString &*name*, bool *visible*) {#setToolBarVisible}

Sets the visibility of a given toolbar. If an invalid name is given, nothing happens.

`name` The internal name of the toolbar.

`visible` The new state of the toolbar's visibility.

This function was introduced in Qt 6.10.

*See also* [isToolBarVisible](kxmlguiwindow.md#isToolBarVisible)()

### void KXmlGuiWindow::setupGUI(KXmlGuiWindow::StandardWindowOptions *options* = Default, const QString &*xmlfile* = QString()) {#setupGUI}

Configures the current window and its actions in the typical KDE fashion.

You can specify which window options/features are going to be set up using `options`, see the [StandardWindowOptions](kxmlguiwindow.md#StandardWindowOption-enum) enum for more details.

```cpp
MainWindow::MainWindow(QWidget* parent) : KXmlGuiWindow(parent){
  textArea = new KTextEdit();
  setCentralWidget(textArea);
  setupGUI(Default, "appnameui.rc");
}
```

Use a bitwise OR (\|) to select multiple enum choices for setupGUI() (except when using StandardWindowOptions::Default).

```cpp
setupGUI(Save | Create, "appnameui.rc");
```

Typically this function replaces [createGUI](kxmlguiwindow.md#createGUI)(), but it is possible to call setupGUI(Create) together with helper functions such as [setStandardToolBarMenuEnabled](kxmlguiwindow.md#setStandardToolBarMenuEnabled)() and [createStandardStatusBarAction](kxmlguiwindow.md#createStandardStatusBarAction)().

> **Warning:** To use [createGUI](kxmlguiwindow.md#createGUI)() and setupGUI() for the same window, you must avoid using [StandardWindowOption::Create](kxmlguiwindow.md#StandardWindowOption-enum). Prefer using only setupGUI().

> **Note:** When [StandardWindowOption::Save](kxmlguiwindow.md#StandardWindowOption-enum) is used, this method will restore the state of the application window (toolbar, dockwindows positions ...etc), so you need to have added all your actions to your UI before calling this method.

`options` A combination of [StandardWindowOptions](kxmlguiwindow.md#StandardWindowOption-enum) to specify UI elements to be present in your application window.

`xmlfile` The relative or absolute path to the local xmlfile. If this is an empty string, the code will look for a local XML file appnameui.rc, where 'appname' is the name of your app. See the note about the xmlfile argument in [createGUI](kxmlguiwindow.md#createGUI)().

*See also* [StandardWindowOption](kxmlguiwindow.md#StandardWindowOption-enum)

### void KXmlGuiWindow::setupGUI(const QSize &*defaultSize*, KXmlGuiWindow::StandardWindowOptions *options* = Default, const QString &*xmlfile* = QString()) {#setupGUI-1}

This is an overloaded function.

`defaultSize` A manually specified window size that overrides the saved size.

`options` A combination of [StandardWindowOptions](kxmlguiwindow.md#StandardWindowOption-enum) to specify UI elements to be present in your application window.

`xmlfile` The relative or absolute path to the local xmlfile.

*See also* [setupGUI](kxmlguiwindow.md#setupGUI)()

### \[virtual slot\] void KXmlGuiWindow::slotStateChanged(const QString &*newstate*) {#slotStateChanged}

Applies a state change

Reimplement this to enable and disable actions as defined in the XmlGui rc file.

`newstate` The state change to be applied.

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kXmlGuiWindow, qOverload<const QString &>(&KXmlGuiWindow::slotStateChanged));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kXmlGuiWindow, [receiver = kXmlGuiWindow](const QString &newstate) { receiver->slotStateChanged(newstate); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).

### \[slot\] void KXmlGuiWindow::slotStateChanged(const QString &*newstate*, bool *reverse*) {#slotStateChanged-1}

Applies a state change

Reimplement this to enable and disable actions as defined in the XmlGui rc file.

This function can "reverse" the state (disable the actions which should be enabled, and vice-versa) if specified.

`newstate` The state change to be applied.

`reverse` Whether to reverse `newstate` or not.

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kXmlGuiWindow, qOverload<const QString &, bool>(&KXmlGuiWindow::slotStateChanged));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kXmlGuiWindow, [receiver = kXmlGuiWindow](const QString &newstate, bool reverse) { receiver->slotStateChanged(newstate, reverse); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).

### QAction \*KXmlGuiWindow::toolBarMenuAction() {#toolBarMenuAction}

Returns a pointer to the main window's action responsible for the toolbar's menu.

### \[since 6.10\] QStringList KXmlGuiWindow::toolBarNames() const {#toolBarNames}

Returns a list of all toolbars for this window in string form

> **Note:** Getter function for property toolBars.

This function was introduced in Qt 6.10.

*See also* [KMainWindow::toolBars](kmainwindow.md#toolBars)()
