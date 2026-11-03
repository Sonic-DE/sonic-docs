---
title: "Plasma::Containment Class"
description: "The base class for plugins that provide backgrounds and applet grouping containers."
---

# Plasma::Containment Class

The base class for plugins that provide backgrounds and applet grouping containers. [More...](#details)

- **Header:** `#include <Plasma/Containment>`
- **CMake:** `find_package(Plasma REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Plasma::Plasma)`
- **Inherits:** [Plasma::Applet](plasma-applet.md)

[List of all members, including inherited members](plasma-containment-members.md)

## Public Types

- [enum Containment::Type](#Type-enum)

## Properties

- [\[read-only\] activity : QString](#activity-prop)
- [\[read-only\] activityName : QString](#activityName-prop)
- [\[read-only\] applets : QList\<Plasma::Applet \*\>](#applets-prop)
- [\[read-only\] availableScreenRect : QRectF](#availableScreenRect-prop)
- [\[read-only\] availableScreenRegion : QList\<QRectF\>](#availableScreenRegion-prop)
- [containmentDisplayHints : Plasma::Types::ContainmentDisplayHints](#containmentDisplayHints-prop)
- [\[read-only\] containmentType : Plasma::Containment::Type](#containmentType-prop)
- [\[read-only\] corona : Plasma::Corona\* const](#corona-prop)
- [\[read-only\] isUiReady : bool](#isUiReady-prop)
- [\[read-only\] screen : int](#screen-prop)
- [\[read-only\] screenGeometry : QRectF](#screenGeometry-prop)
- [wallpaperGraphicsObject : QObject\*](#wallpaperGraphicsObject-prop)
- [wallpaperPlugin : QString](#wallpaperPlugin-prop)

## Public Functions

- [Containment(QObject \*parentObject, const KPluginMetaData &data, const QVariantList &args)](#Containment)
- [QString activity() const](#activity)
- [QString activityName() const](#activityName)
- [void addApplet(Plasma::Applet \*applet, const QRectF &geometryHint = QRectF())](#addApplet)
- [QList\<Plasma::Applet \*\> applets() const](#applets)
- [QRectF availableRelativeScreenRect() const](#availableRelativeScreenRect)
- [QList\<QRectF\> availableRelativeScreenRegion() const](#availableRelativeScreenRegion)
- [QHash\<QString, Plasma::ContainmentActions \*\> &containmentActions()](#containmentActions)
- [Plasma::Containment::Type containmentType() const](#containmentType)
- [Plasma::Corona \*corona() const](#corona)
- [Plasma::Applet \*createApplet(const QString &name, const QVariantList &args = QVariantList(), const QRectF &geometryHint = QRectF(-1, -1, 0, 0))](#createApplet)
- [bool isUiReady() const](#isUiReady)
- [int lastScreen() const](#lastScreen)
- [int screen() const](#screen)
- [QRectF screenGeometry() const](#screenGeometry)
- [void setActivity(const QString &activityId)](#setActivity)
- [void setContainmentActions(const QString &trigger, const QString &pluginName)](#setContainmentActions)
- [void setWallpaperPlugin(const QString &pluginName)](#setWallpaperPlugin)
- [QString wallpaperPlugin() const](#wallpaperPlugin)

## Public Slots

- [void setContainmentDisplayHints(Plasma::Types::ContainmentDisplayHints hints)](#setContainmentDisplayHints)
- [void setFormFactor(Plasma::Types::FormFactor formFactor)](#setFormFactor)
- [void setLocation(Plasma::Types::Location location)](#setLocation)

## Signals

- [void activityChanged(const QString &activity)](#activityChanged)
- [void activityNameChanged(const QString &name)](#activityNameChanged)
- [void appletAboutToBeAdded(Plasma::Applet \*applet, const QRectF &geometryHint)](#appletAboutToBeAdded)
- [void appletAboutToBeRemoved(Plasma::Applet \*applet)](#appletAboutToBeRemoved)
- [void appletAdded(Plasma::Applet \*applet, const QRectF &geometryHint)](#appletAdded)
- [void appletAlternativesRequested(Plasma::Applet \*applet)](#appletAlternativesRequested)
- [void appletCreated(Plasma::Applet \*applet, const QRectF &geometryHint)](#appletCreated)
- [void appletRemoved(Plasma::Applet \*applet)](#appletRemoved)
- [void appletsChanged()](#appletsChanged)
- [void availableRelativeScreenRectChanged(const QRectF &rect)](#availableRelativeScreenRectChanged)
- [void availableRelativeScreenRegionChanged(const QList\<QRectF\> &region)](#availableRelativeScreenRegionChanged)
- [void configureRequested(Plasma::Applet \*applet)](#configureRequested)
- [void containmentTypeChanged()](#containmentTypeChanged)
- [void formFactorChanged(Plasma::Types::FormFactor formFactor)](#formFactorChanged)
- [void locationChanged(Plasma::Types::Location location)](#locationChanged)
- [void screenChanged(int newScreen)](#screenChanged)
- [void screenGeometryChanged(const QRectF &rect)](#screenGeometryChanged)
- [void showAddWidgetsInterface(const QPointF &pos)](#showAddWidgetsInterface)
- [void uiReadyChanged(bool uiReady)](#uiReadyChanged)
- [void wallpaperGraphicsObjectChanged()](#wallpaperGraphicsObjectChanged)
- [void wallpaperPluginChanged()](#wallpaperPluginChanged)

## Protected Functions

- [void restoreContents(KConfigGroup &group)](#restoreContents)
- [void saveContents(KConfigGroup &group) const](#saveContents)

## Detailed Description {#details}

Containment objects provide the means to group applets into functional sets. They also provide the following:

- creation of focusing event
- drawing of the background image (which can be interactive)
- form factors (e.g. panel, desktop, full screen, etc)
- applet layout management

Since Containment is itself a [Plasma::Applet](plasma-applet.md), all the techniques used for writing the visual presentation of Applets is applicable to Containtments. Containments are differentiated from Applets by being marked with the ServiceType of Plasma/Containment. Plugins registered with both the Applet and the Containment ServiceTypes can be loaded for use in either situation.

## Member Type Documentation {#member-type-documentation}

### enum Containment::Type {#Type-enum}

The type of the Containment.

This value is specified in the "X-Plasma-ContainmentType" JSON-metadata value of containments.

| Constant | Value |   |
| --- | --- | --- |
| `Plasma::Containment::NoContainment` | `-1` |   |
| `Plasma::Containment::Desktop` | `0` | Main containments that will own a screen in a mutually exclusive fashion. |
| `Plasma::Containment::Panel` | `1` | A desktop panel. Multiple can be present per screen. |
| `Plasma::Containment::Custom` | `127` | A containment that is neither a desktop nor a panel but something application specific. |
| `Plasma::Containment::CustomPanel` | `128` | A customized desktop panel. "CustomPanel" in metadata. |
| `Plasma::Containment::CustomEmbedded` | `129` | A customized containment embedded into another applet. |

## Property Documentation {#property-documentation}

### \[read-only\] activity : QString {#activity-prop}

Activity UID of this containment.

**Access functions:**

- `QString` **[activity](plasma-containment.md#activity)**() const

**Notifier signal:**

- `void` **[activityChanged](plasma-containment.md#activityChanged)**(const `QString` &*activity*)

### \[read-only\] activityName : QString {#activityName-prop}

Activity name of this containment.

**Access functions:**

- `QString` **[activityName](plasma-containment.md#activityName)**() const

**Notifier signal:**

- `void` **[activityNameChanged](plasma-containment.md#activityNameChanged)**(const `QString` &*name*)

### \[read-only\] applets : QList\<Plasma::Applet \*\> {#applets-prop}

List of applets in this containment.

**Access functions:**

- `QList`\<`Plasma::Applet` \*\> **[applets](plasma-containment.md#applets)**() const

**Notifier signal:**

- `void` **[appletsChanged](plasma-containment.md#appletsChanged)**()

### \[read-only\] availableScreenRect : QRectF {#availableScreenRect-prop}

Screen area used by the Containment by itself (free of enveloping panels).

The coordinates are relative to the containment (that is, x:0 and y:0 match the Containment's upper left corner), and independent from the screen position.

For more precise available geometry use availableScreenRegion().

**Access functions:**

- `QRectF` **[availableRelativeScreenRect](plasma-containment.md#availableRelativeScreenRect)**() const

**Notifier signal:**

- `void` **[availableRelativeScreenRectChanged](plasma-containment.md#availableRelativeScreenRectChanged)**(const `QRectF` &*rect*)

### \[read-only\] availableScreenRegion : QList\<QRectF\> {#availableScreenRegion-prop}

A list of rectangles matching the available region of this screen, panels excluded.

**Access functions:**

- `QList`\<`QRectF`\> **[availableRelativeScreenRegion](plasma-containment.md#availableRelativeScreenRegion)**() const

**Notifier signal:**

- `void` **[availableRelativeScreenRegionChanged](plasma-containment.md#availableRelativeScreenRegionChanged)**(const `QList`\<`QRectF`\> &*region*)

### containmentDisplayHints : Plasma::Types::ContainmentDisplayHints {#containmentDisplayHints-prop}

**Access functions:**

- `Types::ContainmentDisplayHints` **[containmentDisplayHints](plasma-applet.md#containmentDisplayHints)**() const
- `void` **[setContainmentDisplayHints](plasma-containment.md#setContainmentDisplayHints)**(`Plasma::Types::ContainmentDisplayHints` *hints*)

**Notifier signal:**

- `void` **[containmentDisplayHintsChanged](plasma-applet.md#containmentDisplayHintsChanged)**(`Plasma::Types::ContainmentDisplayHints` *hints*)

### \[read-only\] containmentType : Plasma::Containment::Type {#containmentType-prop}

Type of this containment.

**Access functions:**

- `Plasma::Containment::Type` **[containmentType](plasma-containment.md#containmentType)**() const

**Notifier signal:**

- `void` **[containmentTypeChanged](plasma-containment.md#containmentTypeChanged)**()

### \[read-only\] corona : Plasma::Corona\* const {#corona-prop}

The corona for this contaiment.

**Access functions:**

- `Plasma::Corona` \***[corona](plasma-containment.md#corona)**() const

### \[read-only\] isUiReady : bool {#isUiReady-prop}

**Access functions:**

- `bool` **[isUiReady](plasma-containment.md#isUiReady)**() const

**Notifier signal:**

- `void` **[uiReadyChanged](plasma-containment.md#uiReadyChanged)**(`bool` *uiReady*)

### \[read-only\] screen : int {#screen-prop}

The screen number this containment is serving as the desktop for, or -1 if none

**Access functions:**

- `int` **[screen](plasma-containment.md#screen)**() const

**Notifier signal:**

- `void` **[screenChanged](plasma-containment.md#screenChanged)**(`int` *newScreen*)

### \[read-only\] screenGeometry : QRectF {#screenGeometry-prop}

Provides access to the geometry of the screen the applet is in.

Can be useful to figure out what's the absolute position of the applet.

**Access functions:**

- `QRectF` **[screenGeometry](plasma-containment.md#screenGeometry)**() const

**Notifier signal:**

- `void` **[screenGeometryChanged](plasma-containment.md#screenGeometryChanged)**(const `QRectF` &*rect*)

### wallpaperGraphicsObject : QObject\* {#wallpaperGraphicsObject-prop}

**Notifier signal:**

- `void` **[wallpaperGraphicsObjectChanged](plasma-containment.md#wallpaperGraphicsObjectChanged)**()

### wallpaperPlugin : QString {#wallpaperPlugin-prop}

**Access functions:**

- `QString` **[wallpaperPlugin](plasma-containment.md#wallpaperPlugin)**() const
- `void` **[setWallpaperPlugin](plasma-containment.md#setWallpaperPlugin)**(const `QString` &*pluginName*)

**Notifier signal:**

- `void` **[wallpaperPluginChanged](plasma-containment.md#wallpaperPluginChanged)**()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Containment::Containment(QObject \**parentObject*, const KPluginMetaData &*data*, const QVariantList &*args*) {#Containment}

This constructor can be used with the KCoreAddons plugin loading system. The argument list is expected to have contain the [KPackage](../kpackage/kpackage-module.md) of the applet, the meta data file path (for compatibility) and an applet ID which must be a base 10 number.

`parent` a [QObject](https://doc.qt.io/qt-6/qobject.html) parent; you probably want to pass in 0

`data` KPluginMetaData used to create this plugin

`args` a list of strings containing the applet id

### QString Containment::activity() const {#activity}

Returns the current activity id associated with this containment

> **Note:** Getter function for property [activity](plasma-containment.md#activity-prop).

*See also* [setActivity](plasma-containment.md#setActivity)()

### \[signal\] void Containment::activityChanged(const QString &*activity*) {#activityChanged}

Emitted when the activity id has changed

> **Note:** Notifier signal for property [activity](plasma-containment.md#activity-prop).

### QString Containment::activityName() const {#activityName}

Returns Activity name corresponding to the activity UID

> **Note:** Getter function for property [activityName](plasma-containment.md#activityName-prop).

### \[signal\] void Containment::activityNameChanged(const QString &*name*) {#activityNameChanged}

Emitted when the activity name has changed

> **Note:** Notifier signal for property [activityName](plasma-containment.md#activityName-prop).

### \[invokable\] void Containment::addApplet(Plasma::Applet \**applet*, const QRectF &*geometryHint* = QRectF()) {#addApplet}

Adds an existing `applet` to this Containment with the given `geometryHint`.

The hint determines the preferred location and size for the newly created applet. The hint will not be respected if it's not possible to position it in the preferred location.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[signal\] void Containment::appletAboutToBeAdded(Plasma::Applet \**applet*, const QRectF &*geometryHint*) {#appletAboutToBeAdded}

This signal is emitted right before [appletAdded](plasma-containment.md#appletAdded), it can be used to do a preliminary setup on the applet before the handlers of [appletAdded](plasma-containment.md#appletAdded) are executed. Useful for instance to prepare the GUI for the applet

`applet` the applet that is about to be added

`geometryHint` an hint to pass to the GUI on the location and size we prefer for the newly created applet; the gui might choose whether to respect or not this hint

### \[signal\] void Containment::appletAboutToBeRemoved(Plasma::Applet \**applet*) {#appletAboutToBeRemoved}

This signal is emitted right before [appletRemoved](plasma-containment.md#appletRemoved), it can be used to do a preliminary setup on the applet before the handlers of [appletRemoved](plasma-containment.md#appletRemoved) are executed. Useful for instance to prepare or teardown the GUI for the applet

### \[signal\] void Containment::appletAdded(Plasma::Applet \**applet*, const QRectF &*geometryHint*) {#appletAdded}

This signal is emitted when a new applet is added in the containment It may happen in the following situations:

- The user created the applet
- The applet was moved in from another containment
- The applet got restored at startup

`applet` the applet that has been added

`geometryHint` an hint to pass to the GUI on the location and size we prefer for the newly created applet; the gui might choose whether to respect or not this hint

### \[signal\] void Containment::appletAlternativesRequested(Plasma::Applet \**applet*) {#appletAlternativesRequested}

Emitted when the user wants to chose an alternative for this applet or containment.

### \[signal\] void Containment::appletCreated(Plasma::Applet \**applet*, const QRectF &*geometryHint*) {#appletCreated}

This signal is emitted when a new applet is created by the containment. Compared to [appletAdded](plasma-containment.md#appletAdded), this gets emitted only when the user explicitly creates a new applet, either via the widget explorer or the scripting environment.

*See also* [appletAdded](plasma-containment.md#appletAdded)

### \[signal\] void Containment::appletRemoved(Plasma::Applet \**applet*) {#appletRemoved}

This signal is emitted when an applet is destroyed

### QList\<Plasma::Applet \*\> Containment::applets() const {#applets}

Returns the applets currently in this Containment

> **Note:** Getter function for property [applets](plasma-containment.md#applets-prop).

### \[signal\] void Containment::appletsChanged() {#appletsChanged}

Emitted when the list of applets has changed, either added or removed

> **Note:** Notifier signal for property [applets](plasma-containment.md#applets-prop).

### QRectF Containment::availableRelativeScreenRect() const {#availableRelativeScreenRect}

Returns The available screen rect (excluding panels) for the screen this containment is associated to, empty rectangle if the containment is not active in a screen

> **Note:** Getter function for property [availableScreenRect](plasma-containment.md#availableScreenRect-prop).

### \[signal\] void Containment::availableRelativeScreenRectChanged(const QRectF &*rect*) {#availableRelativeScreenRectChanged}

Emitted when the available screen rectangle has changed

> **Note:** Notifier signal for property [availableScreenRect](plasma-containment.md#availableScreenRect-prop).

### QList\<QRectF\> Containment::availableRelativeScreenRegion() const {#availableRelativeScreenRegion}

Returns The available region of this screen, panels excluded. It's a list of rectangles

> **Note:** Getter function for property [availableScreenRegion](plasma-containment.md#availableScreenRegion-prop).

### \[signal\] void Containment::availableRelativeScreenRegionChanged(const QList\<QRectF\> &*region*) {#availableRelativeScreenRegionChanged}

Emitted when the available screen rectangle has changed

> **Note:** Notifier signal for property [availableScreenRegion](plasma-containment.md#availableScreenRegion-prop).

### \[signal\] void Containment::configureRequested(Plasma::Applet \**applet*) {#configureRequested}

Emitted when the user wants to configure/change the containment, or an applet inside it.

### QHash\<QString, Plasma::ContainmentActions \*\> &Containment::containmentActions() {#containmentActions}

Returns all the loaded containment action plugins, indexed by trigger name

*See also* [setContainmentActions](plasma-containment.md#setContainmentActions)()

### Plasma::Containment::Type Containment::containmentType() const {#containmentType}

Returns the type of containment

> **Note:** Getter function for property [containmentType](plasma-containment.md#containmentType-prop).

### \[signal\] void Containment::containmentTypeChanged() {#containmentTypeChanged}

emitted when the containment type changed

> **Note:** Notifier signal for property [containmentType](plasma-containment.md#containmentType-prop).

### Plasma::Corona \*Containment::corona() const {#corona}

Returns the Corona (if any) that this Containment is hosted by

> **Note:** Getter function for property [corona](plasma-containment.md#corona-prop).

### Plasma::Applet \*Containment::createApplet(const QString &*name*, const QVariantList &*args* = QVariantList(), const QRectF &*geometryHint* = QRectF(-1, -1, 0, 0)) {#createApplet}

Adds an applet to this Containment

`name` the plugin name for the applet, as given by KPluginInfo::pluginName()

`args` argument list to pass to the plasmoid

`geometryHint` an hint to pass to the GUI on the location and size we prefer for the newly created applet; the gui might choose whether to respect or not this hint. The default position is (-1, -1) and the default size is (0, 0).

Returns a pointer to the applet on success, or 0 on failure

### \[signal\] void Containment::formFactorChanged(Plasma::Types::FormFactor *formFactor*) {#formFactorChanged}

Emitted when the formFactor has changed

### bool Containment::isUiReady() const {#isUiReady}

Returns `true` when the ui of this containment is fully loaded, as well the ui of every applet in it

> **Note:** Getter function for property [isUiReady](plasma-containment.md#isUiReady-prop).

### int Containment::lastScreen() const {#lastScreen}

Returns the last screen number this containment had only returns -1 if it's never ever been on a screen

### \[signal\] void Containment::locationChanged(Plasma::Types::Location *location*) {#locationChanged}

Emitted when the location has changed

### \[virtual protected\] void Containment::restoreContents(KConfigGroup &*group*) {#restoreContents}

Called when the contents of the containment should be loaded. By default this loads all previously saved Applets

`group` the [KConfigGroup](../kconfigcore/kconfiggroup.md) to save settings under

### \[virtual protected\] void Containment::saveContents(KConfigGroup &*group*) const {#saveContents}

Called when the contents of the containment should be saved. By default this saves all loaded Applets

`group` the [KConfigGroup](../kconfigcore/kconfiggroup.md) to save settings under

### int Containment::screen() const {#screen}

Returns the screen number this containment is serving as the desktop for or -1 if none

> **Note:** Getter function for property [screen](plasma-containment.md#screen-prop).

### \[signal\] void Containment::screenChanged(int *newScreen*) {#screenChanged}

This signal indicates that a containment has been associated (or dissociated) with a physical screen.

`newScreen` the screen it is now associated with

> **Note:** Notifier signal for property [screen](plasma-containment.md#screen-prop).

### QRectF Containment::screenGeometry() const {#screenGeometry}

Returns The geometry of the screen this containment is associated to

> **Note:** Getter function for property [screenGeometry](plasma-containment.md#screenGeometry-prop).

### \[signal\] void Containment::screenGeometryChanged(const QRectF &*rect*) {#screenGeometryChanged}

Emitted when the screen geometry has changed

> **Note:** Notifier signal for property [screenGeometry](plasma-containment.md#screenGeometry-prop).

### void Containment::setActivity(const QString &*activityId*) {#setActivity}

Sets the current activity by id

`activityId` the id of the activity

*See also* [activity](plasma-containment.md#activity)()

### void Containment::setContainmentActions(const QString &*trigger*, const QString &*pluginName*) {#setContainmentActions}

Sets a containmentactions plugin.

`trigger` the mouse button (and optional modifier) to associate the plugin with

`pluginName` the name of the plugin to attempt to load. blank = set no plugin.

*See also* [containmentActions](plasma-containment.md#containmentActions)()

### \[slot\] void Containment::setContainmentDisplayHints(Plasma::Types::ContainmentDisplayHints *hints*) {#setContainmentDisplayHints}

Set Display hints that come from the containment that suggest the applet how to look and behave.

`hints` the new hints, as bitwise OR

> **Note:** Setter function for property [containmentDisplayHints](plasma-containment.md#containmentDisplayHints-prop).

### \[slot\] void Containment::setFormFactor(Plasma::Types::FormFactor *formFactor*) {#setFormFactor}

Sets the form factor for this Containment. This may cause changes in both the arrangement of Applets as well as the display choices of individual Applets.

### \[slot\] void Containment::setLocation(Plasma::Types::Location *location*) {#setLocation}

Informs the Corona as to what position it is in. This is informational only, as the Corona doesn't change its actual location. This is, however, passed on to Applets that may be managed by this Corona.

`location` the new location of this Corona

### void Containment::setWallpaperPlugin(const QString &*pluginName*) {#setWallpaperPlugin}

Sets wallpaper plugin.

`pluginName` the name of the wallpaper to attempt to load

> **Note:** Setter function for property [wallpaperPlugin](plasma-containment.md#wallpaperPlugin-prop).

*See also* [wallpaperPlugin](plasma-containment.md#wallpaperPlugin)()

### \[signal\] void Containment::showAddWidgetsInterface(const QPointF &*pos*) {#showAddWidgetsInterface}

Emitted when the containment requests an add widgets dialog is shown. Usually only used for desktop containments.

`pos` where in the containment this request was made from, or an invalid position (QPointF()) is not location specific

### \[signal\] void Containment::uiReadyChanged(bool *uiReady*) {#uiReadyChanged}

Emitted when the ui has been fully loaded and is fully working

`uiReady` true when the ui of the containment is ready, as well the ui of each applet in it

> **Note:** Notifier signal for property [isUiReady](plasma-containment.md#isUiReady-prop).

### \[signal\] void Containment::wallpaperGraphicsObjectChanged() {#wallpaperGraphicsObjectChanged}

Emitted when the root wallpaper item has changed

> **Note:** Notifier signal for property [wallpaperGraphicsObject](plasma-containment.md#wallpaperGraphicsObject-prop).

### QString Containment::wallpaperPlugin() const {#wallpaperPlugin}

Return wallpaper plugin.

> **Note:** Getter function for property [wallpaperPlugin](plasma-containment.md#wallpaperPlugin-prop).

*See also* [setWallpaperPlugin](plasma-containment.md#setWallpaperPlugin)()

### \[signal\] void Containment::wallpaperPluginChanged() {#wallpaperPluginChanged}

Emitted when the wallpaper plugin is changed

> **Note:** Notifier signal for property [wallpaperPlugin](plasma-containment.md#wallpaperPlugin-prop).
