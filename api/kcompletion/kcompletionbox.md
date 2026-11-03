---
title: "KCompletionBox Class"
description: "A helper widget for \"completion-widgets\" (KLineEdit, KComboBox))."
---

# KCompletionBox Class

A helper widget for "completion-widgets" ([KLineEdit](klineedit.md), [KComboBox](kcombobox.md))). [More...](#details)

- **Header:** `#include <KCompletionBox>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Completion)`  
  `target_link_libraries(mytarget PRIVATE KF6::Completion)`
- **Inherits:** [QListWidget](https://doc.qt.io/qt-6/qlistwidget.html)

[List of all members, including inherited members](kcompletionbox-members.md)

## Properties

- [activateOnSelect : bool](#activateOnSelect-prop)
- [cancelledText : QString](#cancelledText-prop)
- [isTabHandling : bool](#isTabHandling-prop)

## Public Functions

- [KCompletionBox(QWidget \*parent = nullptr)](#KCompletionBox)
- [bool activateOnSelect() const](#activateOnSelect)
- [QString cancelledText() const](#cancelledText)
- [bool isTabHandling() const](#isTabHandling)
- [QStringList items() const](#items)

## Public Slots

- [void down()](#down)
- [void end()](#end)
- [void home()](#home)
- [void insertItems(const QStringList &items, int index = -1)](#insertItems)
- [void pageDown()](#pageDown)
- [void pageUp()](#pageUp)
- [void popup()](#popup)
- [void setActivateOnSelect(bool doEmit)](#setActivateOnSelect)
- [void setCancelledText(const QString &text)](#setCancelledText)
- [void setItems(const QStringList &items)](#setItems)
- [void setTabHandling(bool enable)](#setTabHandling)
- [void setVisible(bool visible)](#setVisible)
- [void slotActivated(QListWidgetItem \*)](#slotActivated)
- [void up()](#up)

## Signals

- [void textActivated(const QString &text)](#textActivated)
- [void userCancelled(const QString &)](#userCancelled)

## Protected Functions

- [QRect calculateGeometry() const](#calculateGeometry)
- [QPoint globalPositionHint() const](#globalPositionHint)
- [void resizeAndReposition()](#resizeAndReposition)

## Detailed Description {#details}

A little utility class for "completion-widgets", like [KLineEdit](klineedit.md) or [KComboBox](kcombobox.md). [KCompletionBox](kcompletionbox.md) is a listbox, displayed as a rectangle without any window decoration, usually directly under the lineedit or combobox. It is filled with all possible matches for a completion, so the user can select the one he wants.

It is used when [KCompletion::CompletionMode](kcompletion.md#CompletionMode-enum) == CompletionPopup or CompletionPopupAuto.

## Property Documentation {#property-documentation}

### activateOnSelect : bool {#activateOnSelect-prop}

**Access functions:**

- `bool` **[activateOnSelect](kcompletionbox.md#activateOnSelect)**() const
- `void` **[setActivateOnSelect](kcompletionbox.md#setActivateOnSelect)**(`bool` *doEmit*)

### cancelledText : QString {#cancelledText-prop}

**Access functions:**

- `QString` **[cancelledText](kcompletionbox.md#cancelledText)**() const
- `void` **[setCancelledText](kcompletionbox.md#setCancelledText)**(const `QString` &*text*)

### isTabHandling : bool {#isTabHandling-prop}

**Access functions:**

- `bool` **[isTabHandling](kcompletionbox.md#isTabHandling)**() const
- `void` **[setTabHandling](kcompletionbox.md#setTabHandling)**(`bool` *enable*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KCompletionBox::KCompletionBox(QWidget \**parent* = nullptr) {#KCompletionBox}

Constructs a [KCompletionBox](kcompletionbox.md).

The `parent` widget is used to give the focus back when pressing the up-button on the very first item.

### bool KCompletionBox::activateOnSelect() const {#activateOnSelect}

Returns `true` if selecting an item results in the emission of the selected() signal.

> **Note:** Getter function for property [activateOnSelect](kcompletionbox.md#activateOnSelect-prop).

*See also* [setActivateOnSelect](kcompletionbox.md#setActivateOnSelect)()

### \[protected\] QRect KCompletionBox::calculateGeometry() const {#calculateGeometry}

This calculates the size of the dropdown and the relative position of the top left corner with respect to the parent widget. This matches the geometry and position normally used by K/[QComboBox](https://doc.qt.io/qt-6/qcombobox.html) when used with one.

### QString KCompletionBox::cancelledText() const {#cancelledText}

Returns the text set via [setCancelledText](kcompletionbox.md#setCancelledText)() or QString().

> **Note:** Getter function for property [cancelledText](kcompletionbox.md#cancelledText-prop).

*See also* [setCancelledText](kcompletionbox.md#setCancelledText)()

### \[slot\] void KCompletionBox::down() {#down}

Moves the selection one line down or select the first item if nothing is selected yet.

### \[slot\] void KCompletionBox::end() {#end}

Moves the selection down to the last item.

### \[virtual protected\] QPoint KCompletionBox::globalPositionHint() const {#globalPositionHint}

The preferred global coordinate at which the completion box's top left corner should be positioned.

### \[slot\] void KCompletionBox::home() {#home}

Moves the selection up to the first item.

### \[slot\] void KCompletionBox::insertItems(const QStringList &*items*, int *index* = -1) {#insertItems}

Inserts `items` into the box. Does not clear the items before. `index` determines at which position `items` will be inserted. (defaults to appending them at the end)

### bool KCompletionBox::isTabHandling() const {#isTabHandling}

Returns `true` if this widget is handling Tab-key events to traverse the items in the dropdown list, otherwise false.

Default is `true`.

> **Note:** Getter function for property [isTabHandling](kcompletionbox.md#isTabHandling-prop).

*See also* [setTabHandling](kcompletionbox.md#setTabHandling)

### QStringList KCompletionBox::items() const {#items}

Returns a list of all items currently in the box.

*See also* [setItems](kcompletionbox.md#setItems)()

### \[slot\] void KCompletionBox::pageDown() {#pageDown}

Moves the selection one page down.

### \[slot\] void KCompletionBox::pageUp() {#pageUp}

Moves the selection one page up.

### \[virtual slot\] void KCompletionBox::popup() {#popup}

Adjusts the size of the box to fit the width of the parent given in the constructor and pops it up at the most appropriate place, relative to the parent.

Depending on the screensize and the position of the parent, this may be a different place, however the default is to pop it up and the lower left corner of the parent.

Make sure to [hide](https://doc.qt.io/qt-6/qwidget.html#hide)() the box when appropriate.

### \[protected\] void KCompletionBox::resizeAndReposition() {#resizeAndReposition}

This properly resizes and repositions the listbox.

### \[slot\] void KCompletionBox::setActivateOnSelect(bool *doEmit*) {#setActivateOnSelect}

Set whether or not the selected signal should be emitted when an item is selected. By default the selected() signal is emitted.

`doEmit` false if the signal should not be emitted.

> **Note:** Setter function for property [activateOnSelect](kcompletionbox.md#activateOnSelect-prop).

*See also* [activateOnSelect](kcompletionbox.md#activateOnSelect)()

### \[slot\] void KCompletionBox::setCancelledText(const QString &*text*) {#setCancelledText}

Sets the text to be emitted if the user chooses not to pick from the available matches.

If the cancelled text is not set through this function, the [userCancelled](kcompletionbox.md#userCancelled) signal will not be emitted.

`text` the text to be emitted if the user cancels this box

> **Note:** Setter function for property [cancelledText](kcompletionbox.md#cancelledText-prop).

*See also* [cancelledText](kcompletionbox.md#cancelledText)(), [userCancelled](kcompletionbox.md#userCancelled)( const QString& )

### \[slot\] void KCompletionBox::setItems(const QStringList &*items*) {#setItems}

Clears the box and inserts `items`.

*See also* [items](kcompletionbox.md#items)()

### \[slot\] void KCompletionBox::setTabHandling(bool *enable*) {#setTabHandling}

Makes this widget (when visible) capture Tab-key events to traverse the items in the dropdown list (Tab goes down, Shift+Tab goes up).

On by default, but should be turned off when used in combination with KUrlCompletion. When off, [KLineEdit](klineedit.md) handles Tab itself, making it select the current item from the completion box, which is particularly useful when using KUrlCompletion.

> **Note:** Setter function for property [isTabHandling](kcompletionbox.md#isTabHandling-prop).

*See also* [isTabHandling](kcompletionbox.md#isTabHandling)

### \[override virtual slot\] void KCompletionBox::setVisible(bool *visible*) {#setVisible}

Reimplemented for internal reasons. API is unaffected. Call it only if you really need it (i.e. the widget was hidden before) to have better performance.

### \[virtual protected slot\] void KCompletionBox::slotActivated(*QListWidgetItem \**) {#slotActivated}

Called when an item is activated. Emits [KCompletionBox::textActivated](kcompletionbox.md#textActivated)(const [QString](https://doc.qt.io/qt-6/qstring.html) &) with the item text.

> **Note:** For releases \<= 5.81, this slot emitted KCompletionBox::activated(const [QString](https://doc.qt.io/qt-6/qstring.html) &) with the item text.

### \[signal\] void KCompletionBox::textActivated(const QString &*text*) {#textActivated}

Emitted when an item is selected, `text` is the text of the selected item.

### \[slot\] void KCompletionBox::up() {#up}

Moves the selection one line up or select the first item if nothing is selected yet.

### \[signal\] void KCompletionBox::userCancelled(*const QString &*) {#userCancelled}

Emitted whenever the user chooses to ignore the available selections and closes this box.
