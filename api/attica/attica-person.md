---
title: "Attica::Person Class"
description: "Represents a person."
---

# Attica::Person Class

Represents a person. [More...](#details)

- **Header:** `#include <Attica/Person>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-person-members.md)

## Public Types

- [Person::List](#List-typedef)

## Public Functions

- [Person()](#Person)
- [void addExtendedAttribute(const QString &key, const QString &value)](#addExtendedAttribute)
- [QUrl avatarUrl() const](#avatarUrl)
- [QDate birthday() const](#birthday)
- [QString city() const](#city)
- [QString country() const](#country)
- [QString extendedAttribute(const QString &key) const](#extendedAttribute)
- [QMap\<QString, QString\> extendedAttributes() const](#extendedAttributes)
- [QString firstName() const](#firstName)
- [QString homepage() const](#homepage)
- [QString id() const](#id)
- [bool isValid() const](#isValid)
- [QString lastName() const](#lastName)
- [qreal latitude() const](#latitude)
- [qreal longitude() const](#longitude)
- [void setAvatarUrl(const QUrl &)](#setAvatarUrl)
- [void setBirthday(const QDate &)](#setBirthday)
- [void setCity(const QString &)](#setCity)
- [void setCountry(const QString &)](#setCountry)
- [void setFirstName(const QString &)](#setFirstName)
- [void setHomepage(const QString &)](#setHomepage)
- [void setId(const QString &)](#setId)
- [void setLastName(const QString &)](#setLastName)
- [void setLatitude(qreal)](#setLatitude)
- [void setLongitude(qreal)](#setLongitude)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### Person::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### Person::Person() {#Person}

### void Person::addExtendedAttribute(const QString &*key*, const QString &*value*) {#addExtendedAttribute}

### QUrl Person::avatarUrl() const {#avatarUrl}

*See also* [setAvatarUrl](attica-person.md#setAvatarUrl)()

### QDate Person::birthday() const {#birthday}

*See also* [setBirthday](attica-person.md#setBirthday)()

### QString Person::city() const {#city}

*See also* [setCity](attica-person.md#setCity)()

### QString Person::country() const {#country}

*See also* [setCountry](attica-person.md#setCountry)()

### QString Person::extendedAttribute(const QString &*key*) const {#extendedAttribute}

### QMap\<QString, QString\> Person::extendedAttributes() const {#extendedAttributes}

### QString Person::firstName() const {#firstName}

*See also* [setFirstName](attica-person.md#setFirstName)()

### QString Person::homepage() const {#homepage}

*See also* [setHomepage](attica-person.md#setHomepage)()

### QString Person::id() const {#id}

*See also* [setId](attica-person.md#setId)()

### bool Person::isValid() const {#isValid}

### QString Person::lastName() const {#lastName}

*See also* [setLastName](attica-person.md#setLastName)()

### qreal Person::latitude() const {#latitude}

*See also* [setLatitude](attica-person.md#setLatitude)()

### qreal Person::longitude() const {#longitude}

*See also* [setLongitude](attica-person.md#setLongitude)()

### void Person::setAvatarUrl(*const QUrl &*) {#setAvatarUrl}

*See also* [avatarUrl](attica-person.md#avatarUrl)()

### void Person::setBirthday(*const QDate &*) {#setBirthday}

*See also* [birthday](attica-person.md#birthday)()

### void Person::setCity(*const QString &*) {#setCity}

*See also* [city](attica-person.md#city)()

### void Person::setCountry(*const QString &*) {#setCountry}

*See also* [country](attica-person.md#country)()

### void Person::setFirstName(*const QString &*) {#setFirstName}

*See also* [firstName](attica-person.md#firstName)()

### void Person::setHomepage(*const QString &*) {#setHomepage}

*See also* [homepage](attica-person.md#homepage)()

### void Person::setId(*const QString &*) {#setId}

*See also* [id](attica-person.md#id)()

### void Person::setLastName(*const QString &*) {#setLastName}

*See also* [lastName](attica-person.md#lastName)()

### void Person::setLatitude(*qreal*) {#setLatitude}

*See also* [latitude](attica-person.md#latitude)()

### void Person::setLongitude(*qreal*) {#setLongitude}

*See also* [longitude](attica-person.md#longitude)()
