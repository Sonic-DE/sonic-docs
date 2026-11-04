---
title: "Sonic::InitInfo Namespace"
description: "Runtime information about the init system and seat manager."
---

# Sonic::InitInfo Namespace

Runtime information about the init system and seat manager. [More...](#details)

- **Header:** `#include <Sonic/InitInfo/InitInfo>`
- **CMake:** `find_package(SonicInitInfo REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Sonic::InitInfo)`

## Detailed Description {#details}

Detection reads PID 1's identity and that init's own configuration; it never consults runtime marker files. Nothing is cached, so callers that query repeatedly should keep the result.

In containers and sandboxes PID 1 is the sandbox helper, so [Pid1::Unknown](sonic-initinfo.md#Pid1-enum), [ServiceManager::Unknown](sonic-initinfo.md#ServiceManager-enum) and [SeatManager::None](sonic-initinfo.md#SeatManager-enum) are normal results that callers must handle.

## Classes {#classes}

### struct [InitInfo::Environment](sonic-initinfo-environment.md)

Tests point these at a fake tree.

## Type Documentation {#type-documentation}

### enum InitInfo::Pid1 {#Pid1-enum}

The program running as PID 1.

| Constant | Value | Description |
| --- | --- | --- |
| `Sonic::InitInfo::Pid1::Unknown` | `0` | Not recognized, for example a container's or sandbox's helper. |
| `Sonic::InitInfo::Pid1::Systemd` | `1` | systemd. |
| `Sonic::InitInfo::Pid1::SysVinit` | `2` | sysvinit. |
| `Sonic::InitInfo::Pid1::OpenRCInit` | `3` | openrc-init. |
| `Sonic::InitInfo::Pid1::RunitInit` | `4` | runit. |
| `Sonic::InitInfo::Pid1::S6LinuxInit` | `5` | s6-linux-init. |
| `Sonic::InitInfo::Pid1::Dinit` | `6` | dinit. |
| `Sonic::InitInfo::Pid1::Busybox` | `7` | BusyBox init. |
| `Sonic::InitInfo::Pid1::BsdInit` | `8` | A BSD init. |

### enum InitInfo::SeatManager {#SeatManager-enum}

What manages seats and sessions.

| Constant | Value | Description |
| --- | --- | --- |
| `Sonic::InitInfo::SeatManager::None` | `0` | No seat manager runs. |
| `Sonic::InitInfo::SeatManager::SystemdLogind` | `1` | systemd-logind. |
| `Sonic::InitInfo::SeatManager::Elogind` | `2` | elogind. |
| `Sonic::InitInfo::SeatManager::ConsoleKit2` | `3` | ConsoleKit2. |
| `Sonic::InitInfo::SeatManager::Seatd` | `4` | seatd. |

### enum InitInfo::ServiceManager {#ServiceManager-enum}

What manages services, which can differ from PID 1 (for example OpenRC under sysvinit).

| Constant | Value | Description |
| --- | --- | --- |
| `Sonic::InitInfo::ServiceManager::Unknown` | `0` | Not recognized. |
| `Sonic::InitInfo::ServiceManager::Systemd` | `1` | systemd. |
| `Sonic::InitInfo::ServiceManager::OpenRC` | `2` | OpenRC. |
| `Sonic::InitInfo::ServiceManager::Runit` | `3` | runit. |
| `Sonic::InitInfo::ServiceManager::S6` | `4` | s6. |
| `Sonic::InitInfo::ServiceManager::Dinit` | `5` | dinit. |
| `Sonic::InitInfo::ServiceManager::SysVinit` | `6` | sysvinit's own rc scripts. |
| `Sonic::InitInfo::ServiceManager::BsdRc` | `7` | The rc.d system of the BSDs other than OpenBSD. |
| `Sonic::InitInfo::ServiceManager::OpenBsdRc` | `8` | OpenBSD's rc. |

## Function Documentation {#function-documentation}

### int InitInfo::defaultInitialVt(Sonic::InitInfo::ServiceManager *manager*) {#defaultInitialVt}

The VT a display manager starts on under `manager`: 2 where getty usually owns VT 1 ([OpenRC](sonic-initinfo.md#ServiceManager-enum), runit, s6), else 1.

### bool InitInfo::hasJournald(const Sonic::InitInfo::Environment &*environment* = {}) {#hasJournald}

True when journald's native socket exists and is a socket. `environment` says where to look.

### QString InitInfo::name(Sonic::InitInfo::Pid1 *value*) {#name}

The name of `value` for logging and display, for example "openrc-init".

### QString InitInfo::name(Sonic::InitInfo::SeatManager *value*) {#name-1}

The name of `value` for logging and display, for example "elogind".

This is an overloaded function.

### QString InitInfo::name(Sonic::InitInfo::ServiceManager *value*) {#name-2}

The name of `value` for logging and display, for example "[OpenRC](sonic-initinfo.md#ServiceManager-enum)".

This is an overloaded function.

### Sonic::InitInfo::Pid1 InitInfo::pid1(const Sonic::InitInfo::Environment &*environment* = {}) {#pid1}

The program running as PID 1, from /proc/1/comm, or from where /sbin/init points when /proc hides it. `environment` says where to look.

### Sonic::InitInfo::SeatManager InitInfo::seatManager(const Sonic::InitInfo::Environment &*environment* = {}) {#seatManager}

The seat manager whose daemon is running; when several run, systemd-logind comes first, then elogind, [ConsoleKit2](sonic-initinfo.md#SeatManager-enum) and seatd. When built with Qt D-Bus, name ownership on the system bus is an extra signal. `environment` says where to look.

### Sonic::InitInfo::ServiceManager InitInfo::serviceManager(const Sonic::InitInfo::Environment &*environment* = {}) {#serviceManager}

What manages services, from PID 1 and that init's own configuration, such as /etc/inittab. `environment` says where to look.
