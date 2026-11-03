---
title: "Attica::Event Class"
description: "Represents a single event."
---

# Attica::Event Class

Represents a single event. [More...](#details)

- **Header:** `#include <Attica/Event>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-event-members.md)

## Public Types

- [Event::List](#List-typedef)

## Public Functions

- [Event()](#Event)
- [void addExtendedAttribute(const QString &key, const QString &value)](#addExtendedAttribute)
- [QString city() const](#city)
- [QString country() const](#country)
- [QString description() const](#description)
- [QDate endDate() const](#endDate)
- [QString extendedAttribute(const QString &key) const](#extendedAttribute)
- [QMap\<QString, QString\> extendedAttributes() const](#extendedAttributes)
- [QUrl homepage() const](#homepage)
- [QString id() const](#id)
- [bool isValid() const](#isValid)
- [qreal latitude() const](#latitude)
- [qreal longitude() const](#longitude)
- [QString name() const](#name)
- [void setCity(const QString &city)](#setCity)
- [void setCountry(const QString &country)](#setCountry)
- [void setDescription(const QString &description)](#setDescription)
- [void setEndDate(const QDate &endDate)](#setEndDate)
- [void setHomepage(const QUrl &homepage)](#setHomepage)
- [void setId(const QString &id)](#setId)
- [void setLatitude(qreal latitude)](#setLatitude)
- [void setLongitude(qreal longitude)](#setLongitude)
- [void setName(const QString &name)](#setName)
- [void setStartDate(const QDate &startDate)](#setStartDate)
- [void setUser(const QString &user)](#setUser)
- [QDate startDate() const](#startDate)
- [QString user() const](#user)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### Event::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### Event::Event() {#Event}

Creates an empty Event

### void Event::addExtendedAttribute(const QString &*key*, const QString &*value*) {#addExtendedAttribute}

Add an attribute that is not included in the basis set of attributes exposed by the Event class.

If the attribute already exists it gets overwritten.

`key` the key of the attribute

`value` the value of the attribute

### QString Event::city() const {#city}

Returns the city where the Event takes place.

*See also* [setCity](attica-event.md#setCity)()

### QString Event::country() const {#country}

Returns the country where the Event takes place.

*See also* [setCountry](attica-event.md#setCountry)()

### QString Event::description() const {#description}

Returns the description of the Event.

*See also* [setDescription](attica-event.md#setDescription)()

### QDate Event::endDate() const {#endDate}

Returns the start date of the Event.

*See also* [setEndDate](attica-event.md#setEndDate)()

### QString Event::extendedAttribute(const QString &*key*) const {#extendedAttribute}

Get an attribute that is not included in the basis set of attributes exposed by the Event class.

`key` the key of the attribute

Returns the value of the attribute with the specified key, or an empty string, if the key has not been found

### QMap\<QString, QString\> Event::extendedAttributes() const {#extendedAttributes}

Get all attributes that are not included in the basis set of attributes exposed by the Event class.

### QUrl Event::homepage() const {#homepage}

Returns the homepage of the Event.

*See also* [setHomepage](attica-event.md#setHomepage)()

### QString Event::id() const {#id}

Returns the id of the Event.

The id uniquely identifies a Event with the OCS API.

*See also* [setId](attica-event.md#setId)()

### bool Event::isValid() const {#isValid}

Checks whether this Event has an id

### qreal Event::latitude() const {#latitude}

Returns the latitude of the position the Event takes place.

*See also* [setLatitude](attica-event.md#setLatitude)()

### qreal Event::longitude() const {#longitude}

Returns the longitude of the position the Event takes place.

*See also* [setLongitude](attica-event.md#setLongitude)()

### QString Event::name() const {#name}

Returns the name of the Event.

*See also* [setName](attica-event.md#setName)()

### void Event::setCity(const QString &*city*) {#setCity}

Sets the city where the Event takes place.

`city` the new city

*See also* [city](attica-event.md#city)()

### void Event::setCountry(const QString &*country*) {#setCountry}

Sets the country where the Event takes place.

`country` the new country

*See also* [country](attica-event.md#country)()

### void Event::setDescription(const QString &*description*) {#setDescription}

Sets the description of the Event.

`description` the new description

*See also* [description](attica-event.md#description)()

### void Event::setEndDate(const QDate &*endDate*) {#setEndDate}

Sets the end date of the Event.

`endDate` the end date

*See also* [endDate](attica-event.md#endDate)()

### void Event::setHomepage(const QUrl &*homepage*) {#setHomepage}

Sets the homepage of the Event.

`homepage` the new homepage

*See also* [homepage](attica-event.md#homepage)()

### void Event::setId(const QString &*id*) {#setId}

Sets the id of the Event.

The id uniquely identifies a Event with the OCS API.

`id` the new id

*See also* [id](attica-event.md#id)()

### void Event::setLatitude(qreal *latitude*) {#setLatitude}

Sets the latitude of the position the Event takes place.

*See also* [latitude](attica-event.md#latitude)()

### void Event::setLongitude(qreal *longitude*) {#setLongitude}

Sets the longitude of the position the Event takes place.

*See also* [longitude](attica-event.md#longitude)()

### void Event::setName(const QString &*name*) {#setName}

Sets the name of the Event.

`name` the new name

*See also* [name](attica-event.md#name)()

### void Event::setStartDate(const QDate &*startDate*) {#setStartDate}

Sets the start date of the Event.

`startDate` the start date

*See also* [startDate](attica-event.md#startDate)()

### void Event::setUser(const QString &*user*) {#setUser}

Sets the id of the user bound to the Event.

`user` the new user id

*See also* [user](attica-event.md#user)()

### QDate Event::startDate() const {#startDate}

Returns the start date of the Event.

*See also* [setStartDate](attica-event.md#setStartDate)()

### QString Event::user() const {#user}

Returns the id of the user bound to the Event.

*See also* [setUser](attica-event.md#setUser)()
