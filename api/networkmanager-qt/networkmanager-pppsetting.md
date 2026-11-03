---
title: "NetworkManager::PppSetting Class"
description: "Represents ppp setting."
---

# NetworkManager::PppSetting Class

Represents ppp setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/PppSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-pppsetting-members.md)

## Public Types

- [PppSetting::List](#List-typedef)
- [PppSetting::Ptr](#Ptr-typedef)

## Public Functions

- [PppSetting()](#PppSetting)
- [PppSetting(const NetworkManager::PppSetting::Ptr &other)](#PppSetting-1)
- [quint32 baud() const](#baud)
- [bool cRtsCts() const](#cRtsCts)
- [quint32 lcpEchoFailure() const](#lcpEchoFailure)
- [quint32 lcpEchoInterval() const](#lcpEchoInterval)
- [bool mppeStateful() const](#mppeStateful)
- [quint32 mru() const](#mru)
- [quint32 mtu() const](#mtu)
- [bool noAuth() const](#noAuth)
- [bool noBsdComp() const](#noBsdComp)
- [bool noDeflate() const](#noDeflate)
- [bool noVjComp() const](#noVjComp)
- [bool refuseChap() const](#refuseChap)
- [bool refuseEap() const](#refuseEap)
- [bool refuseMschap() const](#refuseMschap)
- [bool refuseMschapv2() const](#refuseMschapv2)
- [bool refusePap() const](#refusePap)
- [bool requireMppe128() const](#requireMppe128)
- [bool requireMppe() const](#requireMppe)
- [void setBaud(quint32 baud)](#setBaud)
- [void setCRtsCts(bool control)](#setCRtsCts)
- [void setLcpEchoFailure(quint32 number)](#setLcpEchoFailure)
- [void setLcpEchoInterval(quint32 interval)](#setLcpEchoInterval)
- [void setMppeStateful(bool used)](#setMppeStateful)
- [void setMru(quint32 mru)](#setMru)
- [void setMtu(quint32 mtu)](#setMtu)
- [void setNoAuth(bool require)](#setNoAuth)
- [void setNoBsdComp(bool require)](#setNoBsdComp)
- [void setNoDeflate(bool require)](#setNoDeflate)
- [void setNoVjComp(bool require)](#setNoVjComp)
- [void setRefuseChap(bool refuse)](#setRefuseChap)
- [void setRefuseEap(bool refuse)](#setRefuseEap)
- [void setRefuseMschap(bool refuse)](#setRefuseMschap)
- [void setRefuseMschapv2(bool refuse)](#setRefuseMschapv2)
- [void setRefusePap(bool refuse)](#setRefusePap)
- [void setRequireMppe128(bool require)](#setRequireMppe128)
- [void setRequireMppe(bool require)](#setRequireMppe)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### PppSetting::List {#List-typedef}

### PppSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### PppSetting::PppSetting() {#PppSetting}

### \[explicit\] PppSetting::PppSetting(const NetworkManager::PppSetting::Ptr &*other*) {#PppSetting-1}

### quint32 PppSetting::baud() const {#baud}

*See also* [setBaud](networkmanager-pppsetting.md#setBaud)()

### bool PppSetting::cRtsCts() const {#cRtsCts}

*See also* [setCRtsCts](networkmanager-pppsetting.md#setCRtsCts)()

### quint32 PppSetting::lcpEchoFailure() const {#lcpEchoFailure}

*See also* [setLcpEchoFailure](networkmanager-pppsetting.md#setLcpEchoFailure)()

### quint32 PppSetting::lcpEchoInterval() const {#lcpEchoInterval}

*See also* [setLcpEchoInterval](networkmanager-pppsetting.md#setLcpEchoInterval)()

### bool PppSetting::mppeStateful() const {#mppeStateful}

*See also* [setMppeStateful](networkmanager-pppsetting.md#setMppeStateful)()

### quint32 PppSetting::mru() const {#mru}

*See also* [setMru](networkmanager-pppsetting.md#setMru)()

### quint32 PppSetting::mtu() const {#mtu}

*See also* [setMtu](networkmanager-pppsetting.md#setMtu)()

### bool PppSetting::noAuth() const {#noAuth}

*See also* [setNoAuth](networkmanager-pppsetting.md#setNoAuth)()

### bool PppSetting::noBsdComp() const {#noBsdComp}

*See also* [setNoBsdComp](networkmanager-pppsetting.md#setNoBsdComp)()

### bool PppSetting::noDeflate() const {#noDeflate}

*See also* [setNoDeflate](networkmanager-pppsetting.md#setNoDeflate)()

### bool PppSetting::noVjComp() const {#noVjComp}

*See also* [setNoVjComp](networkmanager-pppsetting.md#setNoVjComp)()

### bool PppSetting::refuseChap() const {#refuseChap}

*See also* [setRefuseChap](networkmanager-pppsetting.md#setRefuseChap)()

### bool PppSetting::refuseEap() const {#refuseEap}

*See also* [setRefuseEap](networkmanager-pppsetting.md#setRefuseEap)()

### bool PppSetting::refuseMschap() const {#refuseMschap}

*See also* [setRefuseMschap](networkmanager-pppsetting.md#setRefuseMschap)()

### bool PppSetting::refuseMschapv2() const {#refuseMschapv2}

*See also* [setRefuseMschapv2](networkmanager-pppsetting.md#setRefuseMschapv2)()

### bool PppSetting::refusePap() const {#refusePap}

*See also* [setRefusePap](networkmanager-pppsetting.md#setRefusePap)()

### bool PppSetting::requireMppe128() const {#requireMppe128}

*See also* [setRequireMppe128](networkmanager-pppsetting.md#setRequireMppe128)()

### bool PppSetting::requireMppe() const {#requireMppe}

*See also* [setRequireMppe](networkmanager-pppsetting.md#setRequireMppe)()

### void PppSetting::setBaud(quint32 *baud*) {#setBaud}

*See also* [baud](networkmanager-pppsetting.md#baud)()

### void PppSetting::setCRtsCts(bool *control*) {#setCRtsCts}

*See also* [cRtsCts](networkmanager-pppsetting.md#cRtsCts)()

### void PppSetting::setLcpEchoFailure(quint32 *number*) {#setLcpEchoFailure}

*See also* [lcpEchoFailure](networkmanager-pppsetting.md#lcpEchoFailure)()

### void PppSetting::setLcpEchoInterval(quint32 *interval*) {#setLcpEchoInterval}

*See also* [lcpEchoInterval](networkmanager-pppsetting.md#lcpEchoInterval)()

### void PppSetting::setMppeStateful(bool *used*) {#setMppeStateful}

*See also* [mppeStateful](networkmanager-pppsetting.md#mppeStateful)()

### void PppSetting::setMru(quint32 *mru*) {#setMru}

*See also* [mru](networkmanager-pppsetting.md#mru)()

### void PppSetting::setMtu(quint32 *mtu*) {#setMtu}

*See also* [mtu](networkmanager-pppsetting.md#mtu)()

### void PppSetting::setNoAuth(bool *require*) {#setNoAuth}

*See also* [noAuth](networkmanager-pppsetting.md#noAuth)()

### void PppSetting::setNoBsdComp(bool *require*) {#setNoBsdComp}

*See also* [noBsdComp](networkmanager-pppsetting.md#noBsdComp)()

### void PppSetting::setNoDeflate(bool *require*) {#setNoDeflate}

*See also* [noDeflate](networkmanager-pppsetting.md#noDeflate)()

### void PppSetting::setNoVjComp(bool *require*) {#setNoVjComp}

*See also* [noVjComp](networkmanager-pppsetting.md#noVjComp)()

### void PppSetting::setRefuseChap(bool *refuse*) {#setRefuseChap}

*See also* [refuseChap](networkmanager-pppsetting.md#refuseChap)()

### void PppSetting::setRefuseEap(bool *refuse*) {#setRefuseEap}

*See also* [refuseEap](networkmanager-pppsetting.md#refuseEap)()

### void PppSetting::setRefuseMschap(bool *refuse*) {#setRefuseMschap}

*See also* [refuseMschap](networkmanager-pppsetting.md#refuseMschap)()

### void PppSetting::setRefuseMschapv2(bool *refuse*) {#setRefuseMschapv2}

*See also* [refuseMschapv2](networkmanager-pppsetting.md#refuseMschapv2)()

### void PppSetting::setRefusePap(bool *refuse*) {#setRefusePap}

*See also* [refusePap](networkmanager-pppsetting.md#refusePap)()

### void PppSetting::setRequireMppe128(bool *require*) {#setRequireMppe128}

*See also* [requireMppe128](networkmanager-pppsetting.md#requireMppe128)()

### void PppSetting::setRequireMppe(bool *require*) {#setRequireMppe}

*See also* [requireMppe](networkmanager-pppsetting.md#requireMppe)()
