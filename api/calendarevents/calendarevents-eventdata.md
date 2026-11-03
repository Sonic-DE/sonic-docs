---
title: "CalendarEvents::EventData Class"
description: "Data about an event."
---

# CalendarEvents::EventData Class

Data about an event. [More...](#details)

- **Header:** `#include <CalendarEvents/CalendarEventsPlugin>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CalendarEvents)`  
  `target_link_libraries(mytarget PRIVATE KF6::CalendarEvents)`

[List of all members, including inherited members](calendarevents-eventdata-members.md)

## Public Types

- [enum EventData::EventType](#EventType-enum)

## Public Functions

- [EventData()](#EventData)
- [QString description() const](#description)
- [QDateTime endDateTime() const](#endDateTime)
- [QString eventColor() const](#eventColor)
- [bool isAllDay() const](#isAllDay)
- [bool isMinor() const](#isMinor)
- [QString location() const](#location) (since 6.27)
- [void setDescription(const QString &description)](#setDescription)
- [void setEndDateTime(const QDateTime &endDateTime)](#setEndDateTime)
- [void setEventColor(const QString &color)](#setEventColor)
- [void setEventType(CalendarEvents::EventData::EventType type)](#setEventType)
- [void setIsAllDay(bool isAllDay)](#setIsAllDay)
- [void setIsMinor(bool isMinor)](#setIsMinor)
- [void setLocation(const QString &location)](#setLocation) (since 6.27)
- [void setStartDateTime(const QDateTime &startDateTime)](#setStartDateTime)
- [void setTitle(const QString &title)](#setTitle)
- [void setUid(const QString &uid)](#setUid)
- [QDateTime startDateTime() const](#startDateTime)
- [QString title() const](#title)
- [CalendarEvents::EventData::EventType type() const](#type)
- [QString uid() const](#uid)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum EventData::EventType {#EventType-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `CalendarEvents::EventData::Holiday` | `0` | Any holiday |
| `CalendarEvents::EventData::Event` | `1` | General Event |
| `CalendarEvents::EventData::Todo` | `2` | A Todo item |

## Member Function Documentation {#member-function-documentation}

### EventData::EventData() {#EventData}

### QString EventData::description() const {#description}

Event description, can provide more details about the event

*See also* [setDescription](calendarevents-eventdata.md#setDescription)()

### QDateTime EventData::endDateTime() const {#endDateTime}

The end date and time of this event

*See also* [setEndDateTime](calendarevents-eventdata.md#setEndDateTime)()

### QString EventData::eventColor() const {#eventColor}

The color that should be used to mark this event with It comes in the HTML hex format, eg. \#AARRGGBB or \#RRGGBB

*See also* [setEventColor](calendarevents-eventdata.md#setEventColor)()

### bool EventData::isAllDay() const {#isAllDay}

If true, this event goes on the whole day (eg. a holiday)

*See also* [setIsAllDay](calendarevents-eventdata.md#setIsAllDay)()

### bool EventData::isMinor() const {#isMinor}

If true, this event won't mark the day in the calendar grid The main purpose for this flag is to support namedays, where in some countries the calendars have different name in them every day. This is just a minor holiday and as such should not mark the calendar grid, otherwise the whole grid would be in a different color.

*See also* [setIsMinor](calendarevents-eventdata.md#setIsMinor)()

### \[since 6.27\] QString EventData::location() const {#location}

Event location (physical place)

This function was introduced in Qt 6.27.

*See also* [setLocation](calendarevents-eventdata.md#setLocation)()

### void EventData::setDescription(const QString &*description*) {#setDescription}

Sets the event description, which allows to add more details about this event

`description` The description

*See also* [description](calendarevents-eventdata.md#description)()

### void EventData::setEndDateTime(const QDateTime &*endDateTime*) {#setEndDateTime}

Set the end date-time of this event

`endDateTime` the date-time of when the event is ending

*See also* [endDateTime](calendarevents-eventdata.md#endDateTime)()

### void EventData::setEventColor(const QString &*color*) {#setEventColor}

This is to support various calendar colors the user might have configured elsewhere

`color` The color for this event in the HTML hex format eg. \#AARRGGBB or \#RRGGBB (this is passed directly to QML)

*See also* [eventColor](calendarevents-eventdata.md#eventColor)()

### void EventData::setEventType(CalendarEvents::EventData::EventType *type*) {#setEventType}

Sets the event type, eg. a holiday, an event or a todo item

`type` The event type,

### void EventData::setIsAllDay(bool *isAllDay*) {#setIsAllDay}

If set to true, it will be displayed in the Calendar agenda without any time besides it, marked as "going on all day"

This is useful for single-day events only, for multiple-day events, leave to false (default)

`isAllDay` set to true if the event takes all day, false otherwise (defaults to false)

*See also* [isAllDay](calendarevents-eventdata.md#isAllDay)()

### void EventData::setIsMinor(bool *isMinor*) {#setIsMinor}

If set to true, it won't be marked in the calendar grid

`isMinor` true if it's a minor event (like a nameday holiday), false otherwise (defaults to false)

*See also* [isMinor](calendarevents-eventdata.md#isMinor)()

### \[since 6.27\] void EventData::setLocation(const QString &*location*) {#setLocation}

Sets the event location

`location` The location string

This function was introduced in Qt 6.27.

*See also* [location](calendarevents-eventdata.md#location)()

### void EventData::setStartDateTime(const QDateTime &*startDateTime*) {#setStartDateTime}

Set the start date-time of this event

`startDateTime` the date-time of when the event is starting

*See also* [startDateTime](calendarevents-eventdata.md#startDateTime)()

### void EventData::setTitle(const QString &*title*) {#setTitle}

Sets the title of the event

`title` The event title

*See also* [title](calendarevents-eventdata.md#title)()

### void EventData::setUid(const QString &*uid*) {#setUid}

Sets the uid of the event

This is a mandatory field only if you want to use the eventModified/eventRemoved signals, otherwise setting it is optional

`uid` A unique id, recommended is to use the plugin name as prefix (to keep it unique)

*See also* [uid](calendarevents-eventdata.md#uid)()

### QDateTime EventData::startDateTime() const {#startDateTime}

The start date and time of this event

*See also* [setStartDateTime](calendarevents-eventdata.md#setStartDateTime)()

### QString EventData::title() const {#title}

Event title

*See also* [setTitle](calendarevents-eventdata.md#setTitle)()

### CalendarEvents::EventData::EventType EventData::type() const {#type}

Type of the current event, eg. a holiday, an event or a todo item

### QString EventData::uid() const {#uid}

Unique ID of the event

*See also* [setUid](calendarevents-eventdata.md#setUid)()
