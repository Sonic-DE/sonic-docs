---
title: "KServiceAction Class"
description: "Represents an action in a .desktop file."
---

# KServiceAction Class

Represents an action in a .desktop file. [More...](#details)

- **Header:** `#include <KServiceAction>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Service)`  
  `target_link_libraries(mytarget PRIVATE KF6::Service)`

[List of all members, including inherited members](kserviceaction-members.md)

## Public Functions

- [KServiceAction(const QString &name, const QString &text, const QString &icon, const QString &exec, bool noDisplay, const KServicePtr &service)](#KServiceAction)
- [QVariant data() const](#data)
- [QString exec() const](#exec)
- [QString icon() const](#icon)
- [bool isSeparator() const](#isSeparator)
- [QString name() const](#name)
- [bool noDisplay() const](#noDisplay)
- [template \<typename T\> T property(const QString &name) const](#property) (since 6.0)
- [KServicePtr service() const](#service)
- [void setData(const QVariant &userData)](#setData)
- [QString text() const](#text)

## Detailed Description {#details}

Actions are defined with the config key Actions in the \[Desktop Entry\] group, followed by one group per action, as per the desktop entry standard.

*See also* [KService::actions](kservice-index.md)

## Member Function Documentation {#member-function-documentation}

### KServiceAction::KServiceAction(const QString &*name*, const QString &*text*, const QString &*icon*, const QString &*exec*, bool *noDisplay*, const KServicePtr &*service*) {#KServiceAction}

Creates a [KServiceAction](kserviceaction.md).

Normally you don't have to do this, [KService](kservice-module.md) creates the actions when parsing the .desktop file.

### QVariant KServiceAction::data() const {#data}

Returns the action's internal data.

*See also* [setData](kserviceaction.md#setData)()

### QString KServiceAction::exec() const {#exec}

Returns the action's exec command, as defined by the Exec key in the desktop action group

### QString KServiceAction::icon() const {#icon}

Returns the action's icon, as defined by the Icon key in the desktop action group

### bool KServiceAction::isSeparator() const {#isSeparator}

Returns whether the action is a separator.

This is true when the Actions key contains "\_SEPARATOR\_".

### QString KServiceAction::name() const {#name}

Returns the action's internal name

For instance Actions=Setup;... and the group \[Desktop Action Setup\] define an action with the name "Setup".

### bool KServiceAction::noDisplay() const {#noDisplay}

Returns whether the action should be suppressed in menus.

This is useful for having actions with a known name that the code looks for explicitly, like Setup and Root for kscreensaver actions, and which should not appear in popup menus.

### \[since 6.0\] template \<typename T\> T KServiceAction::property(const QString &*name*) const {#property}

Returns the requested property.

T the type of the requested property

`name` the name of the requested property

This function was introduced in Qt 6.0.

### KServicePtr KServiceAction::service() const {#service}

Returns the service that this action comes from

### void KServiceAction::setData(const QVariant &*userData*) {#setData}

Sets the action's internal data to the given `userData`.

*See also* [data](kserviceaction.md#data)()

### QString KServiceAction::text() const {#text}

Returns the action's text, as defined by the Name key in the desktop action group
