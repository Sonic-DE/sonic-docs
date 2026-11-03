---
title: "Plasma::Corona Class"
description: "A bookkeeping Scene for Plasma::Applets."
---

# Plasma::Corona Class

A bookkeeping Scene for Plasma::Applets. [More...](#details)

- **Header:** `#include <Plasma/Corona>`
- **CMake:** `find_package(Plasma REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Plasma::Plasma)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](plasma-corona-members.md)

## Properties

- [editMode : bool](#editMode-prop)
- [\[read-only\] isStartupCompleted : bool](#isStartupCompleted-prop)
- [\[read-only\] kPackage : KPackage::Package](#kPackage-prop)

## Public Functions

- [Corona(QObject \*parent = nullptr)](#Corona)
- [QAction \*action(const QString &name) const](#action)
- [QList\<QAction \*\> actions() const](#actions)
- [QRect availableScreenRect(int id) const](#availableScreenRect)
- [QRegion availableScreenRegion(int id) const](#availableScreenRegion)
- [KSharedConfig::Ptr config() const](#config)
- [Plasma::Containment \*containmentForScreen(int screen, const QString &activity, const QString &defaultPluginIfNonExistent, const QVariantList &defaultArgs = QVariantList())](#containmentForScreen)
- [QList\<Plasma::Containment \*\> containments() const](#containments)
- [QList\<Plasma::Containment \*\> containmentsForActivity(const QString &activity)](#containmentsForActivity)
- [QList\<Plasma::Containment \*\> containmentsForScreen(int screen)](#containmentsForScreen)
- [Plasma::Containment \*createContainment(const QString &name, const QVariantList &args = QVariantList())](#createContainment)
- [void exportLayout(KConfigGroup &config, QList\<Plasma::Containment \*\> containments)](#exportLayout)
- [QList\<Plasma::Types::Location\> freeEdges(int screen) const](#freeEdges)
- [Plasma::Types::ImmutabilityType immutability() const](#immutability)
- [bool immutable() const](#immutable) (since 6.4)
- [QList\<Plasma::Containment \*\> importLayout(const KConfigGroup &config)](#importLayout)
- [bool isEditMode() const](#isEditMode)
- [bool isStartupCompleted() const](#isStartupCompleted)
- [KPackage::Package kPackage() const](#kPackage)
- [int numScreens() const](#numScreens)
- [void removeAction(const QString &name)](#removeAction)
- [int screenForContainment(const Plasma::Containment \*containment) const](#screenForContainment)
- [QRect screenGeometry(int id) const](#screenGeometry)
- [void setAction(const QString &name, QAction \*action)](#setAction)
- [void setEditMode(bool edit)](#setEditMode)
- [void setKPackage(const KPackage::Package &package)](#setKPackage)

## Public Slots

- [void loadLayout(const QString &config = QString())](#loadLayout)
- [void requestConfigSync()](#requestConfigSync)
- [void requireConfigSync()](#requireConfigSync)
- [void saveLayout(const QString &config = QString()) const](#saveLayout)
- [void setImmutability(const Plasma::Types::ImmutabilityType immutable)](#setImmutability)

## Signals

- [void availableScreenRectChanged(int id)](#availableScreenRectChanged)
- [void availableScreenRegionChanged(int id)](#availableScreenRegionChanged)
- [void configSynced()](#configSynced)
- [void containmentAdded(Plasma::Containment \*containment)](#containmentAdded)
- [void containmentCreated(Plasma::Containment \*containment)](#containmentCreated)
- [void containmentUiReadyChanged(Plasma::Containment \*containment, bool uiReady)](#containmentUiReadyChanged) (since 6.8)
- [void editModeChanged(bool edit)](#editModeChanged)
- [void immutabilityChanged(Plasma::Types::ImmutabilityType immutability)](#immutabilityChanged)
- [void kPackageChanged(const KPackage::Package &package)](#kPackageChanged)
- [void screenAdded(int id)](#screenAdded)
- [void screenGeometryChanged(int id)](#screenGeometryChanged)
- [void screenOwnerChanged(int isScreen)](#screenOwnerChanged)
- [void screenRemoved(int id)](#screenRemoved)
- [void startupCompleted()](#startupCompleted)

## Protected Functions

- [Plasma::Containment \*createContainmentDelayed(const QString &name, const QVariantList &args = QVariantList())](#createContainmentDelayed)
- [void loadDefaultLayout()](#loadDefaultLayout)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### editMode : bool {#editMode-prop}

**Access functions:**

- `bool` **[isEditMode](plasma-corona.md#isEditMode)**() const
- `void` **[setEditMode](plasma-corona.md#setEditMode)**(`bool` *edit*)

**Notifier signal:**

- `void` **[editModeChanged](plasma-corona.md#editModeChanged)**(`bool` *edit*)

### \[read-only\] isStartupCompleted : bool {#isStartupCompleted-prop}

**Access functions:**

- `bool` **[isStartupCompleted](plasma-corona.md#isStartupCompleted)**() const

**Notifier signal:**

- `void` **[startupCompleted](plasma-corona.md#startupCompleted)**()

### \[read-only\] kPackage : KPackage::Package {#kPackage-prop}

**Access functions:**

- `KPackage::Package` **[kPackage](plasma-corona.md#kPackage)**() const

**Notifier signal:**

- `void` **[kPackageChanged](plasma-corona.md#kPackageChanged)**(const `KPackage::Package` &*package*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Corona::Corona(QObject \**parent* = nullptr) {#Corona}

Constructor

### \[invokable\] QAction \*Corona::action(const QString &*name*) const {#action}

Returns the action with the given name, if any

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [setAction](plasma-corona.md#setAction)()

### QList\<QAction \*\> Corona::actions() const {#actions}

Returns all the actions supported by the corona

### \[virtual\] QRect Corona::availableScreenRect(int *id*) const {#availableScreenRect}

Returns the available rect for a given screen. The difference between this and [availableScreenRegion](plasma-corona.md#availableScreenRegion)() is that this method returns only a rectangular available space (it doesn't care if your panel is not 100% width). The available rect excludes panels and similar windows. Valid screen ids are 0 to [numScreens](plasma-corona.md#numScreens)()-1. By default this method returns a rectangular region equal to [screenGeometry](plasma-corona.md#screenGeometry)(id); subclasses that need another behavior should override this method.

### \[signal\] void Corona::availableScreenRectChanged(int *id*) {#availableScreenRectChanged}

This signal indicates that a change in available screen geometry occurred.

### \[virtual\] QRegion Corona::availableScreenRegion(int *id*) const {#availableScreenRegion}

Returns the available region for a given screen. The available region excludes panels and similar windows. Valid screen ids are 0 to [numScreens](plasma-corona.md#numScreens)()-1. By default this method returns a rectangular region equal to [screenGeometry](plasma-corona.md#screenGeometry)(id); subclasses that need another behavior should override this method.

### \[signal\] void Corona::availableScreenRegionChanged(int *id*) {#availableScreenRegionChanged}

This signal indicates that a change in available screen geometry occurred.

### KSharedConfig::Ptr Corona::config() const {#config}

Returns the config file used to store the configuration for this Corona

### \[signal\] void Corona::configSynced() {#configSynced}

This signal indicates that the configuration file was flushed to disk.

### \[signal\] void Corona::containmentAdded(Plasma::Containment \**containment*) {#containmentAdded}

This signal indicates a new containment has been added to the Corona: it may occur after creation or restore from config

### \[signal\] void Corona::containmentCreated(Plasma::Containment \**containment*) {#containmentCreated}

This signal indicates a new containment has been created in the Corona. Compared to [containmentAdded](plasma-corona.md#containmentAdded) it can only happen after the creation of a new containment.

*See also* [containmentAdded](plasma-corona.md#containmentAdded)

### Plasma::Containment \*Corona::containmentForScreen(int *screen*, const QString &*activity*, const QString &*defaultPluginIfNonExistent*, const QVariantList &*defaultArgs* = QVariantList()) {#containmentForScreen}

Returns the Containment for a given physical screen and desktop, creating one if none exists

`screen` number of the physical screen to locate

`activity` the activity id of the containment we want, and empty string if the activity is not important `defaultPluginIfNonExistent` the plugin to load by default; "null" won't create it and "default" creates the default plugin

`defaultArgs` optional arguments to pass in when creating a Containment if needed

### \[signal, since 6.8\] void Corona::containmentUiReadyChanged(Plasma::Containment \**containment*, bool *uiReady*) {#containmentUiReadyChanged}

This signal indicates that the uiReady state of a containment is changed

`containment` The containment that changed, usually it is just done loading its own QML ui `uiReady` Whether now the ui of the containment is ready or not

This function was introduced in Qt 6.8.

*See also* [Containment::uiReadyChanged](plasma-containment.md#uiReadyChanged)

### QList\<Plasma::Containment \*\> Corona::containments() const {#containments}

Returns all containments on this Corona

### QList\<Plasma::Containment \*\> Corona::containmentsForActivity(const QString &*activity*) {#containmentsForActivity}

Returns all containments which match a particular activity, for any screen `activity` the activity id we want Returns the list of matching containments if any, empty if activity is an empty string

### QList\<Plasma::Containment \*\> Corona::containmentsForScreen(int *screen*) {#containmentsForScreen}

Returns all containments which match a particular screen, for any activity

`screen` the screen number we want

Returns the list of matching containments if any, empty if screen is \< 0

### Plasma::Containment \*Corona::createContainment(const QString &*name*, const QVariantList &*args* = QVariantList()) {#createContainment}

Adds a Containment to the Corona

`name` the plugin name for the containment, as given by KPluginInfo::pluginName(). If an empty string is passed in, the default containment plugin will be used (usually DesktopContainment). If the string literal "null" is passed in, then no plugin will be loaded and a simple Containment object will be created instead.

`args` argument list to pass to the containment

Returns a pointer to the containment on success, or 0 on failure. Failure can be caused by too restrictive of an Immutability type, as containments cannot be added when widgets are locked. If the requested containment plugin can not be located or successfully loaded, the Containment will have an invalid pluginInfo().

### \[protected\] Plasma::Containment \*Corona::createContainmentDelayed(const QString &*name*, const QVariantList &*args* = QVariantList()) {#createContainmentDelayed}

Loads a containment with delayed initialization, primarily useful for implementations of [loadDefaultLayout](plasma-corona.md#loadDefaultLayout). The caller is responsible for all initialization, saving and notification of a new containment.

`name` the plugin name for the containment, as given by KPluginInfo::pluginName(). If an empty string is passed in, the default containment plugin will be used (usually DesktopContainment). If the string literal "null" is passed in, then no plugin will be loaded and a simple Containment object will be created instead.

`args` argument list to pass to the containment

Returns a pointer to the containment on success, or 0 on failure. Failure can be caused by the Immutability type being too restrictive, as containments can't be added when widgets are locked, or if the requested containment plugin can not be located or successfully loaded.

*See also* [createContainment](plasma-corona.md#createContainment)

### \[signal\] void Corona::editModeChanged(bool *edit*) {#editModeChanged}

emitted when the [editMode](plasma-corona.md#editMode-prop) state changes

> **Note:** Notifier signal for property [editMode](plasma-corona.md#editMode-prop).

*See also* [isEditMode](plasma-corona.md#isEditMode)()

### void Corona::exportLayout(KConfigGroup &*config*, QList\<Plasma::Containment \*\> *containments*) {#exportLayout}

Exports a set of containments to a config file.

`config` the config group to save to

`containments` the list of containments to save

### QList\<Plasma::Types::Location\> Corona::freeEdges(int *screen*) const {#freeEdges}

This method is useful in order to retrieve the list of available screen edges for panel type containments.

`screen` the id of the screen to look for free edges.

Returns a list of free edges not filled with panel type containments.

### Plasma::Types::ImmutabilityType Corona::immutability() const {#immutability}

Returns the type of immutability of this Corona

*See also* [setImmutability](plasma-corona.md#setImmutability)()

### \[signal\] void Corona::immutabilityChanged(Plasma::Types::ImmutabilityType *immutability*) {#immutabilityChanged}

emitted when immutability changes. this is for use by things that don't get constraints events, like plasmaapp. it's NOT for containments or applets or any of the other stuff on the scene. if your code's not in shells/ it probably shouldn't be using it.

### \[since 6.4\] bool Corona::immutable() const {#immutable}

Returns `true` if [immutability](plasma-corona.md#immutability)() is not [Types::Mutable](plasma-types.md#ImmutabilityType-enum)

This function was introduced in Qt 6.4.

### QList\<Plasma::Containment \*\> Corona::importLayout(const KConfigGroup &*config*) {#importLayout}

Imports an applet layout from a config file. The results will be added to the current set of Containments.

`config` the name of the config file to load from, or the default config file if QString()

Returns the list of containments that were loaded

### bool Corona::isEditMode() const {#isEditMode}

Returns true if the corona is in edit mode

> **Note:** Getter function for property [editMode](plasma-corona.md#editMode-prop).

### bool Corona::isStartupCompleted() const {#isStartupCompleted}

Returns true when the startup is over, and all the ui graphics has been instantiated

> **Note:** Getter function for property [isStartupCompleted](plasma-corona.md#isStartupCompleted-prop).

### KPackage::Package Corona::kPackage() const {#kPackage}

Accessor for the associated Package object if any. A Corona package defines how Containments are laid out in a View, ToolBoxes, default layout, error messages and in general all the furniture specific of a particular device form factor.

Returns the package object, or an invalid one if none

> **Note:** Getter function for property [kPackage](plasma-corona.md#kPackage-prop).

*See also* [setKPackage](plasma-corona.md#setKPackage)()

### \[signal\] void Corona::kPackageChanged(const KPackage::Package &*package*) {#kPackageChanged}

Emitted when the package for this corona has been changed. Shells must support changing the shell package on the fly (for instance due to device form factor changing)

`package` the new package that defines the Corona furniture and behavior

> **Note:** Notifier signal for property [kPackage](plasma-corona.md#kPackage-prop).

### \[virtual protected\] void Corona::loadDefaultLayout() {#loadDefaultLayout}

Loads the default (system wide) layout for this user

### \[slot\] void Corona::loadLayout(const QString &*config* = QString()) {#loadLayout}

Load applet layout from a config file. The results will be added to the current set of Containments.

`config` the name of the config file to load from, or the default config file if QString()

### \[virtual\] int Corona::numScreens() const {#numScreens}

Returns the number of screens available to plasma. Subclasses should override this method as the default implementation returns a meaningless value.

### void Corona::removeAction(const QString &*name*) {#removeAction}

Remove the action with the given name, if exists

### \[slot\] void Corona::requestConfigSync() {#requestConfigSync}

Schedules a flush-to-disk synchronization of the configuration state at the next convenient moment.

### \[slot\] void Corona::requireConfigSync() {#requireConfigSync}

Schedules a time sensitive flush-to-disk synchronization of the configuration state. Since this method does not provide any sort of event compression, it should only be used when an \*immediate\* disk sync is \*absolutely\* required. Otherwise, use [requestConfigSync](plasma-corona.md#requestConfigSync)() which does do event compression.

### \[slot\] void Corona::saveLayout(const QString &*config* = QString()) const {#saveLayout}

Save applets layout to file

`config` the file to save to, or the default config file if QString()

### \[signal\] void Corona::screenAdded(int *id*) {#screenAdded}

This signal indicates a new screen with the specified id was added.

### \[virtual\] int Corona::screenForContainment(const Plasma::Containment \**containment*) const {#screenForContainment}

Returns the id of the screen which is showing `containment` -1 is returned if the containment is not associated with a screen.

### \[pure virtual\] QRect Corona::screenGeometry(int *id*) const {#screenGeometry}

Returns the geometry of a given screen. Valid screen ids are 0 to numScreen()-1, or -1 for the full desktop geometry. Subclasses should override this method as the default implementation returns a meaningless value.

### \[signal\] void Corona::screenGeometryChanged(int *id*) {#screenGeometryChanged}

This signal indicates that a change in geometry for the screen occurred.

### \[signal\] void Corona::screenOwnerChanged(int *isScreen*) {#screenOwnerChanged}

This signal indicates that a containment has been newly associated (or dissociated) with a physical screen.

`isScreen` the screen it is now associated with

### \[signal\] void Corona::screenRemoved(int *id*) {#screenRemoved}

This signal indicates the screen with the specified id was removed.

### void Corona::setAction(const QString &*name*, QAction \**action*) {#setAction}

Defines a new action with the given name in the internal collection

*See also* [action](plasma-corona.md#action)()

### void Corona::setEditMode(bool *edit*) {#setEditMode}

Set the Corona globally into "edit mode".

Only when the corona is of mutable type can it be set to edit mode. This changes the UI to make it easy for the user to manipulate applets.

`edit` Whether to open or close edit mode

> **Note:** Setter function for property [editMode](plasma-corona.md#editMode-prop).

*See also* [isEditMode](plasma-corona.md#isEditMode)()

### \[slot\] void Corona::setImmutability(const Plasma::Types::ImmutabilityType *immutable*) {#setImmutability}

Sets the immutability type for this Corona (not immutable, user immutable or system immutable)

`immutable` the new immutability type of this applet

*See also* [immutability](plasma-corona.md#immutability)()

### void Corona::setKPackage(const KPackage::Package &*package*) {#setKPackage}

Setting the package for the corona

*See also* [kPackage](plasma-corona.md#kPackage)()

### \[signal\] void Corona::startupCompleted() {#startupCompleted}

Emitted when the startup phase has been completed

> **Note:** Notifier signal for property [isStartupCompleted](plasma-corona.md#isStartupCompleted-prop).
