---
title: "KColorCollection Class"
description: "This class is deprecated since 6.3. We strongly advise against using it in new code."
---

# KColorCollection Class

**This class is deprecated since 6.3. We strongly advise against using it in new code.** [More...](#details)

- **Header:** `#include <KColorCollection>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS GuiAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::GuiAddons)`
- **Status:** Deprecated since 6.3

[List of all members, including inherited members](kcolorcollection-members.md)

## Public Types

- [enum KColorCollection::Editable](#Editable-enum)

## Public Functions

- [KColorCollection(const QString &name = QString())](#KColorCollection-1)
- [KColorCollection(const KColorCollection &)](#KColorCollection)
- [~KColorCollection()](#dtor.KColorCollection)
- [int addColor(const QColor &newColor, const QString &newColorName = QString())](#addColor)
- [int changeColor(const QColor &oldColor, const QColor &newColor, const QString &newColorName = QString())](#changeColor)
- [int changeColor(int index, const QColor &newColor, const QString &newColorName = QString())](#changeColor-1)
- [QColor color(int index) const](#color)
- [int count() const](#count)
- [QString description() const](#description)
- [KColorCollection::Editable editable() const](#editable)
- [int findColor(const QColor &color) const](#findColor)
- [QString name() const](#name)
- [QString name(const QColor &color) const](#name-1)
- [QString name(int index) const](#name-2)
- [bool save()](#save)
- [void setDescription(const QString &desc)](#setDescription)
- [void setEditable(KColorCollection::Editable editable)](#setEditable)
- [void setName(const QString &name)](#setName)
- [KColorCollection &KColorCollection::operator=(const KColorCollection &)](#operator-eq)

## Static Public Members

- [QStringList installedCollections()](#installedCollections)

**This class is deprecated since 6.3. We strongly advise against using it in new code.**

## Detailed Description {#details}

Class for handling color collections ("palettes").

This class makes it easy to handle color collections, sometimes referred to as "palettes". This class can read and write collections from and to a file.

This class uses the "GIMP" palette file format.

Unused and backing data no longer available

## Member Type Documentation {#member-type-documentation}

### enum KColorCollection::Editable {#Editable-enum}

Used to specify whether a collection may be edited.

| Constant | Value | Description |
| --- | --- | --- |
| `KColorCollection::Yes` | `0` | Collection may be edited |
| `KColorCollection::No` | `1` | Collection may not be edited |
| `KColorCollection::Ask` | `2` | Ask user before editing |

*See also* [editable](kcolorcollection.md#editable)(), [setEditable](kcolorcollection.md#setEditable)()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KColorCollection::KColorCollection(const QString &*name* = QString()) {#KColorCollection-1}

[KColorCollection](kcolorcollection.md) constructor. Creates a [KColorCollection](kcolorcollection.md) from a file the filename is derived from the name.

`name` The name of collection as returned by [installedCollections](kcolorcollection.md#installedCollections)()

### KColorCollection::KColorCollection(*const KColorCollection &*) {#KColorCollection}

[KColorCollection](kcolorcollection.md) copy constructor.

### \[noexcept\] KColorCollection::~KColorCollection() {#dtor.KColorCollection}

[KColorCollection](kcolorcollection.md) destructor.

### int KColorCollection::addColor(const QColor &*newColor*, const QString &*newColorName* = QString()) {#addColor}

Add a color.

`newColor` The color to add.

`newColorName` The name of the color, null to remove the name.

Returns The index of the added color.

### int KColorCollection::changeColor(const QColor &*oldColor*, const QColor &*newColor*, const QString &*newColorName* = QString()) {#changeColor}

Change a color.

`oldColor` The original color

`newColor` The new color.

`newColorName` The new color name, null to remove the name.

Returns the index of the new color or -1 if the color couldn't be changed.

### int KColorCollection::changeColor(int *index*, const QColor &*newColor*, const QString &*newColorName* = QString()) {#changeColor-1}

Change a color.

`index` Index of the color to change

`newColor` The new color.

`newColorName` The new color name, null to remove the name.

Returns the index of the new color or -1 if the color couldn't be changed.

### QColor KColorCollection::color(int *index*) const {#color}

Find color by index.

`index` the index of the desired color

Returns The `index` -th color of the collection, null if not found.

### int KColorCollection::count() const {#count}

Return the number of colors in the collection. Returns the number of colors

### QString KColorCollection::description() const {#description}

Get the description of the collection.

Returns the description of the collection.

*See also* [setDescription](kcolorcollection.md#setDescription)()

### KColorCollection::Editable KColorCollection::editable() const {#editable}

Returns whether the collection may be edited. Returns the state of the collection

*See also* [setEditable](kcolorcollection.md#setEditable)()

### int KColorCollection::findColor(const QColor &*color*) const {#findColor}

Find index by `color`.

`color` the color to find

Returns The index of the color in the collection or -1 if the color is not found.

### \[static\] QStringList KColorCollection::installedCollections() {#installedCollections}

Query which KDE color collections are installed.

Returns a list with installed color collection names.

### QString KColorCollection::name() const {#name}

Get the name of the collection.

Returns the name of the collection

*See also* [setName](kcolorcollection.md#setName)()

### QString KColorCollection::name(const QColor &*color*) const {#name-1}

Find color name by `color`.

Returns The name of color according to this collection.

Note that not all collections have named the colors.

Note also that each collection can give the same color a different name.

### QString KColorCollection::name(int *index*) const {#name-2}

Find color name by `index`.

`index` the index of the color

Returns The name of the `index` -th color.

Note that not all collections have named the colors. Null is returned if the color does not exist or has no name.

### bool KColorCollection::save() {#save}

Save the collection

Returns `true` if successful

### void KColorCollection::setDescription(const QString &*desc*) {#setDescription}

Set the description of the collection.

`desc` the new description

*See also* [description](kcolorcollection.md#description)()

### void KColorCollection::setEditable(KColorCollection::Editable *editable*) {#setEditable}

Change whether the collection may be edited.

`editable` the state of the collection

*See also* [editable](kcolorcollection.md#editable)()

### void KColorCollection::setName(const QString &*name*) {#setName}

Set the name of the collection.

`name` the name of the collection

*See also* [name](kcolorcollection.md#name)()

### KColorCollection &KColorCollection::operator=(*const KColorCollection &*) {#operator-eq}

[KColorCollection](kcolorcollection.md) assignment operator
