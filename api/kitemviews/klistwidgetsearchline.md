---
title: "KListWidgetSearchLine Class"
description: "This class makes it easy to add a search line for filtering the items in a listwidget based on a simple text search."
---

# KListWidgetSearchLine Class

This class makes it easy to add a search line for filtering the items in a listwidget based on a simple text search. [More...](#details)

- **Header:** `#include <KListWidgetSearchLine>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ItemViews)`  
  `target_link_libraries(mytarget PRIVATE KF6::ItemViews)`
- **Inherits:** [QLineEdit](https://doc.qt.io/qt-6/qlineedit.html)

[List of all members, including inherited members](klistwidgetsearchline-members.md)

## Public Functions

- [KListWidgetSearchLine(QWidget \*parent = nullptr, QListWidget \*listWidget = nullptr)](#KListWidgetSearchLine)
- [Qt::CaseSensitivity caseSensitive() const](#caseSensitive)
- [QListWidget \*listWidget() const](#listWidget)

## Public Slots

- [void clear()](#clear)
- [void setCaseSensitivity(Qt::CaseSensitivity cs)](#setCaseSensitivity)
- [void setListWidget(QListWidget \*lv)](#setListWidget)
- [void updateSearch(const QString &s = QString())](#updateSearch)

## Protected Functions

- [bool itemMatches(const QListWidgetItem \*item, const QString &s) const](#itemMatches)

## Detailed Description {#details}

No changes to the application other than instantiating this class with an appropriate [QListWidget](https://doc.qt.io/qt-6/qlistwidget.html) should be needed.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KListWidgetSearchLine::KListWidgetSearchLine(QWidget \**parent* = nullptr, QListWidget \**listWidget* = nullptr) {#KListWidgetSearchLine}

Constructs a [KListWidgetSearchLine](klistwidgetsearchline.md) with `listWidget` being the [QListWidget](https://doc.qt.io/qt-6/qlistwidget.html) to be filtered.

If `listWidget` is null then the widget will be disabled until a [listWidget](klistwidgetsearchline.md#listWidget) is set with [setListWidget](klistwidgetsearchline.md#setListWidget)().

### Qt::CaseSensitivity KListWidgetSearchLine::caseSensitive() const {#caseSensitive}

Returns if the search is case sensitive.

This defaults to [Qt::CaseInsensitive](https://doc.qt.io/qt-6/qt.html#CaseSensitivity-enum).

*See also* [setCaseSensitivity](klistwidgetsearchline.md#setCaseSensitivity)()

### \[slot\] void KListWidgetSearchLine::clear() {#clear}

Clear line edit and empty hiddenItems, returning elements to [listWidget](klistwidgetsearchline.md#listWidget).

### \[virtual protected\] bool KListWidgetSearchLine::itemMatches(const QListWidgetItem \**item*, const QString &*s*) const {#itemMatches}

Returns true if `item` matches the search `s`.

This will be evaluated based on the value of [caseSensitive](klistwidgetsearchline.md#caseSensitive)().

This can be overridden in subclasses to implement more complicated matching schemes.

### QListWidget \*KListWidgetSearchLine::listWidget() const {#listWidget}

Returns the listWidget that is currently filtered by the search.

*See also* [setListWidget](klistwidgetsearchline.md#setListWidget)()

### \[slot\] void KListWidgetSearchLine::setCaseSensitivity(Qt::CaseSensitivity *cs*) {#setCaseSensitivity}

Make the search case sensitive or case insensitive.

*See also* [caseSensitive](klistwidgetsearchline.md#caseSensitive)()

### \[slot\] void KListWidgetSearchLine::setListWidget(QListWidget \**lv*) {#setListWidget}

Sets the [QListWidget](https://doc.qt.io/qt-6/qlistwidget.html) that is filtered by this search line.

If `lv` is null then the widget will be disabled.

*See also* [listWidget](klistwidgetsearchline.md#listWidget)()

### \[virtual slot\] void KListWidgetSearchLine::updateSearch(const QString &*s* = QString()) {#updateSearch}

Updates search to only make visible the items that match `s`.

If `s` is null then the line edit's text will be used.
