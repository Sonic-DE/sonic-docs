---
title: "KPluginWidget Class"
description: "A widget that shows a list of available plugins and allows to disable/enable them and open their configuration UI."
---

# KPluginWidget Class

A widget that shows a list of available plugins and allows to disable/enable them and open their configuration UI. [More...](#details)

- **Header:** `#include <KPluginWidget>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KCMUtils)`  
  `target_link_libraries(mytarget PRIVATE KF6::KCMUtils)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kpluginwidget-members.md)

## Public Functions

- [KPluginWidget(QWidget \*parent = nullptr)](#KPluginWidget)
- [void addPlugins(const QList\<KPluginMetaData\> &plugins, const QString &categoryLabel)](#addPlugins)
- [void clear()](#clear)
- [QVariantList configurationArguments() const](#configurationArguments)
- [void defaults()](#defaults)
- [bool isDefault() const](#isDefault)
- [bool isSaveNeeded() const](#isSaveNeeded)
- [void load()](#load)
- [void save()](#save)
- [void setAdditionalButtonHandler(const std::function\<QPushButton \*(const KPluginMetaData &)\> &handler)](#setAdditionalButtonHandler)
- [void setConfig(const KConfigGroup &config)](#setConfig)
- [void setConfigurationArguments(const QVariantList &arguments)](#setConfigurationArguments)
- [void setDefaultsIndicatorsVisible(bool isVisible)](#setDefaultsIndicatorsVisible)
- [void showConfiguration(const QString &pluginId)](#showConfiguration)

## Signals

- [void changed(bool enabled)](#changed)
- [void defaulted(bool isDefault)](#defaulted)
- [void pluginConfigSaved(const QString &pluginId)](#pluginConfigSaved)
- [void pluginEnabledChanged(const QString &pluginId, bool enabled)](#pluginEnabledChanged)

## Detailed Description {#details}

Plugins that get added to the [KPluginWidget](kpluginwidget.md) need to define the `X-KDE-ConfigModule` property. The value for this property is the namespace and file name of the KCM for the plugin.

An example value is "kf6/krunner/kcms/kcm\_krunner\_charrunner", "kf6/krunner/kcms" is the namespace and "kcm\_krunner\_charrunner" the file name. The loaded KCMs don't need any embedded JSON metadata.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KPluginWidget::KPluginWidget(QWidget \**parent* = nullptr) {#KPluginWidget}

### void KPluginWidget::addPlugins(const QList\<KPluginMetaData\> &*plugins*, const QString &*categoryLabel*) {#addPlugins}

Adds the `plugins` with the given `categoryLabel` to the widget.

### \[signal\] void KPluginWidget::changed(bool *enabled*) {#changed}

Emitted when any of the plugins are changed.

`enabled` Whether the given plugin is enabled.

*See also* [isSaveNeeded](kpluginwidget.md#isSaveNeeded)()

### void KPluginWidget::clear() {#clear}

Clears all the added plugins and any unsaved changes.

### QVariantList KPluginWidget::configurationArguments() const {#configurationArguments}

Returns the configuration arguments that will be used.

*See also* [setConfigurationArguments](kpluginwidget.md#setConfigurationArguments)()

### \[signal\] void KPluginWidget::defaulted(bool *isDefault*) {#defaulted}

Emitted after configuration is changed.

`isDefault` Returns whether the configuration state is the default.

### void KPluginWidget::defaults() {#defaults}

Resets the enabled state of the plugins to their defaults.

*See also* [KPluginMetaData::isEnabledByDefault](../kcoreaddons/kpluginmetadata.md#isEnabledByDefault)

### bool KPluginWidget::isDefault() const {#isDefault}

Returns `true` if the enabled state of each plugin is the same as that plugin's default state.

### bool KPluginWidget::isSaveNeeded() const {#isSaveNeeded}

Returns true if the plugin selector has any changes that are not yet saved to configuration.

*See also* [save](kpluginwidget.md#save)()

### void KPluginWidget::load() {#load}

Loads the enabled state of the plugins from the config set by [setConfig](kpluginwidget.md#setConfig)() and clears any changes by the user.

### \[signal\] void KPluginWidget::pluginConfigSaved(const QString &*pluginId*) {#pluginConfigSaved}

Emitted after the config of an embedded KCM has been saved.

The `pluginId` is the name of the parent component that needs to reload its config.

### \[signal\] void KPluginWidget::pluginEnabledChanged(const QString &*pluginId*, bool *enabled*) {#pluginEnabledChanged}

Emitted when any of the plugins are changed.

`pluginId` The ID of the changed plugin.

`enabled` Whether the given plugin is currently enabled.

### void KPluginWidget::save() {#save}

Saves the changes to the config set by [setConfig](kpluginwidget.md#setConfig).

### void KPluginWidget::setAdditionalButtonHandler(const std::function\<QPushButton \*(const KPluginMetaData &)\> &*handler*) {#setAdditionalButtonHandler}

Add additional widgets to each row of the plugin selector.

`handler` Returns the additional button that should be displayed in the row; the handler can return a null pointer if no button should be displayed.

### void KPluginWidget::setConfig(const KConfigGroup &*config*) {#setConfig}

Sets the `config` object that will be used to store the enabled state of the plugins.

When porting away from KPluginSelector, the "Plugins" group from the config root should be used. For example:

```cpp
KSharedConfig::openConfig(QStringLiteral("krunnerrc"))->group("Plugins")
```

### void KPluginWidget::setConfigurationArguments(const QVariantList &*arguments*) {#setConfigurationArguments}

Sets the `arguments` with which the configuration modules will be initialized.

*See also* [configurationArguments](kpluginwidget.md#configurationArguments)()

### void KPluginWidget::setDefaultsIndicatorsVisible(bool *isVisible*) {#setDefaultsIndicatorsVisible}

Shows an indicator when a plugin status is different from default.

`isVisible` Whether the indicator is visible.

### void KPluginWidget::showConfiguration(const QString &*pluginId*) {#showConfiguration}

Shows the configuration dialog for the plugin `pluginId` if it's available.
