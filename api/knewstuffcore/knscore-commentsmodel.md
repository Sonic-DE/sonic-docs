---
title: "KNSCore::CommentsModel Class"
description: "A model which takes care of the comments for a single Entry."
---

# KNSCore::CommentsModel Class

A model which takes care of the comments for a single Entry. [More...](#details)

- **Header:** `#include <CommentsModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NewStuff)`  
  `target_link_libraries(mytarget PRIVATE KF6::NewStuff)`
- **Inherits:** [QAbstractListModel](https://doc.qt.io/qt-6/qabstractlistmodel.html)

[List of all members, including inherited members](knscore-commentsmodel-members.md)

## Public Types

- [enum CommentsModel::Roles](#Roles-enum)

## Properties

- [entry : KNSCore::Entry](#entry-prop)

## Public Functions

- [CommentsModel(KNSCore::EngineBase \*parent = nullptr)](#CommentsModel)

## Detailed Description {#details}

> **Note:** This model should preferably be constructed by asking the Engine to give a model instance to you for a specific entry using the commentsForEntry function. If you insist, you can construct an instance yourself as well, but this is not recommended.

*See also* Engine::commentsForEntry(KNSCore::Entry)

## Member Type Documentation {#member-type-documentation}

### enum CommentsModel::Roles {#Roles-enum}

| Constant |   |
| --- | --- |
| `KNSCore::CommentsModel::SubjectRole` | `Qt::DisplayRole` |
| `KNSCore::CommentsModel::IdRole` | `Qt::UserRole + 1` |
| `KNSCore::CommentsModel::TextRole` | `258` |
| `KNSCore::CommentsModel::ChildCountRole` | `259` |
| `KNSCore::CommentsModel::UsernameRole` | `260` |
| `KNSCore::CommentsModel::DateRole` | `261` |
| `KNSCore::CommentsModel::ScoreRole` | `262` |
| `KNSCore::CommentsModel::ParentIndexRole` | `263` |
| `KNSCore::CommentsModel::DepthRole` | `264` |

## Property Documentation {#property-documentation}

### entry : KNSCore::Entry {#entry-prop}

The Entry for which this model should handle comments

**Access functions:**

- const `KNSCore::Entry` &**entry**() const
- `void` **setEntry**(const `KNSCore::Entry` &*newEntry*)

**Notifier signal:**

- `void` **entryChanged**()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] CommentsModel::CommentsModel(KNSCore::EngineBase \**parent* = nullptr) {#CommentsModel}

Construct a new [CommentsModel](knscore-commentsmodel.md) instance.

> **Note:** The class is intended to be constructed using the Engine::commentsForEntry function

*See also* Engine::commentsForEntry(KNSCore::Entry)
