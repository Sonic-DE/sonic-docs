---
title: "KAboutComponent Class"
description: "This class is used to store information about a third party component."
---

# KAboutComponent Class

This class is used to store information about a third party component. [More...](#details)

- **Header:** `#include <KAboutData>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`

[List of all members, including inherited members](kaboutcomponent-members.md)

## Properties

- [\[read-only\] description : const QString](#description-prop)
- [\[read-only\] licenses : const KAboutLicense](#licenses-prop)
- [\[read-only\] name : const QString](#name-prop)
- [\[read-only\] version : const QString](#version-prop)
- [\[read-only\] webAddress : const QString](#webAddress-prop)

## Public Functions

- [KAboutComponent(const QString &name, const QString &description, const QString &version, const QString &webAddress, const QString &pathToLicenseFile)](#KAboutComponent-1)
- [KAboutComponent(const QString &name = QString(), const QString &description = QString(), const QString &version = QString(), const QString &webAddress = QString(), enum KAboutLicense::LicenseKey licenseType = KAboutLicense::Unknown)](#KAboutComponent-2)
- [KAboutComponent(const KAboutComponent &other)](#KAboutComponent)
- [QString description() const](#description)
- [KAboutLicense license() const](#license)
- [QString name() const](#name)
- [QString version() const](#version)
- [QString webAddress() const](#webAddress)
- [KAboutComponent &KAboutComponent::operator=(const KAboutComponent &other)](#operator-eq)

## Detailed Description {#details}

It can store the component's name, a description, a link to a website and the license of the libary. This class is intended for use in the [KAboutData](kaboutdata.md) class, but it can be used elsewhere as well. Normally you should at least define the libary's name. Creating a [KAboutComponent](kaboutcomponent.md) object by yourself is relatively useless, but the [KAboutData](kaboutdata.md) method KAboutData::libaries() return lists of [KAboutComponent](kaboutcomponent.md) data objects which you can examine.

Example usage within a main(), retrieving the list of components used by a program and re-using data from one of them:

```cpp
KAboutData about("khello", i18n("KHello"), "0.1",
                  i18n("A KDE version of Hello, world!"),
                  KAboutLicense::LGPL,
                  i18n("Copyright (C) 2014 Developer"));

about.addComponent(i18n("Awsom Lib"),
                 i18n("Does awesom stuff. Copyright (C) 2014"),
                 i18n("1.02.3"),
                 "http://example.com",
                 KAboutLicense::LGPL);
QList<KAboutComponent> components = about.components();
```

## Property Documentation {#property-documentation}

### \[read-only\] description : const QString {#description-prop}

**Access functions:**

- `QString` **[description](kaboutcomponent.md#description)**() const

### \[read-only\] licenses : const KAboutLicense {#licenses-prop}

**Access functions:**

- `KAboutLicense` **[license](kaboutcomponent.md#license)**() const

### \[read-only\] name : const QString {#name-prop}

**Access functions:**

- `QString` **[name](kaboutcomponent.md#name)**() const

### \[read-only\] version : const QString {#version-prop}

**Access functions:**

- `QString` **[version](kaboutcomponent.md#version)**() const

### \[read-only\] webAddress : const QString {#webAddress-prop}

**Access functions:**

- `QString` **[webAddress](kaboutcomponent.md#webAddress)**() const

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KAboutComponent::KAboutComponent(const QString &*name*, const QString &*description*, const QString &*version*, const QString &*webAddress*, const QString &*pathToLicenseFile*) {#KAboutComponent-1}

Convenience constructor

`name` The name of the component.

`description` The description of this component.

`version` The version of this component.

`webAddress` Website of the component.

`pathToLicenseFile` Path to the file in the local filesystem containing the license text. The file format has to be plain text in an encoding compatible to the local.

### \[explicit\] KAboutComponent::KAboutComponent(const QString &*name* = QString(), const QString &*description* = QString(), const QString &*version* = QString(), const QString &*webAddress* = QString(), enum KAboutLicense::LicenseKey *licenseType* = KAboutLicense::Unknown) {#KAboutComponent-2}

Convenience constructor

`name` The name of the component.

`description` The description of this component.

`version` The version of this component.

`webAddress` Website of the component.

`licenseType` The license identifier of the component.

### KAboutComponent::KAboutComponent(const KAboutComponent &*other*) {#KAboutComponent}

Copy constructor. Performs a deep copy.

`other` object to copy

### QString KAboutComponent::description() const {#description}

Returns the component's description (can be empty)

> **Note:** Getter function for property [description](kaboutcomponent.md#description-prop).

### KAboutLicense KAboutComponent::license() const {#license}

Returns the component's [KAboutLicense](kaboutlicense.md)

> **Note:** Getter function for property [licenses](kaboutcomponent.md#licenses-prop).

### QString KAboutComponent::name() const {#name}

Returns the component's name (can be QString(), if it has been constructed with an empty name)

> **Note:** Getter function for property [name](kaboutcomponent.md#name-prop).

### QString KAboutComponent::version() const {#version}

Returns the component's task (can be empty)

> **Note:** Getter function for property [version](kaboutcomponent.md#version-prop).

### QString KAboutComponent::webAddress() const {#webAddress}

Returns the component's website (can be empty)

> **Note:** Getter function for property [webAddress](kaboutcomponent.md#webAddress-prop).

### KAboutComponent &KAboutComponent::operator=(const KAboutComponent &*other*) {#operator-eq}

Assignment operator. Performs a deep copy.

`other` object to copy
