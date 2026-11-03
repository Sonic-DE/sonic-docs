---
title: "KConfigDialog Class"
description: "Standard KDE configuration dialog class."
---

# KConfigDialog Class

Standard KDE configuration dialog class. [More...](#details)

- **Header:** `#include <KConfigDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ConfigWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigWidgets)`
- **Inherits:** [KPageDialog](../kwidgetsaddons/kpagedialog.md)

[List of all members, including inherited members](kconfigdialog-members.md)

## Public Functions

- [KConfigDialog(QWidget \*parent, const QString &name, KCoreConfigSkeleton \*config)](#KConfigDialog)
- [~KConfigDialog()](#dtor.KConfigDialog)
- [KPageWidgetItem \*addPage(QWidget \*page, KCoreConfigSkeleton \*config, const QString &itemName, const QString &pixmapName = QString(), const QString &header = QString())](#addPage)
- [KPageWidgetItem \*addPage(QWidget \*page, const QString &itemName, const QString &pixmapName = QString(), const QString &header = QString(), bool manage = true)](#addPage-1)

## Public Slots

- [void setHelp(const QString &anchor, const QString &appname = QString())](#setHelp)
- [void settingsChangedSlot()](#settingsChangedSlot)
- [void showHelp()](#showHelp)
- [void updateButtons()](#updateButtons)
- [void updateSettings()](#updateSettings)
- [void updateWidgets()](#updateWidgets)
- [void updateWidgetsDefault()](#updateWidgetsDefault)

## Signals

- [void settingsChanged(const QString &dialogName)](#settingsChanged)
- [void widgetModified()](#widgetModified)

## Static Public Members

- [KConfigDialog \*exists(const QString &name)](#exists)
- [bool showDialog(const QString &name)](#showDialog)

## Protected Functions

- [bool hasChanged()](#hasChanged)
- [bool isDefault()](#isDefault)

## Detailed Description {#details}

The [KConfigDialog](kconfigdialog.md) class provides an easy and uniform means of displaying a settings dialog using [KPageDialog](../kwidgetsaddons/kpagedialog.md), [KConfigDialogManager](kconfigdialogmanager.md) and a [KConfigSkeleton](../kconfiggui/kconfigskeleton.md) derived settings class.

[KConfigDialog](kconfigdialog.md) handles the enabling and disabling of buttons, creation of the dialog, and deletion of the widgets. Because of [KConfigDialogManager](kconfigdialogmanager.md), this class also manages: restoring the settings, resetting them to the default values, and saving them. This requires that the names of the widgets corresponding to configuration entries have to have the same name plus an additional "kcfg\_" prefix. For example the widget named "kcfg\_MyOption" would be associated with the configuration entry "MyOption".

Here is an example usage of [KConfigDialog](kconfigdialog.md):

```cpp
void KCoolApp::showSettings(){
    if (KConfigDialog::showDialog(QStringLiteral("settings"))) {
      return;
    }
    KConfigDialog *dialog = new KConfigDialog(this, QStringLiteral("settings"), MySettings::self());
    dialog->setFaceType(KPageDialog::List);
    dialog->addPage(new General(0, "General"), i18n("General"));
    dialog->addPage(new Appearance(0, "Style"), i18n("Appearance"));
    connect(dialog, &KConfigDialog::settingsChanged, mainWidget, &Bar::loadSettings);
    connect(dialog, &KConfigDialog::settingsChanged, this, &Foo::loadSettings);
    dialog->show();
}
```

Other than the above code, each class that has settings in the dialog should have a loadSettings() type slot to read settings and perform any necessary changes.

For dialog appearance options (like buttons, default button, ...) please see [KPageDialog](../kwidgetsaddons/kpagedialog.md).

*See also* [KConfigSkeleton](../kconfiggui/kconfigskeleton.md)

## Member Function Documentation {#member-function-documentation}

### KConfigDialog::KConfigDialog(QWidget \**parent*, const QString &*name*, KCoreConfigSkeleton \**config*) {#KConfigDialog}

`parent` The parent of this object. Even though the class deletes itself the parent should be set so the dialog can be centered with the application on the screen.

`name` The name of this object. The name is used in determining if there can be more than one dialog at a time. Use names such as: "Font Settings" or "Color Settings" and not just "Settings" in applications where there is more than one dialog.

`config` Config object containing settings.

### \[override virtual noexcept\] KConfigDialog::~KConfigDialog() {#dtor.KConfigDialog}

Deconstructor, removes name from the list of open dialogs.

*See also* [exists](kconfigdialog.md#exists)()

### KPageWidgetItem \*KConfigDialog::addPage(QWidget \**page*, KCoreConfigSkeleton \**config*, const QString &*itemName*, const QString &*pixmapName* = QString(), const QString &*header* = QString()) {#addPage}

Adds page to the dialog that is managed by a custom [KConfigDialogManager](kconfigdialogmanager.md). This is useful for dialogs that contain settings spread over more than one configuration file and thus have/need more than one [KConfigSkeleton](../kconfiggui/kconfigskeleton.md). When an application is done adding pages [show](https://doc.qt.io/qt-6/qwidget.html#show)() should be called to display the dialog.

`page` Pointer to the page that is to be added to the dialog. This object is reparented.

`config` Config object containing corresponding settings.

`itemName` Name of the page.

`pixmapName` Name of the icon that should be used, if needed, when displaying the page. The string may either be the name of a themed icon (e.g. "document-save"), which the internal icon loader will be used to retrieve, or an absolute path to the pixmap on disk.

`header` Header text use in the list modes. Ignored in Tabbed mode. If empty, the itemName text is used when needed.

Returns the [KPageWidgetItem](../kwidgetsaddons/kpagewidgetitem.md) associated with the page.

### KPageWidgetItem \*KConfigDialog::addPage(QWidget \**page*, const QString &*itemName*, const QString &*pixmapName* = QString(), const QString &*header* = QString(), bool *manage* = true) {#addPage-1}

Adds page to the dialog and to [KConfigDialogManager](kconfigdialogmanager.md). When an application is done adding pages [show](https://doc.qt.io/qt-6/qwidget.html#show)() should be called to display the dialog.

`page` Pointer to the page that is to be added to the dialog. This object is reparented.

`itemName` Name of the page.

`pixmapName` Name of the icon that should be used, if needed, when displaying the page. The string may either be the name of a themed icon (e.g. "document-save"), which the internal icon loader will be used to retrieve, or an absolute path to the pixmap on disk.

`header` Header text use in the list modes. Ignored in Tabbed mode. If empty, the itemName text is used when needed.

`manage` Whether [KConfigDialogManager](kconfigdialogmanager.md) should manage the page or not.

Returns the [KPageWidgetItem](../kwidgetsaddons/kpagewidgetitem.md) associated with the page.

### \[static\] KConfigDialog \*KConfigDialog::exists(const QString &*name*) {#exists}

See if a dialog with the name 'name' already exists.

`name` Dialog name to look for.

Returns pointer to widget or `nullptr` if it does not exist.

*See also* [showDialog](kconfigdialog.md#showDialog)()

### \[virtual protected\] bool KConfigDialog::hasChanged() {#hasChanged}

Returns whether the current state of the dialog is different from the current configuration.

Virtual function for custom additions.

### \[virtual protected\] bool KConfigDialog::isDefault() {#isDefault}

Returns whether the current state of the dialog is the same as the default configuration.

### \[protected slot\] void KConfigDialog::setHelp(const QString &*anchor*, const QString &*appname* = QString()) {#setHelp}

Sets the help path and topic.

The HTML file will be found using the X-DocPath entry in the application's desktop file. It can be either a relative path, or a website URL.

`anchor` This has to be a defined anchor in your docbook sources or website. If empty the main index is loaded.

`appname` This allows you to specify the .desktop file to get the help path from. If empty the [QCoreApplication::applicationName](https://doc.qt.io/qt-6/qcoreapplication.html#applicationName-prop)() is used.

### \[signal\] void KConfigDialog::settingsChanged(const QString &*dialogName*) {#settingsChanged}

One or more of the settings have been permanently changed such as if the user clicked on the Apply or Ok button.

`dialogName` the name of the dialog.

### \[protected slot\] void KConfigDialog::settingsChangedSlot() {#settingsChangedSlot}

Some setting was changed. Emit the signal with the dialogs name.

Connect to this slot if there are widgets not managed by [KConfig](../kconfigcore/kconfig.md).

### \[static\] bool KConfigDialog::showDialog(const QString &*name*) {#showDialog}

Attempts to show the dialog with the name 'name'.

`name` The name of the dialog to show.

Returns `true` if the dialog 'name' exists and was shown.

*See also* [exists](kconfigdialog.md#exists)()

### \[virtual protected slot\] void KConfigDialog::showHelp() {#showHelp}

Displays help for this config dialog.

### \[protected slot\] void KConfigDialog::updateButtons() {#updateButtons}

Updates the Apply and Default buttons.

Connect to this slot if you implement your own [hasChanged](kconfigdialog.md#hasChanged)() or [isDefault](kconfigdialog.md#isDefault)() methods for widgets not managed by [KConfig](../kconfigcore/kconfig.md).

### \[virtual protected slot\] void KConfigDialog::updateSettings() {#updateSettings}

Update the settings from the dialog.

Virtual function for custom additions.

Example use: User clicks Ok or Apply button in a configure dialog.

### \[virtual protected slot\] void KConfigDialog::updateWidgets() {#updateWidgets}

Update the dialog based on the settings.

Virtual function for custom additions.

Example use: Initialisation of dialog.

Example use: User clicks Reset button in a configure dialog.

### \[virtual protected slot\] void KConfigDialog::updateWidgetsDefault() {#updateWidgetsDefault}

Update the dialog based on the default settings.

Virtual function for custom additions.

Example use: User clicks Defaults button in a configure dialog.

### \[signal\] void KConfigDialog::widgetModified() {#widgetModified}

A widget in the dialog was modified.
