---
title: "KTreeWidgetSearchLine Class"
description: "This class makes it easy to add a search line for filtering the items in listviews based on a simple text search."
---

# KTreeWidgetSearchLine Class

This class makes it easy to add a search line for filtering the items in listviews based on a simple text search. [More...](#details)

- **Header:** `#include <KTreeWidgetSearchLine>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ItemViews)`  
  `target_link_libraries(mytarget PRIVATE KF6::ItemViews)`
- **Inherits:** [QLineEdit](https://doc.qt.io/qt-6/qlineedit.html)

[List of all members, including inherited members](ktreewidgetsearchline-members.md)

## Properties

- [caseSensitity : Qt::CaseSensitivity](#caseSensitity-prop)
- [keepParentsVisible : bool](#keepParentsVisible-prop)

## Public Functions

- [KTreeWidgetSearchLine(QWidget \*parent = nullptr, QTreeWidget \*treeWidget = nullptr)](#KTreeWidgetSearchLine)
- [KTreeWidgetSearchLine(QWidget \*parent, const QList\<QTreeWidget \*\> &treeWidgets)](#KTreeWidgetSearchLine-1)
- [Qt::CaseSensitivity caseSensitivity() const](#caseSensitivity)
- [bool keepParentsVisible() const](#keepParentsVisible)
- [QList\<int\> searchColumns() const](#searchColumns)
- [QTreeWidget \*treeWidget() const](#treeWidget)
- [QList\<QTreeWidget \*\> treeWidgets() const](#treeWidgets)

## Public Slots

- [void addTreeWidget(QTreeWidget \*treeWidget)](#addTreeWidget)
- [void removeTreeWidget(QTreeWidget \*treeWidget)](#removeTreeWidget)
- [void setCaseSensitivity(Qt::CaseSensitivity caseSensitivity)](#setCaseSensitivity)
- [void setKeepParentsVisible(bool value)](#setKeepParentsVisible)
- [void setSearchColumns(const QList\<int\> &columns)](#setSearchColumns)
- [void setTreeWidget(QTreeWidget \*treeWidget)](#setTreeWidget)
- [void setTreeWidgets(const QList\<QTreeWidget \*\> &treeWidgets)](#setTreeWidgets)
- [void updateSearch(const QString &pattern = QString())](#updateSearch-1)

## Signals

- [void caseSensitivityChanged(Qt::CaseSensitivity caseSensitivity)](#caseSensitivityChanged)
- [void hiddenChanged(QTreeWidgetItem \*, bool)](#hiddenChanged)
- [void keepParentsVisibleChanged(bool keepParentsVisible)](#keepParentsVisibleChanged)
- [void searchUpdated(const QString &searchString)](#searchUpdated)

## Protected Functions

- [bool canChooseColumnsCheck()](#canChooseColumnsCheck)
- [void connectTreeWidget(QTreeWidget \*)](#connectTreeWidget)
- [void disconnectTreeWidget(QTreeWidget \*)](#disconnectTreeWidget)
- [bool itemMatches(const QTreeWidgetItem \*item, const QString &pattern) const](#itemMatches)
- [void updateSearch(QTreeWidget \*treeWidget)](#updateSearch)

## Detailed Description {#details}

No changes to the application other than instantiating this class with appropriate QTreeWidgets should be needed.

## Property Documentation {#property-documentation}

### caseSensitity : Qt::CaseSensitivity {#caseSensitity-prop}

**Access functions:**

- `Qt::CaseSensitivity` **[caseSensitivity](ktreewidgetsearchline.md#caseSensitivity)**() const
- `void` **[setCaseSensitivity](ktreewidgetsearchline.md#setCaseSensitivity)**(`Qt::CaseSensitivity` *caseSensitivity*)

**Notifier signal:**

- `void` **[caseSensitivityChanged](ktreewidgetsearchline.md#caseSensitivityChanged)**(`Qt::CaseSensitivity` *caseSensitivity*)

### keepParentsVisible : bool {#keepParentsVisible-prop}

**Access functions:**

- `bool` **[keepParentsVisible](ktreewidgetsearchline.md#keepParentsVisible)**() const
- `void` **[setKeepParentsVisible](ktreewidgetsearchline.md#setKeepParentsVisible)**(`bool` *value*)

**Notifier signal:**

- `void` **[keepParentsVisibleChanged](ktreewidgetsearchline.md#keepParentsVisibleChanged)**(`bool` *keepParentsVisible*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KTreeWidgetSearchLine::KTreeWidgetSearchLine(QWidget \**parent* = nullptr, QTreeWidget \**treeWidget* = nullptr) {#KTreeWidgetSearchLine}

Constructs a [KTreeWidgetSearchLine](ktreewidgetsearchline.md) with `treeWidget` being the [QTreeWidget](https://doc.qt.io/qt-6/qtreewidget.html) to be filtered.

If `treeWidget` is null then the widget will be disabled until listviews are set with [setTreeWidget](ktreewidgetsearchline.md#setTreeWidget)(), [setTreeWidgets](ktreewidgetsearchline.md#setTreeWidgets)() or added with [addTreeWidget](ktreewidgetsearchline.md#addTreeWidget)().

### KTreeWidgetSearchLine::KTreeWidgetSearchLine(QWidget \**parent*, const QList\<QTreeWidget \*\> &*treeWidgets*) {#KTreeWidgetSearchLine-1}

Constructs a [KTreeWidgetSearchLine](ktreewidgetsearchline.md) with `treeWidgets` being the list of pointers to QTreeWidgets to be filtered.

If `treeWidgets` is empty then the widget will be disabled until listviews are set with [setTreeWidget](ktreewidgetsearchline.md#setTreeWidget)(), [setTreeWidgets](ktreewidgetsearchline.md#setTreeWidgets)() or added with [addTreeWidget](ktreewidgetsearchline.md#addTreeWidget)().

### \[slot\] void KTreeWidgetSearchLine::addTreeWidget(QTreeWidget \**treeWidget*) {#addTreeWidget}

Adds a [QTreeWidget](https://doc.qt.io/qt-6/qtreewidget.html) to the list of listviews filtered by this search line. If `treeWidget` is null then the widget will be disabled.

*See also* [treeWidget](ktreewidgetsearchline.md#treeWidget)(), [setTreeWidgets](ktreewidgetsearchline.md#setTreeWidgets)(), [removeTreeWidget](ktreewidgetsearchline.md#removeTreeWidget)()

### \[virtual protected\] bool KTreeWidgetSearchLine::canChooseColumnsCheck() {#canChooseColumnsCheck}

Checks columns in all listviews and decides whether choosing columns to filter on makes any sense.

Returns false if either of the following is true: \* there are no listviews connected, \* the listviews have different numbers of columns, \* the listviews have only one column, \* the listviews differ in column labels.

Otherwise it returns true.

*See also* [setSearchColumns](ktreewidgetsearchline.md#setSearchColumns)()

### Qt::CaseSensitivity KTreeWidgetSearchLine::caseSensitivity() const {#caseSensitivity}

Returns true if the search is case sensitive. This defaults to false.

> **Note:** Getter function for property [caseSensitity](ktreewidgetsearchline.md#caseSensitity-prop).

*See also* [setCaseSensitivity](ktreewidgetsearchline.md#setCaseSensitivity)()

### \[signal\] void KTreeWidgetSearchLine::caseSensitivityChanged(Qt::CaseSensitivity *caseSensitivity*) {#caseSensitivityChanged}

> **Note:** Notifier signal for property [caseSensitity](ktreewidgetsearchline.md#caseSensitity-prop).

### \[virtual protected\] void KTreeWidgetSearchLine::connectTreeWidget(*QTreeWidget \**) {#connectTreeWidget}

Connects signals of this listview to the appropriate slots of the search line.

### \[virtual protected\] void KTreeWidgetSearchLine::disconnectTreeWidget(*QTreeWidget \**) {#disconnectTreeWidget}

Disconnects signals of a listviews from the search line.

### \[signal\] void KTreeWidgetSearchLine::hiddenChanged(*QTreeWidgetItem \**, *bool*) {#hiddenChanged}

This signal is emitted whenever an item gets hidden or unhidden due to it not matching or matching the search string.

### \[virtual protected\] bool KTreeWidgetSearchLine::itemMatches(const QTreeWidgetItem \**item*, const QString &*pattern*) const {#itemMatches}

Returns true if `item` matches the search `pattern`. This will be evaluated based on the value of caseSensitive(). This can be overridden in subclasses to implement more complicated matching schemes.

### bool KTreeWidgetSearchLine::keepParentsVisible() const {#keepParentsVisible}

If this is true (the default) then the parents of matched items will also be shown.

> **Note:** Getter function for property [keepParentsVisible](ktreewidgetsearchline.md#keepParentsVisible-prop).

*See also* [setKeepParentsVisible](ktreewidgetsearchline.md#setKeepParentsVisible)()

### \[signal\] void KTreeWidgetSearchLine::keepParentsVisibleChanged(bool *keepParentsVisible*) {#keepParentsVisibleChanged}

> **Note:** Notifier signal for property [keepParentsVisible](ktreewidgetsearchline.md#keepParentsVisible-prop).

### \[slot\] void KTreeWidgetSearchLine::removeTreeWidget(QTreeWidget \**treeWidget*) {#removeTreeWidget}

Removes a [QTreeWidget](https://doc.qt.io/qt-6/qtreewidget.html) from the list of listviews filtered by this search line. Does nothing if `treeWidget` is 0 or is not filtered by the quick search line.

*See also* [setTreeWidgets](ktreewidgetsearchline.md#setTreeWidgets)(), [addTreeWidget](ktreewidgetsearchline.md#addTreeWidget)()

### QList\<int\> KTreeWidgetSearchLine::searchColumns() const {#searchColumns}

Returns the current list of columns that will be searched. If the returned list is empty all visible columns will be searched.

*See also* [setSearchColumns](ktreewidgetsearchline.md#setSearchColumns)

### \[signal\] void KTreeWidgetSearchLine::searchUpdated(const QString &*searchString*) {#searchUpdated}

This signal is emitted when user finished entering filter text or when he made a pause long enough, after the [QTreeWidget](https://doc.qt.io/qt-6/qtreewidget.html) items got filtered

`searchString` is the text currently entered by the user

### \[slot\] void KTreeWidgetSearchLine::setCaseSensitivity(Qt::CaseSensitivity *caseSensitivity*) {#setCaseSensitivity}

Make the search case sensitive or case insensitive.

> **Note:** Setter function for property [caseSensitity](ktreewidgetsearchline.md#caseSensitity-prop).

*See also* [caseSensitivity](ktreewidgetsearchline.md#caseSensitivity)()

### \[slot\] void KTreeWidgetSearchLine::setKeepParentsVisible(bool *value*) {#setKeepParentsVisible}

When a search is active on a list that's organized into a tree view if a parent or ancesestor of an item is does not match the search then it will be hidden and as such so too will any children that match.

If this is set to true (the default) then the parents of matching items will be shown.

> **Warning:** setKeepParentsVisible(true) does not have the expected effect on items being added to or removed from the view while a search is active. When a new search starts afterwards the behavior will be normal.

> **Note:** Setter function for property [keepParentsVisible](ktreewidgetsearchline.md#keepParentsVisible-prop).

*See also* [keepParentsVisible](ktreewidgetsearchline.md#keepParentsVisible)

### \[slot\] void KTreeWidgetSearchLine::setSearchColumns(const QList\<int\> &*columns*) {#setSearchColumns}

Sets the list of columns to be searched. The default is to search all, visible columns which can be restored by passing `columns` as an empty list. If listviews to be filtered have different numbers or labels of columns this method has no effect.

*See also* [searchColumns](ktreewidgetsearchline.md#searchColumns)

### \[slot\] void KTreeWidgetSearchLine::setTreeWidget(QTreeWidget \**treeWidget*) {#setTreeWidget}

Sets the [QTreeWidget](https://doc.qt.io/qt-6/qtreewidget.html) that is filtered by this search line, replacing any previously filtered listviews. If `treeWidget` is null then the widget will be disabled.

*See also* [treeWidget](ktreewidgetsearchline.md#treeWidget)(), [setTreeWidgets](ktreewidgetsearchline.md#setTreeWidgets)()

### \[slot\] void KTreeWidgetSearchLine::setTreeWidgets(const QList\<QTreeWidget \*\> &*treeWidgets*) {#setTreeWidgets}

Sets QTreeWidgets that are filtered by this search line, replacing any previously filtered listviews. If `treeWidgets` is empty then the widget will be disabled.

*See also* [treeWidgets](ktreewidgetsearchline.md#treeWidgets)(), [addTreeWidget](ktreewidgetsearchline.md#addTreeWidget)(), [setTreeWidget](ktreewidgetsearchline.md#setTreeWidget)()

### QTreeWidget \*KTreeWidgetSearchLine::treeWidget() const {#treeWidget}

Returns the listview that is currently filtered by the search. If there are multiple listviews filtered, it returns 0.

*See also* [setTreeWidget](ktreewidgetsearchline.md#setTreeWidget)(), [treeWidgets](ktreewidgetsearchline.md#treeWidgets)()

### QList\<QTreeWidget \*\> KTreeWidgetSearchLine::treeWidgets() const {#treeWidgets}

Returns the list of pointers to listviews that are currently filtered by the search.

*See also* [setTreeWidgets](ktreewidgetsearchline.md#setTreeWidgets)(), [addTreeWidget](ktreewidgetsearchline.md#addTreeWidget)(), [treeWidget](ktreewidgetsearchline.md#treeWidget)()

### \[virtual protected\] void KTreeWidgetSearchLine::updateSearch(QTreeWidget \**treeWidget*) {#updateSearch}

Updates search to only make visible appropriate items in `treeWidget`.

If `treeWidget` is null then nothing is done.

### \[virtual slot\] void KTreeWidgetSearchLine::updateSearch(const QString &*pattern* = QString()) {#updateSearch-1}

Updates search to only make visible the items that match `pattern`. If `s` is null then the line edit's text will be used.

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kTreeWidgetSearchLine, qOverload<const QString &>(&KTreeWidgetSearchLine::updateSearch));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kTreeWidgetSearchLine, [receiver = kTreeWidgetSearchLine](const QString &pattern) { receiver->updateSearch(pattern); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).
