---
title: "KDNSSD::DomainModel Class"
description: "Model for list of Zeroconf domains."
---

# KDNSSD::DomainModel Class

Model for list of Zeroconf domains. [More...](#details)

- **Header:** `#include <KDNSSD/DomainModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS DNSSD)`  
  `target_link_libraries(mytarget PRIVATE KF6::DNSSD)`
- **Inherits:** [QAbstractItemModel](https://doc.qt.io/qt-6/qabstractitemmodel.html)

[List of all members, including inherited members](kdnssd-domainmodel-members.md)

## Public Functions

- [DomainModel(KDNSSD::DomainBrowser \*browser, QObject \*parent = nullptr)](#DomainModel)
- [bool hasIndex(int row, int column, const QModelIndex &parent) const](#hasIndex)

## Detailed Description {#details}

This class provides a Qt Model for [DomainBrowser](kdnssd-domainbrowser.md) to allow easy integration of domain discovery into a GUI. For example, to provide a combo box listing available domains, you can do:

```cpp
KDNSSD::DomainModel *domainModel = new DomainModel(
    new KDNSSD::DomainBrowser(KDNSSD::DomainBrowser::Browsing)
    );
QComboBox *domainCombo = new QComboBox();
domainCombo->setModel(domainModel);
```

## Member Function Documentation {#member-function-documentation}

### \[explicit\] DomainModel::DomainModel(KDNSSD::DomainBrowser \**browser*, QObject \**parent* = nullptr) {#DomainModel}

Creates a model for given domain browser and starts browsing for domains.

The model takes ownership of the browser, so there is no need to delete it afterwards.

> **Note:** You should **not** call [DomainBrowser::startBrowse](kdnssd-domainbrowser.md#startBrowse)() on `browser` before passing it to [DomainModel](kdnssd-domainmodel.md).

`browser` is the domain browser that will provide the domains to be listed by the model

`parent` is the parent object (see [QObject](https://doc.qt.io/qt-6/qobject.html) documentation)

### \[virtual\] bool DomainModel::hasIndex(int *row*, int *column*, const QModelIndex &*parent*) const {#hasIndex}
