---
title: "KWidgetItemDelegate Class"
description: "This class allows to create item delegates embedding simple widgets to interact with items."
---

# KWidgetItemDelegate Class

This class allows to create item delegates embedding simple widgets to interact with items. [More...](#details)

- **Header:** `#include <KWidgetItemDelegate>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ItemViews)`  
  `target_link_libraries(mytarget PRIVATE KF6::ItemViews)`
- **Inherits:** [QAbstractItemDelegate](https://doc.qt.io/qt-6/qabstractitemdelegate.html)

[List of all members, including inherited members](kwidgetitemdelegate-members.md)

## Public Functions

- [KWidgetItemDelegate(QAbstractItemView \*itemView, QObject \*parent = nullptr)](#KWidgetItemDelegate)
- [QPersistentModelIndex focusedIndex() const](#focusedIndex)
- [QAbstractItemView \*itemView() const](#itemView)
- [void resetModel()](#resetModel)

## Protected Functions

- [QList\<QEvent::Type\> blockedEventTypes(QWidget \*widget) const](#blockedEventTypes)
- [QList\<QWidget \*\> createItemWidgets(const QModelIndex &index) const](#createItemWidgets)
- [void setBlockedEventTypes(QWidget \*widget, const QList\<QEvent::Type\> &types) const](#setBlockedEventTypes)
- [void updateItemWidgets(const QList\<QWidget \*\> &widgets, const QStyleOptionViewItem &option, const QPersistentModelIndex &index) const](#updateItemWidgets)

## Detailed Description {#details}

For instance you can add push buttons, line edits, etc. to your delegate and use them to modify the state of your model.

Porting from KF5 to KF6:

The signature of the virtual method [KWidgetItemDelegate::updateItemWidgets](kwidgetitemdelegate.md#updateItemWidgets)(const [QList](https://doc.qt.io/qt-6/qlist.html)\<[QWidget](https://doc.qt.io/qt-6/qwidget.html) \*\>, const [QStyleOptionViewItem](https://doc.qt.io/qt-6/qstyleoptionviewitem.html) &, const [QPersistentModelIndex](https://doc.qt.io/qt-6/qpersistentmodelindex.html) &) const was changed to ; [KWidgetItemDelegate::updateItemWidgets](kwidgetitemdelegate.md#updateItemWidgets)(const [QList](https://doc.qt.io/qt-6/qlist.html)\<[QWidget](https://doc.qt.io/qt-6/qwidget.html) \*\> &, const [QStyleOptionViewItem](https://doc.qt.io/qt-6/qstyleoptionviewitem.html) &, const [QPersistentModelIndex](https://doc.qt.io/qt-6/qpersistentmodelindex.html) &) const.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KWidgetItemDelegate::KWidgetItemDelegate(QAbstractItemView \**itemView*, QObject \**parent* = nullptr) {#KWidgetItemDelegate}

Creates a new ItemDelegate to be used with a given itemview.

`itemView` the item view the new delegate will monitor

`parent` the parent of this delegate

### \[protected\] QList\<QEvent::Type\> KWidgetItemDelegate::blockedEventTypes(QWidget \**widget*) const {#blockedEventTypes}

Retrieves the list of blocked event types for the given widget.

`widget` the specified widget.

Returns the list of blocked event types, can be empty if no events are blocked.

*See also* [setBlockedEventTypes](kwidgetitemdelegate.md#setBlockedEventTypes)()

### \[pure virtual protected\] QList\<QWidget \*\> KWidgetItemDelegate::createItemWidgets(const QModelIndex &*index*) const {#createItemWidgets}

Creates the list of widgets needed for an item.

> **Note:** No initialization of the widgets is supposed to happen here. The widgets will be initialized based on needs for a given item.

> **Note:** If you want to connect some widget signals to any slot, you should do it here.

`index` the index to create widgets for

Returns the list of newly created widgets which will be used to interact with an item.

*See also* [updateItemWidgets](kwidgetitemdelegate.md#updateItemWidgets)()

### QPersistentModelIndex KWidgetItemDelegate::focusedIndex() const {#focusedIndex}

Retrieves the currently focused index. An invalid index if none is focused.

### QAbstractItemView \*KWidgetItemDelegate::itemView() const {#itemView}

Retrieves the item view this delegate is monitoring.

### void KWidgetItemDelegate::resetModel() {#resetModel}

trigger a modelReset

### \[protected\] void KWidgetItemDelegate::setBlockedEventTypes(QWidget \**widget*, const QList\<QEvent::Type\> &*types*) const {#setBlockedEventTypes}

Sets the list of event `types` that a `widget` will block.

Blocked events are not passed to the view. This way you can prevent an item from being selected when a button is clicked for instance.

`widget` the widget which must block events

`types` the list of event types the widget must block

*See also* [blockedEventTypes](kwidgetitemdelegate.md#blockedEventTypes)()

### \[pure virtual protected\] void KWidgetItemDelegate::updateItemWidgets(const QList\<QWidget \*\> &*widgets*, const QStyleOptionViewItem &*option*, const QPersistentModelIndex &*index*) const {#updateItemWidgets}

Updates a list of widgets for its use inside of the delegate (painting or event handling).

> **Note:** All the positioning and sizing should be done in item coordinates.

> **Warning:** Do not make widget connections in here, since this method will be called very regularly.

`widgets` the widgets to update

`option` the current set of style options for the view.

`index` the model index of the item currently manipulated.
