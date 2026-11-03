---
title: "KParts::ListingNotificationExtension Class"
description: "An extension for receiving listing change notification."
---

# KParts::ListingNotificationExtension Class

An extension for receiving listing change notification. [More...](#details)

- **Header:** `#include <KParts/ListingNotificationExtension>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Parts)`  
  `target_link_libraries(mytarget PRIVATE KF6::Parts)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kparts-listingnotificationextension-members.md)

## Public Types

- [enum ListingNotificationExtension::NotificationEventType](#NotificationEventType-enum)

## Public Functions

- [ListingNotificationExtension(KParts::ReadOnlyPart \*parent)](#ListingNotificationExtension)
- [KParts::ListingNotificationExtension::NotificationEventTypes supportedNotificationEventTypes() const](#supportedNotificationEventTypes)

## Signals

- [void listingEvent(KParts::ListingNotificationExtension::NotificationEventType, const KFileItemList &)](#listingEvent)

## Static Public Members

- [KParts::ListingNotificationExtension \*childObject(QObject \*obj)](#childObject)

## Detailed Description {#details}

This extension is intended for implementation by parts that provide listing services, e.g. file management and is intended to notify about changes to a given listing. For example, if file management part implemented this extension it would emit itemsDeleted and itemsAdded signal whenever new files or folders are deleted and added to a directory respectively.

## Member Type Documentation {#member-type-documentation}

### enum ListingNotificationExtension::NotificationEventType {#NotificationEventType-enum}

**flags ListingNotificationExtension::NotificationEventTypes**

Supported notification event types.

| Constant | Value |   |
| --- | --- | --- |
| `KParts::ListingNotificationExtension::None` | `0x00` |   |
| `KParts::ListingNotificationExtension::ItemsAdded` | `0x01` | New items added to the listing. |
| `KParts::ListingNotificationExtension::ItemsDeleted` | `0x02` | Items deleted from the listing. |

The `NotificationEventTypes` type is a typedef for `QFlags<NotificationEventType>. `It stores an OR combination of `NotificationEventType` values.

## Member Function Documentation {#member-function-documentation}

### ListingNotificationExtension::ListingNotificationExtension(KParts::ReadOnlyPart \**parent*) {#ListingNotificationExtension}

Constructor

### \[static\] KParts::ListingNotificationExtension \*ListingNotificationExtension::childObject(QObject \**obj*) {#childObject}

Queries `obj` for a child object which inherits from this class.

### \[signal\] void ListingNotificationExtension::listingEvent(*KParts::ListingNotificationExtension::NotificationEventType*, *const KFileItemList &*) {#listingEvent}

This signal is emitted when one of the notification events listed in [NotificationEventType](kparts-listingnotificationextension.md#NotificationEventType-enum) occur.

### \[virtual\] KParts::ListingNotificationExtension::NotificationEventTypes ListingNotificationExtension::supportedNotificationEventTypes() const {#supportedNotificationEventTypes}

Returns the OR'ed value of the notification types supported by the part that implements this extension.

By default this function returns None.
