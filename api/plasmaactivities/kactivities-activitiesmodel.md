---
title: "KActivities::ActivitiesModel Class"
description: "Data model that shows existing activities."
---

# KActivities::ActivitiesModel Class

Data model that shows existing activities. [More...](#details)

- **Header:** `#include <PlasmaActivities/ActivitiesModel>`
- **CMake:** `find_package(Plasma REQUIRED COMPONENTS Activities)`  
  `target_link_libraries(mytarget PRIVATE Plasma::Activities)`
- **Inherits:** [QAbstractListModel](https://doc.qt.io/qt-6/qabstractlistmodel.html)

[List of all members, including inherited members](kactivities-activitiesmodel-members.md)

## Public Types

- [enum ActivitiesModel::Roles](#Roles-enum)

## Public Functions

- [ActivitiesModel(QObject \*parent = nullptr)](#ActivitiesModel)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum ActivitiesModel::Roles {#Roles-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KActivities::ActivitiesModel::ActivityId` | `Qt::UserRole` | UUID of the activity |
| `KActivities::ActivitiesModel::ActivityName` | `Qt::UserRole + 1` | Activity name |
| `KActivities::ActivitiesModel::ActivityDescription` | `Qt::UserRole + 2` | Activity description |
| `KActivities::ActivitiesModel::ActivityIconSource` | `Qt::UserRole + 3` | Activity icon source name |
| `KActivities::ActivitiesModel::ActivityBackground` | `Qt::UserRole + 5` | Activity wallpaper (currently unsupported) |
| `KActivities::ActivitiesModel::ActivityIsCurrent` | `Qt::UserRole + 6` | Is this activity the current one current |
| `KActivities::ActivitiesModel::UserRole` | `Qt::UserRole + 32` | To be used by models that inherit this one |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ActivitiesModel::ActivitiesModel(QObject \**parent* = nullptr) {#ActivitiesModel}
