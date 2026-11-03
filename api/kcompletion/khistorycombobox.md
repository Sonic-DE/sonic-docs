---
title: "KHistoryComboBox Class"
description: "A combobox for offering a history and completion."
---

# KHistoryComboBox Class

A combobox for offering a history and completion. [More...](#details)

- **Header:** `#include <KHistoryComboBox>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Completion)`  
  `target_link_libraries(mytarget PRIVATE KF6::Completion)`
- **Inherits:** [KComboBox](kcombobox.md)

[List of all members, including inherited members](khistorycombobox-members.md)

## Properties

- [historyItems : QStringList](#historyItems-prop)

## Public Functions

- [KHistoryComboBox(QWidget \*parent = nullptr)](#KHistoryComboBox)
- [KHistoryComboBox(bool useCompletion, QWidget \*parent = nullptr)](#KHistoryComboBox-1)
- [QStringList historyItems() const](#historyItems)
- [bool removeFromHistory(const QString &item)](#removeFromHistory)
- [void setHistoryItems(const QStringList &items)](#setHistoryItems)
- [void setHistoryItems(const QStringList &items, bool setCompletionList)](#setHistoryItems-1)
- [void setIconProvider(std::function\<QIcon (const QString &)\> providerFunction)](#setIconProvider)

## Public Slots

- [void addToHistory(const QString &item)](#addToHistory)
- [void clearHistory()](#clearHistory)
- [void reset()](#reset)

## Signals

- [void cleared()](#cleared)

## Protected Functions

- [void insertItems(const QStringList &items)](#insertItems)
- [bool useCompletion() const](#useCompletion)

## Detailed Description {#details}

A combobox which implements a history like a unix shell. You can navigate through all the items by using the Up or Down arrows (configurable of course). Additionally, weighted completion is available. So you should load and save the completion list to preserve the weighting between sessions.

[KHistoryComboBox](khistorycombobox.md) obeys the HISTCONTROL environment variable to determine whether duplicates in the history should be tolerated in [addToHistory](khistorycombobox.md#addToHistory)() or not. During construction of [KHistoryComboBox](khistorycombobox.md), duplicates will be disabled when HISTCONTROL is set to "ignoredups" or "ignoreboth". Otherwise, duplicates are enabled by default.

## Property Documentation {#property-documentation}

### historyItems : QStringList {#historyItems-prop}

**Access functions:**

- `QStringList` **[historyItems](khistorycombobox.md#historyItems)**() const
- `void` **[setHistoryItems](khistorycombobox.md#setHistoryItems)**(const `QStringList` &*items*)
- `void` **[setHistoryItems](khistorycombobox.md#setHistoryItems-1)**(const `QStringList` &*items*, `bool` *setCompletionList*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KHistoryComboBox::KHistoryComboBox(QWidget \**parent* = nullptr) {#KHistoryComboBox}

Constructs a "read-write" combobox. A read-only history combobox doesn't make much sense, so it is only available as read-write. Completion will be used automatically for the items in the combo.

The insertion-policy is set to NoInsert, you have to add the items yourself via the slot [addToHistory](khistorycombobox.md#addToHistory). If you want every item added, use

```cpp
connect( combo, SIGNAL( activated( const QString& )),
         combo, SLOT( addToHistory( const QString& )));
```

Use [QComboBox::setMaxCount](https://doc.qt.io/qt-6/qcombobox.html#maxCount-prop)() to limit the history.

`parent` the parent object of this widget.

### \[explicit\] KHistoryComboBox::KHistoryComboBox(bool *useCompletion*, QWidget \**parent* = nullptr) {#KHistoryComboBox-1}

Same as the previous constructor, but additionally has the option to specify whether you want to let [KHistoryComboBox](khistorycombobox.md) handle completion or not. If set to `true`, [KHistoryComboBox](khistorycombobox.md) will sync the completion to the contents of the combobox.

### \[slot\] void KHistoryComboBox::addToHistory(const QString &*item*) {#addToHistory}

Adds an item to the end of the history list and to the completion list. If [maxCount](https://doc.qt.io/qt-6/qcombobox.html#maxCount-prop)() is reached, the first item of the list will be removed.

If the last inserted item is the same as `item`, it will not be inserted again.

If [duplicatesEnabled](https://doc.qt.io/qt-6/qcombobox.html#duplicatesEnabled-prop)() is false, any equal existing item will be removed before `item` is added.

> **Note:** By using this method and not the Q and [KComboBox](kcombobox.md) [insertItem](https://doc.qt.io/qt-6/qcombobox.html#insertItem)() methods, you make sure that the combobox stays in sync with the completion. It would be annoying if completion would give an item not in the combobox, and vice versa.

*See also* [removeFromHistory](khistorycombobox.md#removeFromHistory), [QComboBox::setDuplicatesEnabled](https://doc.qt.io/qt-6/qcombobox.html#duplicatesEnabled-prop)

### \[slot\] void KHistoryComboBox::clearHistory() {#clearHistory}

Clears the history and the completion list.

### \[signal\] void KHistoryComboBox::cleared() {#cleared}

Emitted when the history was cleared by the entry in the popup menu.

### QStringList KHistoryComboBox::historyItems() const {#historyItems}

Returns the list of history items. Empty, when this is not a read-write combobox.

> **Note:** Getter function for property [historyItems](khistorycombobox.md#historyItems-prop).

*See also* [setHistoryItems](khistorycombobox.md#setHistoryItems)

### \[protected\] void KHistoryComboBox::insertItems(const QStringList &*items*) {#insertItems}

Inserts `items` into the combo, honoring [setIconProvider](khistorycombobox.md#setIconProvider)() Does not update the completionObject.

> **Note:** [duplicatesEnabled](https://doc.qt.io/qt-6/qcombobox.html#duplicatesEnabled-prop)() is not honored here.

Called from [setHistoryItems](khistorycombobox.md#setHistoryItems)()

### bool KHistoryComboBox::removeFromHistory(const QString &*item*) {#removeFromHistory}

Removes all items named `item`.

Returns `true` if at least one item was removed.

*See also* [addToHistory](khistorycombobox.md#addToHistory)

### \[slot\] void KHistoryComboBox::reset() {#reset}

Resets the current position of the up/down history. Call this when you manually call [setCurrentItem](kcombobox.md#setCurrentItem)() or clearEdit().

### void KHistoryComboBox::setHistoryItems(const QStringList &*items*) {#setHistoryItems}

Inserts `items` into the combobox. `items` might get truncated if it is longer than [maxCount](https://doc.qt.io/qt-6/qcombobox.html#maxCount-prop)()

> **Note:** Setter function for property [historyItems](khistorycombobox.md#historyItems-prop).

*See also* [historyItems](khistorycombobox.md#historyItems)

### void KHistoryComboBox::setHistoryItems(const QStringList &*items*, bool *setCompletionList*) {#setHistoryItems-1}

Inserts `items` into the combobox. `items` might get truncated if it is longer than [maxCount](https://doc.qt.io/qt-6/qcombobox.html#maxCount-prop)()

Set `setCompletionList` to true, if you don't have a list of completions. This tells [KHistoryComboBox](khistorycombobox.md) to use all the items for the completion object as well. You won't have the benefit of weighted completion though, so normally you should do something like

```cpp
KConfigGroup config(KSharedConfig::openConfig(), "somegroup");

// load the history and completion list after creating the history combo
QStringList list;
list = config.readEntry("Completion list", QStringList());
combo->completionObject()->setItems(list);
list = config.readEntry("History list", QStringList());
combo->setHistoryItems(list);

[...]

// save the history and completion list when the history combo is
// destroyed
QStringList list;
KConfigGroup config(KSharedConfig::openConfig(), "somegroup");
list = combo->completionObject()->items();
config.writeEntry("Completion list", list);
list = combo->historyItems();
config.writeEntry("History list", list);
```

Be sure to use different names for saving with KConfig if you have more than one [KHistoryComboBox](khistorycombobox.md).

> **Note:** When setCompletionList is true, the items are inserted into the [KCompletion](kcompletion-module.md) object with mode [KCompletion::Insertion](kcompletion.md#CompOrder-enum) and the mode is set to [KCompletion::Weighted](kcompletion.md#CompOrder-enum) afterwards.

> **Note:** Setter function for property [historyItems](khistorycombobox.md#historyItems-prop).

*See also* [historyItems](khistorycombobox.md#historyItems), [KComboBox::completionObject](kcompletionbase.md#completionObject), [KCompletion::setItems](kcompletion-index.md), [KCompletion::items](kcompletion-index.md)

### void KHistoryComboBox::setIconProvider(std::function\<QIcon (const QString &)\> *providerFunction*) {#setIconProvider}

Sets an icon provider, so that items in the combobox can have an icon.

The provider is a function that takes a [QString](https://doc.qt.io/qt-6/qstring.html) and returns a [QIcon](https://doc.qt.io/qt-6/qicon.html)

### \[protected\] bool KHistoryComboBox::useCompletion() const {#useCompletion}

Returns if we can modify the completion object or not.
