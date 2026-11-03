---
title: "NetworkManager::DcbSetting Class"
description: "Represents Dcb setting."
---

# NetworkManager::DcbSetting Class

Represents Dcb setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/DcbSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-dcbsetting-members.md)

## Public Types

- [enum DcbSetting::DcbFlagType](#DcbFlagType-enum)
- [DcbSetting::List](#List-typedef)
- [DcbSetting::Ptr](#Ptr-typedef)

## Public Functions

- [DcbSetting()](#DcbSetting)
- [DcbSetting(const NetworkManager::DcbSetting::Ptr &other)](#DcbSetting-1)
- [NetworkManager::DcbSetting::DcbFlags appFcoeFlags() const](#appFcoeFlags)
- [QString appFcoeMode() const](#appFcoeMode)
- [qint32 appFcoePriority() const](#appFcoePriority)
- [NetworkManager::DcbSetting::DcbFlags appFipFlags() const](#appFipFlags)
- [qint32 appFipPriority() const](#appFipPriority)
- [NetworkManager::DcbSetting::DcbFlags appIscsiFlags() const](#appIscsiFlags)
- [qint32 appIscsiPriority() const](#appIscsiPriority)
- [UIntList priorityBandwidth() const](#priorityBandwidth)
- [quint32 priorityBandwidth(quint32 userPriority) const](#priorityBandwidth-1)
- [UIntList priorityFlowControl() const](#priorityFlowControl)
- [bool priorityFlowControl(quint32 userPriority) const](#priorityFlowControl-1)
- [NetworkManager::DcbSetting::DcbFlags priorityFlowControlFlags() const](#priorityFlowControlFlags)
- [UIntList priorityGroupBandwidth() const](#priorityGroupBandwidth)
- [quint32 priorityGroupBandwidth(quint32 groupId) const](#priorityGroupBandwidth-1)
- [NetworkManager::DcbSetting::DcbFlags priorityGroupFlags() const](#priorityGroupFlags)
- [UIntList priorityGroupId() const](#priorityGroupId)
- [quint32 priorityGroupId(quint32 userPriority) const](#priorityGroupId-1)
- [UIntList priorityStrictBandwidth() const](#priorityStrictBandwidth)
- [bool priorityStrictBandwidth(quint32 userPriority) const](#priorityStrictBandwidth-1)
- [UIntList priorityTrafficClass() const](#priorityTrafficClass)
- [quint32 priorityTrafficClass(quint32 userPriority) const](#priorityTrafficClass-1)
- [void setAppFcoeFlags(NetworkManager::DcbSetting::DcbFlags flags)](#setAppFcoeFlags)
- [void setAppFcoeMode(const QString &mode)](#setAppFcoeMode)
- [void setAppFcoePriority(qint32 priority)](#setAppFcoePriority)
- [void setAppFipFlags(NetworkManager::DcbSetting::DcbFlags flags)](#setAppFipFlags)
- [void setAppFipPriority(qint32 priority)](#setAppFipPriority)
- [void setAppIscsiFlags(NetworkManager::DcbSetting::DcbFlags flags)](#setAppIscsiFlags)
- [void setAppIscsiPriority(qint32 priority)](#setAppIscsiPriority)
- [void setPriorityBandwidth(const UIntList &list)](#setPriorityBandwidth)
- [void setPriorityBandwidth(quint32 userPriority, quint32 bandwidthPercent)](#setPriorityBandwidth-1)
- [void setPriorityFlowControl(const UIntList &list)](#setPriorityFlowControl)
- [void setPriorityFlowControl(quint32 userPriority, bool enabled)](#setPriorityFlowControl-1)
- [void setPriorityFlowControlFlags(NetworkManager::DcbSetting::DcbFlags flags)](#setPriorityFlowControlFlags)
- [void setPriorityGroupBandwidth(const UIntList &list)](#setPriorityGroupBandwidth)
- [void setPriorityGroupBandwidth(quint32 groupId, quint32 bandwidthPercent)](#setPriorityGroupBandwidth-1)
- [void setPriorityGroupFlags(NetworkManager::DcbSetting::DcbFlags flags)](#setPriorityGroupFlags)
- [void setPriorityGroupId(const UIntList &list)](#setPriorityGroupId)
- [void setPriorityGroupId(quint32 userPriority, quint32 groupId)](#setPriorityGroupId-1)
- [void setPriorityStrictBandwidth(const UIntList &list)](#setPriorityStrictBandwidth)
- [void setPriorityStrictBandwidth(quint32 userPriority, bool strict)](#setPriorityStrictBandwidth-1)
- [void setPriorityTrafficClass(const UIntList &list)](#setPriorityTrafficClass)
- [void setPriorityTrafficClass(quint32 userPriority, quint32 trafficClass)](#setPriorityTrafficClass-1)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum DcbSetting::DcbFlagType {#DcbFlagType-enum}

**flags DcbSetting::DcbFlags**

| Constant |   |
| --- | --- |
| `NetworkManager::DcbSetting::None` | `0` |
| `NetworkManager::DcbSetting::Enable` | `0x01` |
| `NetworkManager::DcbSetting::Advertise` | `0x02` |
| `NetworkManager::DcbSetting::Willing` | `0x04` |

The `DcbFlags` type is a typedef for `QFlags<DcbFlagType>. `It stores an OR combination of `DcbFlagType` values.

### DcbSetting::List {#List-typedef}

### DcbSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### DcbSetting::DcbSetting() {#DcbSetting}

### \[explicit\] DcbSetting::DcbSetting(const NetworkManager::DcbSetting::Ptr &*other*) {#DcbSetting-1}

### NetworkManager::DcbSetting::DcbFlags DcbSetting::appFcoeFlags() const {#appFcoeFlags}

*See also* [setAppFcoeFlags](networkmanager-dcbsetting.md#setAppFcoeFlags)()

### QString DcbSetting::appFcoeMode() const {#appFcoeMode}

*See also* [setAppFcoeMode](networkmanager-dcbsetting.md#setAppFcoeMode)()

### qint32 DcbSetting::appFcoePriority() const {#appFcoePriority}

*See also* [setAppFcoePriority](networkmanager-dcbsetting.md#setAppFcoePriority)()

### NetworkManager::DcbSetting::DcbFlags DcbSetting::appFipFlags() const {#appFipFlags}

*See also* [setAppFipFlags](networkmanager-dcbsetting.md#setAppFipFlags)()

### qint32 DcbSetting::appFipPriority() const {#appFipPriority}

*See also* [setAppFipPriority](networkmanager-dcbsetting.md#setAppFipPriority)()

### NetworkManager::DcbSetting::DcbFlags DcbSetting::appIscsiFlags() const {#appIscsiFlags}

*See also* [setAppIscsiFlags](networkmanager-dcbsetting.md#setAppIscsiFlags)()

### qint32 DcbSetting::appIscsiPriority() const {#appIscsiPriority}

*See also* [setAppIscsiPriority](networkmanager-dcbsetting.md#setAppIscsiPriority)()

### UIntList DcbSetting::priorityBandwidth() const {#priorityBandwidth}

*See also* [setPriorityBandwidth](networkmanager-dcbsetting.md#setPriorityBandwidth)()

### quint32 DcbSetting::priorityBandwidth(quint32 *userPriority*) const {#priorityBandwidth-1}

### UIntList DcbSetting::priorityFlowControl() const {#priorityFlowControl}

*See also* [setPriorityFlowControl](networkmanager-dcbsetting.md#setPriorityFlowControl)()

### bool DcbSetting::priorityFlowControl(quint32 *userPriority*) const {#priorityFlowControl-1}

### NetworkManager::DcbSetting::DcbFlags DcbSetting::priorityFlowControlFlags() const {#priorityFlowControlFlags}

*See also* [setPriorityFlowControlFlags](networkmanager-dcbsetting.md#setPriorityFlowControlFlags)()

### UIntList DcbSetting::priorityGroupBandwidth() const {#priorityGroupBandwidth}

*See also* [setPriorityGroupBandwidth](networkmanager-dcbsetting.md#setPriorityGroupBandwidth)()

### quint32 DcbSetting::priorityGroupBandwidth(quint32 *groupId*) const {#priorityGroupBandwidth-1}

### NetworkManager::DcbSetting::DcbFlags DcbSetting::priorityGroupFlags() const {#priorityGroupFlags}

*See also* [setPriorityGroupFlags](networkmanager-dcbsetting.md#setPriorityGroupFlags)()

### UIntList DcbSetting::priorityGroupId() const {#priorityGroupId}

*See also* [setPriorityGroupId](networkmanager-dcbsetting.md#setPriorityGroupId)()

### quint32 DcbSetting::priorityGroupId(quint32 *userPriority*) const {#priorityGroupId-1}

### UIntList DcbSetting::priorityStrictBandwidth() const {#priorityStrictBandwidth}

*See also* [setPriorityStrictBandwidth](networkmanager-dcbsetting.md#setPriorityStrictBandwidth)()

### bool DcbSetting::priorityStrictBandwidth(quint32 *userPriority*) const {#priorityStrictBandwidth-1}

### UIntList DcbSetting::priorityTrafficClass() const {#priorityTrafficClass}

*See also* [setPriorityTrafficClass](networkmanager-dcbsetting.md#setPriorityTrafficClass)()

### quint32 DcbSetting::priorityTrafficClass(quint32 *userPriority*) const {#priorityTrafficClass-1}

### void DcbSetting::setAppFcoeFlags(NetworkManager::DcbSetting::DcbFlags *flags*) {#setAppFcoeFlags}

*See also* [appFcoeFlags](networkmanager-dcbsetting.md#appFcoeFlags)()

### void DcbSetting::setAppFcoeMode(const QString &*mode*) {#setAppFcoeMode}

*See also* [appFcoeMode](networkmanager-dcbsetting.md#appFcoeMode)()

### void DcbSetting::setAppFcoePriority(qint32 *priority*) {#setAppFcoePriority}

*See also* [appFcoePriority](networkmanager-dcbsetting.md#appFcoePriority)()

### void DcbSetting::setAppFipFlags(NetworkManager::DcbSetting::DcbFlags *flags*) {#setAppFipFlags}

*See also* [appFipFlags](networkmanager-dcbsetting.md#appFipFlags)()

### void DcbSetting::setAppFipPriority(qint32 *priority*) {#setAppFipPriority}

*See also* [appFipPriority](networkmanager-dcbsetting.md#appFipPriority)()

### void DcbSetting::setAppIscsiFlags(NetworkManager::DcbSetting::DcbFlags *flags*) {#setAppIscsiFlags}

*See also* [appIscsiFlags](networkmanager-dcbsetting.md#appIscsiFlags)()

### void DcbSetting::setAppIscsiPriority(qint32 *priority*) {#setAppIscsiPriority}

*See also* [appIscsiPriority](networkmanager-dcbsetting.md#appIscsiPriority)()

### void DcbSetting::setPriorityBandwidth(const UIntList &*list*) {#setPriorityBandwidth}

*See also* [priorityBandwidth](networkmanager-dcbsetting.md#priorityBandwidth)()

### void DcbSetting::setPriorityBandwidth(quint32 *userPriority*, quint32 *bandwidthPercent*) {#setPriorityBandwidth-1}

### void DcbSetting::setPriorityFlowControl(const UIntList &*list*) {#setPriorityFlowControl}

*See also* [priorityFlowControl](networkmanager-dcbsetting.md#priorityFlowControl)()

### void DcbSetting::setPriorityFlowControl(quint32 *userPriority*, bool *enabled*) {#setPriorityFlowControl-1}

### void DcbSetting::setPriorityFlowControlFlags(NetworkManager::DcbSetting::DcbFlags *flags*) {#setPriorityFlowControlFlags}

*See also* [priorityFlowControlFlags](networkmanager-dcbsetting.md#priorityFlowControlFlags)()

### void DcbSetting::setPriorityGroupBandwidth(const UIntList &*list*) {#setPriorityGroupBandwidth}

*See also* [priorityGroupBandwidth](networkmanager-dcbsetting.md#priorityGroupBandwidth)()

### void DcbSetting::setPriorityGroupBandwidth(quint32 *groupId*, quint32 *bandwidthPercent*) {#setPriorityGroupBandwidth-1}

### void DcbSetting::setPriorityGroupFlags(NetworkManager::DcbSetting::DcbFlags *flags*) {#setPriorityGroupFlags}

*See also* [priorityGroupFlags](networkmanager-dcbsetting.md#priorityGroupFlags)()

### void DcbSetting::setPriorityGroupId(const UIntList &*list*) {#setPriorityGroupId}

*See also* [priorityGroupId](networkmanager-dcbsetting.md#priorityGroupId)()

### void DcbSetting::setPriorityGroupId(quint32 *userPriority*, quint32 *groupId*) {#setPriorityGroupId-1}

### void DcbSetting::setPriorityStrictBandwidth(const UIntList &*list*) {#setPriorityStrictBandwidth}

*See also* [priorityStrictBandwidth](networkmanager-dcbsetting.md#priorityStrictBandwidth)()

### void DcbSetting::setPriorityStrictBandwidth(quint32 *userPriority*, bool *strict*) {#setPriorityStrictBandwidth-1}

### void DcbSetting::setPriorityTrafficClass(const UIntList &*list*) {#setPriorityTrafficClass}

*See also* [priorityTrafficClass](networkmanager-dcbsetting.md#priorityTrafficClass)()

### void DcbSetting::setPriorityTrafficClass(quint32 *userPriority*, quint32 *trafficClass*) {#setPriorityTrafficClass-1}
