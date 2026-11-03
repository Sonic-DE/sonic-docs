---
title: "KSortableList Class"
description: "KSortableList is a QList which associates a key with each item in the list. This key is used for sorting when calling sort()."
---

# KSortableList Class

[KSortableList](ksortablelist.md) is a [QList](https://doc.qt.io/qt-6/qlist.html) which associates a key with each item in the list. This key is used for sorting when calling [sort](ksortablelist.md#sort)(). [More...](#details)

- **Header:** `#include <KSortableList>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Completion)`  
  `target_link_libraries(mytarget PRIVATE KF6::Completion)`
- **Inherits:** [QList](https://doc.qt.io/qt-6/qlist.html)

[List of all members, including inherited members](ksortablelist-members.md)

## Public Functions

- [void insert(Key i, const T &t)](#insert)
- [void sort()](#sort)
- [T &KSortableList::operator\[\](Key i)](#operator-5b-5d)
- [const T &KSortableList::operator\[\](Key i) const](#operator-5b-5d-1)

## Detailed Description {#details}

This allows to temporarily calculate a key and use it for sorting, without having to store that key in the items, or calculate that key many times for the same item during sorting if that calculation is expensive.

## Member Function Documentation {#member-function-documentation}

### void KSortableList::insert(Key *i*, const T &*t*) {#insert}

Insert a [KSortableItem](ksortableitem.md) with the given values.

`i` the first value

`t` the second value

### void KSortableList::sort() {#sort}

Sorts the KSortableItems.

### T &KSortableList::operator\[\](Key *i*) {#operator-5b-5d}

Returns the first value of the [KSortableItem](ksortableitem.md) at the given position.

### const T &KSortableList::operator\[\](Key *i*) const {#operator-5b-5d-1}

Returns the first value of the [KSortableItem](ksortableitem.md) at the given position.
