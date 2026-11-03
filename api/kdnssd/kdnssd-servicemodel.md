---
title: "KDNSSD::ServiceModel Class"
description: "Model for list of Zeroconf services."
---

# KDNSSD::ServiceModel Class

Model for list of Zeroconf services. [More...](#details)

- **Header:** `#include <KDNSSD/ServiceModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS DNSSD)`  
  `target_link_libraries(mytarget PRIVATE KF6::DNSSD)`
- **Inherits:** [QAbstractItemModel](https://doc.qt.io/qt-6/qabstractitemmodel.html)

[List of all members, including inherited members](kdnssd-servicemodel-members.md)

## Public Types

- [enum ServiceModel::AdditionalRoles](#AdditionalRoles-enum)
- [enum ServiceModel::ModelColumns](#ModelColumns-enum)

## Public Functions

- [ServiceModel(KDNSSD::ServiceBrowser \*browser, QObject \*parent = nullptr)](#ServiceModel)
- [bool hasIndex(int row, int column, const QModelIndex &parent) const](#hasIndex)

## Detailed Description {#details}

This class provides a Qt Model for [ServiceBrowser](kdnssd-servicebrowser.md) to allow easy integration of service discovery into a GUI. For example, to show the HTTP servers published on the local network, you can do:

```cpp
KDNSSD::ServiceModel *serviceModel = new ServiceModel(
    new KDNSSD::ServiceBrowser("_http._tcp")
    );
QComboBox *serviceCombo = new QComboBox();
serviceCombo->setModel(serviceModel);
```

After the user makes a selection, the application typically needs to get a pointer to the selected service in order to get the host name and port. A RemoteService::Ptr can be obtained from a [QModelIndex](https://doc.qt.io/qt-6/qmodelindex.html) using:

```cpp
void onSelected(const QModelIndex &selection) {
    KDNSSD::RemoteService::Ptr service =
        selection.data(KDNSSD::ServiceModel::ServicePtrRole)
                 .value<KDNSSD::RemoteService::Ptr>();
}
```

## Member Type Documentation {#member-type-documentation}

### enum ServiceModel::AdditionalRoles {#AdditionalRoles-enum}

The additional data roles provided by this model.

| Constant | Value | Description |
| --- | --- | --- |
| `KDNSSD::ServiceModel::ServicePtrRole` | `0x7E6519DE` | Gets a RemoteService::Ptr for the service. |

### enum ServiceModel::ModelColumns {#ModelColumns-enum}

The default columns for this model.

If service browser is not set to resolve automatically, then the model will only ever have one column (the service name).

| Constant | Value | Description |
| --- | --- | --- |
| `KDNSSD::ServiceModel::ServiceName` | `0` | The name of this service. |
| `KDNSSD::ServiceModel::Host` | `1` | The hostname or IP address the service is hosted on. |
| `KDNSSD::ServiceModel::Port` | `2` | The TCP or UDP port the service is hosted on. |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ServiceModel::ServiceModel(KDNSSD::ServiceBrowser \**browser*, QObject \**parent* = nullptr) {#ServiceModel}

Creates a model for the given service browser and starts browsing for services.

> **Note:** The model takes ownership of the browser, so there is no need to delete it afterwards.

> **Note:** You should **not** call [ServiceBrowser::startBrowse](kdnssd-servicebrowser.md#startBrowse)() on `browser` before passing it to [ServiceModel](kdnssd-servicemodel.md).

### \[virtual\] bool ServiceModel::hasIndex(int *row*, int *column*, const QModelIndex &*parent*) const {#hasIndex}
