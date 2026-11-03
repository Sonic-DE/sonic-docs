---
title: "Plasmoid QML Type"
description: "Common attached properties for plasmoids."
---

# Plasmoid QML Type

Common attached properties for plasmoids. [More...](#details)

- Import Statement: import org.kde.plasma.plasmoid
- In C++: [Applet](../plasma/plasma-applet.md)

## Detailed Description {#details}

## Attached Property Documentation {#attached-property-documentation}

### Plasmoid.backgroundHints : Plasma.Types.BackgroundHints {#backgroundHints-attached-prop}

How the plasmoid wants its background to be drawn.

The containment may ignore this hint with [userBackgroundHints](qml-org-kde-plasma-plasmoid-plasmoid.md#userBackgroundHints-attached-prop).

### Plasmoid.busy : bool {#busy-attached-prop}

True if the plasmoid should show a busy status, for instance while doing some network operation.

### \[read-only\] Plasmoid.configuration : KConfigPropertyMap {#configuration-attached-prop}

Configuration for the plasmoid.

Can be used to read and write settings like any JavaScript Object.

### Plasmoid.configurationRequired : bool {#configurationRequired-attached-prop}

If true, the plasmoid requires manual configuration from the user.

### Plasmoid.constraintHints : Plasma.Applet.ConstraintHints {#constraintHints-attached-prop}

Hints how the plasmoid should be constrained, such as asking to fill all the available space ignoring margins.

### \[read-only\] Plasmoid.containment : Containment {#containment-attached-prop}

The Containment managing this plasmoid.

### \[read-only\] Plasmoid.containmentDisplayHints : Plasma.Types.ContainmentDisplayHints {#containmentDisplayHints-attached-prop}

Display hints that come from the containment that suggest how the plasmoid should look and behave. TODO: only in containment?

### \[read-only\] Plasmoid.contextualActions : list\<Action\> {#contextualActions-attached-prop}

Actions to be added in the plasmoid's context menu.

Use PlasmaCore.Action to instantiate QActions declaratively.

### \[read-only\] Plasmoid.effectiveBackgroundHints : Plasma.Types.BackgroundHints {#effectiveBackgroundHints-attached-prop}

Returns the effective background hints.

The [userBackgroundHints](qml-org-kde-plasma-plasmoid-plasmoid.md#userBackgroundHints-attached-prop) will be preferred if set, otherwise returns the plasmoid's [backgroundHints](qml-org-kde-plasma-plasmoid-plasmoid.md#backgroundHints-attached-prop).

### \[read-only\] Plasmoid.formFactor : Plasma.Types.FormFactor {#formFactor-attached-prop}

The current form factor the plasmoid is being displayed in.

### Plasmoid.globalShortcut : Shortcut {#globalShortcut-attached-prop}

The global shortcut to activate the plasmoid.

This is typically only used by the default configuration module.

### Plasmoid.hasConfigurationInterface : bool {#hasConfigurationInterface-attached-prop}

True if this plasmoid will provide a UI for its configuration.

### Plasmoid.icon : string {#icon-attached-prop}

Icon to represent the Plasmoid.

### \[read-only\] Plasmoid.id : int {#id-attached-prop}

The plasmoid's id is unique in the whole Plasma session and will never change across restarts.

### Plasmoid.immutability : Plasma.Types.ImmutabilityType {#immutability-attached-prop}

Sets the immutability of the Corona. Tells the plasmoid whether it should allow for any modification by the user.

### \[read-only\] Plasmoid.immutable : bool {#immutable-attached-prop}

Whether the Corona is immutable.

The plasmoid implementation should avoid allowing "dangerous" modifications from the user when in an immutable mode.

This is true when immutability is not Mutable.

### \[read-only\] Plasmoid.isContainment : bool {#isContainment-attached-prop}

Whether this plasmoid is a Containment and is acting as one, such as a desktop or a panel.

### \[read-only\] Plasmoid.location : Plasma.Types.Location {#location-attached-prop}

The location of the scene which is displaying this plasmoid.

### \[read-only\] Plasmoid.metaData : KPluginMetaData {#metaData-attached-prop}

The metadata of the plasmoid.

### \[read-only\] Plasmoid.pluginName : string {#pluginName-attached-prop}

Plugin name for the plasmoid.

### Plasmoid.status : Plasma.Types.ItemStatus {#status-attached-prop}

Allows to instruct the shell if this plasmoid is requesting attention, accepting input, or if it is in an idle, inactive state.

### Plasmoid.title : string {#title-attached-prop}

User friendly title for the plasmoid, the localized plasmoid name by default.

### Plasmoid.userBackgroundHints : Plasma.Types.BackgroundHints {#userBackgroundHints-attached-prop}

Allows the containment or user to override the set [backgroundHints](qml-org-kde-plasma-plasmoid-plasmoid.md#backgroundHints-attached-prop) if they exist.

### \[read-only\] Plasmoid.userConfiguring : bool {#userConfiguring-attached-prop}

True when the user is configuring, for instance when the configuration dialog is open.
