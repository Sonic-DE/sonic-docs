---
title: "KActionSelector Class"
description: "A widget for selecting and arranging actions/objects."
---

# KActionSelector Class

A widget for selecting and arranging actions/objects. [More...](#details)

- **Header:** `#include <KActionSelector>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kactionselector-members.md)

## Public Types

- [enum KActionSelector::InsertionPolicy](#InsertionPolicy-enum)
- [enum KActionSelector::MoveButton](#MoveButton-enum)

## Properties

- [availableInsertionPolicy : InsertionPolicy](#availableInsertionPolicy-prop)
- [availableLabel : QString](#availableLabel-prop)
- [keyboardEnabled : bool](#keyboardEnabled-prop)
- [moveOnDoubleClick : bool](#moveOnDoubleClick-prop)
- [selectedInsertionPolicy : InsertionPolicy](#selectedInsertionPolicy-prop)
- [selectedLabel : QString](#selectedLabel-prop)
- [showUpDownButtons : bool](#showUpDownButtons-prop)

## Public Functions

- [KActionSelector(QWidget \*parent = nullptr)](#KActionSelector)
- [KActionSelector::InsertionPolicy availableInsertionPolicy() const](#availableInsertionPolicy)
- [QString availableLabel() const](#availableLabel)
- [QListWidget \*availableListWidget() const](#availableListWidget)
- [bool keyboardEnabled() const](#keyboardEnabled)
- [bool moveOnDoubleClick() const](#moveOnDoubleClick)
- [KActionSelector::InsertionPolicy selectedInsertionPolicy() const](#selectedInsertionPolicy)
- [QString selectedLabel() const](#selectedLabel)
- [QListWidget \*selectedListWidget() const](#selectedListWidget)
- [void setAvailableInsertionPolicy(KActionSelector::InsertionPolicy policy)](#setAvailableInsertionPolicy)
- [void setAvailableLabel(const QString &text)](#setAvailableLabel)
- [void setButtonIcon(const QString &icon, KActionSelector::MoveButton button)](#setButtonIcon)
- [void setButtonIconSet(const QIcon &iconset, KActionSelector::MoveButton button)](#setButtonIconSet)
- [void setButtonTooltip(const QString &tip, KActionSelector::MoveButton button)](#setButtonTooltip)
- [void setButtonWhatsThis(const QString &text, KActionSelector::MoveButton button)](#setButtonWhatsThis)
- [void setKeyboardEnabled(bool enable)](#setKeyboardEnabled)
- [void setMoveOnDoubleClick(bool enable)](#setMoveOnDoubleClick)
- [void setSelectedInsertionPolicy(KActionSelector::InsertionPolicy policy)](#setSelectedInsertionPolicy)
- [void setSelectedLabel(const QString &text)](#setSelectedLabel)
- [void setShowUpDownButtons(bool show)](#setShowUpDownButtons)
- [bool showUpDownButtons() const](#showUpDownButtons)

## Public Slots

- [void setButtonsEnabled()](#setButtonsEnabled)

## Signals

- [void added(QListWidgetItem \*item)](#added)
- [void movedDown(QListWidgetItem \*item)](#movedDown)
- [void movedUp(QListWidgetItem \*item)](#movedUp)
- [void removed(QListWidgetItem \*item)](#removed)

## Detailed Description {#details}

This widget allows the user to select from a set of objects and arrange the order of the selected ones using two list boxes labeled "Available" and "Used" with horizontal arrows in between to move selected objects between the two, and vertical arrows on the right to arrange the order of the selected objects.

The widget moves objects to the other listbox when doubleclicked if the property [moveOnDoubleClick](kactionselector.md#moveOnDoubleClick) is set to true (default). See [moveOnDoubleClick](kactionselector.md#moveOnDoubleClick)() and [setMoveOnDoubleClick](kactionselector.md#setMoveOnDoubleClick)().

The user control the widget using the keyboard if enabled (default), see [keyboardEnabled](kactionselector.md#keyboardEnabled).

Note that this may conflict with keyboard selection in the selected list box, if you set that to anything else than QListWidget::Single (which is the default).

To use it, simply construct an instance and then add items to the two listboxes, available through lbAvailable() and lbSelected(). Whenever you want, you can retrieve the selected options using [QListWidget](https://doc.qt.io/qt-6/qlistwidget.html) methods on lbSelected().

This way, you can use your own [QListWidgetItem](https://doc.qt.io/qt-6/qlistwidgetitem.html) class, allowing you to easily store object data in those.

When an item is moved to a listbox, it is placed below the current item of that listbox.

Standard arrow icons are used, but you can use icons of your own choice if desired, see [setButtonIcon](kactionselector.md#setButtonIcon)(). It is also possible to set tooltips and whatsthis help for the buttons. See [setButtonTooltip](kactionselector.md#setButtonTooltip)() and [setButtonWhatsThis](kactionselector.md#setButtonWhatsThis)().

To set whatsthis or tooltips for the listboxes, access them through [availableListWidget](kactionselector.md#availableListWidget)() and [selectedListWidget](kactionselector.md#selectedListWidget)().

All the moving buttons are automatically set enabled as expected.

Signals are sent each time an item is moved, allowing you to follow the users actions if you need to. See addedToSelection(), removedFromSelection(), [movedUp](kactionselector.md#movedUp)() and [movedDown](kactionselector.md#movedDown)()

## Member Type Documentation {#member-type-documentation}

### enum KActionSelector::InsertionPolicy {#InsertionPolicy-enum}

This enum defines policies for where to insert moved items in a listbox.

| Constant | Value | Description |
| --- | --- | --- |
| `KActionSelector::BelowCurrent` | `0` | The item is inserted below the listbox' currentItem() or at the end if there is no current item. |
| `KActionSelector::Sorted` | `1` | The listbox is sort()ed after one or more items are inserted. |
| `KActionSelector::AtTop` | `2` | The item is inserted at index 0 in the listbox. |
| `KActionSelector::AtBottom` | `3` | The item is inserted at the end of the listbox. |

*See also* [availableInsertionPolicy](kactionselector.md#availableInsertionPolicy)(), [setAvailableInsertionPolicy](kactionselector.md#setAvailableInsertionPolicy)(), [selectedInsertionPolicy](kactionselector.md#selectedInsertionPolicy)(), [setSelectedInsertionPolicy](kactionselector.md#setSelectedInsertionPolicy)()

### enum KActionSelector::MoveButton {#MoveButton-enum}

This enum identifies the moving buttons

| Constant |   |
| --- | --- |
| `KActionSelector::ButtonAdd` | `0` |
| `KActionSelector::ButtonRemove` | `1` |
| `KActionSelector::ButtonUp` | `2` |
| `KActionSelector::ButtonDown` | `3` |

## Property Documentation {#property-documentation}

### availableInsertionPolicy : InsertionPolicy {#availableInsertionPolicy-prop}

**Access functions:**

- `KActionSelector::InsertionPolicy` **[availableInsertionPolicy](kactionselector.md#availableInsertionPolicy)**() const
- `void` **[setAvailableInsertionPolicy](kactionselector.md#setAvailableInsertionPolicy)**(`KActionSelector::InsertionPolicy` *policy*)

### availableLabel : QString {#availableLabel-prop}

**Access functions:**

- `QString` **[availableLabel](kactionselector.md#availableLabel)**() const
- `void` **[setAvailableLabel](kactionselector.md#setAvailableLabel)**(const `QString` &*text*)

### keyboardEnabled : bool {#keyboardEnabled-prop}

**Access functions:**

- `bool` **[keyboardEnabled](kactionselector.md#keyboardEnabled)**() const
- `void` **[setKeyboardEnabled](kactionselector.md#setKeyboardEnabled)**(`bool` *enable*)

### moveOnDoubleClick : bool {#moveOnDoubleClick-prop}

**Access functions:**

- `bool` **[moveOnDoubleClick](kactionselector.md#moveOnDoubleClick)**() const
- `void` **[setMoveOnDoubleClick](kactionselector.md#setMoveOnDoubleClick)**(`bool` *enable*)

### selectedInsertionPolicy : InsertionPolicy {#selectedInsertionPolicy-prop}

**Access functions:**

- `KActionSelector::InsertionPolicy` **[selectedInsertionPolicy](kactionselector.md#selectedInsertionPolicy)**() const
- `void` **[setSelectedInsertionPolicy](kactionselector.md#setSelectedInsertionPolicy)**(`KActionSelector::InsertionPolicy` *policy*)

### selectedLabel : QString {#selectedLabel-prop}

**Access functions:**

- `QString` **[selectedLabel](kactionselector.md#selectedLabel)**() const
- `void` **[setSelectedLabel](kactionselector.md#setSelectedLabel)**(const `QString` &*text*)

### showUpDownButtons : bool {#showUpDownButtons-prop}

**Access functions:**

- `bool` **[showUpDownButtons](kactionselector.md#showUpDownButtons)**() const
- `void` **[setShowUpDownButtons](kactionselector.md#setShowUpDownButtons)**(`bool` *show*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KActionSelector::KActionSelector(QWidget \**parent* = nullptr) {#KActionSelector}

### \[signal\] void KActionSelector::added(QListWidgetItem \**item*) {#added}

Emitted when an item is moved to the "selected" listbox.

### KActionSelector::InsertionPolicy KActionSelector::availableInsertionPolicy() const {#availableInsertionPolicy}

Returns The current insertion policy for the available listbox.

The default policy for the available listbox is Sorted.

> **Note:** Getter function for property [availableInsertionPolicy](kactionselector.md#availableInsertionPolicy-prop).

*See also* [InsertionPolicy](kactionselector.md#InsertionPolicy-enum), [setAvailableInsertionPolicy](kactionselector.md#setAvailableInsertionPolicy)()

### QString KActionSelector::availableLabel() const {#availableLabel}

Returns The text of the label for the available items listbox.

> **Note:** Getter function for property [availableLabel](kactionselector.md#availableLabel-prop).

*See also* [setAvailableLabel](kactionselector.md#setAvailableLabel)()

### QListWidget \*KActionSelector::availableListWidget() const {#availableListWidget}

Returns The [QListWidget](https://doc.qt.io/qt-6/qlistwidget.html) holding the available actions

### bool KActionSelector::keyboardEnabled() const {#keyboardEnabled}

Returns Whether keyboard control is enabled.

When Keyboard control is enabled, the widget will react to the following keyboard actions:

- CTRL + Right - simulate clicking the add button
- CTRL + Left - simulate clicking the remove button
- CTRL + Up - simulate clicking the up button
- CTRL + Down - simulate clicking the down button

Additionally, pressing RETURN or ENTER on one of the list boxes will cause the current item of that listbox to be moved to the other listbox.

The keyboard actions are enabled by default.

> **Note:** Getter function for property [keyboardEnabled](kactionselector.md#keyboardEnabled-prop).

*See also* [setKeyboardEnabled](kactionselector.md#setKeyboardEnabled)()

### bool KActionSelector::moveOnDoubleClick() const {#moveOnDoubleClick}

Returns Whether moveOnDoubleClick is enabled.

If enabled, an item in any listbox will be moved to the other one whenever double-clicked.

This feature is enabled by default.

> **Note:** Getter function for property [moveOnDoubleClick](kactionselector.md#moveOnDoubleClick-prop).

*See also* [setMoveOnDoubleClick](kactionselector.md#setMoveOnDoubleClick)()

### \[signal\] void KActionSelector::movedDown(QListWidgetItem \**item*) {#movedDown}

Emitted when an item is moved downwards in the "selected" listbox.

### \[signal\] void KActionSelector::movedUp(QListWidgetItem \**item*) {#movedUp}

Emitted when an item is moved upwards in the "selected" listbox.

### \[signal\] void KActionSelector::removed(QListWidgetItem \**item*) {#removed}

Emitted when an item is moved out of the "selected" listbox.

### KActionSelector::InsertionPolicy KActionSelector::selectedInsertionPolicy() const {#selectedInsertionPolicy}

Returns The current insertion policy for the selected listbox.

The default policy for the selected listbox is [BelowCurrent](kactionselector.md#InsertionPolicy-enum).

> **Note:** Getter function for property [selectedInsertionPolicy](kactionselector.md#selectedInsertionPolicy-prop).

*See also* [InsertionPolicy](kactionselector.md#InsertionPolicy-enum), [setSelectedInsertionPolicy](kactionselector.md#setSelectedInsertionPolicy)()

### QString KActionSelector::selectedLabel() const {#selectedLabel}

Returns the label of the selected items listbox.

> **Note:** Getter function for property [selectedLabel](kactionselector.md#selectedLabel-prop).

*See also* [setSelectedLabel](kactionselector.md#setSelectedLabel)()

### QListWidget \*KActionSelector::selectedListWidget() const {#selectedListWidget}

Returns The [QListWidget](https://doc.qt.io/qt-6/qlistwidget.html) holding the selected actions

### void KActionSelector::setAvailableInsertionPolicy(KActionSelector::InsertionPolicy *policy*) {#setAvailableInsertionPolicy}

Sets the insertion policy for the available listbox.

> **Note:** Setter function for property [availableInsertionPolicy](kactionselector.md#availableInsertionPolicy-prop).

*See also* [InsertionPolicy](kactionselector.md#InsertionPolicy-enum), [availableInsertionPolicy](kactionselector.md#availableInsertionPolicy)()

### void KActionSelector::setAvailableLabel(const QString &*text*) {#setAvailableLabel}

Sets the label for the available items listbox to `text`. Note that this label has the listbox as its buddy, so that if you have a single ampersand in the text, the following character will become the accelerator to focus the listbox.

> **Note:** Setter function for property [availableLabel](kactionselector.md#availableLabel-prop).

*See also* [availableLabel](kactionselector.md#availableLabel)()

### void KActionSelector::setButtonIcon(const QString &*icon*, KActionSelector::MoveButton *button*) {#setButtonIcon}

Sets the pixmap of the button `button` to `icon`. It calls SmallIconSet(pm) to generate the icon set.

### void KActionSelector::setButtonIconSet(const QIcon &*iconset*, KActionSelector::MoveButton *button*) {#setButtonIconSet}

Sets the iconset for button `button` to `iconset`. You can use this method to set a custom icon set. Either created by QIconSet, or use the application instance of KIconLoader (recommended).

### void KActionSelector::setButtonTooltip(const QString &*tip*, KActionSelector::MoveButton *button*) {#setButtonTooltip}

Sets the tooltip for the button `button` to `tip`.

### void KActionSelector::setButtonWhatsThis(const QString &*text*, KActionSelector::MoveButton *button*) {#setButtonWhatsThis}

Sets the whatsthis help for button `button` to `text`.

### \[slot\] void KActionSelector::setButtonsEnabled() {#setButtonsEnabled}

Sets the enabled state of all moving buttons to reflect the current options.

Be sure to call this if you add or removes items to either listbox after the widget is shown

### void KActionSelector::setKeyboardEnabled(bool *enable*) {#setKeyboardEnabled}

Sets the keyboard enabled depending on `enable`.

> **Note:** Setter function for property [keyboardEnabled](kactionselector.md#keyboardEnabled-prop).

*See also* [keyboardEnabled](kactionselector.md#keyboardEnabled)()

### void KActionSelector::setMoveOnDoubleClick(bool *enable*) {#setMoveOnDoubleClick}

Sets [moveOnDoubleClick](kactionselector.md#moveOnDoubleClick) to `enable`

> **Note:** Setter function for property [moveOnDoubleClick](kactionselector.md#moveOnDoubleClick-prop).

*See also* [moveOnDoubleClick](kactionselector.md#moveOnDoubleClick)()

### void KActionSelector::setSelectedInsertionPolicy(KActionSelector::InsertionPolicy *policy*) {#setSelectedInsertionPolicy}

Sets the insertion policy for the selected listbox.

> **Note:** Setter function for property [selectedInsertionPolicy](kactionselector.md#selectedInsertionPolicy-prop).

*See also* [InsertionPolicy](kactionselector.md#InsertionPolicy-enum), [selectedInsertionPolicy](kactionselector.md#selectedInsertionPolicy)()

### void KActionSelector::setSelectedLabel(const QString &*text*) {#setSelectedLabel}

Sets the label for the selected items listbox to `text`. Note that this label has the listbox as its buddy, so that if you have a single ampersand in the text, the following character will become the accelerator to focus the listbox.

> **Note:** Setter function for property [selectedLabel](kactionselector.md#selectedLabel-prop).

*See also* [selectedLabel](kactionselector.md#selectedLabel)()

### void KActionSelector::setShowUpDownButtons(bool *show*) {#setShowUpDownButtons}

Sets whether the Up and Down buttons should be displayed according to `show`

> **Note:** Setter function for property [showUpDownButtons](kactionselector.md#showUpDownButtons-prop).

*See also* [showUpDownButtons](kactionselector.md#showUpDownButtons)()

### bool KActionSelector::showUpDownButtons() const {#showUpDownButtons}

Returns whether the Up and Down buttons should be displayed.

> **Note:** Getter function for property [showUpDownButtons](kactionselector.md#showUpDownButtons-prop).

*See also* [setShowUpDownButtons](kactionselector.md#setShowUpDownButtons)()
