---
title: "Solid::NetworkShare Class"
description: "This device interface is available for network share volumes."
---

# Solid::NetworkShare Class

This device interface is available for network share volumes. [More...](#details)

- **Header:** `#include <Solid/NetworkShare>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Solid)`  
  `target_link_libraries(mytarget PRIVATE KF6::Solid)`
- **Inherits:** [Solid::DeviceInterface](solid-deviceinterface.md)

[List of all members, including inherited members](solid-networkshare-members.md)

## Public Types

- [enum NetworkShare::ShareType](#ShareType-enum)

## Properties

- [\[read-only\] type : ShareType](#type-prop)
- [\[read-only\] url : QUrl](#url-prop)

## Public Functions

- [Solid::NetworkShare::ShareType type() const](#type)
- [QUrl url() const](#url)

## Static Public Members

- [Solid::DeviceInterface::Type deviceInterfaceType()](#deviceInterfaceType)

## Detailed Description {#details}

Used to acquire a list of network device types.

```cpp
const auto devices = Solid::Device::listFromType(Solid::DeviceInterface::NetworkShare);
for (const auto &device : devices) {
    switch (device.as<Solid::NetworkShare>()->type()) {
    case Solid::NetworkShare::Cifs:
        hasCifsShare = true;
        continue;
    case Solid::NetworkShare::Smb3:
        hasSmb3Share = true;
        continue;
    case Solid::NetworkShare::Nfs:
        hasNfsShare = true;
        continue;
    default:
        continue;
    }
}
```

## Member Type Documentation {#member-type-documentation}

### enum NetworkShare::ShareType {#ShareType-enum}

This enum type defines the type of networkShare device can be.

| Constant | Value | Description |
| --- | --- | --- |
| `Solid::NetworkShare::Unknown` | `0` | An unsupported network protocol |
| `Solid::NetworkShare::Nfs` | `1` | NFS protocol |
| `Solid::NetworkShare::Cifs` | `2` | Samba protocol |
| `Solid::NetworkShare::Smb3` | `3` | Samba protocol (version 3) |

## Property Documentation {#property-documentation}

### \[read-only\] type : ShareType {#type-prop}

**Access functions:**

- `Solid::NetworkShare::ShareType` **[type](solid-networkshare.md#type)**() const

### \[read-only\] url : QUrl {#url-prop}

**Access functions:**

- `QUrl` **[url](solid-networkshare.md#url)**() const

## Member Function Documentation {#member-function-documentation}

### \[static\] Solid::DeviceInterface::Type NetworkShare::deviceInterfaceType() {#deviceInterfaceType}

Returns the [Solid::DeviceInterface::Type](solid-deviceinterface.md#Type-enum) of the [NetworkShare](solid-networkshare.md) device interface.

*See also* [Solid::DeviceInterface::Type](solid-index.md)

### Solid::NetworkShare::ShareType NetworkShare::type() const {#type}

Returns the type of network share.

> **Note:** Getter function for property [type](solid-networkshare.md#type-prop).

### QUrl NetworkShare::url() const {#url}

Returns the url of network share.

> **Note:** Getter function for property [url](solid-networkshare.md#url-prop).
