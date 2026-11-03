---
title: "NetworkManager::DeviceStateReason Class"
description: "Qt wrapper for NetworkManager API."
---

# NetworkManager::DeviceStateReason Class

Qt wrapper for NetworkManager API. [More...](#details)

- **Header:** `#include <NetworkManagerQt/Device>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`

[List of all members, including inherited members](networkmanager-devicestatereason-members.md)

## Public Functions

- [DeviceStateReason(NetworkManager::Device::State state, NetworkManager::Device::StateChangeReason reason)](#DeviceStateReason-1)
- [DeviceStateReason(const NetworkManager::DeviceStateReason &)](#DeviceStateReason)
- [~DeviceStateReason()](#dtor.DeviceStateReason)
- [NetworkManager::Device::StateChangeReason reason() const](#reason)
- [NetworkManager::Device::State state() const](#state)
- [NetworkManager::DeviceStateReason &DeviceStateReason::operator=(const NetworkManager::DeviceStateReason &)](#operator-eq)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### DeviceStateReason::DeviceStateReason(NetworkManager::Device::State *state*, NetworkManager::Device::StateChangeReason *reason*) {#DeviceStateReason-1}

### DeviceStateReason::DeviceStateReason(*const NetworkManager::DeviceStateReason &*) {#DeviceStateReason}

### \[noexcept\] DeviceStateReason::~DeviceStateReason() {#dtor.DeviceStateReason}

### NetworkManager::Device::StateChangeReason DeviceStateReason::reason() const {#reason}

### NetworkManager::Device::State DeviceStateReason::state() const {#state}

### NetworkManager::DeviceStateReason &DeviceStateReason::operator=(*const NetworkManager::DeviceStateReason &*) {#operator-eq}
