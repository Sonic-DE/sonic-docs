---
title: "Plasma::ContainmentActions Class"
description: "The base ContainmentActions class."
---

# Plasma::ContainmentActions Class

The base [ContainmentActions](plasma-containmentactions.md) class. [More...](#details)

- **Header:** `#include <Plasma/ContainmentActions>`
- **CMake:** `find_package(Plasma REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Plasma::Plasma)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](plasma-containmentactions-members.md)

## Public Functions

- [ContainmentActions(QObject \*parent = nullptr)](#ContainmentActions)
- [void configurationAccepted()](#configurationAccepted)
- [Plasma::Containment \*containment()](#containment)
- [QList\<QAction \*\> contextualActions()](#contextualActions)
- [QWidget \*createConfigurationInterface(QWidget \*parent)](#createConfigurationInterface)
- [bool hasConfigurationInterface() const](#hasConfigurationInterface) (since 6.4)
- [QString id() const](#id) (since 6.4)
- [KPluginMetaData metadata() const](#metadata)
- [void performNextAction()](#performNextAction)
- [void performPreviousAction()](#performPreviousAction)
- [void restore(const KConfigGroup &config)](#restore)
- [void save(KConfigGroup &config)](#save)
- [void setContainment(Plasma::Containment \*newContainment)](#setContainment)

## Static Public Members

- [QString eventToString(QEvent \*event)](#eventToString)

## Protected Functions

- [ContainmentActions(QObject \*parent, const QVariantList &args)](#ContainmentActions-1)

## Detailed Description {#details}

"[ContainmentActions](plasma-containmentactions.md)" are components that provide actions (usually displaying a contextmenu) in response to an event with a position (usually a mouse event).

[ContainmentActions](plasma-containmentactions.md) plugins are registered using .desktop files. These files should be named using the following naming scheme:

`plasma-containmentactions-\<pluginname\>.desktop`

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ContainmentActions::ContainmentActions(QObject \**parent* = nullptr) {#ContainmentActions}

Default constructor for an empty or null containmentactions

### \[protected\] ContainmentActions::ContainmentActions(QObject \**parent*, const QVariantList &*args*) {#ContainmentActions-1}

This constructor is to be used with the plugin loading systems found in KPluginInfo and KService. The argument list is expected to have one element: the KService service ID for the desktop entry.

`parent` a [QObject](https://doc.qt.io/qt-6/qobject.html) parent; you probably want to pass in 0

`args` a list of strings containing one entry: the service id

### \[virtual\] void ContainmentActions::configurationAccepted() {#configurationAccepted}

This method is called when the user's configuration changes are accepted

### Plasma::Containment \*ContainmentActions::containment() {#containment}

Returns the containment the plugin is associated with.

*See also* [setContainment](plasma-containmentactions.md#setContainment)()

### \[virtual\] QList\<QAction \*\> ContainmentActions::contextualActions() {#contextualActions}

Implement this to provide a list of actions that can be added to another menu for example, when right-clicking an applet, the "Activity Options" submenu is populated with this.

### \[virtual\] QWidget \*ContainmentActions::createConfigurationInterface(QWidget \**parent*) {#createConfigurationInterface}

Returns the widget used in the configuration dialog. Add the configuration interface of the containmentactions to this widget.

### \[static\] QString ContainmentActions::eventToString(QEvent \**event*) {#eventToString}

Turns a mouse or wheel event into a string suitable for a [ContainmentActions](plasma-containmentactions.md) Returns the string representation of the event

### \[since 6.4\] bool ContainmentActions::hasConfigurationInterface() const {#hasConfigurationInterface}

Returns whether this plugin has a configuration UI

This function was introduced in Qt 6.4.

### \[since 6.4\] QString ContainmentActions::id() const {#id}

Returns the ID of this plugin

This function was introduced in Qt 6.4.

### KPluginMetaData ContainmentActions::metadata() const {#metadata}

Returns the metadata for this [ContainmentActions](plasma-containmentactions.md) instance including name, pluginName and icon

### \[virtual\] void ContainmentActions::performNextAction() {#performNextAction}

Called when a "next" action is triggered (e.g. by mouse wheel scroll). This can be used to scroll through a list of items this plugin manages such as windows, virtual desktops, activities, etc.

*See also* performPrevious

### \[virtual\] void ContainmentActions::performPreviousAction() {#performPreviousAction}

Called when a "previous" action is triggered (e.g. by mouse wheel scroll). This can be used to scroll through a list of items this plugin manages such as windows, virtual desktops, activities, etc.

*See also* performNext

### \[virtual\] void ContainmentActions::restore(const KConfigGroup &*config*) {#restore}

This method should be called once the plugin is loaded or settings are changed.

`config` Config group to load settings

*See also* init

### \[virtual\] void ContainmentActions::save(KConfigGroup &*config*) {#save}

This method is called when settings need to be saved.

`config` Config group to save settings

### void ContainmentActions::setContainment(Plasma::Containment \**newContainment*) {#setContainment}

`newContainment` the containment the plugin should be associated with.

*See also* [containment](plasma-containmentactions.md#containment)()
