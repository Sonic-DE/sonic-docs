---
title: "KDarkLightTransition Class"
description: "The KDarkLightTransition type represents a transition from day to night or vice versa."
---

# KDarkLightTransition Class

The [KDarkLightTransition](kdarklighttransition.md) type represents a transition from day to night or vice versa. [More...](#details)

- **Header:** `#include <KDarkLightTransition>`
- **CMake:** `find_package(KNightTime REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE KNightTime::KNightTime)`

[List of all members, including inherited members](kdarklighttransition-members.md)

## Public Types

- [enum KDarkLightTransition::Relation](#Relation-enum)
- [enum KDarkLightTransition::Type](#Type-enum)

## Public Functions

- [KDarkLightTransition()](#KDarkLightTransition)
- [KDarkLightTransition(KDarkLightTransition::Type type, const QDateTime &startDateTime, const QDateTime &endDateTime)](#KDarkLightTransition-1)
- [QDateTime endDateTime() const](#endDateTime)
- [qreal progress(const QDateTime &dateTime) const](#progress)
- [QDateTime startDateTime() const](#startDateTime)
- [KDarkLightTransition::Relation test(const QDateTime &dateTime) const](#test)
- [KDarkLightTransition::Type type() const](#type)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum KDarkLightTransition::Relation {#Relation-enum}

The Relation enum specifies the relationship between this transition and a point in time.

| Constant | Value | Description |
| --- | --- | --- |
| `KDarkLightTransition::Upcoming` | `0` | The specified point in time comes before the transition |
| `KDarkLightTransition::InProgress` | `1` | The specified point in time is between the start and the end of the transition |
| `KDarkLightTransition::Passed` | `2` | The specified point in time is after the transition |

### enum KDarkLightTransition::Type {#Type-enum}

The Type enum specifies the type of a transition.

| Constant | Value | Description |
| --- | --- | --- |
| `KDarkLightTransition::Morning` | `0` | Transitioning from night time to daylight |
| `KDarkLightTransition::Evening` | `1` | Transitioning from daylight to night time |

## Member Function Documentation {#member-function-documentation}

### KDarkLightTransition::KDarkLightTransition() {#KDarkLightTransition}

Constructs an invalid [KDarkLightTransition](kdarklighttransition.md) object.

### KDarkLightTransition::KDarkLightTransition(KDarkLightTransition::Type *type*, const QDateTime &*startDateTime*, const QDateTime &*endDateTime*) {#KDarkLightTransition-1}

Constructs a [KDarkLightTransition](kdarklighttransition.md) object with the specified `type`, `startDateTime`, and `endDateTime`.

### QDateTime KDarkLightTransition::endDateTime() const {#endDateTime}

Returns the date and time when the transition ends.

### qreal KDarkLightTransition::progress(const QDateTime &*dateTime*) const {#progress}

Returns the progress of the transition at the specified `dateTime`. The progress value is in \[0.0, 1.0\] range, where 0.0 corresponds to the start of the transition, and 1.0 corresponds to the end of the transition.

### QDateTime KDarkLightTransition::startDateTime() const {#startDateTime}

Returns the date and time when the transition starts.

### KDarkLightTransition::Relation KDarkLightTransition::test(const QDateTime &*dateTime*) const {#test}

Checks how the specified `dateTime` relates to this transition.

### KDarkLightTransition::Type KDarkLightTransition::type() const {#type}

Returns the type of the transition.
