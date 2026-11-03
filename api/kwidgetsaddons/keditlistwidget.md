---
title: "KEditListWidget Class"
description: "An editable listbox."
---

# KEditListWidget Class

An editable listbox. [More...](#details)

- **Header:** `#include <KEditListWidget>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](keditlistwidget-members.md)

## Public Types

- [enum KEditListWidget::Button](#Button-enum)

## Properties

- [buttons : Buttons](#buttons-prop)
- [checkAtEntering : bool](#checkAtEntering-prop)
- [items : QStringList](#items-prop)

## Public Functions

- [KEditListWidget(QWidget \*parent = nullptr)](#KEditListWidget)
- [KEditListWidget(const KEditListWidget::CustomEditor &customEditor, QWidget \*parent = nullptr, bool checkAtEntering = false, KEditListWidget::Buttons buttons = All)](#KEditListWidget-1)
- [QPushButton \*addButton() const](#addButton)
- [KEditListWidget::Buttons buttons() const](#buttons)
- [bool checkAtEntering()](#checkAtEntering)
- [void clear()](#clear)
- [int count() const](#count)
- [int currentItem() const](#currentItem)
- [QString currentText() const](#currentText)
- [QPushButton \*downButton() const](#downButton)
- [void insertItem(const QString &text, int index = -1)](#insertItem)
- [void insertStringList(const QStringList &list, int index = -1)](#insertStringList)
- [QStringList items() const](#items)
- [QLineEdit \*lineEdit() const](#lineEdit)
- [QListView \*listView() const](#listView)
- [QPushButton \*removeButton() const](#removeButton)
- [void setButtons(KEditListWidget::Buttons buttons)](#setButtons)
- [void setCheckAtEntering(bool check)](#setCheckAtEntering)
- [void setCustomEditor(const KEditListWidget::CustomEditor &editor)](#setCustomEditor)
- [void setItems(const QStringList &items)](#setItems)
- [QString text(int index) const](#text)
- [QPushButton \*upButton() const](#upButton)

## Signals

- [void added(const QString &text)](#added)
- [void removed(const QString &text)](#removed)

## Detailed Description {#details}

This class provides an editable listbox, this means a listbox which is accompanied by a line edit to enter new items into the listbox and pushbuttons to add and remove items from the listbox and two buttons to move items up and down.

## Member Type Documentation {#member-type-documentation}

### enum KEditListWidget::Button {#Button-enum}

**flags KEditListWidget::Buttons**

Enumeration of the buttons, the listbox offers. Specify them in the constructor in the buttons parameter, or in [setButtons](keditlistwidget.md#setButtons).

| Constant |   |
| --- | --- |
| `KEditListWidget::Add` | `0x0001` |
| `KEditListWidget::Remove` | `0x0002` |
| `KEditListWidget::UpDown` | `0x0004` |
| `KEditListWidget::All` | `Add | Remove | UpDown` |

The `Buttons` type is a typedef for `QFlags<Button>. `It stores an OR combination of `Button` values.

## Property Documentation {#property-documentation}

### buttons : Buttons {#buttons-prop}

**Access functions:**

- `KEditListWidget::Buttons` **[buttons](keditlistwidget.md#buttons)**() const
- `void` **[setButtons](keditlistwidget.md#setButtons)**(`KEditListWidget::Buttons` *buttons*)

### checkAtEntering : bool {#checkAtEntering-prop}

**Access functions:**

- `bool` **[checkAtEntering](keditlistwidget.md#checkAtEntering)**()
- `void` **[setCheckAtEntering](keditlistwidget.md#setCheckAtEntering)**(`bool` *check*)

### items : QStringList {#items-prop}

**Access functions:**

- `QStringList` **[items](keditlistwidget.md#items)**() const
- `void` **[setItems](keditlistwidget.md#setItems)**(const `QStringList` &*items*)

**Notifier signal:**

- `void` **changed**()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KEditListWidget::KEditListWidget(QWidget \**parent* = nullptr) {#KEditListWidget}

Create an editable listbox.

### KEditListWidget::KEditListWidget(const KEditListWidget::CustomEditor &*customEditor*, QWidget \**parent* = nullptr, bool *checkAtEntering* = false, KEditListWidget::Buttons *buttons* = All) {#KEditListWidget-1}

Constructor which allows to use a custom editing widget instead of the standard [QLineEdit](https://doc.qt.io/qt-6/qlineedit.html) widget. E.g. you can use a KUrlRequester or a [QComboBox](https://doc.qt.io/qt-6/qcombobox.html) as input widget. The custom editor must consist of a lineedit and optionally another widget that is used as representation. A [QComboBox](https://doc.qt.io/qt-6/qcombobox.html) or a KUrlRequester have a [QLineEdit](https://doc.qt.io/qt-6/qlineedit.html) as child-widget for example, so the [QComboBox](https://doc.qt.io/qt-6/qcombobox.html) is used as the representation widget.

*See also* KUrlRequester::customEditor(), [setCustomEditor](keditlistwidget.md#setCustomEditor)

### QPushButton \*KEditListWidget::addButton() const {#addButton}

Returns a pointer to the Add button

### \[signal\] void KEditListWidget::added(const QString &*text*) {#added}

This signal is emitted when the user adds a new string to the list, the parameter is the added string.

### KEditListWidget::Buttons KEditListWidget::buttons() const {#buttons}

Returns which buttons are visible

> **Note:** Getter function for property [buttons](keditlistwidget.md#buttons-prop).

*See also* [setButtons](keditlistwidget.md#setButtons)()

### bool KEditListWidget::checkAtEntering() {#checkAtEntering}

Returns true if check at entering is enabled.

> **Note:** Getter function for property [checkAtEntering](keditlistwidget.md#checkAtEntering-prop).

*See also* [setCheckAtEntering](keditlistwidget.md#setCheckAtEntering)()

### void KEditListWidget::clear() {#clear}

Clears both the listbox and the line edit.

### int KEditListWidget::count() const {#count}

Returns the count of elements in the list

### int KEditListWidget::currentItem() const {#currentItem}

Returns the currently selected item

### QString KEditListWidget::currentText() const {#currentText}

Returns the currently selected item's text

### QPushButton \*KEditListWidget::downButton() const {#downButton}

Returns a pointer to the Down button

### void KEditListWidget::insertItem(const QString &*text*, int *index* = -1) {#insertItem}

Inserts a `text` element at the `index` position If `index` is negative, the element will be appended

### void KEditListWidget::insertStringList(const QStringList &*list*, int *index* = -1) {#insertStringList}

Inserts a `list` of elements from the `index` element If `index` is negative, the elements will be appended

### QStringList KEditListWidget::items() const {#items}

Returns a list with the text of all items in the listbox

> **Note:** Getter function for property [items](keditlistwidget.md#items-prop).

*See also* [setItems](keditlistwidget.md#setItems)()

### QLineEdit \*KEditListWidget::lineEdit() const {#lineEdit}

Returns a pointer to the embedded [QLineEdit](https://doc.qt.io/qt-6/qlineedit.html).

### QListView \*KEditListWidget::listView() const {#listView}

Returns a pointer to the embedded [QListView](https://doc.qt.io/qt-6/qlistview.html).

### QPushButton \*KEditListWidget::removeButton() const {#removeButton}

Returns a pointer to the Remove button

### \[signal\] void KEditListWidget::removed(const QString &*text*) {#removed}

This signal is emitted when the user removes a string from the list, the parameter is the removed string.

### void KEditListWidget::setButtons(KEditListWidget::Buttons *buttons*) {#setButtons}

Specifies which `buttons` are visible

> **Note:** Setter function for property [buttons](keditlistwidget.md#buttons-prop).

*See also* [buttons](keditlistwidget.md#buttons)()

### void KEditListWidget::setCheckAtEntering(bool *check*) {#setCheckAtEntering}

If `check` is true, after every character you type in the line edit [KEditListWidget](keditlistwidget.md) will enable or disable the Add-button, depending whether the current content of the line edit is already in the listbox. Maybe this can become a performance hit with large lists on slow machines.

If `check` is false, it will be checked if you press the Add-button. It is not possible to enter items twice into the listbox. Default is false.

> **Note:** Setter function for property [checkAtEntering](keditlistwidget.md#checkAtEntering-prop).

*See also* [checkAtEntering](keditlistwidget.md#checkAtEntering)()

### void KEditListWidget::setCustomEditor(const KEditListWidget::CustomEditor &*editor*) {#setCustomEditor}

Allows to use a custom editing widget instead of the standard [QLineEdit](https://doc.qt.io/qt-6/qlineedit.html) widget. E.g. you can use a KUrlRequester or a [QComboBox](https://doc.qt.io/qt-6/qcombobox.html) as input widget. The custom editor must consist of a lineedit and optionally another widget that is used as representation. A [QComboBox](https://doc.qt.io/qt-6/qcombobox.html) or a KUrlRequester have a [QLineEdit](https://doc.qt.io/qt-6/qlineedit.html) as child-widget for example, so the [QComboBox](https://doc.qt.io/qt-6/qcombobox.html) is used as the representation widget.

### void KEditListWidget::setItems(const QStringList &*items*) {#setItems}

Clears the listbox and sets the contents to `items`

> **Note:** Setter function for property [items](keditlistwidget.md#items-prop).

*See also* [items](keditlistwidget.md#items)()

### QString KEditListWidget::text(int *index*) const {#text}

Returns the text at the `index` position

### QPushButton \*KEditListWidget::upButton() const {#upButton}

Returns a pointer to the Up button
