---
title: "NetworkManager::VxlanSetting Class"
description: "Represents vxlan setting."
---

# NetworkManager::VxlanSetting Class

Represents vxlan setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/VxlanSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-vxlansetting-members.md)

## Public Types

- [VxlanSetting::List](#List-typedef)
- [VxlanSetting::Ptr](#Ptr-typedef)

## Public Functions

- [VxlanSetting()](#VxlanSetting)
- [VxlanSetting(const NetworkManager::VxlanSetting::Ptr &other)](#VxlanSetting-1)
- [quint32 ageing() const](#ageing)
- [quint32 destinationPort() const](#destinationPort)
- [quint32 id() const](#id)
- [bool l2Miss() const](#l2Miss)
- [bool l3Miss() const](#l3Miss)
- [bool learning() const](#learning)
- [quint32 limit() const](#limit)
- [QString local() const](#local)
- [QString parent() const](#parent)
- [bool proxy() const](#proxy)
- [QString remote() const](#remote)
- [bool rsc() const](#rsc)
- [void setAgeing(quint32 ageing)](#setAgeing)
- [void setDestinationPort(quint32 port)](#setDestinationPort)
- [void setId(quint32 id)](#setId)
- [void setL2Miss(bool enable)](#setL2Miss)
- [void setL3Miss(bool enable)](#setL3Miss)
- [void setLearning(bool enable)](#setLearning)
- [void setLimit(quint32 limit)](#setLimit)
- [void setLocal(QString local)](#setLocal)
- [void setParent(QString parent)](#setParent)
- [void setProxy(bool enable)](#setProxy)
- [void setRemote(QString remote)](#setRemote)
- [void setRsc(bool enable)](#setRsc)
- [void setSourcePortMax(quint32 maxPort)](#setSourcePortMax)
- [void setSourcePortMin(quint32 minPort)](#setSourcePortMin)
- [void setTos(quint32 tos)](#setTos)
- [void setTtl(quint32 ttl)](#setTtl)
- [quint32 sourcePortMax() const](#sourcePortMax)
- [quint32 sourcePortMin() const](#sourcePortMin)
- [quint32 tos() const](#tos)
- [quint32 ttl() const](#ttl)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### VxlanSetting::List {#List-typedef}

### VxlanSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### VxlanSetting::VxlanSetting() {#VxlanSetting}

### \[explicit\] VxlanSetting::VxlanSetting(const NetworkManager::VxlanSetting::Ptr &*other*) {#VxlanSetting-1}

### quint32 VxlanSetting::ageing() const {#ageing}

*See also* [setAgeing](networkmanager-vxlansetting.md#setAgeing)()

### quint32 VxlanSetting::destinationPort() const {#destinationPort}

*See also* [setDestinationPort](networkmanager-vxlansetting.md#setDestinationPort)()

### quint32 VxlanSetting::id() const {#id}

*See also* [setId](networkmanager-vxlansetting.md#setId)()

### bool VxlanSetting::l2Miss() const {#l2Miss}

*See also* [setL2Miss](networkmanager-vxlansetting.md#setL2Miss)()

### bool VxlanSetting::l3Miss() const {#l3Miss}

*See also* [setL3Miss](networkmanager-vxlansetting.md#setL3Miss)()

### bool VxlanSetting::learning() const {#learning}

*See also* [setLearning](networkmanager-vxlansetting.md#setLearning)()

### quint32 VxlanSetting::limit() const {#limit}

*See also* [setLimit](networkmanager-vxlansetting.md#setLimit)()

### QString VxlanSetting::local() const {#local}

*See also* [setLocal](networkmanager-vxlansetting.md#setLocal)()

### QString VxlanSetting::parent() const {#parent}

*See also* [setParent](networkmanager-vxlansetting.md#setParent)()

### bool VxlanSetting::proxy() const {#proxy}

*See also* [setProxy](networkmanager-vxlansetting.md#setProxy)()

### QString VxlanSetting::remote() const {#remote}

*See also* [setRemote](networkmanager-vxlansetting.md#setRemote)()

### bool VxlanSetting::rsc() const {#rsc}

*See also* [setRsc](networkmanager-vxlansetting.md#setRsc)()

### void VxlanSetting::setAgeing(quint32 *ageing*) {#setAgeing}

*See also* [ageing](networkmanager-vxlansetting.md#ageing)()

### void VxlanSetting::setDestinationPort(quint32 *port*) {#setDestinationPort}

*See also* [destinationPort](networkmanager-vxlansetting.md#destinationPort)()

### void VxlanSetting::setId(quint32 *id*) {#setId}

*See also* [id](networkmanager-vxlansetting.md#id)()

### void VxlanSetting::setL2Miss(bool *enable*) {#setL2Miss}

*See also* [l2Miss](networkmanager-vxlansetting.md#l2Miss)()

### void VxlanSetting::setL3Miss(bool *enable*) {#setL3Miss}

*See also* [l3Miss](networkmanager-vxlansetting.md#l3Miss)()

### void VxlanSetting::setLearning(bool *enable*) {#setLearning}

*See also* [learning](networkmanager-vxlansetting.md#learning)()

### void VxlanSetting::setLimit(quint32 *limit*) {#setLimit}

*See also* [limit](networkmanager-vxlansetting.md#limit)()

### void VxlanSetting::setLocal(QString *local*) {#setLocal}

*See also* [local](networkmanager-vxlansetting.md#local)()

### void VxlanSetting::setParent(QString *parent*) {#setParent}

*See also* [parent](networkmanager-vxlansetting.md#parent)()

### void VxlanSetting::setProxy(bool *enable*) {#setProxy}

*See also* [proxy](networkmanager-vxlansetting.md#proxy)()

### void VxlanSetting::setRemote(QString *remote*) {#setRemote}

*See also* [remote](networkmanager-vxlansetting.md#remote)()

### void VxlanSetting::setRsc(bool *enable*) {#setRsc}

*See also* [rsc](networkmanager-vxlansetting.md#rsc)()

### void VxlanSetting::setSourcePortMax(quint32 *maxPort*) {#setSourcePortMax}

*See also* [sourcePortMax](networkmanager-vxlansetting.md#sourcePortMax)()

### void VxlanSetting::setSourcePortMin(quint32 *minPort*) {#setSourcePortMin}

*See also* [sourcePortMin](networkmanager-vxlansetting.md#sourcePortMin)()

### void VxlanSetting::setTos(quint32 *tos*) {#setTos}

*See also* [tos](networkmanager-vxlansetting.md#tos)()

### void VxlanSetting::setTtl(quint32 *ttl*) {#setTtl}

*See also* [ttl](networkmanager-vxlansetting.md#ttl)()

### quint32 VxlanSetting::sourcePortMax() const {#sourcePortMax}

*See also* [setSourcePortMax](networkmanager-vxlansetting.md#setSourcePortMax)()

### quint32 VxlanSetting::sourcePortMin() const {#sourcePortMin}

*See also* [setSourcePortMin](networkmanager-vxlansetting.md#setSourcePortMin)()

### quint32 VxlanSetting::tos() const {#tos}

*See also* [setTos](networkmanager-vxlansetting.md#setTos)()

### quint32 VxlanSetting::ttl() const {#ttl}

*See also* [setTtl](networkmanager-vxlansetting.md#setTtl)()
