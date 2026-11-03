---
title: "KViewStateMaintainer Class"
description: "Encapsulates the maintenance of state between resets of QAbstractItemModel."
---

# KViewStateMaintainer Class

Encapsulates the maintenance of state between resets of [QAbstractItemModel](https://doc.qt.io/qt-6/qabstractitemmodel.html). [More...](#details)

- **Header:** `#include <KViewStateMaintainer>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ConfigWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigWidgets)`
- **Inherits:** [KViewStateMaintainerBase](../kwidgetsaddons/kviewstatemaintainerbase.md)

[List of all members, including inherited members](kviewstatemaintainer-members.md)

## Public Functions

- [KViewStateMaintainer(const KConfigGroup &configGroup, QObject \*parent = nullptr)](#KViewStateMaintainer)

## Detailed Description {#details}

```cpp
m_collectionViewStateMaintainer = new KViewStateMaintainer<Akonadi::ETMViewStateSaver>(KSharedConfig::openConfig()->group("collectionView"));
m_collectionViewStateMaintainer->setView(m_collectionView);

m_collectionCheckStateMaintainer = new KViewStateMaintainer<Akonadi::ETMViewStateSaver>(KSharedConfig::openConfig()->group("collectionCheckState"));
m_collectionCheckStateMaintainer->setSelectionModel(m_checkableProxy->selectionModel());
```

*See also* [KConfigViewStateSaver](kconfigviewstatesaver.md)

## Member Function Documentation {#member-function-documentation}

### KViewStateMaintainer::KViewStateMaintainer(const KConfigGroup &*configGroup*, QObject \**parent* = nullptr) {#KViewStateMaintainer}
