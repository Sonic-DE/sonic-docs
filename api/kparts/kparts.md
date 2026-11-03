---
title: "KParts Namespace"
description: "Plugin framework for user interface components."
---

# KParts Namespace

Plugin framework for user interface components. [More...](#details)

- Header: KParts
- CMake: find\_package(KF6 REQUIRED COMPONENTS Parts) target\_link\_libraries(mytarget PRIVATE KF6::Parts)

## Detailed Description {#details}

## Namespaces {#namespaces}

### \[since KParts 5.69\] namespace KParts::PartLoader

This is based upon [KPluginFactory](../kcoreaddons/kpluginfactory.md), but it takes care of querying by mimetype, sorting the available parts by builtin preference and by user preference.

This namespace was introduced in KParts 5.69.

## Classes {#classes}

### class [FileInfoExtension](kparts-fileinfoextension.md)

An extension for obtaining file information from the part.

### class [GUIActivateEvent](kparts-guiactivateevent.md)

This event is sent to a Part when its GUI has been activated or deactivated.

### class [ListingFilterExtension](kparts-listingfilterextension.md)

An extension for filtering listings.

### class [ListingNotificationExtension](kparts-listingnotificationextension.md)

An extension for receiving listing change notification.

### class [MainWindow](kparts-mainwindow.md)

A KPart-aware main window, whose user interface is described in XML.

### class [NavigationExtension](kparts-navigationextension.md)

An extension to [KParts::ReadOnlyPart](kparts-readonlypart.md), which allows a better integration of parts with browsers (in particular Konqueror).

### class [OpenUrlArguments](kparts-openurlarguments.md)

[OpenUrlArguments](kparts-openurlarguments.md) is the set of arguments that specify how a URL should be opened by KParts::ReadOnlyPart::openUrl().

### class [OpenUrlEvent](kparts-openurlevent.md)

The [KParts::OpenUrlEvent](kparts-openurlevent.md) event informs that a given part has opened a given URL.

### class [Part](kparts-part.md)

Base class for parts.

### class [PartActivateEvent](kparts-partactivateevent.md)

This event is sent by the part manager when the active part changes.

### class [PartBase](kparts-partbase.md)

Base class for all parts.

### class [PartManager](kparts-partmanager.md)

The part manager is an object which knows about a collection of parts (even nested ones) and handles activation/deactivation.

### class [ReadOnlyPart](kparts-readonlypart.md)

Base class for any "viewer" part.

### class [ReadWritePart](kparts-readwritepart.md)

Base class for an "editor" part.

### class [StatusBarExtension](kparts-statusbarextension.md)

An extension for [KParts](kparts-module.md) that allows more sophisticated statusbar handling.

## Type Documentation {#type-documentation}

### enum KParts::PartCapability {#PartCapability-enum}

**flags KParts::PartCapabilities**

Enum for standardized capabilities of [KParts](kparts-module.md)

```cpp
{
 "KPlugin": {...},
 "KParts": {
     "Capabilities": [
         "ReadOnly"
     ],
     "InitialPreference": 42
 }
}
```

| Constant |   |
| --- | --- |
| `KParts::PartCapability::ReadOnly` | `1` |
| `KParts::PartCapability::ReadWrite` | `2` |
| `KParts::PartCapability::BrowserView` | `4` |

The `PartCapabilities` type is a typedef for `QFlags<PartCapability>. `It stores an OR combination of `PartCapability` values.
