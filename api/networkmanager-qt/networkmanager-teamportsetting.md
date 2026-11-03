---
title: "NetworkManager::TeamPortSetting Class"
description: "Represents TeamPort setting."
---

# NetworkManager::TeamPortSetting Class

Represents TeamPort setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/TeamPortSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-teamportsetting-members.md)

## Public Types

- [TeamPortSetting::List](#List-typedef)
- [TeamPortSetting::Ptr](#Ptr-typedef)

## Public Functions

- [TeamPortSetting()](#TeamPortSetting)
- [TeamPortSetting(const NetworkManager::TeamPortSetting::Ptr &other)](#TeamPortSetting-1)
- [QString config() const](#config)
- [void config(const QString &config)](#config-1)
- [qint32 lacpKey() const](#lacpKey)
- [void lacpKey(qint32 key)](#lacpKey-1)
- [qint32 lacpPrio() const](#lacpPrio)
- [void lacpPrio(qint32 priority)](#lacpPrio-1)
- [NMVariantMapList linkWatchers() const](#linkWatchers)
- [qint32 prio() const](#prio)
- [void prio(qint32 prio)](#prio-1)
- [qint32 queueId() const](#queueId)
- [void queueId(qint32 id)](#queueId-1)
- [void setLinkWatchers(const NMVariantMapList &linkWatchers)](#setLinkWatchers)
- [bool sticky() const](#sticky)
- [void sticky(bool sticky)](#sticky-1)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### TeamPortSetting::List {#List-typedef}

### TeamPortSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### TeamPortSetting::TeamPortSetting() {#TeamPortSetting}

### \[explicit\] TeamPortSetting::TeamPortSetting(const NetworkManager::TeamPortSetting::Ptr &*other*) {#TeamPortSetting-1}

### QString TeamPortSetting::config() const {#config}

### void TeamPortSetting::config(const QString &*config*) {#config-1}

### qint32 TeamPortSetting::lacpKey() const {#lacpKey}

### void TeamPortSetting::lacpKey(qint32 *key*) {#lacpKey-1}

### qint32 TeamPortSetting::lacpPrio() const {#lacpPrio}

### void TeamPortSetting::lacpPrio(qint32 *priority*) {#lacpPrio-1}

### NMVariantMapList TeamPortSetting::linkWatchers() const {#linkWatchers}

*See also* [setLinkWatchers](networkmanager-teamportsetting.md#setLinkWatchers)()

### qint32 TeamPortSetting::prio() const {#prio}

### void TeamPortSetting::prio(qint32 *prio*) {#prio-1}

### qint32 TeamPortSetting::queueId() const {#queueId}

### void TeamPortSetting::queueId(qint32 *id*) {#queueId-1}

### void TeamPortSetting::setLinkWatchers(const NMVariantMapList &*linkWatchers*) {#setLinkWatchers}

*See also* [linkWatchers](networkmanager-teamportsetting.md#linkWatchers)()

### bool TeamPortSetting::sticky() const {#sticky}

### void TeamPortSetting::sticky(bool *sticky*) {#sticky-1}
