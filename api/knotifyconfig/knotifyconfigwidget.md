---
title: "KNotifyConfigWidget Class"
description: "Configure the notification for a given application."
---

# KNotifyConfigWidget Class

Configure the notification for a given application. [More...](#details)

- **Header:** `#include <KNotifyConfigWidget>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NotifyConfig)`  
  `target_link_libraries(mytarget PRIVATE KF6::NotifyConfig)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](knotifyconfigwidget-members.md)

## Public Functions

- [KNotifyConfigWidget(QWidget \*parent)](#KNotifyConfigWidget)
- [void selectEvent(const QString &eventId)](#selectEvent)
- [void setApplication(const QString &appname = QString())](#setApplication)

## Public Slots

- [void disableAllSounds()](#disableAllSounds)
- [void revertToDefaults()](#revertToDefaults)
- [void save()](#save)

## Signals

- [void changed(bool state)](#changed)

## Static Public Members

- [KNotifyConfigWidget \*configure(QWidget \*parent = nullptr, const QString &appname = QString())](#configure)

## Detailed Description {#details}

You probably will want to use the static function configure

If you create the widget yourself, you must call [setApplication](knotifyconfigwidget.md#setApplication) before showing it.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KNotifyConfigWidget::KNotifyConfigWidget(QWidget \**parent*) {#KNotifyConfigWidget}

### \[signal\] void KNotifyConfigWidget::changed(bool *state*) {#changed}

Indicate that the state of the modules contents has changed. This signal is emitted whenever the state of the configuration changes.

*See also* KCModule::changed

### \[static\] KNotifyConfigWidget \*KNotifyConfigWidget::configure(QWidget \**parent* = nullptr, const QString &*appname* = QString()) {#configure}

Show a dialog with the widget.

`parent` the parent widget of the dialog

`appname` the application name, if null, it is autodetected

Returns the widget itself the topLevelWidget of it is probably a KDialog

### \[slot\] void KNotifyConfigWidget::disableAllSounds() {#disableAllSounds}

Disable all sounds for the current application

### \[slot\] void KNotifyConfigWidget::revertToDefaults() {#revertToDefaults}

Reset the UI to display the default values

*See also* [KCModule::defaults](../kcmutils/kabstractconfigmodule.md#defaults)

### \[slot\] void KNotifyConfigWidget::save() {#save}

save to the config file

### void KNotifyConfigWidget::selectEvent(const QString &*eventId*) {#selectEvent}

Select a given notification in the current list

`id` The id of the notification

### void KNotifyConfigWidget::setApplication(const QString &*appname* = QString()) {#setApplication}

Change the application

`appname` name of the application. If null [QCoreApplication::instance](https://doc.qt.io/qt-6/qcoreapplication.html#instance)()-\>applicationName() is used
