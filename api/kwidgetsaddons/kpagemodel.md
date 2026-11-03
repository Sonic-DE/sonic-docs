---
title: "KPageModel Class"
description: "A base class for a model used by KPageView."
---

# KPageModel Class

A base class for a model used by [KPageView](kpageview.md). [More...](#details)

- **Header:** `#include <KPageModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QAbstractItemModel](https://doc.qt.io/qt-6/qabstractitemmodel.html)
- **Inherited By:** [KPageWidgetModel](kpagewidgetmodel.md)

[List of all members, including inherited members](kpagemodel-members.md)

## Public Types

- [enum KPageModel::Role](#Role-enum)

## Public Functions

- [KPageModel(QObject \*parent = nullptr)](#KPageModel)

## Detailed Description {#details}

This class is an abstract base class which must be used to implement custom models for [KPageView](kpageview.md). Additional to the standard Qt::ItemDataRoles it provides the two roles

- [HeaderRole](kpagemodel.md#Role-enum)
- [HeaderVisibleRole](kpagemodel.md#Role-enum)
- [WidgetRole](kpagemodel.md#Role-enum)

which are used to return a header string for a page and a [QWidget](https://doc.qt.io/qt-6/qwidget.html) pointer to the page itself.

Example:

```cpp
KPageView *view = new KPageView( this );
KPageModel *model = new MyPageModel( this );

view->setModel( model );
```

*See also* [KPageView](kpageview.md)

## Member Type Documentation {#member-type-documentation}

### enum KPageModel::Role {#Role-enum}

Additional roles that [KPageView](kpageview.md) uses.

| Constant | Value | Description |
| --- | --- | --- |
| `KPageModel::HeaderRole` | `Qt::UserRole + 1` | A string to be rendered as page header. |
| `KPageModel::WidgetRole` | `258` | A pointer to the page widget. This is the widget that is shown when the item is selected. You can make [QVariant](https://doc.qt.io/qt-6/qvariant.html) take a [QWidget](https://doc.qt.io/qt-6/qwidget.html) using ```cpp QWidget *myWidget = new QWidget; QVariant v = QVariant::fromValue(myWidget); ``` |
| `KPageModel::When (since Qt 5.52)` | ? | true, show the page header, if false don't |
| `KPageModel::The (since Qt 6.6)` | ? | list of actions associated to the page |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KPageModel::KPageModel(QObject \**parent* = nullptr) {#KPageModel}

Constructs a page model with the given parent.
