---
title: "KMainWindow Class"
description: "KMainWindow represents a top-level main window."
---

# KMainWindow Class

[KMainWindow](kmainwindow.md) represents a top-level main window. [More...](#details)

- **Header:** `#include <KMainWindow>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS XmlGui)`  
  `target_link_libraries(mytarget PRIVATE KF6::XmlGui)`
- **Inherits:** [QMainWindow](https://doc.qt.io/qt-6/qmainwindow.html)
- **Inherited By:** [KXmlGuiWindow](kxmlguiwindow.md)

[List of all members, including inherited members](kmainwindow-members.md)

## Properties

- [\[read-only\] autoSaveGroup : QString](#autoSaveGroup-prop)
- [\[read-only\] autoSaveSettings : bool](#autoSaveSettings-prop)
- [\[read-only\] hasMenuBar : bool](#hasMenuBar-prop)

## Public Functions

- [KMainWindow(QWidget \*parent = nullptr, Qt::WindowFlags flags = WindowFlags())](#KMainWindow)
- [~KMainWindow()](#dtor.KMainWindow)
- [void applyMainWindowSettings(const KConfigGroup &config)](#applyMainWindowSettings)
- [KConfigGroup autoSaveConfigGroup() const](#autoSaveConfigGroup)
- [QString autoSaveGroup() const](#autoSaveGroup)
- [bool autoSaveSettings() const](#autoSaveSettings)
- [QString dbusName() const](#dbusName)
- [bool hasMenuBar()](#hasMenuBar)
- [void resetAutoSaveSettings()](#resetAutoSaveSettings)
- [bool restore(int numberOfInstances, bool show = true)](#restore)
- [void saveMainWindowSettings(KConfigGroup &config)](#saveMainWindowSettings)
- [void setAutoSaveSettings(const QString &groupName = QStringLiteral("MainWindow"), bool saveWindowSize = true)](#setAutoSaveSettings)
- [void setAutoSaveSettings(const KConfigGroup &group, bool saveWindowSize = true)](#setAutoSaveSettings-1)
- [void setStateConfigGroup(const QString &configGroup)](#setStateConfigGroup)
- [KConfigGroup stateConfigGroup() const](#stateConfigGroup)
- [KToolBar \*toolBar(const QString &name = QString())](#toolBar)
- [QList\<KToolBar \*\> toolBars() const](#toolBars)

## Public Slots

- [void appHelpActivated()](#appHelpActivated)
- [void saveAutoSaveSettings()](#saveAutoSaveSettings)
- [void setCaption(const QString &caption)](#setCaption)
- [void setCaption(const QString &caption, bool modified)](#setCaption-1)
- [void setPlainCaption(const QString &caption)](#setPlainCaption)
- [void setSettingsDirty()](#setSettingsDirty)

## Static Public Members

- [bool canBeRestored(int numberOfInstances)](#canBeRestored)
- [const QString classNameOfToplevel(int instanceNumber)](#classNameOfToplevel)
- [QList\<KMainWindow \*\> memberList()](#memberList)

## Protected Functions

- [void closeEvent(QCloseEvent \*)](#closeEvent)
- [bool event(QEvent \*event)](#event)
- [void keyPressEvent(QKeyEvent \*keyEvent)](#keyPressEvent)
- [bool queryClose()](#queryClose)
- [void readGlobalProperties(KConfig \*sessionConfig)](#readGlobalProperties)
- [void readProperties(const KConfigGroup &)](#readProperties)
- [void saveGlobalProperties(KConfig \*sessionConfig)](#saveGlobalProperties)
- [void saveProperties(KConfigGroup &)](#saveProperties)
- [bool settingsDirty() const](#settingsDirty)

## Detailed Description {#details}

It extends [QMainWindow](https://doc.qt.io/qt-6/qmainwindow.html) with session management capabilities. For ready-made window functionality and simpler UI management, use [KXmlGuiWindow](kxmlguiwindow.md) instead.

Define the minimum/maximum height/width of your central widget and [KMainWindow](kmainwindow.md) will take this into account. For fixed size windows set your main widget to a fixed size. Fixed aspect ratios ([QWidget::heightForWidth](https://doc.qt.io/qt-6/qwidget.html#heightForWidth)()) and fixed width widgets are not supported.

Use [toolBar](kmainwindow.md#toolBar)() to generate a main toolbar "mainToolBar" or refer to a specific toolbar. For a simpler way to manage your toolbars, use [KXmlGuiWindow::setupGUI](kxmlguiwindow.md#setupGUI)() instead.

Use [setAutoSaveSettings](kmainwindow.md#setAutoSaveSettings)() to automatically save and restore the window geometry and toolbar/menubar/statusbar state when the application is restarted.

Use [kRestoreMainWindows](kmainwindow.md#kRestoreMainWindows)() in your main function to restore your windows when the session is restored.

The window state is saved when the application is exited. Reimplement [queryClose](kmainwindow.md#queryClose)() to warn the user of unsaved data upon close or exit.

Reimplement [saveProperties](kmainwindow.md#saveProperties)() / [readProperties](kmainwindow.md#readProperties)() or [saveGlobalProperties](kmainwindow.md#saveGlobalProperties)() / [readGlobalProperties](kmainwindow.md#readGlobalProperties)() to save/restore application-specific state during session management.

Note that session saving is automatically called, session restoring is not, and so it needs to be implemented in your main() function.

See [https://develop.kde.org/docs/features/session-managment](https://develop.kde.org/docs/features/session-managment) for more information on session management.

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

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KMainWindow::KMainWindow(QWidget \**parent* = nullptr, Qt::WindowFlags *flags* = Qt::WindowFlags()) {#KMainWindow}

Constructs a main window.

`parent` The parent widget. This is usually `nullptr`, but it may also be the window group leader. In that case, the [KMainWindow](kmainwindow.md) becomes a secondary window.

`flags` Specify the window flags. The default is none.

Note that by default a [KMainWindow](kmainwindow.md) is created with the [Qt::WA\_DeleteOnClose](https://doc.qt.io/qt-6/qt.html#WidgetAttribute-enum) attribute set, i.e. it is automatically destroyed when the window is closed. If you do not want this behavior, call

```cpp
window->setAttribute(Qt::WA_DeleteOnClose, false);
```

KMainWindows must be created on the heap with 'new', like:

```cpp
KMainWindow *kmw = new KMainWindow(...);
kmw->setObjectName(...);
```

Since KDE Frameworks 5.16, [KMainWindow](kmainwindow.md) will enter information regarding the application's translators by default, using [KAboutData::setTranslator](../kcoreaddons/kaboutdata.md#setTranslator)(). This only occurs if no translators are already assigned in [KAboutData](../kcoreaddons/kaboutdata.md) (see [KAboutData::setTranslator](../kcoreaddons/kaboutdata.md#setTranslator)() for details – the auto-assignment here uses the same translated strings as specified for that function).

> **Warning:** For session management and window management to work properly, all main windows in the application should have a different name. Otherwise, [KMainWindow](kmainwindow.md) will create a unique name, but it's recommended to explicitly pass a window name that will also describe the type of the window. If there can be several windows of the same type, append '\#' (hash) to the name, and [KMainWindow](kmainwindow.md) will replace it with numbers to make the names unique. For example, for a mail client which has one main window showing the mails and folders, and which can also have one or more windows for composing mails, the name for the folders window should be e.g. "mainwindow" and for the composer windows "composer\#".

*See also* [KAboutData](../kcoreaddons/kaboutdata.md)

### \[override virtual noexcept\] KMainWindow::~KMainWindow() {#dtor.KMainWindow}

Destructor.

Will also destroy the toolbars and menubar if needed.

### \[slot\] void KMainWindow::appHelpActivated() {#appHelpActivated}

Opens the help page for the application.

The application name is used as a key to determine what to display and the system will attempt to open \<appName\>/index.html.

This method is intended for use by a help button in the toolbar or components outside the regular help menu.

Use helpMenu() when you want to provide access to the help system from the help menu.

Example (adding a help button to the first toolbar):

```cpp
toolBar()->addAction(QIcon::fromTheme("help-contents"), i18n("Help"),
                      this, &KMainWindow::appHelpActivated);
```

*See also* helpMenu(), [toolBar](kmainwindow.md#toolBar)()

### \[virtual\] void KMainWindow::applyMainWindowSettings(const KConfigGroup &*config*) {#applyMainWindowSettings}

Read settings for statusbar, menubar and toolbar from their respective groups in the config file and apply them.

`config` Config group to read the settings from.

### KConfigGroup KMainWindow::autoSaveConfigGroup() const {#autoSaveConfigGroup}

Returns The group used for autosaving settings.

Only meaningful if [setAutoSaveSettings](kmainwindow.md#setAutoSaveSettings)(const [QString](https://doc.qt.io/qt-6/qstring.html)&, bool) was called.

Do not use this method if [setAutoSaveSettings](kmainwindow.md#setAutoSaveSettings)(const [KConfigGroup](../kconfigcore/kconfiggroup.md)&, bool) was called.

This can be useful for forcing an apply, e.g. after using [KEditToolBar](kedittoolbar.md).

*See also* [setAutoSaveSettings](kmainwindow.md#setAutoSaveSettings)(), [autoSaveGroup](kmainwindow.md#autoSaveGroup)()

### QString KMainWindow::autoSaveGroup() const {#autoSaveGroup}

Returns The group used for autosaving settings.

Do not mistake this with [autoSaveConfigGroup](kmainwindow.md#autoSaveConfigGroup).

Only meaningful if [setAutoSaveSettings](kmainwindow.md#setAutoSaveSettings)(const [QString](https://doc.qt.io/qt-6/qstring.html)&, bool) was called.

Do not use this method if [setAutoSaveSettings](kmainwindow.md#setAutoSaveSettings)(const [KConfigGroup](../kconfigcore/kconfiggroup.md)&, bool) was called.

This can be useful for forcing a save or an apply, e.g. before and after using [KEditToolBar](kedittoolbar.md).

> **Note:** Prefer [saveAutoSaveSettings](kmainwindow.md#saveAutoSaveSettings)() for saving or [autoSaveConfigGroup](kmainwindow.md#autoSaveConfigGroup)() for loading.

> **Note:** Getter function for property [autoSaveGroup](kmainwindow.md#autoSaveGroup-prop).

*See also* [autoSaveSettings](kmainwindow.md#autoSaveSettings)(), [setAutoSaveSettings](kmainwindow.md#setAutoSaveSettings)(), [saveAutoSaveSettings](kmainwindow.md#saveAutoSaveSettings)(), [resetAutoSaveSettings](kmainwindow.md#resetAutoSaveSettings)(), [autoSaveConfigGroup](kmainwindow.md#autoSaveConfigGroup)()

### bool KMainWindow::autoSaveSettings() const {#autoSaveSettings}

Returns `true` if [setAutoSaveSettings](kmainwindow.md#setAutoSaveSettings)() was called, `false` by default or if [resetAutoSaveSettings](kmainwindow.md#resetAutoSaveSettings)() was called.

> **Note:** Getter function for property [autoSaveSettings](kmainwindow.md#autoSaveSettings-prop).

*See also* [setAutoSaveSettings](kmainwindow.md#setAutoSaveSettings)(), [resetAutoSaveSettings](kmainwindow.md#resetAutoSaveSettings)()

### \[static\] bool KMainWindow::canBeRestored(int *numberOfInstances*) {#canBeRestored}

Returns `true` if the number of [KMainWindow](kmainwindow.md) instances of the previous session did contain the requested `numberOfInstances`, `false` otherwise.

`numberOfInstances` The number of [KMainWindow](kmainwindow.md) instances in the application.

*See also* [restore](kmainwindow.md#restore)()

### \[static\] const QString KMainWindow::classNameOfToplevel(int *instanceNumber*) {#classNameOfToplevel}

Useful if your application uses different kinds of top-level windows.

Returns The class name of the top-level window to be restored that corresponds to `instanceNumber`.

*See also* [restore](kmainwindow.md#restore)()

### \[override virtual protected\] void KMainWindow::closeEvent(*QCloseEvent \**) {#closeEvent}

Reimplements: [QWidget::closeEvent(QCloseEvent \*event)](https://doc.qt.io/qt-6/qwidget.html#closeEvent).

Reimplemented to autosave settings and call [queryClose](kmainwindow.md#queryClose)().

We recommend that you reimplement [queryClose](kmainwindow.md#queryClose)() rather than closeEvent(). If you do it anyway, ensure to call the base implementation to keep the feature of autosaving window settings working.

### QString KMainWindow::dbusName() const {#dbusName}

Returns The path for the exported window's D-Bus object.

### \[override virtual protected\] bool KMainWindow::event(QEvent \**event*) {#event}

Reimplements: [QMainWindow::event(QEvent \*event)](https://doc.qt.io/qt-6/qmainwindow.html#event).

Reimplemented to return the `event` [QEvent::Polish](https://doc.qt.io/qt-6/qevent.html#Type-enum) in order to adjust the object name if needed, once all constructor code for the main window has run. Also reimplemented to catch when a [QDockWidget](https://doc.qt.io/qt-6/qdockwidget.html) is added or removed.

### bool KMainWindow::hasMenuBar() {#hasMenuBar}

Returns `true` if there is a menubar, `false` otherwise.

> **Note:** Getter function for property [hasMenuBar](kmainwindow.md#hasMenuBar-prop).

### \[override virtual protected\] void KMainWindow::keyPressEvent(QKeyEvent \**keyEvent*) {#keyPressEvent}

Reimplements: [QWidget::keyPressEvent(QKeyEvent \*event)](https://doc.qt.io/qt-6/qwidget.html#keyPressEvent).

Reimplemented to open context menus on Shift+F10.

`keyEvent` The event assigned to a key press.

### \[static\] QList\<KMainWindow \*\> KMainWindow::memberList() {#memberList}

Returns The list of members of the [KMainWindow](kmainwindow.md) class.

### \[virtual protected\] bool KMainWindow::queryClose() {#queryClose}

This function is called before the window is closed, either by the user or indirectly by the session manager.

This can be used to prompt the user to save unsaved data before the window is closed.

Usage example:

```cpp
switch ( KMessageBox::warningTwoActionsCancel( this,
         i18n("Save changes to document foo?"), QString(),
         KStandardGuiItem::save(), KStandardGuiItem::discard())) ) {
  case KMessageBox::PrimaryAction :
    // save document here. If saving fails, return false;
    return true;
  case KMessageBox::SecondaryAction :
    return true;
  default: // cancel
    return false;
```

> **Note:** Do **not** close the document from within this method, as it may be called by the session manager before the session is saved. If the document is closed before the session save occurs, its location might not be properly saved. In addition, the session shutdown may be canceled, in which case the document should remain open.

Returns `true` by default, `false` according to the reimplementation. Returning `false` will cancel the closing operation, and if KApplication::sessionSaving() is true, it cancels logout.

### \[virtual protected\] void KMainWindow::readGlobalProperties(KConfig \**sessionConfig*) {#readGlobalProperties}

Reads your application-wide properties.

`sessionConfig` A pointer to the [KConfig](../kconfigcore/kconfig.md) instance used to load the session data.

*See also* [saveGlobalProperties](kmainwindow.md#saveGlobalProperties)(), [readProperties](kmainwindow.md#readProperties)()

### \[virtual protected\] void KMainWindow::readProperties(*const KConfigGroup &*) {#readProperties}

Reads your instance-specific properties.

This function is called indirectly by [restore](kmainwindow.md#restore)().

```cpp
void MainWindow::readProperties(KConfigGroup &config) {
  if (config.hasKey("myKey")) {
    config.readEntry("myKey", "DefaultValue");
  }
  ...
}
```

*See also* [readGlobalProperties](kmainwindow.md#readGlobalProperties)()

### void KMainWindow::resetAutoSaveSettings() {#resetAutoSaveSettings}

Disables the autosave settings feature. You don't normally need to call this, ever.

*See also* [setAutoSaveSettings](kmainwindow.md#setAutoSaveSettings)(), [autoSaveSettings](kmainwindow.md#autoSaveSettings)()

### bool KMainWindow::restore(int *numberOfInstances*, bool *show* = true) {#restore}

Attempt to restore the top-level widget as defined by `numberOfInstances` (1..X).

You should call [canBeRestored](kmainwindow.md#canBeRestored)() first.

If the session did not contain so high a number, the configuration is not changed and `false` is returned.

That means clients could simply do the following:

```cpp
if (qApp->isSessionRestored()){
  int n = 1;
  while (KMainWindow::canBeRestored(n)){
    (new childMW)->restore(n);
    n++;
  }
} else {
  // create default application as usual
}
```

Note that if `show` is `true` (default), [QWidget::show](https://doc.qt.io/qt-6/qwidget.html#show)() is called implicitly in restore.

With this you can easily restore all top-level windows of your application.

If your application uses different kinds of top-level windows, then you can use [KMainWindow::classNameOfToplevel](kmainwindow.md#classNameOfToplevel)(n) to determine the exact type before calling the childMW constructor in the example from above.

> **Note:** You don't need to deal with this function. Use the [kRestoreMainWindows](kmainwindow.md#kRestoreMainWindows)() convenience template function instead!

`numberOfInstances` The number of [KMainWindow](kmainwindow.md) instances from the last session.

`show` Whether the [KMainWindow](kmainwindow.md) instances will be visible by default.

Returns `true` if the session contained the same number of instances as the requested number, `false` if the session contained less instances than the requested number, in which case no configuration is changed.

*See also* [kRestoreMainWindows](kmainwindow.md#kRestoreMainWindows)(), [readProperties](kmainwindow.md#readProperties)(), [canBeRestored](kmainwindow.md#canBeRestored)()

### \[protected slot\] void KMainWindow::saveAutoSaveSettings() {#saveAutoSaveSettings}

This slot should only be called in case you reimplement [closeEvent](kmainwindow.md#closeEvent)() and if you are using the autosave feature. In all other cases, [setSettingsDirty](kmainwindow.md#setSettingsDirty)() should be called instead to benefit from the delayed saving.

Usage example:

```cpp
void MyMainWindow::closeEvent( QCloseEvent *e )
{
  // Save settings if autosave is enabled, and settings have changed
  if ( settingsDirty() && autoSaveSettings() )
    saveAutoSaveSettings();
  ..
}
```

*See also* [setAutoSaveSettings](kmainwindow.md#setAutoSaveSettings)(), [setSettingsDirty](kmainwindow.md#setSettingsDirty)()

### \[virtual protected\] void KMainWindow::saveGlobalProperties(KConfig \**sessionConfig*) {#saveGlobalProperties}

Saves your application-wide properties.

`sessionConfig` A pointer to the [KConfig](../kconfigcore/kconfig.md) instance used to save the session data.

This function is invoked when the session manager requests your application to save its state. It is similar to [saveProperties](kmainwindow.md#saveProperties)(), but it is only called for the first main window. This is useful to save global state of your application that isn't bound to a particular window.

The default implementation does nothing.

*See also* [readGlobalProperties](kmainwindow.md#readGlobalProperties)(), [saveProperties](kmainwindow.md#saveProperties)()

### void KMainWindow::saveMainWindowSettings(KConfigGroup &*config*) {#saveMainWindowSettings}

Manually save the settings for statusbar, menubar and toolbar to their respective groups in the [KConfigGroup](../kconfigcore/kconfiggroup.md) `config`.

Usage example:

```cpp
KConfigGroup group(KSharedConfig::openConfig(), "MainWindow");
saveMainWindowSettings(group);
```

`config` Config group to save the settings to.

*See also* [setAutoSaveSettings](kmainwindow.md#setAutoSaveSettings)(), [KConfig](../kconfigcore/kconfig-index.md), [KSharedConfig](../kconfigcore/ksharedconfig.md), [KConfigGroup](../kconfigcore/kconfiggroup.md)

### \[virtual protected\] void KMainWindow::saveProperties(*KConfigGroup &*) {#saveProperties}

Saves your instance-specific properties.

The function is invoked when the session manager requests your application to save its state.

Reimplement this function in child classes.

Usage example:

```cpp
void MainWindow::saveProperties(KConfigGroup &config) {
  config.writeEntry("myKey", "newValue");
  ...
}
```

> **Note:** No user interaction is allowed in this function!

### void KMainWindow::setAutoSaveSettings(const QString &*groupName* = QStringLiteral("MainWindow"), bool *saveWindowSize* = true) {#setAutoSaveSettings}

This enables autosave of toolbar/menubar/statusbar settings (and optionally window size).

`groupName` A name that identifies the type of window. You can have several types of window in the same application. If no `groupName` is specified, the value defaults to "MainWindow".

`saveWindowSize` Whether to include the window size when saving. `true` by default.

If the \*bars were modified when the window is closed, `saveMainWindowSettings( KConfigGroup(KSharedConfig::openConfig(), groupName) )` will be called.

Typically, you will call setAutoSaveSettings() in your [KMainWindow](kmainwindow.md)-inherited class constructor, and it will take care of restoring and saving automatically.

By default, this generates an appnamerc ini file as if using default [KConfig](../kconfigcore/kconfig.md) constructor or [KConfig::SimpleConfig](../kconfigcore/kconfig.md#OpenFlag-enum).

Make sure you call this **after** all your \*bars have been created.

To make sure that [KMainWindow](kmainwindow.md) properly obtains the default size of the window you should do the following: - Remove hardcoded [resize](https://doc.qt.io/qt-6/qwidget.html#size-prop)() calls in the constructor or main to let the automatic resizing determine the default window size. Hardcoded window sizes will be wrong for users that have big fonts, use different styles, long/small translations, large toolbars, and other factors. - Put the setAutoSaveSettings() call after all widgets have been created and placed inside the main window (for most apps this means [QMainWindow::setCentralWidget](https://doc.qt.io/qt-6/qmainwindow.html#setCentralWidget)()) - [QWidget](https://doc.qt.io/qt-6/qwidget.html)-based objects should overload "virtual [QSize](https://doc.qt.io/qt-6/qsize.html) [sizeHint](https://doc.qt.io/qt-6/qwidget.html#sizeHint-prop)() const;" to specify a default size.

*See also* [autoSaveSettings](kmainwindow.md#autoSaveSettings)(), [KConfig](../kconfigcore/kconfig-index.md), [KSharedConfig](../kconfigcore/ksharedconfig.md), [saveMainWindowSettings](kmainwindow.md#saveMainWindowSettings)(), [toolBar](kmainwindow.md#toolBar)(), [KXmlGuiWindow::setupGUI](kxmlguiwindow.md#setupGUI)()

### void KMainWindow::setAutoSaveSettings(const KConfigGroup &*group*, bool *saveWindowSize* = true) {#setAutoSaveSettings-1}

This allows the settings to be saved into a different file that does not correspond to that used for [KSharedConfig::openConfig](../kconfigcore/ksharedconfig.md#openConfig)().

`group` A name that identifies the type of window. You can have several types of window in the same application.

`saveWindowSize` Whether to include the window size when saving. `true` by default.

This function overloads KMainWindow::setAutoSaveSettings(const QString &groupName = QStringLiteral("MainWindow"), bool saveWindowSize = true).

*See also* [setAutoSaveSettings](kmainwindow.md#setAutoSaveSettings)(const QString &groupName, bool saveWindowSize), [KConfig](../kconfigcore/kconfig-index.md), [KSharedConfig](../kconfigcore/ksharedconfig.md)

### \[virtual slot\] void KMainWindow::setCaption(const QString &*caption*) {#setCaption}

Assigns a KDE compliant caption (window title).

`caption` The string that will be displayed in the window title, before the application name.

> **Note:** This function does the same as [setPlainCaption](kmainwindow.md#setPlainCaption)().

> **Note:** Do not include the application name in this string. It will be added automatically according to the KDE standard.

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kMainWindow, qOverload<const QString &>(&KMainWindow::setCaption));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kMainWindow, [receiver = kMainWindow](const QString &caption) { receiver->setCaption(caption); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).

*See also* [setPlainCaption](kmainwindow.md#setPlainCaption)()

### \[virtual slot\] void KMainWindow::setCaption(const QString &*caption*, bool *modified*) {#setCaption-1}

Makes a KDE compliant caption.

`caption` Your caption.

`modified` Whether the document is modified. This displays an additional sign in the title bar, usually "\*\*".

> **Note:** Do not include the application name in this string. It will be added automatically according to the KDE standard.

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kMainWindow, qOverload<const QString &, bool>(&KMainWindow::setCaption));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kMainWindow, [receiver = kMainWindow](const QString &caption, bool modified) { receiver->setCaption(caption, modified); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).

### \[virtual slot\] void KMainWindow::setPlainCaption(const QString &*caption*) {#setPlainCaption}

Make a plain caption without any modifications.

`caption` The string that will be displayed in the window title, before the application name.

> **Note:** This function does the same as [setCaption](kmainwindow.md#setCaption)().

> **Note:** Do not include the application name in this string. It will be added automatically according to the KDE standard.

*See also* [setCaption](kmainwindow.md#setCaption)()

### \[slot\] void KMainWindow::setSettingsDirty() {#setSettingsDirty}

Tell the main window that it should save its settings when being closed.

This is part of the autosave settings feature.

For everything related to toolbars this happens automatically, but you have to call setSettingsDirty() in the slot that toggles the visibility of the statusbar.

*See also* [settingsDirty](kmainwindow.md#settingsDirty)(), [saveAutoSaveSettings](kmainwindow.md#saveAutoSaveSettings)()

### void KMainWindow::setStateConfigGroup(const QString &*configGroup*) {#setStateConfigGroup}

Assigns the config group name for the [KConfigGroup](../kconfigcore/kconfiggroup.md) returned by [stateConfigGroup](kmainwindow.md#stateConfigGroup).

`configGroup` The config group to be assigned.

Window size and state are stored in the resulting [KConfigGroup](../kconfigcore/kconfiggroup.md) when this function is called.

> **Note:** If this is used in combination with [setAutoSaveSettings](kmainwindow.md#setAutoSaveSettings), you should call this method first.

*See also* [KConfigGroup](../kconfigcore/kconfiggroup.md), [KSharedConfig::openStateConfig](../kconfigcore/ksharedconfig.md#openStateConfig)(), [stateConfigGroup](kmainwindow.md#stateConfigGroup)()

### \[protected\] bool KMainWindow::settingsDirty() const {#settingsDirty}

Returns whether there are unsaved changes.

For inherited classes.

### KConfigGroup KMainWindow::stateConfigGroup() const {#stateConfigGroup}

Returns The [KConfigGroup](../kconfigcore/kconfiggroup.md) used to store state data like window sizes or window state.

The resulting group is invalid if setStateConfig is not called explicitly.

*See also* [setStateConfigGroup](kmainwindow.md#setStateConfigGroup)(), [KConfigGroup](../kconfigcore/kconfiggroup.md)

### KToolBar \*KMainWindow::toolBar(const QString &*name* = QString()) {#toolBar}

This is useful to both call specific toolbars that have been created or to generate a default one upon call.

This refers to toolbars created dynamically from the XML UI framework via [KConfig](../kconfigcore/kconfig.md) or appnameui.rc.

If the toolbar does not exist, one will be created.

`name` The internal name of the toolbar. If no name is specified, "mainToolBar" is assumed.

Returns A pointer to the toolbar with the specified name.

*See also* [toolBars](kmainwindow.md#toolBars)()

### QList\<KToolBar \*\> KMainWindow::toolBars() const {#toolBars}

Returns a list of all toolbars for this window

## Related Non-Members {#related-non-members}

### template \<typename T\> void kRestoreMainWindows() {#kRestoreMainWindows}

Restores the last session. (To be used in your main function).

These functions work also if you have more than one kind of top-level widget (each derived from [KMainWindow](kmainwindow.md), of course).

Imagine you have three kinds of top-level widgets: the classes `ChildMW1`, `ChildMW2` and `ChildMW3`. Then you can just do:

```cpp
int main(int argc, char *argv[])
{
    // [...]
    if (qApp->isSessionRestored())
        kRestoreMainWindows<ChildMW1, ChildMW2, ChildMW3>();
    else {
      // create default application as usual
    }
    // [...]
}
```

kRestoreMainWindows will create (on the heap) as many instances of your main windows as have existed in the last session and call [KMainWindow::restore](kmainwindow.md#restore)() with the correct arguments. Note that also [QWidget::show](https://doc.qt.io/qt-6/qwidget.html#show)() is called implicitly.

Currently, these functions are provided for up to three template arguments. If you need more, tell us. To help you in deciding whether or not you can use kRestoreMainWindows, a define [KDE\_RESTORE\_MAIN\_WINDOWS\_NUM\_TEMPLATE\_ARGS](kmainwindow.md#KDE_RESTORE_MAIN_WINDOWS_NUM_TEMPLATE_ARGS) is provided.

> **Note:** Prefer this function over directly calling [KMainWindow::restore](kmainwindow.md#restore)().

*See also* [KMainWindow::restore](kmainwindow.md#restore)(), [KMainWindow::classNameOfToplevel](kmainwindow.md#classNameOfToplevel)()

## Macro Documentation {#macro-documentation}

### KDE\_RESTORE\_MAIN\_WINDOWS\_NUM\_TEMPLATE\_ARGS {#KDE_RESTORE_MAIN_WINDOWS_NUM_TEMPLATE_ARGS}

Returns the maximal number of arguments that are actually supported by [kRestoreMainWindows](kmainwindow.md#kRestoreMainWindows)().
