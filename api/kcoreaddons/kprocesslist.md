---
title: "KProcessList Namespace"
description: "Additions to Qt Core."
---

# KProcessList Namespace

Additions to Qt Core. [More...](#details)

- Header: KProcessList
- CMake: find\_package(KF6 REQUIRED COMPONENTS CoreAddons) target\_link\_libraries(mytarget PRIVATE KF6::CoreAddons)

## Detailed Description {#details}

## Classes {#classes}

### class [KProcessInfo](kprocesslist-kprocessinfo.md)

Contains information about a process.

## Type Documentation {#type-documentation}

### KProcessList::KProcessInfoList {#KProcessInfoList-typedef}

## Function Documentation {#function-documentation}

### KProcessList::KProcessInfo KProcessList::processInfo(qint64 *pid*) {#processInfo}

Retrieves process information for a specific process-id. If the process is not found a [KProcessInfo](kprocesslist-kprocessinfo.md) with isValid == false will be returned.

`pid` The process-id to retrieve information for.

### KProcessList::KProcessInfoList KProcessList::processInfoList() {#processInfoList}

Retrieves the list of currently active processes.
