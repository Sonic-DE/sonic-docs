---
title: "KSortableItem Class"
description: "KSortableItem is a QPair that provides several operators for sorting."
---

# KSortableItem Class

[KSortableItem](ksortableitem.md) is a [QPair](https://doc.qt.io/qt-6/qpair.html#QPair-typedef) that provides several operators for sorting. [More...](#details)

- **Header:** `#include <KSortableList>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Completion)`  
  `target_link_libraries(mytarget PRIVATE KF6::Completion)`

[List of all members, including inherited members](ksortableitem-members.md)

## Public Functions

- [KSortableItem()](#KSortableItem)
- [KSortableItem(Key i, const T &t)](#KSortableItem-2)
- [KSortableItem(const KSortableItem\<T, Key\> &rhs)](#KSortableItem-1)
- [Key key() const](#key)
- [T &value()](#value)
- [const T &value() const](#value-1)
- [bool KSortableItem::operator!=(const KSortableItem\<T, Key\> &i2) const](#operator-not-eq)
- [bool KSortableItem::operator\<(const KSortableItem\<T, Key\> &i2) const](#operator-lt)
- [bool KSortableItem::operator\<=(const KSortableItem\<T, Key\> &i2) const](#operator-lt-eq)
- [KSortableItem\<T, Key\> &KSortableItem::operator=(const KSortableItem\<T, Key\> &i)](#operator-eq)
- [bool KSortableItem::operator==(const KSortableItem\<T, Key\> &i2) const](#operator-eq-eq)
- [bool KSortableItem::operator\>(const KSortableItem\<T, Key\> &i2) const](#operator-gt)
- [bool KSortableItem::operator\>=(const KSortableItem\<T, Key\> &i2) const](#operator-gt-eq)

## Detailed Description {#details}

*See also* [KSortableList](ksortablelist.md)

## Member Function Documentation {#member-function-documentation}

### KSortableItem::KSortableItem() {#KSortableItem}

Creates a new [KSortableItem](ksortableitem.md) with uninitialized values.

### KSortableItem::KSortableItem(Key *i*, const T &*t*) {#KSortableItem-2}

Creates a new [KSortableItem](ksortableitem.md) with the given values.

`i` the first value (the key)

`t` the second value (the item)

### KSortableItem::KSortableItem(const KSortableItem\<T, Key\> &*rhs*) {#KSortableItem-1}

Creates a new [KSortableItem](ksortableitem.md) that copies another one.

`rhs` the other item to copy

### Key KSortableItem::key() const {#key}

Returns the first value.

### T &KSortableItem::value() {#value}

Returns the second value (the item)

### const T &KSortableItem::value() const {#value-1}

Returns the second value (the item)

### bool KSortableItem::operator!=(const KSortableItem\<T, Key\> &*i2*) const {#operator-not-eq}

Compares the two items. This implementation only compares the first value.

### bool KSortableItem::operator\<(const KSortableItem\<T, Key\> &*i2*) const {#operator-lt}

Compares the two items. This implementation only compares the first value.

### bool KSortableItem::operator\<=(const KSortableItem\<T, Key\> &*i2*) const {#operator-lt-eq}

Compares the two items. This implementation only compares the first value.

### KSortableItem\<T, Key\> &KSortableItem::operator=(const KSortableItem\<T, Key\> &*i*) {#operator-eq}

Assignment operator, just copies the item.

### bool KSortableItem::operator==(const KSortableItem\<T, Key\> &*i2*) const {#operator-eq-eq}

Compares the two items. This implementation only compares the first value.

### bool KSortableItem::operator\>(const KSortableItem\<T, Key\> &*i2*) const {#operator-gt}

Compares the two items. This implementation only compares the first value.

### bool KSortableItem::operator\>=(const KSortableItem\<T, Key\> &*i2*) const {#operator-gt-eq}

Compares the two items. This implementation only compares the first value.
