---
title: "CalendarEvents::ShowEventInterface Class"
description: "Interface for displaying event details."
---

# CalendarEvents::ShowEventInterface Class

Interface for displaying event details. [More...](#details)

- **Header:** `#include <CalendarEvents/CalendarEventsPlugin>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CalendarEvents)`  
  `target_link_libraries(mytarget PRIVATE KF6::CalendarEvents)`

[List of all members, including inherited members](calendarevents-showeventinterface-members.md)

## Public Functions

- [bool showEvent(const QString &uid)](#showEvent)

## Detailed Description {#details}

[ShowEventInterface](calendarevents-showeventinterface.md) is an additional interface the [CalendarEventsPlugin](calendarevents-calendareventsplugin.md) implementations can implement if they support displaying details about events (e.g. opening the event in KOrganizer).

## Member Function Documentation {#member-function-documentation}

### \[pure virtual\] bool ShowEventInterface::showEvent(const QString &*uid*) {#showEvent}

When this is called, the plugin should show a window displaying the full preview of the event.

The plugin should return true if the event details can be displayed, false otherwise.
