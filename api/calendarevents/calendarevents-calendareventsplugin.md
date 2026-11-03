---
title: "CalendarEvents::CalendarEventsPlugin Class"
description: "Plugin for feeding events to a calendar instance."
---

# CalendarEvents::CalendarEventsPlugin Class

Plugin for feeding events to a calendar instance. [More...](#details)

- **Header:** `#include <CalendarEvents/CalendarEventsPlugin>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CalendarEvents)`  
  `target_link_libraries(mytarget PRIVATE KF6::CalendarEvents)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](calendarevents-calendareventsplugin-members.md)

## Public Types

- [enum CalendarEventsPlugin::SubLabelPriority](#SubLabelPriority-enum)

## Public Functions

- [CalendarEventsPlugin(QObject \*parent = nullptr)](#CalendarEventsPlugin)
- [void loadEventsForDateRange(const QDate &startDate, const QDate &endDate)](#loadEventsForDateRange)

## Signals

- [void alternateCalendarDateReady(const QHash\<QDate, QCalendar::YearMonthDay\> &data)](#alternateCalendarDateReady) (since 6.0)
- [void dataReady(const QMultiHash\<QDate, CalendarEvents::EventData\> &data)](#dataReady)
- [void eventModified(const CalendarEvents::EventData &modifiedEvent)](#eventModified)
- [void eventRemoved(const QString &uid)](#eventRemoved)
- [void subLabelReady(const QHash\<QDate, CalendarEvents::CalendarEventsPlugin::SubLabel\> &data)](#subLabelReady)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum CalendarEventsPlugin::SubLabelPriority {#SubLabelPriority-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `CalendarEvents::CalendarEventsPlugin::SubLabelPriority::Low` | `0` | Usually used in alternate calendars |
| `CalendarEvents::CalendarEventsPlugin::SubLabelPriority::Default` | `1` | For holidays or normal events |
| `CalendarEvents::CalendarEventsPlugin::SubLabelPriority::High` | `2` | For flagged or marked events |
| `CalendarEvents::CalendarEventsPlugin::SubLabelPriority::Urgent` | `3` |   |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] CalendarEventsPlugin::CalendarEventsPlugin(QObject \**parent* = nullptr) {#CalendarEventsPlugin}

### \[signal, since 6.0\] void CalendarEventsPlugin::alternateCalendarDateReady(const QHash\<QDate, QCalendar::YearMonthDay\> &*data*) {#alternateCalendarDateReady}

Emitted when the plugin has loaded the alternate dates

`data` A hash containing a [QDate](https://doc.qt.io/qt-6/qdate.html) key from Gregorian calendar for the alternate date in the value, [QDate](https://doc.qt.io/qt-6/qdate.html).

This function was introduced in Qt 6.0.

### \[signal\] void CalendarEventsPlugin::dataReady(const QMultiHash\<QDate, CalendarEvents::EventData\> &*data*) {#dataReady}

Emitted when the plugin has loaded the events data

`data` A hash containing a [QDate](https://doc.qt.io/qt-6/qdate.html) key for the event in the value, [CalendarEvents::EventData](calendarevents-eventdata.md), which holds all the details for the given event It's a multihash as there can be multiple events in the same day For multi-day events, insert just one with the key being the startdate of the event

### \[signal\] void CalendarEventsPlugin::eventModified(const CalendarEvents::EventData &*modifiedEvent*) {#eventModified}

Should be emitted when there is a modification of an event that was previously returned via the [dataReady](calendarevents-calendareventsplugin.md#dataReady)() signal

`event` The modified event data

### \[signal\] void CalendarEventsPlugin::eventRemoved(const QString &*uid*) {#eventRemoved}

Should be emitted when the plugin removes some event from its collection

`uid` The uid of the event that was removed

### \[pure virtual\] void CalendarEventsPlugin::loadEventsForDateRange(const QDate &*startDate*, const QDate &*endDate*) {#loadEventsForDateRange}

When this is called, the plugin should load all events data between those two date ranges. Once the data are ready, it should just emit the [dataReady](calendarevents-calendareventsplugin.md#dataReady)() signal. The range is usually one month

`startDate` the start of the range

`endDate` the end of the range

### \[signal\] void CalendarEventsPlugin::subLabelReady(const QHash\<QDate, CalendarEvents::CalendarEventsPlugin::SubLabel\> &*data*) {#subLabelReady}

Emitted when the plugin has loaded the sublabels

`data` A hash containing a [QDate](https://doc.qt.io/qt-6/qdate.html) key for the sublabels in the value, [SubLabel](calendarevents-calendareventsplugin-sublabel.md).
