---
title: "KExtendableItemDelegate Class"
description: "This delegate makes it possible to display an arbitrary QWidget (\"extender\") that spans all columns below a line of items."
---

# KExtendableItemDelegate Class

This delegate makes it possible to display an arbitrary [QWidget](https://doc.qt.io/qt-6/qwidget.html) ("extender") that spans all columns below a line of items. [More...](#details)

- **Header:** `#include <KExtendableItemDelegate>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ItemViews)`  
  `target_link_libraries(mytarget PRIVATE KF6::ItemViews)`
- **Inherits:** [QStyledItemDelegate](https://doc.qt.io/qt-6/qstyleditemdelegate.html)

[List of all members, including inherited members](kextendableitemdelegate-members.md)

## Public Types

- [enum KExtendableItemDelegate::auxDataRoles](#auxDataRoles-enum)

## Public Functions

- [KExtendableItemDelegate(QAbstractItemView \*parent)](#KExtendableItemDelegate)
- [void contractAll()](#contractAll)
- [void contractItem(const QModelIndex &index)](#contractItem)
- [void extendItem(QWidget \*extender, const QModelIndex &index)](#extendItem)
- [bool isExtended(const QModelIndex &index) const](#isExtended)
- [void updateExtenderGeometry(QWidget \*extender, const QStyleOptionViewItem &option, const QModelIndex &index) const](#updateExtenderGeometry)

## Signals

- [void extenderCreated(QWidget \*extender, const QModelIndex &index)](#extenderCreated)
- [void extenderDestroyed(QWidget \*extender, const QModelIndex &index)](#extenderDestroyed)

## Protected Functions

- [QPixmap contractPixmap()](#contractPixmap)
- [QPixmap extendPixmap()](#extendPixmap)
- [QRect extenderRect(QWidget \*extender, const QStyleOptionViewItem &option, const QModelIndex &index) const](#extenderRect)
- [void setContractPixmap(const QPixmap &pixmap)](#setContractPixmap)
- [void setExtendPixmap(const QPixmap &pixmap)](#setExtendPixmap)

## Detailed Description {#details}

The extender will logically belong to a column in the row above it.

It is your responsibility to devise a way to trigger extension and contraction of items, by calling [extendItem](kextendableitemdelegate.md#extendItem)() and [contractItem](kextendableitemdelegate.md#contractItem)(). You can e.g. reimplement itemActivated() and similar functions.

> **Warning:** [extendItem](kextendableitemdelegate.md#extendItem)() reparents the provided widget `extender` to the viewport of the itemview it belongs to. The `extender` is destroyed when you call [contractItem](kextendableitemdelegate.md#contractItem)() for the associated index. If you fail to do that and the associated item gets deleted you're in trouble. It remains as a visible artefact in your treeview. Additionally when closing your application you get an assertion failure from [KExtendableItemDelegate](kextendableitemdelegate.md). Make sure that you always call [contractItem](kextendableitemdelegate.md#contractItem) for indices before you delete them.

## Member Type Documentation {#member-type-documentation}

### enum KExtendableItemDelegate::auxDataRoles {#auxDataRoles-enum}

| Constant |   |
| --- | --- |
| `KExtendableItemDelegate::ShowExtensionIndicatorRole` | `Qt::UserRole + 200` |

## Member Function Documentation {#member-function-documentation}

### KExtendableItemDelegate::KExtendableItemDelegate(QAbstractItemView \**parent*) {#KExtendableItemDelegate}

Create a new [KExtendableItemDelegate](kextendableitemdelegate.md) that belongs to `parent`. In contrast to generic QAbstractItemDelegates, an instance of this class can only ever be the delegate for one instance of af [QAbstractItemView](https://doc.qt.io/qt-6/qabstractitemview.html) subclass.

### void KExtendableItemDelegate::contractAll() {#contractAll}

Close all extenders and delete all extender widgets.

### void KExtendableItemDelegate::contractItem(const QModelIndex &*index*) {#contractItem}

Remove the extender of item at `index` from the view. The extender widget will be deleted.

### \[protected\] QPixmap KExtendableItemDelegate::contractPixmap() {#contractPixmap}

Return the pixmap that is displayed to contract an item.

*See also* [setContractPixmap](kextendableitemdelegate.md#setContractPixmap)()

### void KExtendableItemDelegate::extendItem(QWidget \**extender*, const QModelIndex &*index*) {#extendItem}

Insert the `extender` for item at `index` into the view. If you need a parent for the extender at construction time, use the itemview's viewport(). The delegate takes ownership of the extender; the extender will also be reparented and resized to the viewport.

### \[protected\] QPixmap KExtendableItemDelegate::extendPixmap() {#extendPixmap}

Return the pixmap that is displayed to extend an item.

*See also* [setExtendPixmap](kextendableitemdelegate.md#setExtendPixmap)()

### \[signal\] void KExtendableItemDelegate::extenderCreated(QWidget \**extender*, const QModelIndex &*index*) {#extenderCreated}

This signal indicates that the item at `index` was extended with `extender`.

### \[signal\] void KExtendableItemDelegate::extenderDestroyed(QWidget \**extender*, const QModelIndex &*index*) {#extenderDestroyed}

This signal indicates that the `extender` belonging to `index` has emitted the [destroyed](https://doc.qt.io/qt-6/qobject.html#destroyed)() signal.

### \[protected\] QRect KExtendableItemDelegate::extenderRect(QWidget \**extender*, const QStyleOptionViewItem &*option*, const QModelIndex &*index*) const {#extenderRect}

Reimplement this function to fine-tune the position of the extender. `option.rect` will be a rectangle that is as wide as the viewport and as high as the usual item height plus the extender size hint's height. Its upper left corner will be at the upper left corner of the usual item. You can place the returned rectangle of this function anywhere inside that area.

### bool KExtendableItemDelegate::isExtended(const QModelIndex &*index*) const {#isExtended}

Return whether there is an extender that belongs to `index`.

### \[protected\] void KExtendableItemDelegate::setContractPixmap(const QPixmap &*pixmap*) {#setContractPixmap}

The pixmap that is displayed to contract an item. `pixmap` must have the same size as the pixmap in [setExtendPixmap](kextendableitemdelegate.md#setExtendPixmap).

*See also* [contractPixmap](kextendableitemdelegate.md#contractPixmap)()

### \[protected\] void KExtendableItemDelegate::setExtendPixmap(const QPixmap &*pixmap*) {#setExtendPixmap}

The pixmap that is displayed to extend an item. `pixmap` must have the same size as the pixmap in [setContractPixmap](kextendableitemdelegate.md#setContractPixmap).

*See also* [extendPixmap](kextendableitemdelegate.md#extendPixmap)()

### \[virtual\] void KExtendableItemDelegate::updateExtenderGeometry(QWidget \**extender*, const QStyleOptionViewItem &*option*, const QModelIndex &*index*) const {#updateExtenderGeometry}

Reimplement this function to adjust the internal geometry of the extender. The external geometry of the extender will be set by the delegate.
