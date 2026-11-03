---
title: "KSelectAction Class"
description: "Action for selecting one of several items."
---

# KSelectAction Class

Action for selecting one of several items. [More...](#details)

- **Header:** `#include <KSelectAction>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidgetAction](https://doc.qt.io/qt-6/qwidgetaction.html)
- **Inherited By:** [KFontAction](kfontaction.md) and [KFontSizeAction](kfontsizeaction.md)

[List of all members, including inherited members](kselectaction-members.md)

## Public Types

- [enum KSelectAction::ToolBarMode](#ToolBarMode-enum)

## Properties

- [comboWidth : int](#comboWidth-prop)
- [currentAction : QAction\*](#currentAction-prop)
- [currentItem : int](#currentItem-prop)
- [\[read-only\] currentText : QString](#currentText-prop)
- [editable : bool](#editable-prop)
- [items : QStringList](#items-prop)
- [toolBarMode : ToolBarMode](#toolBarMode-prop)
- [toolButtonPopupMode : QToolButton::ToolButtonPopupMode](#toolButtonPopupMode-prop)

## Public Functions

- [KSelectAction(QObject \*parent)](#KSelectAction)
- [KSelectAction(const QString &text, QObject \*parent)](#KSelectAction-1)
- [KSelectAction(const QIcon &icon, const QString &text, QObject \*parent)](#KSelectAction-2)
- [QAction \*action(int index) const](#action)
- [QAction \*action(const QString &text, Qt::CaseSensitivity cs = Qt::CaseSensitive) const](#action-1)
- [QList\<QAction \*\> actions() const](#actions)
- [void addAction(QAction \*action)](#addAction)
- [QAction \*addAction(const QString &text)](#addAction-1)
- [QAction \*addAction(const QIcon &icon, const QString &text)](#addAction-2)
- [void changeItem(int index, const QString &text)](#changeItem)
- [void clear()](#clear)
- [int comboWidth() const](#comboWidth)
- [QAction \*currentAction() const](#currentAction)
- [int currentItem() const](#currentItem)
- [QString currentText() const](#currentText)
- [void insertAction(QAction \*before, QAction \*action)](#insertAction)
- [bool isEditable() const](#isEditable)
- [QStringList items() const](#items)
- [bool menuAccelsEnabled() const](#menuAccelsEnabled)
- [QAction \*removeAction(QAction \*action)](#removeAction)
- [void removeAllActions()](#removeAllActions)
- [QActionGroup \*selectableActionGroup() const](#selectableActionGroup)
- [void setComboWidth(int width)](#setComboWidth)
- [bool setCurrentAction(QAction \*action)](#setCurrentAction)
- [bool setCurrentAction(const QString &text, Qt::CaseSensitivity cs = Qt::CaseSensitive)](#setCurrentAction-1)
- [bool setCurrentItem(int index)](#setCurrentItem)
- [void setEditable(bool)](#setEditable)
- [void setItems(const QStringList &lst)](#setItems)
- [void setMaxComboViewCount(int n)](#setMaxComboViewCount)
- [void setMenuAccelsEnabled(bool b)](#setMenuAccelsEnabled)
- [void setToolBarMode(KSelectAction::ToolBarMode mode)](#setToolBarMode)
- [void setToolButtonPopupMode(QToolButton::ToolButtonPopupMode mode)](#setToolButtonPopupMode)
- [KSelectAction::ToolBarMode toolBarMode() const](#toolBarMode)
- [QToolButton::ToolButtonPopupMode toolButtonPopupMode() const](#toolButtonPopupMode)

## Public Slots

- [void slotActionTriggered(QAction \*action)](#slotActionTriggered) (since 6.0)
- [void slotToggled(bool)](#slotToggled)

## Signals

- [void actionTriggered(QAction \*action)](#actionTriggered) (since 6.0)
- [void indexTriggered(int index)](#indexTriggered)
- [void textTriggered(const QString &text)](#textTriggered)

## Detailed Description {#details}

Action for selecting one of several items.

This action shows up a submenu with a list of items. One of them can be checked. If the user clicks on an item this item will automatically be checked, the formerly checked item becomes unchecked. There can be only one item checked at a time.

Porting from KF5 to KF6:

The overloaded signal KSelectAction::triggered([QAction](https://doc.qt.io/qt-6/qaction.html) \*action) was renamed to [KSelectAction::actionTriggered](kselectaction.md#actionTriggered)([QAction](https://doc.qt.io/qt-6/qaction.html) \*action).

The protected virtual method [KSelectAction::actionTriggered](kselectaction.md#actionTriggered)([QAction](https://doc.qt.io/qt-6/qaction.html) \*action) was renamed to [KSelectAction::slotActionTriggered](kselectaction.md#slotActionTriggered)([QAction](https://doc.qt.io/qt-6/qaction.html) \*action).

## Member Type Documentation {#member-type-documentation}

### enum KSelectAction::ToolBarMode {#ToolBarMode-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KSelectAction::MenuMode` | `0` | Creates a button which pops up a menu when interacted with, as defined by [toolButtonPopupMode](kselectaction.md#toolButtonPopupMode)(). |
| `KSelectAction::Creates` | ? | a combo box which contains the actions. This is the default. |

## Property Documentation {#property-documentation}

### comboWidth : int {#comboWidth-prop}

**Access functions:**

- `int` **[comboWidth](kselectaction.md#comboWidth)**() const
- `void` **[setComboWidth](kselectaction.md#setComboWidth)**(`int` *width*)

### currentAction : QAction\* {#currentAction-prop}

**Access functions:**

- `QAction` \***[currentAction](kselectaction.md#currentAction)**() const
- `bool` **[setCurrentAction](kselectaction.md#setCurrentAction)**(`QAction` \**action*)
- `bool` **[setCurrentAction](kselectaction.md#setCurrentAction-1)**(const `QString` &*text*, `Qt::CaseSensitivity` *cs* = Qt::CaseSensitive)

### currentItem : int {#currentItem-prop}

**Access functions:**

- `int` **[currentItem](kselectaction.md#currentItem)**() const
- `bool` **[setCurrentItem](kselectaction.md#setCurrentItem)**(`int` *index*)

### \[read-only\] currentText : QString {#currentText-prop}

**Access functions:**

- `QString` **[currentText](kselectaction.md#currentText)**() const

### editable : bool {#editable-prop}

**Access functions:**

- `bool` **[isEditable](kselectaction.md#isEditable)**() const
- `void` **[setEditable](kselectaction.md#setEditable)**(*bool*)

### items : QStringList {#items-prop}

**Access functions:**

- `QStringList` **[items](kselectaction.md#items)**() const
- `void` **[setItems](kselectaction.md#setItems)**(const `QStringList` &*lst*)

### toolBarMode : ToolBarMode {#toolBarMode-prop}

**Access functions:**

- `KSelectAction::ToolBarMode` **[toolBarMode](kselectaction.md#toolBarMode)**() const
- `void` **[setToolBarMode](kselectaction.md#setToolBarMode)**(`KSelectAction::ToolBarMode` *mode*)

### toolButtonPopupMode : QToolButton::ToolButtonPopupMode {#toolButtonPopupMode-prop}

**Access functions:**

- `QToolButton::ToolButtonPopupMode` **[toolButtonPopupMode](kselectaction.md#toolButtonPopupMode)**() const
- `void` **[setToolButtonPopupMode](kselectaction.md#setToolButtonPopupMode)**(`QToolButton::ToolButtonPopupMode` *mode*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KSelectAction::KSelectAction(QObject \**parent*) {#KSelectAction}

Constructs a selection action with the specified parent.

`parent` The action's parent object.

### KSelectAction::KSelectAction(const QString &*text*, QObject \**parent*) {#KSelectAction-1}

Constructs a selection action with text; a shortcut may be specified by the ampersand character (e.g. "&Option" creates a shortcut with key `O` )

This is the most common [KSelectAction](kselectaction.md) used when you do not have a corresponding icon (note that it won't appear in the current version of the "Edit ToolBar" dialog, because an action needs an icon to be plugged in a toolbar...).

`text` The text that will be displayed.

`parent` The action's parent object.

### KSelectAction::KSelectAction(const QIcon &*icon*, const QString &*text*, QObject \**parent*) {#KSelectAction-2}

Constructs a selection action with text and an icon; a shortcut may be specified by the ampersand character (e.g. "&Option" creates a shortcut with key `O` )

This is the other common [KSelectAction](kselectaction.md) used. Use it when you do have a corresponding icon.

`icon` The icon to display.

`text` The text that will be displayed.

`parent` The action's parent object.

### QAction \*KSelectAction::action(int *index*) const {#action}

Returns the action at `index`, if one exists.

### QAction \*KSelectAction::action(const QString &*text*, Qt::CaseSensitivity *cs* = Qt::CaseSensitive) const {#action-1}

Searches for an action with the specified `text`, using a search whose case sensitivity is defined by `cs`.

### \[signal, since 6.0\] void KSelectAction::actionTriggered(QAction \**action*) {#actionTriggered}

This signal is emitted when an item is selected.

`action` indicates the item selected

This function was introduced in Qt 6.0.

### QList\<QAction \*\> KSelectAction::actions() const {#actions}

Returns the list of selectable actions

### void KSelectAction::addAction(QAction \**action*) {#addAction}

Add `action` to the list of selectable actions.

### QAction \*KSelectAction::addAction(const QString &*text*) {#addAction-1}

Overloaded member function, provided for convenience, which creates an action from `text` and inserts it into the list of selectable actions.

The newly created action is checkable and not user configurable.

### QAction \*KSelectAction::addAction(const QIcon &*icon*, const QString &*text*) {#addAction-2}

Overloaded member function, provided for convenience, which creates an action from `text` and `icon` and inserts it into the list of selectable actions.

The newly created action is checkable and not user configurable.

### void KSelectAction::changeItem(int *index*, const QString &*text*) {#changeItem}

Changes the text of item `index` to `text` .

### void KSelectAction::clear() {#clear}

Remove and delete all the items in this action.

*See also* [removeAllActions](kselectaction.md#removeAllActions)()

### int KSelectAction::comboWidth() const {#comboWidth}

When this action is plugged into a toolbar, it creates a combobox.

This returns the maximum width set by [setComboWidth](kselectaction.md#setComboWidth)

> **Note:** Getter function for property [comboWidth](kselectaction.md#comboWidth-prop).

*See also* [setComboWidth](kselectaction.md#setComboWidth)()

### QAction \*KSelectAction::currentAction() const {#currentAction}

Returns the current [QAction](https://doc.qt.io/qt-6/qaction.html).

> **Note:** Getter function for property [currentAction](kselectaction.md#currentAction-prop).

*See also* [setCurrentAction](kselectaction.md#setCurrentAction)

### int KSelectAction::currentItem() const {#currentItem}

Returns the index of the current item.

> **Note:** Getter function for property [currentItem](kselectaction.md#currentItem-prop).

*See also* [setCurrentItem](kselectaction.md#setCurrentItem)(), [currentText](kselectaction.md#currentText)(), [currentAction](kselectaction.md#currentAction)()

### QString KSelectAction::currentText() const {#currentText}

Returns the text of the currently selected item.

> **Note:** Getter function for property [currentText](kselectaction.md#currentText-prop).

*See also* [currentItem](kselectaction.md#currentItem)(), [currentAction](kselectaction.md#currentAction)()

### \[signal\] void KSelectAction::indexTriggered(int *index*) {#indexTriggered}

This signal is emitted when an item is selected.

`index` indicates the item selected

### \[virtual\] void KSelectAction::insertAction(QAction \**before*, QAction \**action*) {#insertAction}

Inserts the action action to this widget's list of actions, before the action before. It appends the action if before is a null pointer or before is not a valid action for this widget.

### bool KSelectAction::isEditable() const {#isEditable}

When this action is plugged into a toolbar, it creates a combobox.

Returns `true` if the combo editable.

> **Note:** Getter function for property [editable](kselectaction.md#editable-prop).

### QStringList KSelectAction::items() const {#items}

Convenience function which returns the items that can be selected with this action.

It is the same as iterating [selectableActionGroup](kselectaction.md#selectableActionGroup)()-\>[actions](kselectaction.md#actions)() and looking at each action's [text](https://doc.qt.io/qt-6/qaction.html#text-prop)().

> **Note:** Getter function for property [items](kselectaction.md#items-prop).

*See also* [setItems](kselectaction.md#setItems)()

### bool KSelectAction::menuAccelsEnabled() const {#menuAccelsEnabled}

Returns whether ampersands passed to methods using QStrings are interpreted as keyboard accelerator indicators or as literal ampersands.

*See also* [setMenuAccelsEnabled](kselectaction.md#setMenuAccelsEnabled)()

### \[virtual\] QAction \*KSelectAction::removeAction(QAction \**action*) {#removeAction}

Remove the specified `action` from this action selector.

You take ownership here, so save or delete it in order to not leak the action.

### void KSelectAction::removeAllActions() {#removeAllActions}

Remove all the items in this action.

Unlike [clear](kselectaction.md#clear)(), this will not delete the actions.

*See also* [clear](kselectaction.md#clear)()

### QActionGroup \*KSelectAction::selectableActionGroup() const {#selectableActionGroup}

The action group used to create exclusivity between the actions associated with this action.

### void KSelectAction::setComboWidth(int *width*) {#setComboWidth}

When this action is plugged into a toolbar, it creates a combobox.

This gives a \_maximum\_ size to the combobox.

The minimum size is automatically given by the contents (the items).

> **Note:** Setter function for property [comboWidth](kselectaction.md#comboWidth-prop).

*See also* [comboWidth](kselectaction.md#comboWidth)()

### bool KSelectAction::setCurrentAction(QAction \**action*) {#setCurrentAction}

Sets the currently checked item.

`action` the [QAction](https://doc.qt.io/qt-6/qaction.html) to become the currently checked item.

Returns `true` if a corresponding action was found and successfully checked.

> **Note:** Setter function for property [currentAction](kselectaction.md#currentAction-prop).

*See also* [currentAction](kselectaction.md#currentAction)()

### bool KSelectAction::setCurrentAction(const QString &*text*, Qt::CaseSensitivity *cs* = Qt::CaseSensitive) {#setCurrentAction-1}

Overloaded member function, provided for convenience, to set the currently checked action to be the action which has `text` as its [text](https://doc.qt.io/qt-6/qaction.html#text-prop)().

If there is no action at that index, the currently checked action (if any) will be deselected.

Returns `true` if a corresponding action was found, otherwise `false`

> **Note:** Setter function for property [currentAction](kselectaction.md#currentAction-prop).

### bool KSelectAction::setCurrentItem(int *index*) {#setCurrentItem}

Convenience function to set the currently checked action to be the action at index `index`.

If there is no action at that index, the currently checked action (if any) will be deselected.

Returns `true` if a corresponding action was found and thus set to the current action, otherwise *false*

> **Note:** Setter function for property [currentItem](kselectaction.md#currentItem-prop).

*See also* [currentItem](kselectaction.md#currentItem)()

### void KSelectAction::setEditable(*bool*) {#setEditable}

When this action is plugged into a toolbar, it creates a combobox.

This makes the combo editable or read-only.

> **Note:** Setter function for property [editable](kselectaction.md#editable-prop).

*See also* [isEditable](kselectaction.md#isEditable)()

### void KSelectAction::setItems(const QStringList &*lst*) {#setItems}

Convenience function to create the list of selectable items.

Any previously existing items will be cleared.

> **Note:** Setter function for property [items](kselectaction.md#items-prop).

*See also* [items](kselectaction.md#items)()

### void KSelectAction::setMaxComboViewCount(int *n*) {#setMaxComboViewCount}

Sets the maximum items that are visible at once if the action is a combobox, that is the number of items in the combobox's viewport

### void KSelectAction::setMenuAccelsEnabled(bool *b*) {#setMenuAccelsEnabled}

Sets whether any occurrence of the ampersand character ( & ) in items should be interpreted as keyboard accelerator for items displayed in a menu or not. Only applies to (overloaded) methods dealing with QStrings, not those dealing with QActions.

Defaults to true.

`b` true if ampersands indicate a keyboard accelerator, otherwise false.

*See also* [menuAccelsEnabled](kselectaction.md#menuAccelsEnabled)()

### void KSelectAction::setToolBarMode(KSelectAction::ToolBarMode *mode*) {#setToolBarMode}

Set the type of widget to be inserted in a toolbar to `mode`.

> **Note:** Setter function for property [toolBarMode](kselectaction.md#toolBarMode-prop).

*See also* [toolBarMode](kselectaction.md#toolBarMode)()

### void KSelectAction::setToolButtonPopupMode(QToolButton::ToolButtonPopupMode *mode*) {#setToolButtonPopupMode}

Set how this list of actions should behave when in popup mode and plugged into a toolbar.

> **Note:** Setter function for property [toolButtonPopupMode](kselectaction.md#toolButtonPopupMode-prop).

*See also* [toolButtonPopupMode](kselectaction.md#toolButtonPopupMode)()

### \[virtual protected slot, since 6.0\] void KSelectAction::slotActionTriggered(QAction \**action*) {#slotActionTriggered}

This function is called whenever an action from the selections is triggered. The default implementation calls [trigger](https://doc.qt.io/qt-6/qaction.html#trigger)() if [isCheckable](https://doc.qt.io/qt-6/qaction.html#checkable-prop)() is `true`, then emits the signals [actionTriggered](kselectaction.md#actionTriggered)([QAction](https://doc.qt.io/qt-6/qaction.html) \*), [indexTriggered](kselectaction.md#indexTriggered)(int) and [textTriggered](kselectaction.md#textTriggered)(const [QString](https://doc.qt.io/qt-6/qstring.html) &).

This function was introduced in Qt 6.0.

### \[protected slot\] void KSelectAction::slotToggled(*bool*) {#slotToggled}

For structured menu building. Deselects all items if the action was unchecked by the top menu

### \[signal\] void KSelectAction::textTriggered(const QString &*text*) {#textTriggered}

This signal is emitted when an item is selected.

`text` indicates the item selected

### KSelectAction::ToolBarMode KSelectAction::toolBarMode() const {#toolBarMode}

Returns which type of widget (combo box or button with drop-down menu) will be inserted in a toolbar.

> **Note:** Getter function for property [toolBarMode](kselectaction.md#toolBarMode-prop).

*See also* [setToolBarMode](kselectaction.md#setToolBarMode)()

### QToolButton::ToolButtonPopupMode KSelectAction::toolButtonPopupMode() const {#toolButtonPopupMode}

Returns the style for the list of actions, when this action is plugged into a KToolBar. The default value is [QToolButton::InstantPopup](https://doc.qt.io/qt-6/qtoolbutton.html#ToolButtonPopupMode-enum)

> **Note:** Getter function for property [toolButtonPopupMode](kselectaction.md#toolButtonPopupMode-prop).

*See also* [setToolButtonPopupMode](kselectaction.md#setToolButtonPopupMode)(), [QToolButton::setPopupMode](https://doc.qt.io/qt-6/qtoolbutton.html#popupMode-prop)()
