---
title: "KProcessList::KProcessInfo Class"
description: "Contains information about a process."
---

# KProcessList::KProcessInfo Class

Contains information about a process. [More...](#details)

- **Header:** `#include <KProcessInfo>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`

[List of all members, including inherited members](kprocesslist-kprocessinfo-members.md)

## Public Functions

- [KProcessInfo()](#KProcessInfo)
- [KProcessInfo(qint64 pid, const QString &command, const QString &user)](#KProcessInfo-1)
- [KProcessInfo(qint64 pid, const QString &command, const QString &name, const QString &user)](#KProcessInfo-2)
- [QString command() const](#command)
- [bool isValid() const](#isValid)
- [QString name() const](#name)
- [qint64 pid() const](#pid)
- [QString user() const](#user)

## Detailed Description {#details}

This class is usually not used alone but rather returned by [processInfoList](kprocesslist.md#processInfoList) and [processInfo](kprocesslist.md#processInfo). To check if the data contained in this class is valid use the [isValid](kprocesslist-kprocessinfo.md#isValid) method.

## Member Function Documentation {#member-function-documentation}

### KProcessInfo::KProcessInfo() {#KProcessInfo}

### KProcessInfo::KProcessInfo(qint64 *pid*, const QString &*command*, const QString &*user*) {#KProcessInfo-1}

### KProcessInfo::KProcessInfo(qint64 *pid*, const QString &*command*, const QString &*name*, const QString &*user*) {#KProcessInfo-2}

### QString KProcessInfo::command() const {#command}

The command line running this process e.g /bin/ls /some/path -R

### bool KProcessInfo::isValid() const {#isValid}

If the [KProcessInfo](kprocesslist-kprocessinfo.md) contains valid information. If it returns true the pid, name and user function returns valid information, otherwise they return value is undefined.

### QString KProcessInfo::name() const {#name}

The name of the process.

The class will try to get the full path to the executable file for the process but if it is not available the name of the process will be used instead. e.g /bin/ls

### qint64 KProcessInfo::pid() const {#pid}

The pid of the process

### QString KProcessInfo::user() const {#user}

The username the process is running under.
