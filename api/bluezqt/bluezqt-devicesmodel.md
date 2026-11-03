---
title: "BluezQt::DevicesModel Class"
description: "Model of all devices."
---

# BluezQt::DevicesModel Class

Model of all devices. [More...](#details)

- **Header:** `#include <BluezQt/DevicesModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QAbstractListModel](https://doc.qt.io/qt-6/qabstractlistmodel.html)

[List of all members, including inherited members](bluezqt-devicesmodel-members.md)

## Public Types

- [enum DevicesModel::DeviceRoles](#DeviceRoles-enum)

## Public Functions

- [DevicesModel(BluezQt::Manager \*manager, QObject \*parent = nullptr)](#DevicesModel)
- [BluezQt::DevicePtr device(const QModelIndex &index) const](#device)

## Detailed Description {#details}

This class represents a model of all devices.

Example use in QML code:

```cpp
import org.kde.bluezqt 1.0 as BluezQt

ListView {
    model: BluezQt.DevicesModel { }
    delegate: Text {
        text: "%1 (%2)".arg(Name).arg(Address)
    }
}
```

## Member Type Documentation {#member-type-documentation}

### enum DevicesModel::DeviceRoles {#DeviceRoles-enum}

Device data roles.

| Constant | Value | Description |
| --- | --- | --- |
| `BluezQt::DevicesModel::UbiRole` | `Qt::UserRole + 100` | UBI of the device ([QString](https://doc.qt.io/qt-6/qstring.html)). |
| `BluezQt::DevicesModel::AddressRole` | `Qt::UserRole + 101` | Address of the device ([QString](https://doc.qt.io/qt-6/qstring.html)). |
| `BluezQt::DevicesModel::NameRole` | `Qt::UserRole + 102` | Name of the device ([QString](https://doc.qt.io/qt-6/qstring.html)). |
| `BluezQt::DevicesModel::FriendlyNameRole` | `Qt::UserRole + 103` | Friendly name of the device ([QString](https://doc.qt.io/qt-6/qstring.html)). |
| `BluezQt::DevicesModel::RemoteNameRole` | `Qt::UserRole + 104` | Remote name of the device ([QString](https://doc.qt.io/qt-6/qstring.html)). |
| `BluezQt::DevicesModel::ClassRole` | `Qt::UserRole + 105` | Class of the device (quint32). |
| `BluezQt::DevicesModel::TypeRole` | `Qt::UserRole + 106` | Type of the device ([Device::Type](bluezqt-device.md#Type-enum)). |
| `BluezQt::DevicesModel::AppearanceRole` | `Qt::UserRole + 107` | Appearance of the device (quint16). |
| `BluezQt::DevicesModel::IconRole` | `Qt::UserRole + 108` | Icon name of the device ([QString](https://doc.qt.io/qt-6/qstring.html)). |
| `BluezQt::DevicesModel::PairedRole` | `Qt::UserRole + 109` | Indicates whether the device is paired (bool). |
| `BluezQt::DevicesModel::TrustedRole` | `Qt::UserRole + 110` | Indicates whether the device is trusted (bool). |
| `BluezQt::DevicesModel::BlockedRole` | `Qt::UserRole + 111` | Indicates whether the device is blocked (bool). |
| `BluezQt::DevicesModel::LegacyPairingRole` | `Qt::UserRole + 112` | Indicates whether the device has legacy pairing (bool). |
| `BluezQt::DevicesModel::RssiRole` | `Qt::UserRole + 113` | Received Signal Strength Indicator of the device (qint16). |
| `BluezQt::DevicesModel::ConnectedRole` | `Qt::UserRole + 114` | Indicates whether the device is connected (bool). |
| `BluezQt::DevicesModel::UuidsRole` | `Qt::UserRole + 115` | UUIDs of supported services by the device ([QStringList](https://doc.qt.io/qt-6/qstringlist.html)). |
| `BluezQt::DevicesModel::ModaliasRole` | `Qt::UserRole + 116` | Modalias of the device ([QString](https://doc.qt.io/qt-6/qstring.html)). |
| `BluezQt::DevicesModel::AdapterNameRole` | `Qt::UserRole + 117` | Name of the associated adapter ([QString](https://doc.qt.io/qt-6/qstring.html)). |
| `BluezQt::DevicesModel::AdapterAddressRole` | `Qt::UserRole + 118` | Address of the associated adapter ([QString](https://doc.qt.io/qt-6/qstring.html)). |
| `BluezQt::DevicesModel::AdapterPoweredRole` | `Qt::UserRole + 119` | Indicates whether the associated adapter is powered (bool). |
| `BluezQt::DevicesModel::AdapterDiscoverableRole` | `Qt::UserRole + 120` | Indicates whether the associated adapter is discoverable (bool). |
| `BluezQt::DevicesModel::AdapterPairableRole` | `Qt::UserRole + 121` | Indicates whether the associated adapter is pairable (bool). |
| `BluezQt::DevicesModel::AdapterDiscoveringRole` | `Qt::UserRole + 122` | Indicates whether the associated adapter is discovering (bool). |
| `BluezQt::DevicesModel::AdapterUuidsRole` | `Qt::UserRole + 123` | UUIDs of supported services by the associated adapter ([QStringList](https://doc.qt.io/qt-6/qstringlist.html)). |
| `BluezQt::DevicesModel::LastRole` | `Qt::UserRole + 124` | Last role used by [DevicesModel](bluezqt-devicesmodel.md). |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] DevicesModel::DevicesModel(BluezQt::Manager \**manager*, QObject \**parent* = nullptr) {#DevicesModel}

Creates a new [DevicesModel](bluezqt-devicesmodel.md) object using the given `manager` as a child of `parent`.

### BluezQt::DevicePtr DevicesModel::device(const QModelIndex &*index*) const {#device}

Returns a device object for the specified `index` in the model.
