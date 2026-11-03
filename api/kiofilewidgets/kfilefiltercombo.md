---
title: "KFileFilterCombo Class"
description: "File filter combo box."
---

# KFileFilterCombo Class

File filter combo box. [More...](#details)

- **Header:** `#include <KFileFilterCombo>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOFileWidgets)`
- **Inherits:** [KComboBox](../kcompletion/kcombobox.md)

[List of all members, including inherited members](kfilefiltercombo-members.md)

## Public Functions

- [KFileFilterCombo(QWidget \*parent = nullptr)](#KFileFilterCombo)
- [KFileFilter currentFilter() const](#currentFilter) (since 6.0)
- [KFileFilter defaultFilter() const](#defaultFilter) (since 6.0)
- [QList\<KFileFilter\> filters() const](#filters) (since 6.0)
- [void setCurrentFilter(const KFileFilter &filter)](#setCurrentFilter) (since 6.0)
- [void setDefaultFilter(const KFileFilter &filter)](#setDefaultFilter) (since 6.0)
- [void setFilters(const QList\<KFileFilter\> &filters, const KFileFilter &defaultFilter = KFileFilter())](#setFilters) (since 6.0)
- [bool showsAllTypes() const](#showsAllTypes)

## Signals

- [void filterChanged()](#filterChanged)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KFileFilterCombo::KFileFilterCombo(QWidget \**parent* = nullptr) {#KFileFilterCombo}

Creates a new filter combo box.

`parent` The parent widget.

### \[since 6.0\] KFileFilter KFileFilterCombo::currentFilter() const {#currentFilter}

The currently selected/active filter.

This function was introduced in Qt 6.0.

*See also* [setCurrentFilter](kfilefiltercombo.md#setCurrentFilter)()

### \[since 6.0\] KFileFilter KFileFilterCombo::defaultFilter() const {#defaultFilter}

Returns the default filter, used when an empty filter is set.

This function was introduced in Qt 6.0.

*See also* [setDefaultFilter](kfilefiltercombo.md#setDefaultFilter)

### \[signal\] void KFileFilterCombo::filterChanged() {#filterChanged}

This signal is emitted whenever the filter has been changed.

### \[since 6.0\] QList\<KFileFilter\> KFileFilterCombo::filters() const {#filters}

The current filters.

This is not necessarily the same as the list set by setFileFilters() since entries for "All files" and "All supported files" are added automatically as needed.

This function was introduced in Qt 6.0.

*See also* [setFilters](kfilefiltercombo.md#setFilters)()

### \[since 6.0\] void KFileFilterCombo::setCurrentFilter(const KFileFilter &*filter*) {#setCurrentFilter}

Sets the current filter. Filter must match one of the filter items passed before to this widget.

This function was introduced in Qt 6.0.

*See also* [currentFilter](kfilefiltercombo.md#currentFilter)()

### \[since 6.0\] void KFileFilterCombo::setDefaultFilter(const KFileFilter &*filter*) {#setDefaultFilter}

This method allows to set a default-filter, that is used when an empty filter is set. Make sure you call this before calling setFileFilter().

By default, this is set to match all files.

This function was introduced in Qt 6.0.

*See also* [defaultFilter](kfilefiltercombo.md#defaultFilter)

### \[since 6.0\] void KFileFilterCombo::setFilters(const QList\<KFileFilter\> &*filters*, const KFileFilter &*defaultFilter* = KFileFilter()) {#setFilters}

Sets the filters to be used.

`filters` each item in the list corresponds to one item in the combobox. Entries for "All files" and "All supported files" are added automatically as needed.

`defaultFilter` if not empty this will be the by default active filter

This function was introduced in Qt 6.0.

*See also* [filters](kfilefiltercombo.md#filters)()

### bool KFileFilterCombo::showsAllTypes() const {#showsAllTypes}

Returns true if the filter's first item is the list of all MIME types
