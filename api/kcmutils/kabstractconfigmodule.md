---
title: "KAbstractConfigModule Class"
description: "Base class for QML and QWidgets config modules. This class was introduced in Qt 6.0."
---

# KAbstractConfigModule Class

Base class for QML and QWidgets config modules. This class was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <KAbstractConfigModule>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KCMUtils)`  
  `target_link_libraries(mytarget PRIVATE KCMUtilsCore)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)
- **Inherited By:** [KCModule](kcmodule.md) and [KQuickConfigModule](kquickconfigmodule.md)

[List of all members, including inherited members](kabstractconfigmodule-members.md)

## Public Types

- [enum KAbstractConfigModule::Button](#Button-enum)

## Properties

- [buttons : KAbstractConfigModule::Buttons](#buttons-prop)
- [defaultsIndicatorsVisible : bool](#defaultsIndicatorsVisible-prop)
- [\[read-only\] description : const QString](#description-prop)
- [\[read-only\] name : const QString](#name-prop)
- [\[read-only\] needsAuthorization : bool](#needsAuthorization-prop)
- [needsSave : bool](#needsSave-prop)
- [representsDefaults : bool](#representsDefaults-prop)
- [\[since 6.16\] supportsInstantApply : bool](#supportsInstantApply-prop)

## Public Functions

- [KAbstractConfigModule(QObject \*parent, const KPluginMetaData &metaData)](#KAbstractConfigModule)
- [QString authActionName() const](#authActionName)
- [KAbstractConfigModule::Buttons buttons() const](#buttons)
- [void defaults()](#defaults)
- [bool defaultsIndicatorsVisible() const](#defaultsIndicatorsVisible)
- [QString description() const](#description)
- [void load()](#load)
- [KPluginMetaData metaData() const](#metaData)
- [QString name() const](#name)
- [bool needsAuthorization() const](#needsAuthorization)
- [bool needsSave() const](#needsSave)
- [bool representsDefaults() const](#representsDefaults)
- [void save()](#save)
- [void setAuthActionName(const QString &action)](#setAuthActionName)
- [void setButtons(const KAbstractConfigModule::Buttons btn)](#setButtons)
- [void setDefaultsIndicatorsVisible(bool visible)](#setDefaultsIndicatorsVisible)
- [void setNeedsSave(bool needs)](#setNeedsSave)
- [void setRepresentsDefaults(bool defaults)](#setRepresentsDefaults)
- [void setSupportsInstantApply(bool supported)](#setSupportsInstantApply) (since 6.16)
- [bool supportsInstantApply() const](#supportsInstantApply) (since 6.16)

## Signals

- [void activationRequested(const QVariantList &args)](#activationRequested)
- [void authActionNameChanged()](#authActionNameChanged)
- [void buttonsChanged()](#buttonsChanged)
- [void defaultsIndicatorsVisibleChanged()](#defaultsIndicatorsVisibleChanged)
- [void needsSaveChanged()](#needsSaveChanged)
- [void representsDefaultsChanged()](#representsDefaultsChanged)
- [void supportsInstantApplyChanged()](#supportsInstantApplyChanged) (since 6.16)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum KAbstractConfigModule::Button {#Button-enum}

**flags KAbstractConfigModule::Buttons**

An enumeration type for the buttons used by this module.

If Apply is not specified, kcmshell will show a "Close" button.

| Constant | Value | Description |
| --- | --- | --- |
| `KAbstractConfigModule::NoAdditionalButton` | `0` | Shows the "Ok" and "Cancel" buttons. |
| `KAbstractConfigModule::Help` | `1` | Shows a "Help" button. |
| `KAbstractConfigModule::Default` | `2` | Shows a "Use Defaults" button. |
| `KAbstractConfigModule::Apply` | `4` | Shows the "Ok", "Apply", and "Cancel" buttons. |
| `KAbstractConfigModule::Export` | `8` | Obsolete. |

The `Buttons` type is a typedef for `QFlags<Button>. `It stores an OR combination of `Button` values.

*See also* [buttons](kabstractconfigmodule.md#buttons), [setButtons](kabstractconfigmodule.md#setButtons)

## Property Documentation {#property-documentation}

### buttons : KAbstractConfigModule::Buttons {#buttons-prop}

**Access functions:**

- `KAbstractConfigModule::Buttons` **[buttons](kabstractconfigmodule.md#buttons)**() const
- `void` **[setButtons](kabstractconfigmodule.md#setButtons)**(const `KAbstractConfigModule::Buttons` *btn*)

**Notifier signal:**

- `void` **[buttonsChanged](kabstractconfigmodule.md#buttonsChanged)**()

### defaultsIndicatorsVisible : bool {#defaultsIndicatorsVisible-prop}

**Access functions:**

- `bool` **[defaultsIndicatorsVisible](kabstractconfigmodule.md#defaultsIndicatorsVisible)**() const
- `void` **[setDefaultsIndicatorsVisible](kabstractconfigmodule.md#setDefaultsIndicatorsVisible)**(`bool` *visible*)

**Notifier signal:**

- `void` **[defaultsIndicatorsVisibleChanged](kabstractconfigmodule.md#defaultsIndicatorsVisibleChanged)**()

### \[read-only\] description : const QString {#description-prop}

**Access functions:**

- `QString` **[description](kabstractconfigmodule.md#description)**() const

### \[read-only\] name : const QString {#name-prop}

**Access functions:**

- `QString` **[name](kabstractconfigmodule.md#name)**() const

### \[read-only\] needsAuthorization : bool {#needsAuthorization-prop}

**Access functions:**

- `bool` **[needsAuthorization](kabstractconfigmodule.md#needsAuthorization)**() const

**Notifier signal:**

- `void` **[authActionNameChanged](kabstractconfigmodule.md#authActionNameChanged)**()

### needsSave : bool {#needsSave-prop}

**Access functions:**

- `bool` **[needsSave](kabstractconfigmodule.md#needsSave)**() const
- `void` **[setNeedsSave](kabstractconfigmodule.md#setNeedsSave)**(`bool` *needs*)

**Notifier signal:**

- `void` **[needsSaveChanged](kabstractconfigmodule.md#needsSaveChanged)**()

### representsDefaults : bool {#representsDefaults-prop}

**Access functions:**

- `bool` **[representsDefaults](kabstractconfigmodule.md#representsDefaults)**() const
- `void` **[setRepresentsDefaults](kabstractconfigmodule.md#setRepresentsDefaults)**(`bool` *defaults*)

**Notifier signal:**

- `void` **[representsDefaultsChanged](kabstractconfigmodule.md#representsDefaultsChanged)**()

### \[since 6.16\] supportsInstantApply : bool {#supportsInstantApply-prop}

This property was introduced in Qt 6.16.

**Access functions:**

- `bool` **[supportsInstantApply](kabstractconfigmodule.md#supportsInstantApply)**() const
- `void` **[setSupportsInstantApply](kabstractconfigmodule.md#setSupportsInstantApply)**(`bool` *supported*)

**Notifier signal:**

- `void` **[supportsInstantApplyChanged](kabstractconfigmodule.md#supportsInstantApplyChanged)**()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KAbstractConfigModule::KAbstractConfigModule(QObject \**parent*, const KPluginMetaData &*metaData*) {#KAbstractConfigModule}

### \[signal\] void KAbstractConfigModule::activationRequested(const QVariantList &*args*) {#activationRequested}

Emitted by a single-instance application (such as System Settings) to request activation and update `args` to a module that is already running.

The module should connect to this signal when it needs to handle the activation request and specially the new arguments.

`args` A list of arguments that get passed to the module.

### QString KAbstractConfigModule::authActionName() const {#authActionName}

Returns the action previously set with [setAuthActionName](kabstractconfigmodule.md#setAuthActionName)() and that is authorized to execute the [save](kabstractconfigmodule.md#save)() method.

By default this will be a empty string.

*See also* [setAuthActionName](kabstractconfigmodule.md#setAuthActionName)()

### \[signal\] void KAbstractConfigModule::authActionNameChanged() {#authActionNameChanged}

Emitted when the auth action name has changed.

> **Note:** Notifier signal for property [needsAuthorization](kabstractconfigmodule.md#needsAuthorization-prop).

### KAbstractConfigModule::Buttons KAbstractConfigModule::buttons() const {#buttons}

Indicate which buttons will be used.

The return value is a value or'ed together from the Button enumeration type.

> **Note:** Getter function for property [buttons](kabstractconfigmodule.md#buttons-prop).

*See also* [setButtons](kabstractconfigmodule.md#setButtons)

### \[signal\] void KAbstractConfigModule::buttonsChanged() {#buttonsChanged}

Emitted when the buttons to display have changed.

> **Note:** Notifier signal for property [buttons](kabstractconfigmodule.md#buttons-prop).

### \[virtual\] void KAbstractConfigModule::defaults() {#defaults}

Sets the configuration to default values.

This method is called when the user clicks the "Default" button.

### bool KAbstractConfigModule::defaultsIndicatorsVisible() const {#defaultsIndicatorsVisible}

Returns the defaultness indicator visibility.

> **Note:** Getter function for property [defaultsIndicatorsVisible](kabstractconfigmodule.md#defaultsIndicatorsVisible-prop).

*See also* [setDefaultsIndicatorsVisible](kabstractconfigmodule.md#setDefaultsIndicatorsVisible)()

### \[signal\] void KAbstractConfigModule::defaultsIndicatorsVisibleChanged() {#defaultsIndicatorsVisibleChanged}

Emitted when the KCM needs to display indicators for field with non default value.

> **Note:** Notifier signal for property [defaultsIndicatorsVisible](kabstractconfigmodule.md#defaultsIndicatorsVisible-prop).

### QString KAbstractConfigModule::description() const {#description}

Returns the description of the config module.

> **Note:** Getter function for property [description](kabstractconfigmodule.md#description-prop).

### \[virtual\] void KAbstractConfigModule::load() {#load}

Loads the configuration data into the module.

The load method sets the user interface elements of the module to reflect the current settings stored in the configuration files.

This method is invoked whenever the module should read its configuration (most of the times from a config file) and update the user interface. This happens when the user clicks the "Reset" button in the control center, to undo all of his changes and restore the currently valid settings. It is also called right after construction.

### KPluginMetaData KAbstractConfigModule::metaData() const {#metaData}

Returns the metaData that was used when instantiating the plugin.

### QString KAbstractConfigModule::name() const {#name}

Returns the name of the config module.

> **Note:** Getter function for property [name](kabstractconfigmodule.md#name-prop).

### bool KAbstractConfigModule::needsAuthorization() const {#needsAuthorization}

Returns `true` if the [authActionName](kabstractconfigmodule.md#authActionName) is not empty.

> **Note:** Getter function for property [needsAuthorization](kabstractconfigmodule.md#needsAuthorization-prop).

*See also* [setAuthActionName](kabstractconfigmodule.md#setAuthActionName)

### bool KAbstractConfigModule::needsSave() const {#needsSave}

Returns `true` when the module has something changed and needs save.

> **Note:** Getter function for property [needsSave](kabstractconfigmodule.md#needsSave-prop).

*See also* [setNeedsSave](kabstractconfigmodule.md#setNeedsSave)()

### \[signal\] void KAbstractConfigModule::needsSaveChanged() {#needsSaveChanged}

Emitted when the state of the modules contents has changed.

This signal is emitted whenever the state of the configuration shown in the module changes. It allows the module container to keep track of unsaved changes.

> **Note:** Notifier signal for property [needsSave](kabstractconfigmodule.md#needsSave-prop).

### bool KAbstractConfigModule::representsDefaults() const {#representsDefaults}

Returns `true` when the module state represents the default settings.

> **Note:** Getter function for property [representsDefaults](kabstractconfigmodule.md#representsDefaults-prop).

*See also* [setRepresentsDefaults](kabstractconfigmodule.md#setRepresentsDefaults)()

### \[signal\] void KAbstractConfigModule::representsDefaultsChanged() {#representsDefaultsChanged}

Emitted when the state of the modules contents has changed in a way that it might represents the defaults settings, or stopped representing them.

> **Note:** Notifier signal for property [representsDefaults](kabstractconfigmodule.md#representsDefaults-prop).

### \[virtual\] void KAbstractConfigModule::save() {#save}

The save method stores the config information as shown in the user interface in the config files.

This method is called when the user clicks "Apply" or "Ok".

### void KAbstractConfigModule::setAuthActionName(const QString &*action*) {#setAuthActionName}

Set if the module's [save](kabstractconfigmodule.md#save)() method requires authorization to be executed.

It will still have to execute the action itself using the KAuth library, so this method is not technically needed to perform the action, but using this method will ensure that hosting applications like System Settings or kcmshell behave correctly.

`action` The action that will be used by this ConfigModule.

*See also* [authActionName](kabstractconfigmodule.md#authActionName)()

### void KAbstractConfigModule::setButtons(const KAbstractConfigModule::Buttons *btn*) {#setButtons}

Sets the `btn` to display.

> **Note:** Setter function for property [buttons](kabstractconfigmodule.md#buttons-prop).

*See also* [buttons](kabstractconfigmodule.md#buttons)

### void KAbstractConfigModule::setDefaultsIndicatorsVisible(bool *visible*) {#setDefaultsIndicatorsVisible}

Changes the defaultness indicator visibility.

`visible` Whether the indicator should be visible.

> **Note:** Setter function for property [defaultsIndicatorsVisible](kabstractconfigmodule.md#defaultsIndicatorsVisible-prop).

*See also* [defaultsIndicatorsVisible](kabstractconfigmodule.md#defaultsIndicatorsVisible)()

### void KAbstractConfigModule::setNeedsSave(bool *needs*) {#setNeedsSave}

Set this property to `true` when the user changes something in the module, signaling that it `needs` a save (such as user pressing Ok or Apply).

> **Note:** Setter function for property [needsSave](kabstractconfigmodule.md#needsSave-prop).

*See also* [needsSave](kabstractconfigmodule.md#needsSave)()

### void KAbstractConfigModule::setRepresentsDefaults(bool *defaults*) {#setRepresentsDefaults}

Set this property to `true` when the user sets the state of the module to the `defaults` settings (e.g. clicking Defaults would do nothing).

> **Note:** Setter function for property [representsDefaults](kabstractconfigmodule.md#representsDefaults-prop).

*See also* [representsDefaults](kabstractconfigmodule.md#representsDefaults)()

### \[since 6.16\] void KAbstractConfigModule::setSupportsInstantApply(bool *supported*) {#setSupportsInstantApply}

Indicate whether a config module supports instant apply.

`supportes` The config module supports instant apply. If false, the settings application is exptected show Apply/OK buttons.

The default is `true`.

> **Note:** Setter function for property [supportsInstantApply](kabstractconfigmodule.md#supportsInstantApply-prop).

This function was introduced in Qt 6.16.

*See also* [supportsInstantApply](kabstractconfigmodule.md#supportsInstantApply)()

### \[since 6.16\] bool KAbstractConfigModule::supportsInstantApply() const {#supportsInstantApply}

Returns if the config module supports instant apply.

Config modules that do not support instant apply only save their settings once Apply/OK are clicked by the user. The settings application is expected to show these buttons.

The default is `true`.

> **Note:** Getter function for property [supportsInstantApply](kabstractconfigmodule.md#supportsInstantApply-prop).

This function was introduced in Qt 6.16.

*See also* [setSupportsInstantApply](kabstractconfigmodule.md#setSupportsInstantApply)()

### \[signal, since 6.16\] void KAbstractConfigModule::supportsInstantApplyChanged() {#supportsInstantApplyChanged}

Emitted when the KCM's [supportsInstantApply](kabstractconfigmodule.md#supportsInstantApply) property changes.

> **Note:** Notifier signal for property [supportsInstantApply](kabstractconfigmodule.md#supportsInstantApply-prop).

This function was introduced in Qt 6.16.
