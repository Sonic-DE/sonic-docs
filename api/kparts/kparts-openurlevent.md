---
title: "KParts::OpenUrlEvent Class"
description: "The KParts::OpenUrlEvent event informs that a given part has opened a given URL."
---

# KParts::OpenUrlEvent Class

The [KParts::OpenUrlEvent](kparts-openurlevent.md) event informs that a given part has opened a given URL. [More...](#details)

- **Header:** `#include <KParts/OpenUrlEvent>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Parts)`  
  `target_link_libraries(mytarget PRIVATE KF6::Parts)`
- **Inherits:** [QEvent](https://doc.qt.io/qt-6/qevent.html)

[List of all members, including inherited members](kparts-openurlevent-members.md)

## Public Functions

- [OpenUrlEvent(KParts::ReadOnlyPart \*part, const QUrl &url, const KParts::OpenUrlArguments &args = OpenUrlArguments())](#OpenUrlEvent)
- [KParts::OpenUrlArguments arguments() const](#arguments)
- [KParts::ReadOnlyPart \*part() const](#part)
- [QUrl url() const](#url)

## Static Public Members

- [bool test(const QEvent \*event)](#test)

## Detailed Description {#details}

Applications can use this event to send this information to interested plugins.

The event should be sent before opening the URL in the part, so that the plugins can use [part](kparts-openurlevent.md#part)()-\>[url](kparts-openurlevent.md#url)() to get the old URL.

## Member Function Documentation {#member-function-documentation}

### OpenUrlEvent::OpenUrlEvent(KParts::ReadOnlyPart \**part*, const QUrl &*url*, const KParts::OpenUrlArguments &*args* = OpenUrlArguments()) {#OpenUrlEvent}

### KParts::OpenUrlArguments OpenUrlEvent::arguments() const {#arguments}

### KParts::ReadOnlyPart \*OpenUrlEvent::part() const {#part}

### \[static\] bool OpenUrlEvent::test(const QEvent \**event*) {#test}

### QUrl OpenUrlEvent::url() const {#url}
