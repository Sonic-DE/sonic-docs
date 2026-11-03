---
title: "KParts C++ Classes"
description: "Plugin framework for user interface components."
---

# KParts C++ Classes

Plugin framework for user interface components. [More...](#details)

## Namespaces {#namespaces}

- [KParts](kparts.md)
- [KParts::PartLoader](kparts-partloader.md): Helper methods for locating and loading parts.

## Classes {#classes}

- [KParts::FileInfoExtension](kparts-fileinfoextension.md): An extension for obtaining file information from the part.
- [KParts::GUIActivateEvent](kparts-guiactivateevent.md): This event is sent to a Part when its GUI has been activated or deactivated.
- [KParts::ListingFilterExtension](kparts-listingfilterextension.md): An extension for filtering listings.
- [KParts::ListingNotificationExtension](kparts-listingnotificationextension.md): An extension for receiving listing change notification.
- [KParts::MainWindow](kparts-mainwindow.md): A KPart-aware main window, whose user interface is described in XML.
- [KParts::NavigationExtension](kparts-navigationextension.md): An extension to KParts::ReadOnlyPart, which allows a better integration of parts with browsers (in particular Konqueror).
- [KParts::OpenUrlArguments](kparts-openurlarguments.md): OpenUrlArguments is the set of arguments that specify how a URL should be opened by KParts::ReadOnlyPart::openUrl().
- [KParts::OpenUrlEvent](kparts-openurlevent.md): The KParts::OpenUrlEvent event informs that a given part has opened a given URL.
- [KParts::Part](kparts-part.md): Base class for parts.
- [KParts::PartActivateEvent](kparts-partactivateevent.md): This event is sent by the part manager when the active part changes.
- [KParts::PartBase](kparts-partbase.md): Base class for all parts.
- [KParts::PartManager](kparts-partmanager.md): The part manager is an object which knows about a collection of parts (even nested ones) and handles activation/deactivation.
- [KParts::ReadOnlyPart](kparts-readonlypart.md): Base class for any "viewer" part.
- [KParts::ReadWritePart](kparts-readwritepart.md): Base class for an "editor" part.
- [KParts::StatusBarExtension](kparts-statusbarextension.md): An extension for KParts that allows more sophisticated statusbar handling.

## Detailed Description {#details}
