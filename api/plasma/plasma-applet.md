---
title: "Plasma::Applet Class"
description: "The base Applet class."
---

# Plasma::Applet Class

The base Applet class. [More...](#details)

- **Header:** `#include <Plasma/Applet>`
- **CMake:** `find_package(Plasma REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Plasma::Plasma)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)
- **Inherited By:** [Plasma::Containment](plasma-containment.md)

[List of all members, including inherited members](plasma-applet-members.md)

## Public Types

- [enum Applet::Constraint](#Constraint-enum)
- [enum Applet::ConstraintHint](#ConstraintHint-enum)

## Properties

- [backgroundHints : Plasma::Types::BackgroundHints](#backgroundHints-prop)
- [busy : bool](#busy-prop)
- [\[read-only\] configuration : KConfigPropertyMap\* const](#configuration-prop)
- [configurationRequired : bool](#configurationRequired-prop)
- [constraintHints : Plasma::Applet::ConstraintHints](#constraintHints-prop)
- [\[read-only\] containment : Plasma::Containment\*](#containment-prop)
- [\[read-only\] containmentDisplayHints : Plasma::Types::ContainmentDisplayHints](#containmentDisplayHints-prop)
- [\[read-only\] contextualActions : QQmlListProperty\<QAction\>](#contextualActions-prop)
- [\[read-only\] effectiveBackgroundHints : Plasma::Types::BackgroundHints](#effectiveBackgroundHints-prop)
- [\[read-only\] formFactor : Plasma::Types::FormFactor](#formFactor-prop)
- [globalShortcut : QKeySequence](#globalShortcut-prop)
- [hasConfigurationInterface : bool](#hasConfigurationInterface-prop)
- [icon : QString](#icon-prop)
- [\[read-only\] id : const uint](#id-prop)
- [immutability : Plasma::Types::ImmutabilityType](#immutability-prop)
- [\[read-only\] immutable : bool](#immutable-prop)
- [\[read-only\] isContainment : const bool](#isContainment-prop)
- [\[read-only\] location : Plasma::Types::Location](#location-prop)
- [\[read-only\] metaData : const KPluginMetaData](#metaData-prop)
- [\[read-only\] pluginName : const QString](#pluginName-prop)
- [status : Plasma::Types::ItemStatus](#status-prop)
- [title : QString](#title-prop)
- [userBackgroundHints : Plasma::Types::BackgroundHints](#userBackgroundHints-prop)
- [\[read-only\] userConfiguring : bool](#userConfiguring-prop)

## Public Functions

- [Applet(QObject \*parentObject, const KPluginMetaData &data, const QVariantList &args)](#Applet)
- [Plasma::Types::BackgroundHints backgroundHints() const](#backgroundHints)
- [KConfigGroup config() const](#config)
- [KConfigLoader \*configScheme() const](#configScheme)
- [KConfigPropertyMap \*configuration()](#configuration)
- [bool configurationRequired() const](#configurationRequired)
- [QString configurationRequiredReason() const](#configurationRequiredReason)
- [Plasma::Applet::ConstraintHints constraintHints() const](#constraintHints)
- [Plasma::Containment \*containment() const](#containment)
- [Types::ContainmentDisplayHints containmentDisplayHints() const](#containmentDisplayHints)
- [QList\<QAction \*\> contextualActions()](#contextualActions)
- [bool destroyed() const](#destroyed)
- [Plasma::Types::BackgroundHints effectiveBackgroundHints() const](#effectiveBackgroundHints)
- [bool failedToLaunch() const](#failedToLaunch)
- [Plasma::Types::FormFactor formFactor() const](#formFactor)
- [KConfigGroup globalConfig() const](#globalConfig)
- [QKeySequence globalShortcut() const](#globalShortcut)
- [bool hasConfigurationInterface() const](#hasConfigurationInterface)
- [QString icon() const](#icon)
- [uint id() const](#id)
- [Plasma::Types::ImmutabilityType immutability() const](#immutability)
- [bool immutable() const](#immutable)
- [QAction \*internalAction(const QString &name) const](#internalAction)
- [QList\<QAction \*\> internalActions() const](#internalActions)
- [bool isBusy() const](#isBusy)
- [bool isContainment() const](#isContainment)
- [bool isUserConfiguring() const](#isUserConfiguring)
- [QString launchErrorMessage() const](#launchErrorMessage)
- [Plasma::Types::Location location() const](#location)
- [KPluginMetaData pluginMetaData() const](#pluginMetaData)
- [QString pluginName() const](#pluginName)
- [void removeInternalAction(const QString &name)](#removeInternalAction)
- [void restore(KConfigGroup &group)](#restore)
- [void save(KConfigGroup &group) const](#save)
- [void setBackgroundHints(Plasma::Types::BackgroundHints hint)](#setBackgroundHints)
- [void setBusy(bool busy)](#setBusy)
- [void setConfigurationRequired(bool needsConfiguring, const QString &reason = QString())](#setConfigurationRequired)
- [void setConstraintHints(Plasma::Applet::ConstraintHints constraintHints)](#setConstraintHints)
- [void setGlobalShortcut(const QKeySequence &shortcut = QKeySequence())](#setGlobalShortcut)
- [void setHasConfigurationInterface(bool hasInterface)](#setHasConfigurationInterface)
- [void setIcon(const QString &icon)](#setIcon)
- [void setInternalAction(const QString &name, QAction \*action)](#setInternalAction)
- [void setTitle(const QString &title)](#setTitle)
- [void setUserBackgroundHints(Plasma::Types::BackgroundHints hint)](#setUserBackgroundHints)
- [void setUserConfiguring(bool configuring)](#setUserConfiguring)
- [QVariantList startupArguments() const](#startupArguments)
- [Plasma::Types::ItemStatus status() const](#status)
- [QString title() const](#title)
- [QString translationDomain() const](#translationDomain) (since 6.1)
- [void updateConstraints(Plasma::Applet::Constraints constraints = AllConstraints)](#updateConstraints)
- [Plasma::Types::BackgroundHints userBackgroundHints() const](#userBackgroundHints)

## Public Slots

- [void configChanged()](#configChanged)
- [void destroy()](#destroy)
- [void flushPendingConstraintsEvents()](#flushPendingConstraintsEvents)
- [void init()](#init)
- [void setImmutability(const Plasma::Types::ImmutabilityType immutable)](#setImmutability)
- [void setLaunchErrorMessage(const QString &reason = QString())](#setLaunchErrorMessage)
- [void setStatus(const Plasma::Types::ItemStatus stat)](#setStatus)

## Signals

- [void activated()](#activated)
- [void appletDeleted(Plasma::Applet \*applet)](#appletDeleted)
- [void backgroundHintsChanged()](#backgroundHintsChanged)
- [void busyChanged(bool busy)](#busyChanged)
- [void configNeedsSaving()](#configNeedsSaving)
- [void configurationRequiredChanged(bool needsConfig, const QString &reason)](#configurationRequiredChanged)
- [void constraintHintsChanged(Plasma::Applet::ConstraintHints constraintHints)](#constraintHintsChanged)
- [void containmentChanged(Plasma::Containment \*containment)](#containmentChanged)
- [void containmentDisplayHintsChanged(Plasma::Types::ContainmentDisplayHints hints)](#containmentDisplayHintsChanged)
- [void contextualActionsAboutToShow()](#contextualActionsAboutToShow)
- [void contextualActionsChanged(const QList\<QAction \*\> &actions)](#contextualActionsChanged)
- [void destroyedChanged(bool destroyed)](#destroyedChanged)
- [void effectiveBackgroundHintsChanged()](#effectiveBackgroundHintsChanged)
- [void formFactorChanged(Plasma::Types::FormFactor formFactor)](#formFactorChanged)
- [void globalShortcutChanged(const QKeySequence &sequence)](#globalShortcutChanged)
- [void hasConfigurationInterfaceChanged(bool hasConfiguration)](#hasConfigurationInterfaceChanged) (since 6.0)
- [void iconChanged(const QString &icon)](#iconChanged)
- [void immutabilityChanged(Plasma::Types::ImmutabilityType immutable)](#immutabilityChanged)
- [void internalActionsChanged(const QList\<QAction \*\> &actions)](#internalActionsChanged)
- [void locationChanged(Plasma::Types::Location location)](#locationChanged)
- [void secondaryActivated()](#secondaryActivated) (since 6.3)
- [void statusChanged(Plasma::Types::ItemStatus status)](#statusChanged)
- [void titleChanged(const QString &title)](#titleChanged)
- [void userBackgroundHintsChanged()](#userBackgroundHintsChanged)
- [void userConfiguringChanged(bool configuring)](#userConfiguringChanged)

## Protected Functions

- [void constraintsEvent(Plasma::Applet::Constraints constraints)](#constraintsEvent)
- [void saveState(KConfigGroup &config) const](#saveState)

## Detailed Description {#details}

> **Note:** Since 2022 we have standardized on "Plasmoid" for internal API usage and "Widget" as a public facing name. The name "Applet" is kept for backwards compatibility.

Applet provides several important roles for add-ons widgets in Plasma.

First, it is the base class for the plugin system and therefore is the interface to applets for host applications. Background painting (allowing for consistent and complex look and feel in just one line of code for applets), loading and starting of scripting support for each applet, providing access to the associated plasmoid package (if any) and access to configuration data.

See techbase.kde.org for tutorials on writing Applets using this class.

## Member Type Documentation {#member-type-documentation}

### enum Applet::Constraint {#Constraint-enum}

**flags Applet::Constraints**

The Constraint enumeration lists the various constraints that Plasma objects have managed for them and which they may wish to react to, for instance in Applet::constraintsUpdated

| Constant | Value | Description |
| --- | --- | --- |
| `Plasma::Applet::NoConstraint` | `0` | No constraint; never passed in to [Applet::constraintsEvent](plasma-applet.md#constraintsEvent) on its own |
| `Plasma::Applet::FormFactorConstraint` | `1` | The FormFactor for an object |
| `Plasma::Applet::LocationConstraint` | `2` | The Location of an object |
| `Plasma::Applet::ScreenConstraint` | `4` | Which screen an object is on |
| `Plasma::Applet::ImmutableConstraint` | `8` | The immutability (locked) nature of the applet changed |
| `Plasma::Applet::StartupCompletedConstraint` | `16` | Application startup has completed |
| `Plasma::Applet::UiReadyConstraint` | `32` | The ui has been completely loaded |
| `Plasma::Applet::AllConstraints` | `FormFactorConstraint | LocationConstraint | ScreenConstraint | ImmutableConstraint` |   |

The `Constraints` type is a typedef for `QFlags<Constraint>. `It stores an OR combination of `Constraint` values.

### enum Applet::ConstraintHint {#ConstraintHint-enum}

**flags Applet::ConstraintHints**

This enumeration lists the various hints that an applet can pass to its constraint regarding the way that it is represented

| Constant | Value |   |
| --- | --- | --- |
| `Plasma::Applet::NoHint` | `0` |   |
| `Plasma::Applet::CanFillArea` | `1` | The CompactRepresentation can fill the area and ignore constraint margins |
| `Plasma::Applet::MarginAreasSeparator` | `CanFillArea | 2` | The applet acts as a separator between the standard and slim panel margin areas |

The `ConstraintHints` type is a typedef for `QFlags<ConstraintHint>. `It stores an OR combination of `ConstraintHint` values.

## Property Documentation {#property-documentation}

### backgroundHints : Plasma::Types::BackgroundHints {#backgroundHints-prop}

How the plasmoid wants its background to be drawn.

The containment may ignore this hint with [userBackgroundHints](plasma-applet.md#userBackgroundHints).

**Access functions:**

- `Plasma::Types::BackgroundHints` **[backgroundHints](plasma-applet.md#backgroundHints)**() const
- `void` **[setBackgroundHints](plasma-applet.md#setBackgroundHints)**(`Plasma::Types::BackgroundHints` *hint*)

**Notifier signal:**

- `void` **[backgroundHintsChanged](plasma-applet.md#backgroundHintsChanged)**()

### busy : bool {#busy-prop}

True if the applet should show a busy status, for instance while doing some network operation

**Access functions:**

- `bool` **[isBusy](plasma-applet.md#isBusy)**() const
- `void` **[setBusy](plasma-applet.md#setBusy)**(`bool` *busy*)

**Notifier signal:**

- `void` **[busyChanged](plasma-applet.md#busyChanged)**(`bool` *busy*)

### \[read-only\] configuration : KConfigPropertyMap\* const {#configuration-prop}

Configuration for the applet.

Can be used to read and write settings like any JavaScript Object.

**Access functions:**

- `KConfigPropertyMap` \***[configuration](plasma-applet.md#configuration)**()

### configurationRequired : bool {#configurationRequired-prop}

If true, the applet requires manual configuration from the user.

**Access functions:**

- `bool` **[configurationRequired](plasma-applet.md#configurationRequired)**() const
- `void` **[setConfigurationRequired](plasma-applet.md#setConfigurationRequired)**(`bool` *needsConfiguring*, const `QString` &*reason* = QString())

**Notifier signal:**

- `void` **[configurationRequiredChanged](plasma-applet.md#configurationRequiredChanged)**(`bool` *needsConfig*, const `QString` &*reason*)

### constraintHints : Plasma::Applet::ConstraintHints {#constraintHints-prop}

Hints how the applet should be constrained, such as asking to fill all the available space ignoring margins.

**Access functions:**

- `Plasma::Applet::ConstraintHints` **[constraintHints](plasma-applet.md#constraintHints)**() const
- `void` **[setConstraintHints](plasma-applet.md#setConstraintHints)**(`Plasma::Applet::ConstraintHints` *constraintHints*)

**Notifier signal:**

- `void` **[constraintHintsChanged](plasma-applet.md#constraintHintsChanged)**(`Plasma::Applet::ConstraintHints` *constraintHints*)

### \[read-only\] containment : Plasma::Containment\* {#containment-prop}

The Containment managing this applet.

**Access functions:**

- `Plasma::Containment` \***[containment](plasma-applet.md#containment)**() const

**Notifier signal:**

- `void` **[containmentChanged](plasma-applet.md#containmentChanged)**(`Plasma::Containment` \**containment*)

### \[read-only\] containmentDisplayHints : Plasma::Types::ContainmentDisplayHints {#containmentDisplayHints-prop}

Display hints that come from the containment that suggest the applet how to look and behave. TODO: only in containment?

**Access functions:**

- `Types::ContainmentDisplayHints` **[containmentDisplayHints](plasma-applet.md#containmentDisplayHints)**() const

**Notifier signal:**

- `void` **[containmentDisplayHintsChanged](plasma-applet.md#containmentDisplayHintsChanged)**(`Plasma::Types::ContainmentDisplayHints` *hints*)

### \[read-only\] contextualActions : QQmlListProperty\<QAction\> {#contextualActions-prop}

Actions to be added in the plasmoid's context menu.

Use [PlasmaCore](../plasmacore/plasmacore-module.md).Action to instantiate QActions declaratively.

**Access functions:**

- `QQmlListProperty`\<`QAction`\> **qmlContextualActions**()

**Notifier signal:**

- `void` **[contextualActionsChanged](plasma-applet.md#contextualActionsChanged)**(const `QList`\<`QAction` \*\> &*actions*)

### \[read-only\] effectiveBackgroundHints : Plasma::Types::BackgroundHints {#effectiveBackgroundHints-prop}

Returns the effective background hints.

The [userBackgroundHints](plasma-applet.md#userBackgroundHints) will be preferred if set, otherwise returns the plasmoid's [backgroundHints](plasma-applet.md#backgroundHints).

**Access functions:**

- `Plasma::Types::BackgroundHints` **[effectiveBackgroundHints](plasma-applet.md#effectiveBackgroundHints)**() const

**Notifier signal:**

- `void` **[effectiveBackgroundHintsChanged](plasma-applet.md#effectiveBackgroundHintsChanged)**()

### \[read-only\] formFactor : Plasma::Types::FormFactor {#formFactor-prop}

The current form factor the applet is being displayed in.

**Access functions:**

- `Plasma::Types::FormFactor` **[formFactor](plasma-applet.md#formFactor)**() const

**Notifier signal:**

- `void` **[formFactorChanged](plasma-applet.md#formFactorChanged)**(`Plasma::Types::FormFactor` *formFactor*)

### globalShortcut : QKeySequence {#globalShortcut-prop}

The global shortcut to activate the plasmoid.

This is typically only used by the default configuration module.

**Access functions:**

- `QKeySequence` **[globalShortcut](plasma-applet.md#globalShortcut)**() const
- `void` **[setGlobalShortcut](plasma-applet.md#setGlobalShortcut)**(const `QKeySequence` &*shortcut* = QKeySequence())

**Notifier signal:**

- `void` **[globalShortcutChanged](plasma-applet.md#globalShortcutChanged)**(const `QKeySequence` &*sequence*)

### hasConfigurationInterface : bool {#hasConfigurationInterface-prop}

True if this applet will provide a UI for its configuration.

**Access functions:**

- `bool` **[hasConfigurationInterface](plasma-applet.md#hasConfigurationInterface)**() const
- `void` **[setHasConfigurationInterface](plasma-applet.md#setHasConfigurationInterface)**(`bool` *hasInterface*)

**Notifier signal:**

- `void` **[hasConfigurationInterfaceChanged](plasma-applet.md#hasConfigurationInterfaceChanged)**(`bool` *hasConfiguration*)

### icon : QString {#icon-prop}

Icon to represent the applet.

**Access functions:**

- `QString` **[icon](plasma-applet.md#icon)**() const
- `void` **[setIcon](plasma-applet.md#setIcon)**(const `QString` &*icon*)

**Notifier signal:**

- `void` **[iconChanged](plasma-applet.md#iconChanged)**(const `QString` &*icon*)

### \[read-only\] id : const uint {#id-prop}

The applet's id is unique in the whole Plasma session and will never change across restarts.

**Access functions:**

- `uint` **[id](plasma-applet.md#id)**() const

### immutability : Plasma::Types::ImmutabilityType {#immutability-prop}

Sets the immutability of the Corona.

Tells the applet whether it should allow for any modification by the user.

**Access functions:**

- `Plasma::Types::ImmutabilityType` **[immutability](plasma-applet.md#immutability)**() const
- `void` **[setImmutability](plasma-applet.md#setImmutability)**(const `Plasma::Types::ImmutabilityType` *immutable*)

**Notifier signal:**

- `void` **[immutabilityChanged](plasma-applet.md#immutabilityChanged)**(`Plasma::Types::ImmutabilityType` *immutable*)

### \[read-only\] immutable : bool {#immutable-prop}

Whether the Corona is immutable.

The applet implementation should avoid allowing "dangerous" modifications from the user when in an immutable mode.

This is true when immutability is not Mutable.

**Access functions:**

- `bool` **[immutable](plasma-applet.md#immutable)**() const

**Notifier signal:**

- `void` **[immutabilityChanged](plasma-applet.md#immutabilityChanged)**(`Plasma::Types::ImmutabilityType` *immutable*)

### \[read-only\] isContainment : const bool {#isContainment-prop}

Whether this plasmoid is a Containment and is acting as one, such as a desktop or a panel.

**Access functions:**

- `bool` **[isContainment](plasma-applet.md#isContainment)**() const

### \[read-only\] location : Plasma::Types::Location {#location-prop}

The location of the scene which is displaying this applet.

**Access functions:**

- `Plasma::Types::Location` **[location](plasma-applet.md#location)**() const

**Notifier signal:**

- `void` **[locationChanged](plasma-applet.md#locationChanged)**(`Plasma::Types::Location` *location*)

### \[read-only\] metaData : const KPluginMetaData {#metaData-prop}

The metadata of the applet.

**Access functions:**

- `KPluginMetaData` **[pluginMetaData](plasma-applet.md#pluginMetaData)**() const

### \[read-only\] pluginName : const QString {#pluginName-prop}

Plugin name for the applet.

**Access functions:**

- `QString` **[pluginName](plasma-applet.md#pluginName)**() const

### status : Plasma::Types::ItemStatus {#status-prop}

Allows to instruct the shell if this applet is requesting attention, accepting input, or if it is in an idle, inactive state.

**Access functions:**

- `Plasma::Types::ItemStatus` **[status](plasma-applet.md#status)**() const
- `void` **[setStatus](plasma-applet.md#setStatus)**(const `Plasma::Types::ItemStatus` *stat*)

**Notifier signal:**

- `void` **[statusChanged](plasma-applet.md#statusChanged)**(`Plasma::Types::ItemStatus` *status*)

### title : QString {#title-prop}

User friendly title for the plasmoid, the localized applet name by default.

**Access functions:**

- `QString` **[title](plasma-applet.md#title)**() const
- `void` **[setTitle](plasma-applet.md#setTitle)**(const `QString` &*title*)

**Notifier signal:**

- `void` **[titleChanged](plasma-applet.md#titleChanged)**(const `QString` &*title*)

### userBackgroundHints : Plasma::Types::BackgroundHints {#userBackgroundHints-prop}

Allows the containment or user to override the set [backgroundHints](plasma-applet.md#backgroundHints) if they exist.

**Access functions:**

- `Plasma::Types::BackgroundHints` **[userBackgroundHints](plasma-applet.md#userBackgroundHints)**() const
- `void` **[setUserBackgroundHints](plasma-applet.md#setUserBackgroundHints)**(`Plasma::Types::BackgroundHints` *hint*)

**Notifier signal:**

- `void` **[userBackgroundHintsChanged](plasma-applet.md#userBackgroundHintsChanged)**()

### \[read-only\] userConfiguring : bool {#userConfiguring-prop}

True when the user is configuring, for instance when the configuration dialog is open.

**Access functions:**

- `bool` **[isUserConfiguring](plasma-applet.md#isUserConfiguring)**() const

**Notifier signal:**

- `void` **[userConfiguringChanged](plasma-applet.md#userConfiguringChanged)**(`bool` *configuring*)

## Member Function Documentation {#member-function-documentation}

### Applet::Applet(QObject \**parentObject*, const KPluginMetaData &*data*, const QVariantList &*args*) {#Applet}

This constructor can be used with the KCoreAddons plugin loading system. The argument list is expected to have contain the [KPackage](../kpackage/kpackage-module.md) of the applet, the meta data file path (for compatibility) and an applet ID which must be a base 10 number.

`parent` a [QObject](https://doc.qt.io/qt-6/qobject.html) parent; you probably want to pass in 0

`data`, KPluginMetaData used to create this plugin

`args` a list of strings containing the applet id

### \[signal\] void Applet::activated() {#activated}

Emitted when activation is requested due to, for example, a global keyboard shortcut. By default the widget is given focus.

### \[signal\] void Applet::appletDeleted(Plasma::Applet \**applet*) {#appletDeleted}

Emitted when the applet is deleted

### Plasma::Types::BackgroundHints Applet::backgroundHints() const {#backgroundHints}

How the applet wants its background to be drawn. The containment may chose to ignore this hint.

> **Note:** Getter function for property [backgroundHints](plasma-applet.md#backgroundHints-prop).

*See also* [setBackgroundHints](plasma-applet.md#setBackgroundHints)()

### \[signal\] void Applet::backgroundHintsChanged() {#backgroundHintsChanged}

Emitted when the background hints have changed

> **Note:** Notifier signal for property [backgroundHints](plasma-applet.md#backgroundHints-prop).

### \[signal\] void Applet::busyChanged(bool *busy*) {#busyChanged}

Emitted when the busy status has changed

> **Note:** Notifier signal for property [busy](plasma-applet.md#busy-prop).

### KConfigGroup Applet::config() const {#config}

Returns the [KConfigGroup](../kconfigcore/kconfiggroup.md) to access the applets configuration.

This config object will write to an instance specific config file named \<appletname\>\<instanceid\>rc in the Plasma appdata directory.

### \[virtual slot\] void Applet::configChanged() {#configChanged}

Called when applet configuration values have changed.

### \[signal\] void Applet::configNeedsSaving() {#configNeedsSaving}

Emitted when an applet has changed values in its configuration and wishes for them to be saved at the next save point. As this implies disk activity, this signal should be used with care.

> **Note:** This does not need to be emitted from [saveState](plasma-applet.md#saveState) by individual applets.

### KConfigLoader \*Applet::configScheme() const {#configScheme}

Returns the config skeleton object from this applet's package, if any.

Returns config skeleton object, or 0 if none

### KConfigPropertyMap \*Applet::configuration() {#configuration}

Returns a [KConfigPropertyMap](../kconfigqml/kconfigpropertymap.md) instance that represents the configuration which is usable from QML to read and write settings like any JavaScript Object

> **Note:** Getter function for property [configuration](plasma-applet.md#configuration-prop).

### bool Applet::configurationRequired() const {#configurationRequired}

Returns true if the applet currently needs to be configured, otherwise, false

> **Note:** Getter function for property [configurationRequired](plasma-applet.md#configurationRequired-prop).

*See also* [setConfigurationRequired](plasma-applet.md#setConfigurationRequired)()

### \[signal\] void Applet::configurationRequiredChanged(bool *needsConfig*, const QString &*reason*) {#configurationRequiredChanged}

Emitted when [setConfigurationRequired](plasma-applet.md#setConfigurationRequired) was called

> **Note:** Notifier signal for property [configurationRequired](plasma-applet.md#configurationRequired-prop).

*See also* [setConfigurationRequired](plasma-applet.md#setConfigurationRequired)

### QString Applet::configurationRequiredReason() const {#configurationRequiredReason}

Returns A translated message for the user explaining that the applet needs configuring; this should note what needs to be configured

*See also* [setConfigurationRequired](plasma-applet.md#setConfigurationRequired)

### Plasma::Applet::ConstraintHints Applet::constraintHints() const {#constraintHints}

Returns The constraint hints such as [CanFillArea](plasma-applet.md#ConstraintHint-enum) or [MarginAreasSeparator](plasma-applet.md#ConstraintHint-enum), they can be in bitwise OR

> **Note:** Getter function for property [constraintHints](plasma-applet.md#constraintHints-prop).

*See also* [setConstraintHints](plasma-applet.md#setConstraintHints)()

### \[signal\] void Applet::constraintHintsChanged(Plasma::Applet::ConstraintHints *constraintHints*) {#constraintHintsChanged}

Emitted when the constraint hints changed

> **Note:** Notifier signal for property [constraintHints](plasma-applet.md#constraintHints-prop).

*See also* [setConstraintHints](plasma-applet.md#setConstraintHints)

### \[virtual protected\] void Applet::constraintsEvent(Plasma::Applet::Constraints *constraints*) {#constraintsEvent}

Called when any of the constraints for the applet have been updated. These constraints range from notifying when the applet has officially "started up" to when geometry changes to when the form factor changes.

Each constraint that has been changed is passed in the constraints flag. All of the constraints and how they work is documented in the

enumeration.

On applet creation, this is always called prior to painting and can be used as an opportunity to layout the widget, calculate sizings, etc.

Do not call update() from this method; an update() will be triggered at the appropriate time for the applet.

`constraints` the type of constraints that were updated

*See also* [Plasma::Constraints](plasma-index.md)

### Plasma::Containment \*Applet::containment() const {#containment}

Returns the Containment, if any, this applet belongs to.

A containment will return itself if is a first level containment such as a desktop or a panel, or will return the other containment is in if it's a nested containment such a system tray

> **Note:** Getter function for property [containment](plasma-applet.md#containment-prop).

### \[signal\] void Applet::containmentChanged(Plasma::Containment \**containment*) {#containmentChanged}

Emitted when the containment changes

> **Note:** Notifier signal for property [containment](plasma-applet.md#containment-prop).

### Types::ContainmentDisplayHints Applet::containmentDisplayHints() const {#containmentDisplayHints}

Returns Display hints that come from the containment that suggest the applet how to look and behave.

> **Note:** Getter function for property [containmentDisplayHints](plasma-applet.md#containmentDisplayHints-prop).

### \[signal\] void Applet::containmentDisplayHintsChanged(Plasma::Types::ContainmentDisplayHints *hints*) {#containmentDisplayHintsChanged}

Emitted when the containment display hints change

> **Note:** Notifier signal for property [containmentDisplayHints](plasma-applet.md#containmentDisplayHints-prop).

### \[virtual\] QList\<QAction \*\> Applet::contextualActions() {#contextualActions}

Returns a list of context-related [QAction](https://doc.qt.io/qt-6/qaction.html) instances.

This is used e.g. within the `DesktopView` to display a contextmenu.

Returns A list of actions. The default implementation returns an empty list.

### \[signal\] void Applet::contextualActionsAboutToShow() {#contextualActionsAboutToShow}

Emitted just before the contextual actions are about to show For instance just before the context menu containing the actions added with setAction() is shown

### \[signal\] void Applet::contextualActionsChanged(const QList\<QAction \*\> &*actions*) {#contextualActionsChanged}

Emitted when the list of contextual actions has changed

> **Note:** Notifier signal for property [contextualActions](plasma-applet.md#contextualActions-prop).

### \[slot\] void Applet::destroy() {#destroy}

Destroys the applet; it will be removed nicely and deleted. Its configuration will also be deleted. If you want to remove the Applet configuration, use this, don't just delete the Applet \*

### bool Applet::destroyed() const {#destroyed}

Returns true if [destroy](plasma-applet.md#destroy)() was called; useful for Applets which should avoid certain tasks if they are about to be deleted permanently

### \[signal\] void Applet::destroyedChanged(bool *destroyed*) {#destroyedChanged}

Emitted when the applet has been scheduled for destruction or the destruction has been undone

### Plasma::Types::BackgroundHints Applet::effectiveBackgroundHints() const {#effectiveBackgroundHints}

The effective background hints the applet will have: it will follow [userBackgroundHints](plasma-applet.md#userBackgroundHints) only if [backgroundHints](plasma-applet.md#backgroundHints) has the [Plasma::Types::ConfigurableBackground](plasma-types.md#BackgroundHints-enum) flag set

> **Note:** Getter function for property [effectiveBackgroundHints](plasma-applet.md#effectiveBackgroundHints-prop).

### \[signal\] void Applet::effectiveBackgroundHintsChanged() {#effectiveBackgroundHintsChanged}

Emitted when the effective background hints have changed

> **Note:** Notifier signal for property [effectiveBackgroundHints](plasma-applet.md#effectiveBackgroundHints-prop).

### bool Applet::failedToLaunch() const {#failedToLaunch}

If for some reason, the applet fails to get up on its feet (the library couldn't be loaded, necessary hardware support wasn't found, etc..) this method returns true.

### \[slot\] void Applet::flushPendingConstraintsEvents() {#flushPendingConstraintsEvents}

Sends all pending constraints updates to the applet. Will usually be called automatically, but can also be called manually if needed.

### Plasma::Types::FormFactor Applet::formFactor() const {#formFactor}

Returns the current form factor the applet is being displayed in.

> **Note:** Getter function for property [formFactor](plasma-applet.md#formFactor-prop).

### \[signal\] void Applet::formFactorChanged(Plasma::Types::FormFactor *formFactor*) {#formFactorChanged}

Emitted when the formfactor changes

> **Note:** Notifier signal for property [formFactor](plasma-applet.md#formFactor-prop).

### KConfigGroup Applet::globalConfig() const {#globalConfig}

Returns a [KConfigGroup](../kconfigcore/kconfiggroup.md) object to be shared by all applets of this type.

This config object will write to an applet-specific config object named plasma\_\<appletname\>rc in the local config directory.

### QKeySequence Applet::globalShortcut() const {#globalShortcut}

Returns the global shortcut associated with this widget, or an empty shortcut if no global shortcut is associated.

> **Note:** Getter function for property [globalShortcut](plasma-applet.md#globalShortcut-prop).

*See also* [setGlobalShortcut](plasma-applet.md#setGlobalShortcut)()

### \[signal\] void Applet::globalShortcutChanged(const QKeySequence &*sequence*) {#globalShortcutChanged}

Emitted when the global shortcut to activate this applet has changed

> **Note:** Notifier signal for property [globalShortcut](plasma-applet.md#globalShortcut-prop).

### bool Applet::hasConfigurationInterface() const {#hasConfigurationInterface}

Returns true if this plasmoid provides a GUI configuration

> **Note:** Getter function for property [hasConfigurationInterface](plasma-applet.md#hasConfigurationInterface-prop).

*See also* [setHasConfigurationInterface](plasma-applet.md#setHasConfigurationInterface)()

### \[signal, since 6.0\] void Applet::hasConfigurationInterfaceChanged(bool *hasConfiguration*) {#hasConfigurationInterfaceChanged}

Emitted when the applet gains or loses the ability to show a configuration interface

> **Note:** Notifier signal for property [hasConfigurationInterface](plasma-applet.md#hasConfigurationInterface-prop).

This function was introduced in Qt 6.0.

*See also* [hasConfigurationInterface](plasma-applet.md#hasConfigurationInterface)

### QString Applet::icon() const {#icon}

Returns The icon name related to this applet By default is the one in the plasmoid desktop file

> **Note:** Getter function for property [icon](plasma-applet.md#icon-prop).

*See also* [setIcon](plasma-applet.md#setIcon)()

### \[signal\] void Applet::iconChanged(const QString &*icon*) {#iconChanged}

Emitted when the icon name for the applet has changed

> **Note:** Notifier signal for property [icon](plasma-applet.md#icon-prop).

### uint Applet::id() const {#id}

Returns the id of this applet

> **Note:** Getter function for property [id](plasma-applet.md#id-prop).

### Plasma::Types::ImmutabilityType Applet::immutability() const {#immutability}

Returns The type of immutability of this applet

> **Note:** Getter function for property [immutability](plasma-applet.md#immutability-prop).

*See also* [setImmutability](plasma-applet.md#setImmutability)()

### \[signal\] void Applet::immutabilityChanged(Plasma::Types::ImmutabilityType *immutable*) {#immutabilityChanged}

Emitted when the immutability changes

> **Note:** Notifier signal for properties [immutability](plasma-applet.md#immutability-prop) and [immutable](plasma-applet.md#immutable-prop).

### bool Applet::immutable() const {#immutable}

Returns true if [immutability](plasma-applet.md#immutability)() is not [Types::Mutable](plasma-types.md#ImmutabilityType-enum)

> **Note:** Getter function for property [immutable](plasma-applet.md#immutable-prop).

### \[virtual slot\] void Applet::init() {#init}

This method is called once the applet is loaded and added to a Corona. If the applet requires a Scene or has an particularly intensive set of initialization routines to go through, consider implementing it in this method instead of the constructor.

> **Note:** paintInterface may get called before init() depending on initialization order. Painting is managed by the canvas (QGraphisScene), and may schedule a paint event prior to init() being called.

### \[invokable\] QAction \*Applet::internalAction(const QString &*name*) const {#internalAction}

Returnss the internal action with the given name if available

`name` the unique name of the action we want

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [setInternalAction](plasma-applet.md#setInternalAction)()

### QList\<QAction \*\> Applet::internalActions() const {#internalActions}

Returnss All the internal actions such as configure, remove, alternatives etc

### \[signal\] void Applet::internalActionsChanged(const QList\<QAction \*\> &*actions*) {#internalActionsChanged}

Emitted when the list of internal actions has changed

### bool Applet::isBusy() const {#isBusy}

Returns true if the applet should show a busy status, for instance doing some network operation

> **Note:** Getter function for property [busy](plasma-applet.md#busy-prop).

### bool Applet::isContainment() const {#isContainment}

Returns `true` if this Applet is currently being used as a Containment, false otherwise.

Normally only first level Containments directly children of Corona can act as containments, except Containments of Type CustomEmbedded which can be containments also when inside another containment, such as a Systray inside a Panel.

> **Note:** Getter function for property [isContainment](plasma-applet.md#isContainment-prop).

### bool Applet::isUserConfiguring() const {#isUserConfiguring}

Returns true when the configuration interface is being shown

> **Note:** Getter function for property [userConfiguring](plasma-applet.md#userConfiguring-prop).

### QString Applet::launchErrorMessage() const {#launchErrorMessage}

If for some reason, the applet fails to get up on its feet (the library couldn't be loaded, necessary hardware support wasn't found, etc..) this method returns the reason why, in an user-readable way.

*See also* [setLaunchErrorMessage](plasma-applet.md#setLaunchErrorMessage)()

### Plasma::Types::Location Applet::location() const {#location}

Returns the location of the scene which is displaying applet.

> **Note:** Getter function for property [location](plasma-applet.md#location-prop).

### \[signal\] void Applet::locationChanged(Plasma::Types::Location *location*) {#locationChanged}

Emitted when the location changes

> **Note:** Notifier signal for property [location](plasma-applet.md#location-prop).

### KPluginMetaData Applet::pluginMetaData() const {#pluginMetaData}

Returns metadata information about this plugin

> **Note:** Getter function for property [metaData](plasma-applet.md#metaData-prop).

### QString Applet::pluginName() const {#pluginName}

Returns the plugin name form KPluginMetaData

> **Note:** Getter function for property [pluginName](plasma-applet.md#pluginName-prop).

### \[invokable\] void Applet::removeInternalAction(const QString &*name*) {#removeInternalAction}

Removes an action from the internal actions

`name` the action to be removed

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[virtual\] void Applet::restore(KConfigGroup &*group*) {#restore}

Restores state information about this applet saved previously in save([KConfigGroup](../kconfigcore/kconfiggroup.md)&).

This method does not need to be reimplemented by Applet subclasses, but can be useful for Applet specializations (such as Containment) to do so.

### \[virtual\] void Applet::save(KConfigGroup &*group*) const {#save}

Saves state information about this applet that will be accessed when next instantiated in the restore([KConfigGroup](../kconfigcore/kconfiggroup.md)&) method.

This method does not need to be reimplemented by Applet subclasses, but can be useful for Applet specializations (such as Containment) to do so.

Applet subclasses may instead want to reimplement [saveState](plasma-applet.md#saveState)().

### \[virtual protected\] void Applet::saveState(KConfigGroup &*config*) const {#saveState}

When called, the Applet should write any information needed as part of the Applet's running state to the configuration object in [config](plasma-applet.md#config)() and/or [globalConfig](plasma-applet.md#globalConfig)().

Applets that always sync their settings/state with the config objects when these settings/states change do not need to reimplement this method.

### \[signal, since 6.3\] void Applet::secondaryActivated() {#secondaryActivated}

Emitted when activation is requested due to, for example, middle click.

This function was introduced in Qt 6.3.

### void Applet::setBackgroundHints(Plasma::Types::BackgroundHints *hint*) {#setBackgroundHints}

Sets the applet background hints. Only Applet implementations should write this property

> **Note:** Setter function for property [backgroundHints](plasma-applet.md#backgroundHints-prop).

*See also* [backgroundHints](plasma-applet.md#backgroundHints)()

### void Applet::setBusy(bool *busy*) {#setBusy}

Sets the Applet to have a busy status hint, for instance the applet doing some network operation. The graphical representation of the busy status depends completely from the visualization.

`busy` true if the applet is busy

> **Note:** Setter function for property [busy](plasma-applet.md#busy-prop).

*See also* [isBusy](plasma-applet.md#isBusy)()

### void Applet::setConfigurationRequired(bool *needsConfiguring*, const QString &*reason* = QString()) {#setConfigurationRequired}

When the applet needs to be configured before being usable, this method can be called to show a standard interface prompting the user to configure the applet

`needsConfiguring` true if the applet needs to be configured, or false if it doesn't

`reason` a translated message for the user explaining that the applet needs configuring; this should note what needs to be configured

> **Note:** Setter function for property [configurationRequired](plasma-applet.md#configurationRequired-prop).

*See also* [configurationRequired](plasma-applet.md#configurationRequired)()

### void Applet::setConstraintHints(Plasma::Applet::ConstraintHints *constraintHints*) {#setConstraintHints}

Sets the constraint hits which give a more granular control over sizing in constrained layouts such as panels

`constraintHints` such as [CanFillArea](plasma-applet.md#ConstraintHint-enum) or [MarginAreasSeparator](plasma-applet.md#ConstraintHint-enum), they can be in bitwise OR

> **Note:** Setter function for property [constraintHints](plasma-applet.md#constraintHints-prop).

*See also* [constraintHints](plasma-applet.md#constraintHints)()

### void Applet::setGlobalShortcut(const QKeySequence &*shortcut* = QKeySequence()) {#setGlobalShortcut}

Sets the global shortcut to associate with this widget.

> **Note:** Setter function for property [globalShortcut](plasma-applet.md#globalShortcut-prop).

*See also* [globalShortcut](plasma-applet.md#globalShortcut)()

### void Applet::setHasConfigurationInterface(bool *hasInterface*) {#setHasConfigurationInterface}

Sets whether or not this applet provides a user interface for configuring the applet.

It defaults to false, and if true is passed in you should also reimplement createConfigurationInterface()

`hasInterface` whether or not there is a user interface available

> **Note:** Setter function for property [hasConfigurationInterface](plasma-applet.md#hasConfigurationInterface-prop).

*See also* [hasConfigurationInterface](plasma-applet.md#hasConfigurationInterface)()

### void Applet::setIcon(const QString &*icon*) {#setIcon}

Sets an icon name for this applet `icon` Freedesktop compatible icon name

> **Note:** Setter function for property [icon](plasma-applet.md#icon-prop).

*See also* [icon](plasma-applet.md#icon)()

### \[slot\] void Applet::setImmutability(const Plasma::Types::ImmutabilityType *immutable*) {#setImmutability}

Sets the immutability type for this applet (not immutable, user immutable or system immutable)

`immutable` the new immutability type of this applet

> **Note:** Setter function for property [immutability](plasma-applet.md#immutability-prop).

*See also* [immutability](plasma-applet.md#immutability)()

### \[invokable\] void Applet::setInternalAction(const QString &*name*, QAction \**action*) {#setInternalAction}

Add a new internal action. if an internal action with the same name already exists, it will be replaced with this new one. Those are usually actions defined by the system, such as "configure" and "remove"

`name` The unique name for the action

`action` The new [QAction](https://doc.qt.io/qt-6/qaction.html) to be added

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [internalAction](plasma-applet.md#internalAction)()

### \[slot\] void Applet::setLaunchErrorMessage(const QString &*reason* = QString()) {#setLaunchErrorMessage}

Call this method when the applet fails to launch properly. An optional reason can be provided.

Not that all children items will be deleted when this method is called. If you have pointers to these items, you will need to reset them after calling this method.

`failed` true when the applet failed, false when it succeeded

`reason` an optional reason to show the user why the applet failed to launch

*See also* [launchErrorMessage](plasma-applet.md#launchErrorMessage)()

### \[slot\] void Applet::setStatus(const Plasma::Types::ItemStatus *stat*) {#setStatus}

sets the status for this applet

> **Note:** Setter function for property [status](plasma-applet.md#status-prop).

*See also* [status](plasma-applet.md#status)()

### void Applet::setTitle(const QString &*title*) {#setTitle}

Sets a custom title for this instance of the applet. E.g. a clock might use the timezone as its name rather than the .desktop file

`title` the user-visible title for the applet.

> **Note:** Setter function for property [title](plasma-applet.md#title-prop).

*See also* [title](plasma-applet.md#title)()

### void Applet::setUserBackgroundHints(Plasma::Types::BackgroundHints *hint*) {#setUserBackgroundHints}

Sets the hints the user wished the background style for the applet to be.

> **Note:** Setter function for property [userBackgroundHints](plasma-applet.md#userBackgroundHints-prop).

*See also* [userBackgroundHints](plasma-applet.md#userBackgroundHints)()

### void Applet::setUserConfiguring(bool *configuring*) {#setUserConfiguring}

Tells the applet the user is configuring

`configuring` true if the configuration ui is showing

*See also* [isUserConfiguring](plasma-applet.md#isUserConfiguring)()

### QVariantList Applet::startupArguments() const {#startupArguments}

Returns the arguments this applet was started with.

Some applets support arguments, for instance the notes applet supports to be instantiated with a given text already passed as parameter

### Plasma::Types::ItemStatus Applet::status() const {#status}

Returns the status of the applet

> **Note:** Getter function for property [status](plasma-applet.md#status-prop).

*See also* [setStatus](plasma-applet.md#setStatus)()

### \[signal\] void Applet::statusChanged(Plasma::Types::ItemStatus *status*) {#statusChanged}

Emitted when the applet status changes

> **Note:** Notifier signal for property [status](plasma-applet.md#status-prop).

### QString Applet::title() const {#title}

Returns the user-visible title for the applet, as specified in the Name field of the .desktop file. Can be changed with [setTitle](plasma-applet.md#setTitle)

Returns the user-visible title for the applet.

> **Note:** Getter function for property [title](plasma-applet.md#title-prop).

*See also* [setTitle](plasma-applet.md#setTitle)()

### \[signal\] void Applet::titleChanged(const QString &*title*) {#titleChanged}

Emitted when the title has changed

> **Note:** Notifier signal for property [title](plasma-applet.md#title-prop).

### \[since 6.1\] QString Applet::translationDomain() const {#translationDomain}

The translation domain for this applet

This function was introduced in Qt 6.1.

### void Applet::updateConstraints(Plasma::Applet::Constraints *constraints* = AllConstraints) {#updateConstraints}

Called when any of the geometry constraints have been updated. This method calls [constraintsEvent](plasma-applet.md#constraintsEvent), which may be reimplemented, once the Applet has been prepared for updating the constraints.

`constraints` the type of constraints that were updated

### Plasma::Types::BackgroundHints Applet::userBackgroundHints() const {#userBackgroundHints}

The containment (and/or the user) may decide to use another kind of background instead if supported by the applet. In order for an applet to support user configuration of the background, it needs to have the [Plasma::Types::ConfigurableBackground](plasma-types.md#BackgroundHints-enum) flag set in its [backgroundHints](plasma-applet.md#backgroundHints)

> **Note:** Getter function for property [userBackgroundHints](plasma-applet.md#userBackgroundHints-prop).

*See also* [setUserBackgroundHints](plasma-applet.md#setUserBackgroundHints)()

### \[signal\] void Applet::userBackgroundHintsChanged() {#userBackgroundHintsChanged}

Emitted when the user background hints have changed

> **Note:** Notifier signal for property [userBackgroundHints](plasma-applet.md#userBackgroundHints-prop).

### \[signal\] void Applet::userConfiguringChanged(bool *configuring*) {#userConfiguringChanged}

emitted when the config ui appears or disappears

> **Note:** Notifier signal for property [userConfiguring](plasma-applet.md#userConfiguring-prop).
