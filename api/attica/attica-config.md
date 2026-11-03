---
title: "Attica::Config Class"
description: "Represents a server config."
---

# Attica::Config Class

Represents a server config. [More...](#details)

- **Header:** `#include <Attica/Config>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-config-members.md)

## Public Types

- [Config::List](#List-typedef)

## Public Functions

- [Config()](#Config)
- [QString contact() const](#contact)
- [QString host() const](#host)
- [bool isValid() const](#isValid)
- [void setContact(const QString &contact)](#setContact)
- [void setHost(const QString &host)](#setHost)
- [void setSsl(bool ssl)](#setSsl)
- [void setVersion(const QString &version)](#setVersion)
- [void setWebsite(const QString &website)](#setWebsite)
- [bool ssl() const](#ssl)
- [QString version() const](#version)
- [QString website() const](#website)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### Config::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### Config::Config() {#Config}

Creates an empty Config

### QString Config::contact() const {#contact}

*See also* [setContact](attica-config.md#setContact)()

### QString Config::host() const {#host}

*See also* [setHost](attica-config.md#setHost)()

### bool Config::isValid() const {#isValid}

Returns whether this config is valid

### void Config::setContact(const QString &*contact*) {#setContact}

*See also* [contact](attica-config.md#contact)()

### void Config::setHost(const QString &*host*) {#setHost}

*See also* [host](attica-config.md#host)()

### void Config::setSsl(bool *ssl*) {#setSsl}

*See also* [ssl](attica-config.md#ssl)()

### void Config::setVersion(const QString &*version*) {#setVersion}

*See also* [version](attica-config.md#version)()

### void Config::setWebsite(const QString &*website*) {#setWebsite}

*See also* [website](attica-config.md#website)()

### bool Config::ssl() const {#ssl}

*See also* [setSsl](attica-config.md#setSsl)()

### QString Config::version() const {#version}

*See also* [setVersion](attica-config.md#setVersion)()

### QString Config::website() const {#website}

*See also* [setWebsite](attica-config.md#setWebsite)()
