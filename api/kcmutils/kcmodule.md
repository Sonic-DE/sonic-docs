---
title: "KCModule Class"
description: "The base class for QWidgets configuration modules. This class was introduced in Qt 6.0."
---

# KCModule Class

The base class for QWidgets configuration modules. This class was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <KCModule>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KCMUtils)`  
  `target_link_libraries(mytarget PRIVATE KF6::KCMUtils)`
- **Inherits:** [KAbstractConfigModule](kabstractconfigmodule.md)

[List of all members, including inherited members](kcmodule-members.md)

## Public Functions

- [KCModule(QWidget \*parent, const KPluginMetaData &data)](#KCModule-2)
- [~KCModule()](#dtor.KCModule)
- [QList\<KConfigDialogManager \*\> configs() const](#configs)
- [void markAsChanged()](#markAsChanged)
- [QWidget \*widget()](#widget)

## Public Slots

- [void widgetChanged()](#widgetChanged)

## Protected Functions

- [KCModule(QObject \*parent)](#KCModule)
- [KCModule(QObject \*parent, const KPluginMetaData &data)](#KCModule-1)
- [KConfigDialogManager \*addConfig(KCoreConfigSkeleton \*config, QWidget \*widget)](#addConfig)
- [bool managedWidgetChangeState() const](#managedWidgetChangeState)
- [bool managedWidgetDefaultState() const](#managedWidgetDefaultState)
- [void unmanagedWidgetChangeState(bool)](#unmanagedWidgetChangeState)
- [void unmanagedWidgetDefaultState(bool)](#unmanagedWidgetDefaultState)

## Detailed Description {#details}

Configuration modules are loaded as plugins.

The module in principle is a simple widget displaying the item to be changed. The module has a very small interface.

To write a config module, you have to create a library that contains a factory class like the following:

```cpp
#include <KPluginFactory>

K_PLUGIN_CLASS_WITH_JSON(MyKCModule, "mykcmodule.json")
```

The constructor of the [KCModule](kcmodule.md) then looks like this:

```cpp
YourKCModule::YourKCModule(QWidget *parent, const KPluginMetaData &data)
  : KCModule(parent, data)
{
    // KCModule does not directly extend QWidget due to ambiguity with KAbstractConfigModule
    // Because of this, you need to call widget() to get the parent widget
    auto label = new QLabel(widget());
    label->setText(QStringLiteral("Demo Text"));
}
```

This KCM can be loaded in a [KCMultiDialog](kcmultidialog.md) of kcmshell6.

## Member Function Documentation {#member-function-documentation}

### \[explicit protected\] KCModule::KCModule(QObject \**parent*) {#KCModule}

Utility constructor for creating a [KCModule](kcmodule.md) that is embedded, for example in a [KPluginWidget](kpluginwidget.md).

This constructor should not be used for KCMs that are part launched in systemsettings!

> **Note:** Do not emit changed signals here, since they are not yet connected to any slot.

`parent` The [KCModule](kcmodule.md) parent.

### \[explicit protected\] KCModule::KCModule(QObject \**parent*, const KPluginMetaData &*data*) {#KCModule-1}

Utility overload to avoid having to take both parent and parentWidget [KCModuleLoader::loadModule](kcmoduleloader.md#loadModule) enforces the parent to be a [QWidget](https://doc.qt.io/qt-6/qwidget.html) anyway.

`parent` The [KCModule](kcmodule.md) parent.

`data` The JSON metadata of the [KCModule](kcmodule.md).

### \[explicit\] KCModule::KCModule(QWidget \**parent*, const KPluginMetaData &*data*) {#KCModule-2}

Base class for all QWidgets configuration modules.

`parent` The [KCModule](kcmodule.md) parent.

`data` The JSON metadata of the [KCModule](kcmodule.md).

> **Note:** Do not emit changed signals here, since they are not yet connected to any slot.

### \[override virtual noexcept\] KCModule::~KCModule() {#dtor.KCModule}

Destroys the module.

### \[protected\] KConfigDialogManager \*KCModule::addConfig(KCoreConfigSkeleton \**config*, QWidget \**widget*) {#addConfig}

Adds a KCoreConfigskeleton `config` to watch the widget `widget`.

This function is useful if you need to handle multiple configuration files.

Returns a pointer to the KCoreConfigDialogManager in use.

`config` The [KCoreConfigSkeleton](../kconfigcore/kcoreconfigskeleton.md) to use.

`widget` The widget to watch.

### QList\<KConfigDialogManager \*\> KCModule::configs() const {#configs}

Returns a list of [KConfigDialogManager](../kconfigwidgets/kconfigdialogmanager.md)'s in use, if any.

### \[protected\] bool KCModule::managedWidgetChangeState() const {#managedWidgetChangeState}

Returns the changed state of automatically managed widgets in this dialog.

### \[protected\] bool KCModule::managedWidgetDefaultState() const {#managedWidgetDefaultState}

Returns the defaulted state of automatically managed widgets in this dialog.

### void KCModule::markAsChanged() {#markAsChanged}

Utility function that marks the KCM as changed.

### \[protected\] void KCModule::unmanagedWidgetChangeState(*bool*) {#unmanagedWidgetChangeState}

Call this method when your manually managed widgets change state between "changed" and "not changed".

### \[protected\] void KCModule::unmanagedWidgetDefaultState(*bool*) {#unmanagedWidgetDefaultState}

Call this method when your manually managed widgets change state between "defaulted" and "not defaulted".

### \[virtual\] QWidget \*KCModule::widget() {#widget}

Get the associated widget that can be embedded.

The returned widget should be used as a parent for widgets you create

> **Note:** Overwriting this function should not be necessary for consumers!

### \[protected slot\] void KCModule::widgetChanged() {#widgetChanged}

A managed widget was changed, the widget settings and the current settings are compared, and a corresponding [needsSaveChanged](kabstractconfigmodule.md#needsSaveChanged)() signal is emitted.
