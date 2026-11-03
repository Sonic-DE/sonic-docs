---
title: ""
description: "Plugin System for Calendar Events."
---

# 

Plugin System for Calendar Events. [More...](#details)

- Header: SubLabel
- CMake: find\_package(KF6 REQUIRED COMPONENTS CalendarEvents) target\_link\_libraries(mytarget PRIVATE KF6::CalendarEvents)

## Detailed Description {#details}

## Member Variable Documentation {#member-variable-documentation}

### QString SubLabel::dayLabel {#dayLabel-var}

The label will be displayed under the day number

### QString SubLabel::label {#label-var}

The label will be displayed in the tooltip or beside the full date

### QString SubLabel::monthLabel {#monthLabel-var}

The label will be displayed under the month number

### CalendarEvents::CalendarEventsPlugin::SubLabelPriority SubLabel::priority {#priority-var}

The display priority of the sublabel

### QString SubLabel::yearLabel {#yearLabel-var}

The label will be displayed under the year number
