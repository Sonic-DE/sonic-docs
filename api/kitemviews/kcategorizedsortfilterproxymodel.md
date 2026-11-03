---
title: "KCategorizedSortFilterProxyModel Class"
description: "This class lets you categorize a view. It is meant to be used along with KCategorizedView class."
---

# KCategorizedSortFilterProxyModel Class

This class lets you categorize a view. It is meant to be used along with [KCategorizedView](kcategorizedview.md) class. [More...](#details)

- **Header:** `#include <KCategorizedSortFilterProxyModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ItemViews)`  
  `target_link_libraries(mytarget PRIVATE KF6::ItemViews)`
- **Inherits:** [QSortFilterProxyModel](https://doc.qt.io/qt-6/qsortfilterproxymodel.html)

[List of all members, including inherited members](kcategorizedsortfilterproxymodel-members.md)

## Public Types

- [enum KCategorizedSortFilterProxyModel::AdditionalRoles](#AdditionalRoles-enum)

## Public Functions

- [KCategorizedSortFilterProxyModel(QObject \*parent = nullptr)](#KCategorizedSortFilterProxyModel)
- [bool isCategorizedModel() const](#isCategorizedModel)
- [void setCategorizedModel(bool categorizedModel)](#setCategorizedModel)
- [void setSortCategoriesByNaturalComparison(bool sortCategoriesByNaturalComparison)](#setSortCategoriesByNaturalComparison)
- [void sort(int column, Qt::SortOrder order = Qt::AscendingOrder)](#sort)
- [bool sortCategoriesByNaturalComparison() const](#sortCategoriesByNaturalComparison)
- [int sortColumn() const](#sortColumn)
- [Qt::SortOrder sortOrder() const](#sortOrder)

## Protected Functions

- [int compareCategories(const QModelIndex &left, const QModelIndex &right) const](#compareCategories)
- [bool lessThan(const QModelIndex &left, const QModelIndex &right) const](#lessThan)
- [bool subSortLessThan(const QModelIndex &left, const QModelIndex &right) const](#subSortLessThan)

## Detailed Description {#details}

In general terms all you need to do is to reimplement [subSortLessThan](kcategorizedsortfilterproxymodel.md#subSortLessThan)() and [compareCategories](kcategorizedsortfilterproxymodel.md#compareCategories)() methods. In order to make categorization work, you need to also call [setCategorizedModel](kcategorizedsortfilterproxymodel.md#setCategorizedModel)() class to enable it, since the categorization is disabled by default.

*See also* [KCategorizedView](kcategorizedview.md)

## Member Type Documentation {#member-type-documentation}

### enum KCategorizedSortFilterProxyModel::AdditionalRoles {#AdditionalRoles-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KCategorizedSortFilterProxyModel::CategoryDisplayRole` | `0x17CE990A` | This role is used for asking the category to a given index |
| `KCategorizedSortFilterProxyModel::CategorySortRole` | `0x27857E60` | This role is used for sorting categories. You can return a string or a long long value. Strings will be sorted alphabetically while long long will be sorted by their value. Please note that this value won't be shown on the view, is only for sorting purposes. What will be shown as "Category" on the view will be asked with the role CategoryDisplayRole. |

## Member Function Documentation {#member-function-documentation}

### KCategorizedSortFilterProxyModel::KCategorizedSortFilterProxyModel(QObject \**parent* = nullptr) {#KCategorizedSortFilterProxyModel}

### \[virtual protected\] int KCategorizedSortFilterProxyModel::compareCategories(const QModelIndex &*left*, const QModelIndex &*right*) const {#compareCategories}

This method compares the category of the `left` index with the category of the `right` index.

Internally and if not reimplemented, this method will ask for `left` and `right` models for role [CategorySortRole](kcategorizedsortfilterproxymodel.md#AdditionalRoles-enum). In order to correctly sort categories, the [data](https://doc.qt.io/qt-6/qsortfilterproxymodel.html#data)() method of the model should return a qlonglong (or numeric) value, or a [QString](https://doc.qt.io/qt-6/qstring.html) object. [QString](https://doc.qt.io/qt-6/qstring.html) objects will be sorted with [QString::localeAwareCompare](https://doc.qt.io/qt-6/qstring.html#localeAwareCompare) if [sortCategoriesByNaturalComparison](kcategorizedsortfilterproxymodel.md#sortCategoriesByNaturalComparison)() is true.

> **Note:** Please have present that: [QString](https://doc.qt.io/qt-6/qstring.html)([QChar](https://doc.qt.io/qt-6/qchar.html)([QChar::ObjectReplacementCharacter](https://doc.qt.io/qt-6/qchar.html#SpecialCharacter-enum))) \> [QString](https://doc.qt.io/qt-6/qstring.html)([QChar](https://doc.qt.io/qt-6/qchar.html)([QChar::ReplacementCharacter](https://doc.qt.io/qt-6/qchar.html#SpecialCharacter-enum))) \> \[ all possible strings \] \> QString();

This means that QString() will be sorted the first one, while [QString](https://doc.qt.io/qt-6/qstring.html)([QChar](https://doc.qt.io/qt-6/qchar.html)([QChar::ObjectReplacementCharacter](https://doc.qt.io/qt-6/qchar.html#SpecialCharacter-enum))) and [QString](https://doc.qt.io/qt-6/qstring.html)([QChar](https://doc.qt.io/qt-6/qchar.html)([QChar::ReplacementCharacter](https://doc.qt.io/qt-6/qchar.html#SpecialCharacter-enum))) will be sorted in last position.

> **Warning:** Please note that [data](https://doc.qt.io/qt-6/qsortfilterproxymodel.html#data)() method of the model should return always information of the same type. If you return a [QString](https://doc.qt.io/qt-6/qstring.html) for an index, you should return always QStrings for all indexes for role [CategorySortRole](kcategorizedsortfilterproxymodel.md#AdditionalRoles-enum) in order to correctly sort categories. You can't mix by returning a [QString](https://doc.qt.io/qt-6/qstring.html) for one index, and a qlonglong for other.

> **Note:** If you need a more complex layout, you will have to reimplement this method.

Returns A negative value if the category of `left` should be placed before the category of `right`. 0 if `left` and `right` are on the same category, and a positive value if the category of `left` should be placed after the category of `right`.

### bool KCategorizedSortFilterProxyModel::isCategorizedModel() const {#isCategorizedModel}

Returns whether the model is categorized or not. Disabled by default.

### \[override virtual protected\] bool KCategorizedSortFilterProxyModel::lessThan(const QModelIndex &*left*, const QModelIndex &*right*) const {#lessThan}

Reimplements: [QSortFilterProxyModel::lessThan(const QModelIndex &source\_left, const QModelIndex &source\_right) const](https://doc.qt.io/qt-6/qsortfilterproxymodel.html#lessThan).

Overridden from [QSortFilterProxyModel](https://doc.qt.io/qt-6/qsortfilterproxymodel.html). If you are subclassing [KCategorizedSortFilterProxyModel](kcategorizedsortfilterproxymodel.md), you will probably not need to reimplement this method.

It calls [compareCategories](kcategorizedsortfilterproxymodel.md#compareCategories)() to sort by category. If the both items are in the same category (i.e. [compareCategories](kcategorizedsortfilterproxymodel.md#compareCategories) returns 0), then [subSortLessThan](kcategorizedsortfilterproxymodel.md#subSortLessThan) is called.

Returns true if the item `left` is less than the item `right` when sorting.

> **Warning:** You usually won't need to reimplement this method when subclassing from [KCategorizedSortFilterProxyModel](kcategorizedsortfilterproxymodel.md).

### void KCategorizedSortFilterProxyModel::setCategorizedModel(bool *categorizedModel*) {#setCategorizedModel}

Enables or disables the categorization feature.

`categorizedModel` whether to enable or disable the categorization feature.

*See also* [isCategorizedModel](kcategorizedsortfilterproxymodel.md#isCategorizedModel)()

### void KCategorizedSortFilterProxyModel::setSortCategoriesByNaturalComparison(bool *sortCategoriesByNaturalComparison*) {#setSortCategoriesByNaturalComparison}

Set if the sorting using [CategorySortRole](kcategorizedsortfilterproxymodel.md#AdditionalRoles-enum) will use a natural comparison in the case that strings were returned. If enabled, [QCollator](https://doc.qt.io/qt-6/qcollator.html) will be used for sorting.

`sortCategoriesByNaturalComparison` whether to sort using a natural comparison or not.

*See also* [sortCategoriesByNaturalComparison](kcategorizedsortfilterproxymodel.md#sortCategoriesByNaturalComparison)()

### \[override virtual\] void KCategorizedSortFilterProxyModel::sort(int *column*, Qt::SortOrder *order* = Qt::AscendingOrder) {#sort}

Reimplements: [QSortFilterProxyModel::sort(int column, Qt::SortOrder order)](https://doc.qt.io/qt-6/qsortfilterproxymodel.html#sort).

Overridden from [QSortFilterProxyModel](https://doc.qt.io/qt-6/qsortfilterproxymodel.html). Sorts the source model using `column` for the given `order`.

### bool KCategorizedSortFilterProxyModel::sortCategoriesByNaturalComparison() const {#sortCategoriesByNaturalComparison}

Returns whether it is being used a natural comparison for sorting. Enabled by default.

*See also* [setSortCategoriesByNaturalComparison](kcategorizedsortfilterproxymodel.md#setSortCategoriesByNaturalComparison)()

### int KCategorizedSortFilterProxyModel::sortColumn() const {#sortColumn}

Returns the column being used for sorting.

### Qt::SortOrder KCategorizedSortFilterProxyModel::sortOrder() const {#sortOrder}

Returns the sort order being used for sorting.

### \[virtual protected\] bool KCategorizedSortFilterProxyModel::subSortLessThan(const QModelIndex &*left*, const QModelIndex &*right*) const {#subSortLessThan}

This method has a similar purpose as [lessThan](kcategorizedsortfilterproxymodel.md#lessThan)() has on [QSortFilterProxyModel](https://doc.qt.io/qt-6/qsortfilterproxymodel.html). It is used for sorting items that are in the same category.

Returns true if the item `left` is less than the item `right` when sorting.
