---
title: "KAboutPerson Class"
description: "This class is used to store information about a person or developer."
---

# KAboutPerson Class

This class is used to store information about a person or developer. [More...](#details)

- **Header:** `#include <KAboutData>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`

[List of all members, including inherited members](kaboutperson-members.md)

## Properties

- [\[read-only\] avatarUrl : const QUrl](#avatarUrl-prop)
- [\[read-only\] emailAddress : const QString](#emailAddress-prop)
- [\[read-only\] name : const QString](#name-prop)
- [\[read-only\] task : const QString](#task-prop)
- [\[read-only\] webAddress : const QString](#webAddress-prop)

## Public Functions

- [KAboutPerson(const QString &name = QString(), const QString &task = QString(), const QString &emailAddress = QString(), const QString &webAddress = QString(), const QUrl &avatarUrl = QUrl())](#KAboutPerson-1)
- [KAboutPerson(const KAboutPerson &other)](#KAboutPerson)
- [QUrl avatarUrl() const](#avatarUrl) (since 6.0)
- [QString emailAddress() const](#emailAddress)
- [QString name() const](#name)
- [QString task() const](#task)
- [QString webAddress() const](#webAddress)
- [KAboutPerson &KAboutPerson::operator=(const KAboutPerson &other)](#operator-eq)

## Static Public Members

- [KAboutPerson fromJSON(const QJsonObject &obj)](#fromJSON)

## Detailed Description {#details}

It can store the person's name, a task, an email address and a link to a home page. This class is intended for use in the [KAboutData](kaboutdata.md) class, but it can be used elsewhere as well. Normally you should at least define the person's name. Creating a [KAboutPerson](kaboutperson.md) object by yourself is relatively useless, but the [KAboutData](kaboutdata.md) methods [KAboutData::authors](kaboutdata.md#authors)() and [KAboutData::credits](kaboutdata.md#credits)() return lists of [KAboutPerson](kaboutperson.md) data objects which you can examine.

Example usage within a main(), retrieving the list of people involved with a program and re-using data from one of them:

```cpp
KAboutData about("khello", i18n("KHello"), "0.1",
                  i18n("A KDE version of Hello, world!"),
                  KAboutLicense::LGPL,
                  i18n("Copyright (C) 2014 Developer"));

about.addAuthor(i18n("Joe Developer"), i18n("developer"), "joe@host.com", 0);
QList<KAboutPerson> people = about.authors();
about.addCredit(people[0].name(), people[0].task());
```

## Property Documentation {#property-documentation}

### \[read-only\] avatarUrl : const QUrl {#avatarUrl-prop}

**Access functions:**

- `QUrl` **[avatarUrl](kaboutperson.md#avatarUrl)**() const

### \[read-only\] emailAddress : const QString {#emailAddress-prop}

**Access functions:**

- `QString` **[emailAddress](kaboutperson.md#emailAddress)**() const

### \[read-only\] name : const QString {#name-prop}

**Access functions:**

- `QString` **[name](kaboutperson.md#name)**() const

### \[read-only\] task : const QString {#task-prop}

**Access functions:**

- `QString` **[task](kaboutperson.md#task)**() const

### \[read-only\] webAddress : const QString {#webAddress-prop}

**Access functions:**

- `QString` **[webAddress](kaboutperson.md#webAddress)**() const

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KAboutPerson::KAboutPerson(const QString &*name* = QString(), const QString &*task* = QString(), const QString &*emailAddress* = QString(), const QString &*webAddress* = QString(), const QUrl &*avatarUrl* = QUrl()) {#KAboutPerson-1}

Convenience constructor

`name` The name of the person.

`task` The task of this person.

`emailAddress` The email address of the person.

`webAddress` Home page of the person.

`avatarUrl` URL to the avatar of the person, since 6.0

`name` default argument, since 5.53

### KAboutPerson::KAboutPerson(const KAboutPerson &*other*) {#KAboutPerson}

Copy constructor. Performs a deep copy.

`other` object to copy

### \[since 6.0\] QUrl KAboutPerson::avatarUrl() const {#avatarUrl}

Returns an URL pointing to the user's avatar

> **Note:** Getter function for property [avatarUrl](kaboutperson.md#avatarUrl-prop).

This function was introduced in Qt 6.0.

### QString KAboutPerson::emailAddress() const {#emailAddress}

Returns the person's email address (can be QString(), if it has been constructed with an empty email)

> **Note:** Getter function for property [emailAddress](kaboutperson.md#emailAddress-prop).

### \[static\] KAboutPerson KAboutPerson::fromJSON(const QJsonObject &*obj*) {#fromJSON}

Creates a `KAboutPerson` from a JSON object with the following structure:

| Key | Accessor |
| --- | --- |
| Name | [name](kaboutperson.md#name)() |
| EMail | [emailAddress](kaboutperson.md#emailAddress)() |
| Task | [task](kaboutperson.md#task)() |
| Website | [webAddress](kaboutperson.md#webAddress)() |
| AvatarUrl | [avatarUrl](kaboutperson.md#avatarUrl)() |

The `Name` and `Task` key are translatable (by using e.g. a "Task\[de\_DE\]" key) The AvatarUrl exists since version 6.0

### QString KAboutPerson::name() const {#name}

Returns the person's name (can be QString(), if it has been constructed with an empty name)

> **Note:** Getter function for property [name](kaboutperson.md#name-prop).

### QString KAboutPerson::task() const {#task}

Returns the person's task (can be QString(), if it has been constructed with an empty task)

> **Note:** Getter function for property [task](kaboutperson.md#task-prop).

### QString KAboutPerson::webAddress() const {#webAddress}

Returns the persons home page (can be QString(), if it has been constructed with an empty home page)

> **Note:** Getter function for property [webAddress](kaboutperson.md#webAddress-prop).

### KAboutPerson &KAboutPerson::operator=(const KAboutPerson &*other*) {#operator-eq}

Assignment operator. Performs a deep copy.

`other` object to copy
