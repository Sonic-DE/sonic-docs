---
title: "KCategorizedView Class"
description: "Item view for listing items in a categorized fashion optionally."
---

# KCategorizedView Class

Item view for listing items in a categorized fashion optionally. [More...](#details)

- **Header:** `#include <KCategorizedView>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ItemViews)`  
  `target_link_libraries(mytarget PRIVATE KF6::ItemViews)`
- **Inherits:** [QListView](https://doc.qt.io/qt-6/qlistview.html)

[List of all members, including inherited members](kcategorizedview-members.md)

## Properties

- [alternatingBlockColors : bool](#alternatingBlockColors-prop)
- [categorySpacing : int](#categorySpacing-prop)
- [collapsibleBlocks : bool](#collapsibleBlocks-prop)

## Public Functions

- [KCategorizedView(QWidget \*parent = nullptr)](#KCategorizedView)
- [bool alternatingBlockColors() const](#alternatingBlockColors)
- [QModelIndexList block(const QModelIndex &representative)](#block)
- [QModelIndexList block(const QString &category)](#block-1)
- [KCategoryDrawer \*categoryDrawer() const](#categoryDrawer)
- [int categorySpacing() const](#categorySpacing)
- [bool collapsibleBlocks() const](#collapsibleBlocks)
- [void setAlternatingBlockColors(bool enable)](#setAlternatingBlockColors)
- [void setCategoryDrawer(KCategoryDrawer \*categoryDrawer)](#setCategoryDrawer)
- [void setCategorySpacing(int categorySpacing)](#setCategorySpacing)
- [void setCollapsibleBlocks(bool enable)](#setCollapsibleBlocks)
- [void setGridSize(const QSize &size)](#setGridSize)
- [void setGridSizeOwn(const QSize &size)](#setGridSizeOwn)

## Signals

- [void alternatingBlockColorsChanged(bool enable)](#alternatingBlockColorsChanged)
- [void categorySpacingChanged(int spacing)](#categorySpacingChanged)
- [void collapsibleBlocksChanged(bool enable)](#collapsibleBlocksChanged)

## Detailed Description {#details}

[KCategorizedView](kcategorizedview.md) basically has the same functionality as [QListView](https://doc.qt.io/qt-6/qlistview.html), only that it also lets you layout items in a way that they are categorized visually.

For it to work you will need to set a [KCategorizedSortFilterProxyModel](kcategorizedsortfilterproxymodel.md) and a [KCategoryDrawer](kcategorydrawer.md) with methods [setModel](https://doc.qt.io/qt-6/qabstractitemview.html#setModel)() and [setCategoryDrawer](kcategorizedview.md#setCategoryDrawer)() respectively. Also, the model will need to be flagged as categorized with [KCategorizedSortFilterProxyModel::setCategorizedModel](kcategorizedsortfilterproxymodel.md#setCategorizedModel)(true).

The way it works (if categorization enabled):

- When sorting, it does more things than [QListView](https://doc.qt.io/qt-6/qlistview.html) does. It will ask the model for the special role CategorySortRole (see [KCategorizedSortFilterProxyModel](kcategorizedsortfilterproxymodel.md)). This can return a [QString](https://doc.qt.io/qt-6/qstring.html) or an int in order to tell the view the order of categories. In this sense, for instance, if we are sorting by name ascending, "A" would be before than "B". If we are sorting by size ascending, 512 bytes would be before 1024 bytes. This way categories are also sorted.
- When the view has to paint, it will ask the model with the role CategoryDisplayRole (see [KCategorizedSortFilterProxyModel](kcategorizedsortfilterproxymodel.md)). It will for instance return "F" for "foo.pdf" if we are sorting by name ascending, or "Small" if a certain item has 100 bytes, for example.

For drawing categories, [KCategoryDrawer](kcategorydrawer.md) will be used. You can inherit this class to do your own drawing.

> **Note:** All examples cited before talk about filesystems and such, but have present that this is a completely generic class, and it can be used for whatever your purpose is. For instance when talking about animals, you can separate them by "Mammal" and "Oviparous". In this very case, for example, the CategorySortRole and the CategoryDisplayRole could be the same ("Mammal" and "Oviparous").

> **Note:** There is a really performance boost if CategorySortRole returns an int instead of a [QString](https://doc.qt.io/qt-6/qstring.html). Have present that this role is asked (n \* log n) times when sorting and compared. Comparing ints is always faster than comparing strings, without mattering how fast the string comparison is. Consider thinking of a way of returning ints instead of QStrings if your model can contain a high number of items.

> **Warning:** Note that for really drawing items in blocks you will need some things to be done:

- The model set to this view has to be (or inherit if you want to do special stuff in it) [KCategorizedSortFilterProxyModel](kcategorizedsortfilterproxymodel.md).
- This model needs to be set setCategorizedModel to true.
- Set a category drawer by calling [setCategoryDrawer](kcategorizedview.md#setCategoryDrawer).

*See also* [KCategorizedSortFilterProxyModel](kcategorizedsortfilterproxymodel.md), [KCategoryDrawer](kcategorydrawer.md)

## Property Documentation {#property-documentation}

### alternatingBlockColors : bool {#alternatingBlockColors-prop}

**Access functions:**

- `bool` **[alternatingBlockColors](kcategorizedview.md#alternatingBlockColors)**() const
- `void` **[setAlternatingBlockColors](kcategorizedview.md#setAlternatingBlockColors)**(`bool` *enable*)

**Notifier signal:**

- `void` **[alternatingBlockColorsChanged](kcategorizedview.md#alternatingBlockColorsChanged)**(`bool` *enable*)

### categorySpacing : int {#categorySpacing-prop}

**Access functions:**

- `int` **[categorySpacing](kcategorizedview.md#categorySpacing)**() const
- `void` **[setCategorySpacing](kcategorizedview.md#setCategorySpacing)**(`int` *categorySpacing*)

**Notifier signal:**

- `void` **[categorySpacingChanged](kcategorizedview.md#categorySpacingChanged)**(`int` *spacing*)

### collapsibleBlocks : bool {#collapsibleBlocks-prop}

**Access functions:**

- `bool` **[collapsibleBlocks](kcategorizedview.md#collapsibleBlocks)**() const
- `void` **[setCollapsibleBlocks](kcategorizedview.md#setCollapsibleBlocks)**(`bool` *enable*)

**Notifier signal:**

- `void` **[collapsibleBlocksChanged](kcategorizedview.md#collapsibleBlocksChanged)**(`bool` *enable*)

## Member Function Documentation {#member-function-documentation}

### KCategorizedView::KCategorizedView(QWidget \**parent* = nullptr) {#KCategorizedView}

### bool KCategorizedView::alternatingBlockColors() const {#alternatingBlockColors}

Returns whether blocks should be drawn with alternating colors.

> **Note:** Getter function for property [alternatingBlockColors](kcategorizedview.md#alternatingBlockColors-prop).

*See also* [setAlternatingBlockColors](kcategorizedview.md#setAlternatingBlockColors)()

### \[signal\] void KCategorizedView::alternatingBlockColorsChanged(bool *enable*) {#alternatingBlockColorsChanged}

> **Note:** Notifier signal for property [alternatingBlockColors](kcategorizedview.md#alternatingBlockColors-prop).

### QModelIndexList KCategorizedView::block(const QModelIndex &*representative*) {#block}

Returns the block of indexes that are represented by `representative`.

### QModelIndexList KCategorizedView::block(const QString &*category*) {#block-1}

Returns the block of indexes that are in `category`.

### KCategoryDrawer \*KCategorizedView::categoryDrawer() const {#categoryDrawer}

Returns the current category drawer.

*See also* [setCategoryDrawer](kcategorizedview.md#setCategoryDrawer)()

### int KCategorizedView::categorySpacing() const {#categorySpacing}

Returns the spacing between categories.

> **Note:** Getter function for property [categorySpacing](kcategorizedview.md#categorySpacing-prop).

*See also* [setCategorySpacing](kcategorizedview.md#setCategorySpacing)()

### \[signal\] void KCategorizedView::categorySpacingChanged(int *spacing*) {#categorySpacingChanged}

> **Note:** Notifier signal for property [categorySpacing](kcategorizedview.md#categorySpacing-prop).

### bool KCategorizedView::collapsibleBlocks() const {#collapsibleBlocks}

Returns whether blocks can be collapsed or not.

> **Note:** Getter function for property [collapsibleBlocks](kcategorizedview.md#collapsibleBlocks-prop).

*See also* [setCollapsibleBlocks](kcategorizedview.md#setCollapsibleBlocks)()

### \[signal\] void KCategorizedView::collapsibleBlocksChanged(bool *enable*) {#collapsibleBlocksChanged}

> **Note:** Notifier signal for property [collapsibleBlocks](kcategorizedview.md#collapsibleBlocks-prop).

### void KCategorizedView::setAlternatingBlockColors(bool *enable*) {#setAlternatingBlockColors}

Sets whether blocks should be drawn with alternating colors.

> **Note:** Setter function for property [alternatingBlockColors](kcategorizedview.md#alternatingBlockColors-prop).

*See also* [alternatingBlockColors](kcategorizedview.md#alternatingBlockColors)()

### void KCategorizedView::setCategoryDrawer(KCategoryDrawer \**categoryDrawer*) {#setCategoryDrawer}

The category drawer that will be used for drawing categories.

*See also* [categoryDrawer](kcategorizedview.md#categoryDrawer)()

### void KCategorizedView::setCategorySpacing(int *categorySpacing*) {#setCategorySpacing}

Sets the spacing between categories.

> **Note:** Setter function for property [categorySpacing](kcategorizedview.md#categorySpacing-prop).

*See also* [categorySpacing](kcategorizedview.md#categorySpacing)()

### void KCategorizedView::setCollapsibleBlocks(bool *enable*) {#setCollapsibleBlocks}

Sets whether blocks can be collapsed or not.

> **Note:** Setter function for property [collapsibleBlocks](kcategorizedview.md#collapsibleBlocks-prop).

*See also* [collapsibleBlocks](kcategorizedview.md#collapsibleBlocks)()

### void KCategorizedView::setGridSize(const QSize &*size*) {#setGridSize}

Calls to [setGridSizeOwn](kcategorizedview.md#setGridSizeOwn)().

### void KCategorizedView::setGridSizeOwn(const QSize &*size*) {#setGridSizeOwn}

> **Warning:** note that [setGridSize](kcategorizedview.md#setGridSize) is not virtual in the base class ([QListView](https://doc.qt.io/qt-6/qlistview.html)), so if you are calling to this method, make sure you have a [KCategorizedView](kcategorizedview.md) pointer around. This means that something like:

```cpp
QListView *lv = new KCategorizedView();
lv->setGridSize(mySize);
```

will not call to the expected [setGridSize](kcategorizedview.md#setGridSize) method. Instead do something like this:

```cpp
QListView *lv;
...
KCategorizedView *cv = qobject_cast<KCategorizedView*>(lv);
if (cv) {
    cv->setGridSizeOwn(mySize);
} else {
    lv->setGridSize(mySize);
}
```

> **Note:** this method will call to [QListView::setGridSize](https://doc.qt.io/qt-6/qlistview.html#gridSize-prop) among other operations.
