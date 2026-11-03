---
title: "KConfigDialogManager Class"
description: "Provides a means of automatically retrieving, saving and resetting KConfigSkeleton based settings in a dialog."
---

# KConfigDialogManager Class

Provides a means of automatically retrieving, saving and resetting [KConfigSkeleton](../kconfiggui/kconfigskeleton.md) based settings in a dialog. [More...](#details)

- **Header:** `#include <KConfigDialogManager>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ConfigWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigWidgets)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kconfigdialogmanager-members.md)

## Public Functions

- [KConfigDialogManager(QWidget \*parent, KCoreConfigSkeleton \*conf)](#KConfigDialogManager)
- [void addWidget(QWidget \*widget)](#addWidget)
- [bool hasChanged() const](#hasChanged)
- [bool isDefault() const](#isDefault)

## Public Slots

- [void setDefaultsIndicatorsVisible(bool enabled)](#setDefaultsIndicatorsVisible)
- [void updateSettings()](#updateSettings)
- [void updateWidgets()](#updateWidgets)
- [void updateWidgetsDefault()](#updateWidgetsDefault)

## Signals

- [void settingsChanged()](#settingsChanged)
- [void widgetModified()](#widgetModified)

## Static Public Members

- [void initMaps()](#initMaps)
- [QHash\<QString, QByteArray\> \*propertyMap()](#propertyMap)

## Protected Functions

- [QByteArray getCustomProperty(const QWidget \*widget) const](#getCustomProperty)
- [QByteArray getCustomPropertyChangedSignal(const QWidget \*widget) const](#getCustomPropertyChangedSignal)
- [QByteArray getUserProperty(const QWidget \*widget) const](#getUserProperty)
- [QByteArray getUserPropertyChangedSignal(const QWidget \*widget) const](#getUserPropertyChangedSignal)
- [void init(bool trackChanges)](#init)
- [bool parseChildren(const QWidget \*widget, bool trackChanges)](#parseChildren)
- [QVariant property(QWidget \*w) const](#property)
- [void setProperty(QWidget \*w, const QVariant &v)](#setProperty)
- [void setupWidget(QWidget \*widget, KConfigSkeletonItem \*item)](#setupWidget)

## Detailed Description {#details}

The [KConfigDialogManager](kconfigdialogmanager.md) class provides a means of automatically retrieving, saving and resetting basic settings. It also can emit signals when settings have been changed (settings were saved) or modified (the user changes a checkbox from on to off).

The object names of the widgets to be managed have to correspond to the names of the configuration entries in the [KConfigSkeleton](../kconfiggui/kconfigskeleton.md) object plus an additional "kcfg\_" prefix. For example a widget with the object name "kcfg\_MyOption" would be associated to the configuration entry "MyOption".

The widget classes of Qt and KDE Frameworks are supported out of the box, for other widgets see below:

### Using Custom Widgets {#using-custom-widgets}

Custom widget classes are supported if they have a [Q\_PROPERTY](https://doc.qt.io/qt-6/qobject.html#Q_PROPERTY) defined for the property representing the value edited by the widget. By default the property is used for which "USER true" is set. For using another property, see below.

Example:

A class ColorEditWidget is used in the settings UI to select a color. The color value is set and read as type [QColor](https://doc.qt.io/qt-6/qcolor.html). For that it has a definition of the value property similar to this:

```cpp
Q_PROPERTY(QColor color READ color WRITE setColor NOTIFY colorChanged USER true)
```

And of course it has the definition and implementation of the respective read & write methods and the notify signal. This class then can be used directly with [KConfigDialogManager](kconfigdialogmanager.md) and does not need further setup.

### Using Other Properties than The USER Property {#using-other-properties-than-the-user-property}

To use a widget's property that is not the USER property, the property to use can be selected by setting onto the widget instance a property with the key "kcfg\_property" and as the value the name of the property:

```cpp
ColorEditWidget *myWidget = new ColorEditWidget;
myWidget->setProperty("kcfg_property", QByteArray("redColorPart"));
```

This selection of the property to use is just valid for this widget instance. When using a UI file, the "kcfg\_property" property can also be set using Qt Designer.

### Configuring Classes to use Other Properties Globally {#configuring-classes-to-use-other-properties-globally}

Alternatively a non-USER property can be defined for a widget class globally by registering it for the class in the [KConfigDialogManager::propertyMap](kconfigdialogmanager.md#propertyMap)(). This global registration has lower priority than any "kcfg\_property" property set on a class instance though, so the latter overrules this global setting. Note: setting the property in the [propertyMap](kconfigdialogmanager.md#propertyMap) affects any instances of that widget class in the current application, so use only when needed and prefer instead the "kcfg\_property" property. Especially with software with many libraries and 3rd-party plugins in one process there is a chance of conflicting settings.

Example:

If the ColorEditWidget has another property redColor defined by

```cpp
Q_PROPERTY(int redColorPart READ redColorPart WRITE setRedColorPart NOTIFY redColorPartChanged)
```

and this one should be used in the settings, call somewhere in the code before using the settings:

```cpp
KConfigDialogManager::propertyMap()->insert("ColorEditWidget", QByteArray("redColorPart"));
```

### Using Different Signals than The NOTIFY Signal {#using-different-signals-than-the-notify-signal}

If some non-default signal should be used, e.g. because the property to use does not have a NOTIFY setting, for a given widget instance the signal to use can be set by a property with the key "kcfg\_propertyNotify" and as the value the signal signature. This will take priority over the signal noted by NOTIFY for the chosen property as well as the content of KConfigDialogManager::changedMap(). Since 5.32.

Example:

If for a class OtherColorEditWidget there was no NOTIFY set on the USER property, but some signal colorSelected([QColor](https://doc.qt.io/qt-6/qcolor.html)) defined which would be good enough to reflect the settings change, defined by

```cpp
Q_PROPERTY(QColor color READ color WRITE setColor USER true)
Q_SIGNALS:
    void colorSelected(const QColor &color);
```

the signal to use would be defined by this:

```cpp
OtherColorEditWidget *myWidget = new OtherColorEditWidget;
myWidget->setProperty("kcfg_propertyNotify", QByteArray(SIGNAL(colorSelected(QColor))));
```

## Member Function Documentation {#member-function-documentation}

### KConfigDialogManager::KConfigDialogManager(QWidget \**parent*, KCoreConfigSkeleton \**conf*) {#KConfigDialogManager}

Constructor.

`parent` Dialog widget to manage

`conf` Object that contains settings

### void KConfigDialogManager::addWidget(QWidget \**widget*) {#addWidget}

Add additional widgets to manage

`widget` Additional widget to manage, including all its children

### \[protected\] QByteArray KConfigDialogManager::getCustomProperty(const QWidget \**widget*) const {#getCustomProperty}

Find the property to use for a widget by querying the "kcfg\_property" property of the widget. Like a widget can use a property other than the USER property.

### \[protected\] QByteArray KConfigDialogManager::getCustomPropertyChangedSignal(const QWidget \**widget*) const {#getCustomPropertyChangedSignal}

Find the changed signal of the property to use for a widget by querying the "kcfg\_propertyNotify" property of the widget. Like a widget can use a property change signal other than the one for USER property, if there even is one.

### \[protected\] QByteArray KConfigDialogManager::getUserProperty(const QWidget \**widget*) const {#getUserProperty}

Finds the USER property name using Qt's MetaProperty system, and caches it in the property map (the cache could be retrieved by [propertyMap](kconfigdialogmanager.md#propertyMap)() ).

### \[protected\] QByteArray KConfigDialogManager::getUserPropertyChangedSignal(const QWidget \**widget*) const {#getUserPropertyChangedSignal}

Finds the changed signal of the USER property using Qt's MetaProperty system.

### bool KConfigDialogManager::hasChanged() const {#hasChanged}

Returns whether the current state of the known widgets are different from the state in the config object.

### \[protected\] void KConfigDialogManager::init(bool *trackChanges*) {#init}

`trackChanges` If any changes by the widgets should be tracked set true. This causes the emitting the modified() signal when something changes.

### \[static protected\] void KConfigDialogManager::initMaps() {#initMaps}

Initializes the property maps

### bool KConfigDialogManager::isDefault() const {#isDefault}

Returns whether the current state of the known widgets are the same as the default state in the config object.

### \[protected\] bool KConfigDialogManager::parseChildren(const QWidget \**widget*, bool *trackChanges*) {#parseChildren}

Recursive function that finds all known children.

Goes through the children of widget and if any are known and not being ignored, stores them in currentGroup. Also checks if the widget should be disabled because it is set immutable.

`widget` Parent of the children to look at.

`trackChanges` If `true` then tracks any changes to the children of widget that are known. Returns bool: if a widget was set to something other than its default.

### \[protected\] QVariant KConfigDialogManager::property(QWidget \**w*) const {#property}

Retrieve a property

*See also* [setProperty](kconfigdialogmanager.md#setProperty)()

### \[static\] QHash\<QString, QByteArray\> \*KConfigDialogManager::propertyMap() {#propertyMap}

Retrieve the map between widgets class names and the USER properties used for the configuration values.

### \[slot\] void KConfigDialogManager::setDefaultsIndicatorsVisible(bool *enabled*) {#setDefaultsIndicatorsVisible}

Show or hide an indicator when settings have changed from their default value. Update all widgets to show or hide the indicator accordingly.

### \[protected\] void KConfigDialogManager::setProperty(QWidget \**w*, const QVariant &*v*) {#setProperty}

Set a property

*See also* [property](kconfigdialogmanager.md#property)()

### \[signal\] void KConfigDialogManager::settingsChanged() {#settingsChanged}

One or more of the settings have been saved (such as when the user clicks on the Apply button). This is only emitted by [updateSettings](kconfigdialogmanager.md#updateSettings)() whenever one or more setting were changed and consequently saved.

### \[protected\] void KConfigDialogManager::setupWidget(QWidget \**widget*, KConfigSkeletonItem \**item*) {#setupWidget}

Setup secondary widget properties

### \[slot\] void KConfigDialogManager::updateSettings() {#updateSettings}

Traverse the specified widgets, saving the settings of all known widgets in the settings object.

Example use: User clicks Ok or Apply button in a configure dialog.

### \[slot\] void KConfigDialogManager::updateWidgets() {#updateWidgets}

Traverse the specified widgets, sets the state of all known widgets according to the state in the settings object.

Example use: Initialisation of dialog.

Example use: User clicks Reset button in a configure dialog.

### \[slot\] void KConfigDialogManager::updateWidgetsDefault() {#updateWidgetsDefault}

Traverse the specified widgets, sets the state of all known widgets according to the default state in the settings object.

Example use: User clicks Defaults button in a configure dialog.

### \[signal\] void KConfigDialogManager::widgetModified() {#widgetModified}

If retrieveSettings() was told to track changes then if any known setting was changed this signal will be emitted. Note that a settings can be modified several times and might go back to the original saved state. [hasChanged](kconfigdialogmanager.md#hasChanged)() will tell you if anything has actually changed from the saved values.
