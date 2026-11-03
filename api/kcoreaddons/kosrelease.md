---
title: "KOSRelease Class"
description: "The OSRelease class parses /etc/os-release files."
---

# KOSRelease Class

The OSRelease class parses /etc/os-release files. [More...](#details)

- **Header:** `#include <KOSRelease>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`

[List of all members, including inherited members](kosrelease-members.md)

## Public Functions

- [KOSRelease(const QString &filePath = QString())](#KOSRelease)
- [QString ansiColor() const](#ansiColor)
- [QString bugReportUrl() const](#bugReportUrl)
- [QString buildId() const](#buildId)
- [QString cpeName() const](#cpeName)
- [QString documentationUrl() const](#documentationUrl)
- [QStringList extraKeys() const](#extraKeys)
- [QString extraValue(const QString &key) const](#extraValue)
- [QString homeUrl() const](#homeUrl)
- [QString id() const](#id)
- [QStringList idLike() const](#idLike)
- [QString logo() const](#logo)
- [QString name() const](#name)
- [QString prettyName() const](#prettyName)
- [QString privacyPolicyUrl() const](#privacyPolicyUrl)
- [QString supportUrl() const](#supportUrl)
- [QString variant() const](#variant)
- [QString variantId() const](#variantId)
- [QString version() const](#version)
- [QString versionCodename() const](#versionCodename)
- [QString versionId() const](#versionId)

## Detailed Description {#details}

https://www.freedesktop.org/software/systemd/man/os-release.html

os-release is a free desktop standard for describing an operating system. This class parses and models os-release files.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KOSRelease::KOSRelease(const QString &*filePath* = QString()) {#KOSRelease}

Constructs a new OSRelease instance. Parsing happens in the constructor and the data is not cached across instances.

> **Note:** The format specification makes no assertions about trailing \# comments being supported. They result in undefined behavior.

`filePath` The path to the os-release file. By default the first available file of the paths specified in the os-release manpage is parsed.

### QString KOSRelease::ansiColor() const {#ansiColor}

See [https://www.freedesktop.org/software/systemd/man/os-release.html#ANSI_COLOR=](https://www.freedesktop.org/software/systemd/man/os-release.html#ANSI_COLOR=)

### QString KOSRelease::bugReportUrl() const {#bugReportUrl}

See [https://www.freedesktop.org/software/systemd/man/os-release.html#HOME_URL=](https://www.freedesktop.org/software/systemd/man/os-release.html#HOME_URL=)

### QString KOSRelease::buildId() const {#buildId}

See [https://www.freedesktop.org/software/systemd/man/os-release.html#BUILD_ID=](https://www.freedesktop.org/software/systemd/man/os-release.html#BUILD_ID=)

### QString KOSRelease::cpeName() const {#cpeName}

See [https://www.freedesktop.org/software/systemd/man/os-release.html#CPE_NAME=](https://www.freedesktop.org/software/systemd/man/os-release.html#CPE_NAME=)

### QString KOSRelease::documentationUrl() const {#documentationUrl}

See [https://www.freedesktop.org/software/systemd/man/os-release.html#HOME_URL=](https://www.freedesktop.org/software/systemd/man/os-release.html#HOME_URL=)

### QStringList KOSRelease::extraKeys() const {#extraKeys}

Extra keys are keys that are unknown or specified by a vendor.

### QString KOSRelease::extraValue(const QString &*key*) const {#extraValue}

Extra values are values associated with keys that are unknown.

### QString KOSRelease::homeUrl() const {#homeUrl}

See [https://www.freedesktop.org/software/systemd/man/os-release.html#HOME_URL=](https://www.freedesktop.org/software/systemd/man/os-release.html#HOME_URL=)

### QString KOSRelease::id() const {#id}

See [https://www.freedesktop.org/software/systemd/man/os-release.html#ID=](https://www.freedesktop.org/software/systemd/man/os-release.html#ID=)

### QStringList KOSRelease::idLike() const {#idLike}

See [https://www.freedesktop.org/software/systemd/man/os-release.html#ID_LIKE=](https://www.freedesktop.org/software/systemd/man/os-release.html#ID_LIKE=)

### QString KOSRelease::logo() const {#logo}

See [https://www.freedesktop.org/software/systemd/man/os-release.html#LOGO=](https://www.freedesktop.org/software/systemd/man/os-release.html#LOGO=)

### QString KOSRelease::name() const {#name}

See [https://www.freedesktop.org/software/systemd/man/os-release.html#NAME=](https://www.freedesktop.org/software/systemd/man/os-release.html#NAME=)

### QString KOSRelease::prettyName() const {#prettyName}

See [https://www.freedesktop.org/software/systemd/man/os-release.html#PRETTY_NAME=](https://www.freedesktop.org/software/systemd/man/os-release.html#PRETTY_NAME=)

### QString KOSRelease::privacyPolicyUrl() const {#privacyPolicyUrl}

See [https://www.freedesktop.org/software/systemd/man/os-release.html#HOME_URL=](https://www.freedesktop.org/software/systemd/man/os-release.html#HOME_URL=)

### QString KOSRelease::supportUrl() const {#supportUrl}

See [https://www.freedesktop.org/software/systemd/man/os-release.html#HOME_URL=](https://www.freedesktop.org/software/systemd/man/os-release.html#HOME_URL=)

### QString KOSRelease::variant() const {#variant}

See [https://www.freedesktop.org/software/systemd/man/os-release.html#VARIANT=](https://www.freedesktop.org/software/systemd/man/os-release.html#VARIANT=)

### QString KOSRelease::variantId() const {#variantId}

See [https://www.freedesktop.org/software/systemd/man/os-release.html#VARIANT_ID=](https://www.freedesktop.org/software/systemd/man/os-release.html#VARIANT_ID=)

### QString KOSRelease::version() const {#version}

See [https://www.freedesktop.org/software/systemd/man/os-release.html#VERSION=](https://www.freedesktop.org/software/systemd/man/os-release.html#VERSION=)

### QString KOSRelease::versionCodename() const {#versionCodename}

See [https://www.freedesktop.org/software/systemd/man/os-release.html#VERSION_CODENAME=](https://www.freedesktop.org/software/systemd/man/os-release.html#VERSION_CODENAME=)

### QString KOSRelease::versionId() const {#versionId}

See [https://www.freedesktop.org/software/systemd/man/os-release.html#VERSION_ID=](https://www.freedesktop.org/software/systemd/man/os-release.html#VERSION_ID=)
