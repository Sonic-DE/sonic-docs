---
title: "KComboBox Class"
description: "A combo box with completion support."
---

# KComboBox Class

A combo box with completion support. [More...](#details)

- **Header:** `#include <KComboBox>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Completion)`  
  `target_link_libraries(mytarget PRIVATE KF6::Completion)`
- **Inherits:** [QComboBox](https://doc.qt.io/qt-6/qcombobox.html) and [KCompletionBase](kcompletionbase.md)
- **Inherited By:** [KHistoryComboBox](khistorycombobox.md)

[List of all members, including inherited members](kcombobox-members.md)

## Properties

- [autoCompletion : bool](#autoCompletion-prop)
- [trapReturnKey : bool](#trapReturnKey-prop)

## Public Functions

- [KComboBox(QWidget \*parent = nullptr)](#KComboBox)
- [KComboBox(bool rw, QWidget \*parent = nullptr)](#KComboBox-1)
- [void addUrl(const QUrl &url)](#addUrl)
- [void addUrl(const QIcon &icon, const QUrl &url)](#addUrl-1)
- [bool autoCompletion() const](#autoCompletion)
- [void changeUrl(int index, const QUrl &url)](#changeUrl)
- [void changeUrl(int index, const QIcon &icon, const QUrl &url)](#changeUrl-1)
- [KCompletionBox \*completionBox(bool create = true)](#completionBox)
- [bool contains(const QString &text) const](#contains)
- [QMenu \*contextMenu() const](#contextMenu)
- [int cursorPosition() const](#cursorPosition)
- [void insertUrl(int index, const QUrl &url)](#insertUrl)
- [void insertUrl(int index, const QIcon &icon, const QUrl &url)](#insertUrl-1)
- [void setAutoCompletion(bool autocomplete)](#setAutoCompletion)
- [void setEditUrl(const QUrl &url)](#setEditUrl)
- [void setEditable(bool editable)](#setEditable)
- [void setLineEdit(QLineEdit \*)](#setLineEdit)
- [void setTrapReturnKey(bool trap)](#setTrapReturnKey)
- [bool trapReturnKey() const](#trapReturnKey)
- [bool urlDropsEnabled() const](#urlDropsEnabled)

## Public Slots

- [void makeCompletion(const QString &)](#makeCompletion)
- [void rotateText(KCompletionBase::KeyBindingType type)](#rotateText)
- [void setCompletedItems(const QStringList &items, bool autoSuggest = true)](#setCompletedItems)
- [void setCompletedText(const QString &)](#setCompletedText)
- [void setCurrentItem(const QString &item, bool insert = false, int index = -1)](#setCurrentItem)

## Signals

- [void aboutToShowContextMenu(QMenu \*contextMenu)](#aboutToShowContextMenu)
- [void completion(const QString &)](#completion)
- [void completionModeChanged(KCompletion::CompletionMode)](#completionModeChanged)
- [void returnPressed(const QString &text)](#returnPressed)
- [void substringCompletion(const QString &)](#substringCompletion)
- [void textRotation(KCompletionBase::KeyBindingType)](#textRotation)

## Protected Functions

- [void setCompletedText(const QString &text, bool marked)](#setCompletedText-1)

## Detailed Description {#details}

This widget inherits from [QComboBox](https://doc.qt.io/qt-6/qcombobox.html) and implements the following additional features:

- A completion object that provides both automatic and manual text completion as well as text rotation
- Configurable key bindings to activate these features
- A popup menu item that can be used to allow the user to change the text completion mode on the fly.

To support these additional features, [KComboBox](kcombobox.md) emits a few additional signals such as completion(const [QString](https://doc.qt.io/qt-6/qstring.html)&) and [textRotation](kcombobox.md#textRotation)(KeyBindingType).

The completion signal can be connected to a slot that will assist the user in filling out the remaining text while the rotation signal can be used to traverse through all possible matches whenever text completion results in multiple matches. Additionally, the [returnPressed](kcombobox.md#returnPressed)(const [QString](https://doc.qt.io/qt-6/qstring.html) &) signal is emitted when the user presses the Return or Enter key.

KCombobox by default creates a completion object when you invoke the completionObject(bool) member function for the first time or explicitly use setCompletionObject([KCompletion](kcompletion-module.md)\*, bool) to assign your own completion object. Additionally, to make this widget more functional, [KComboBox](kcombobox.md) will by default handle text rotation and completion events internally whenever a completion object is created through either one of the methods mentioned above. If you do not need this functionality, simply use [KCompletionBase::setHandleSignals](kcompletionbase.md#setHandleSignals)(bool) or alternatively set the boolean parameter in the [setCompletionObject](kcompletionbase.md#setCompletionObject)() call to `false`.

Beware: The completion object can be deleted on you, especially if a call such as [setEditable](kcombobox.md#setEditable)(false) is made. Store the pointer at your own risk, and consider using [QPointer](https://doc.qt.io/qt-6/qpointer.html)\<[KCompletion](kcompletion-module.md)\>.

The default key bindings for completion and rotation are determined from the global settings in KStandardShortcut. These values, however, can be overridden locally by invoking [KCompletionBase::setKeyBinding](kcompletionbase.md#setKeyBinding)(). The values can easily be reverted back to the default settings by calling [useGlobalKeyBindings](kcompletionbase.md#useGlobalKeyBindings)(). An alternate method would be to default individual key bindings by using [setKeyBinding](kcompletionbase.md#setKeyBinding)() with the default second argument.

A non-editable combo box only has one completion mode, CompletionAuto. Unlike an editable combo box, the CompletionAuto mode works by matching any typed key with the first letter of entries in the combo box. Please note that if you call [setEditable](kcombobox.md#setEditable)(false) to change an editable combo box to a non-editable one, the text completion object associated with the combo box will no longer exist unless you created the completion object yourself and assigned it to this widget or you called setAutoDeleteCompletionObject(false). In other words do not do the following:

```cpp
KComboBox* combo = new KComboBox(true, this);
KCompletion* comp = combo->completionObject();
combo->setEditable(false);
comp->clear(); // CRASH: completion object does not exist anymore.
```

A read-only [KComboBox](kcombobox.md) will have the same background color as a disabled [KComboBox](kcombobox.md), but its foreground color will be the one used for the editable mode. This differs from [QComboBox](https://doc.qt.io/qt-6/qcombobox.html)'s implementation and is done to give visual distinction between the three different modes: disabled, read-only, and editable.

**Usage**

To enable the basic completion feature:

```cpp
KComboBox *combo = new KComboBox(true, this);
KCompletion *comp = combo->completionObject();
// Connect to the Return pressed signal - optional
connect(combo, &KComboBox::returnPressed, comp, [this](const QString &text) { addItem(text); });

// Provide the to be completed strings. Note that those are separate from the combo's
// contents.
comp->insertItems(someQStringList);
```

To use your own completion object:

```cpp
KComboBox *combo = new KComboBox(this);
KUrlCompletion *comp = new KUrlCompletion();
// You can either delete the allocated completion object manually when you
// don't need it anymore, or call setAutoDeleteCompletionObject(true) and it
// will be deleted automatically
comp->setAutoDeleteCompletionObject(true);
combo->setCompletionObject(comp);
// Connect to the return pressed signal - optional
connect(combo, &KComboBox::returnPressed, comp, [this](const QString &text) { addItem(text); });
```

Miscellaneous function calls:

```cpp
// Tell the widget not to handle completion and rotation
combo->setHandleSignals(false);
// Set your own completion key for manual completions.
combo->setKeyBinding(KCompletionBase::TextCompletion, Qt::End);
```

## Property Documentation {#property-documentation}

### autoCompletion : bool {#autoCompletion-prop}

**Access functions:**

- `bool` **[autoCompletion](kcombobox.md#autoCompletion)**() const
- virtual `void` **[setAutoCompletion](kcombobox.md#setAutoCompletion)**(`bool` *autocomplete*)

### trapReturnKey : bool {#trapReturnKey-prop}

**Access functions:**

- `bool` **[trapReturnKey](kcombobox.md#trapReturnKey)**() const
- `void` **[setTrapReturnKey](kcombobox.md#setTrapReturnKey)**(`bool` *trap*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KComboBox::KComboBox(QWidget \**parent* = nullptr) {#KComboBox}

Constructs a read-only (or rather select-only) combo box.

`parent` The parent object of this widget

### \[explicit\] KComboBox::KComboBox(bool *rw*, QWidget \**parent* = nullptr) {#KComboBox-1}

Constructs an editable or read-only combo box.

`rw` When `true`, widget will be editable.

`parent` The parent object of this widget.

### \[signal\] void KComboBox::aboutToShowContextMenu(QMenu \**contextMenu*) {#aboutToShowContextMenu}

Emitted before the context menu is displayed.

The signal allows you to add your own entries into the context menu. Note that you *must not* store the pointer to the QPopupMenu since it is created and deleted on demand. Otherwise, you can crash your app.

`contextMenu` the context menu about to be displayed

### void KComboBox::addUrl(const QUrl &*url*) {#addUrl}

Appends `url` to the combo box.

[QUrl::toDisplayString](https://doc.qt.io/qt-6/qurl.html#toDisplayString)() is used so that the url is properly decoded for displaying.

### void KComboBox::addUrl(const QIcon &*icon*, const QUrl &*url*) {#addUrl-1}

Appends `url` with the `icon` to the combo box.

[QUrl::toDisplayString](https://doc.qt.io/qt-6/qurl.html#toDisplayString)() is used so that the url is properly decoded for displaying.

### bool KComboBox::autoCompletion() const {#autoCompletion}

Returns `true` if the current completion mode is set to automatic. See its more comprehensive replacement [completionMode](kcompletionbase.md#completionMode)().

Returns `true` when completion mode is automatic.

> **Note:** Getter function for property [autoCompletion](kcombobox.md#autoCompletion-prop).

*See also* [setAutoCompletion](kcombobox.md#setAutoCompletion)()

### void KComboBox::changeUrl(int *index*, const QUrl &*url*) {#changeUrl}

Replaces the item at position `index` with `url`.

[QUrl::toDisplayString](https://doc.qt.io/qt-6/qurl.html#toDisplayString)() is used so that the url is properly decoded for displaying.

### void KComboBox::changeUrl(int *index*, const QIcon &*icon*, const QUrl &*url*) {#changeUrl-1}

Replaces the item at position `index` with `url` and `icon`.

[QUrl::toDisplayString](https://doc.qt.io/qt-6/qurl.html#toDisplayString)() is used so that the url is properly decoded for displaying.

### \[signal\] void KComboBox::completion(*const QString &*) {#completion}

Emitted when the completion key is pressed.

The argument is the current text being edited.

Note that this signal is *not* available when the widget is non-editable or the completion mode is set to `CompletionNone`.

### KCompletionBox \*KComboBox::completionBox(bool *create* = true) {#completionBox}

This method will create a completion box by calling [KLineEdit::completionBox](klineedit.md#completionBox), if none is there yet.

`create` Set this to false if you don't want the box to be created i.e. to test if it is available. Returns the completion box that is used in completion mode CompletionPopup and CompletionPopupAuto.

### \[signal\] void KComboBox::completionModeChanged(*KCompletion::CompletionMode*) {#completionModeChanged}

Emitted whenever the completion mode is changed by the user through the context menu.

### bool KComboBox::contains(const QString &*text*) const {#contains}

Convenience method which iterates over all items and checks if any of them is equal to `text`.

If `text` is an empty string, `false` is returned.

Returns `true` if an item with the string `text` is in the combo box.

### QMenu \*KComboBox::contextMenu() const {#contextMenu}

Pointer to [KLineEdit](klineedit.md)'s context menu, or nullptr if it does not exist at the given moment.

### int KComboBox::cursorPosition() const {#cursorPosition}

Returns the current cursor position.

This method always returns a -1 if the combo box is *not* editable (read-only).

Returns current cursor position.

### void KComboBox::insertUrl(int *index*, const QUrl &*url*) {#insertUrl}

Inserts `url` at position `index` into the combo box.

[QUrl::toDisplayString](https://doc.qt.io/qt-6/qurl.html#toDisplayString)() is used so that the url is properly decoded for displaying.

### void KComboBox::insertUrl(int *index*, const QIcon &*icon*, const QUrl &*url*) {#insertUrl-1}

Inserts `url` with the `icon` at position `index` into the combo box.

[QUrl::toDisplayString](https://doc.qt.io/qt-6/qurl.html#toDisplayString)() is used so that the url is properly decoded for displaying.

### \[virtual protected slot\] void KComboBox::makeCompletion(*const QString &*) {#makeCompletion}

Completes text according to the completion mode.

> **Note:** This method is not invoked if the completion mode is set to CompletionNone. Also if the mode is set to CompletionShell and multiple matches are found, this method will complete the text to the first match with a beep to indicate that there are more matches. Then any successive completion key event iterates through the remaining matches. This way the rotation functionality is left to iterate through the list as usual.

### \[signal\] void KComboBox::returnPressed(const QString &*text*) {#returnPressed}

Emitted when the user presses the Return or Enter key.

The argument is the current text being edited.

> **Note:** This signal is only emitted when the widget is editable.

### \[slot\] void KComboBox::rotateText(KCompletionBase::KeyBindingType *type*) {#rotateText}

Iterates through all possible matches of the completed text or the history list.

Depending on the value of the argument, this function either iterates through the history list of this widget or all the possible matches in whenever multiple matches result from a text completion request. Note that the all-possible-match iteration will not work if there are no previous matches, i.e. no text has been completed and the \*nix shell history list rotation is only available if the insertion policy for this widget is set either QComobBox::AtTop or QComboBox::AtBottom. For other insertion modes whatever has been typed by the user when the rotation event was initiated will be lost.

`type` The key binding invoked.

### \[virtual\] void KComboBox::setAutoCompletion(bool *autocomplete*) {#setAutoCompletion}

If `true`, the completion mode will be set to automatic. Otherwise, it is defaulted to the global setting. This method has been replaced by the more comprehensive [setCompletionMode](kcompletionbase.md#setCompletionMode)().

`autocomplete` Flag to enable/disable automatic completion mode.

> **Note:** Setter function for property [autoCompletion](kcombobox.md#autoCompletion-prop).

*See also* [autoCompletion](kcombobox.md#autoCompletion)()

### \[override virtual slot\] void KComboBox::setCompletedItems(const QStringList &*items*, bool *autoSuggest* = true) {#setCompletedItems}

Reimplements: [KCompletionBase::setCompletedItems(const QStringList &items, bool autoSuggest)](kcompletionbase.md#setCompletedItems).

Sets `items` into the completion box if [completionMode](kcompletionbase.md#completionMode)() is CompletionPopup. The popup will be shown immediately.

### \[override virtual slot\] void KComboBox::setCompletedText(*const QString &*) {#setCompletedText}

Reimplements: [KCompletionBase::setCompletedText(const QString &text)](kcompletionbase.md#setCompletedText).

Sets the completed text in the line edit appropriately.

This function is an implementation for [KCompletionBase::setCompletedText](kcompletionbase.md#setCompletedText).

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kComboBox, qOverload<const QString &>(&KComboBox::setCompletedText));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kComboBox, [receiver = kComboBox](const QString &) { receiver->setCompletedText(arg1); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).

### \[virtual protected\] void KComboBox::setCompletedText(const QString &*text*, bool *marked*) {#setCompletedText-1}

This function sets the line edit text and highlights the text appropriately if the boolean value is set to true.

`text` The text to be set in the line edit

`marked` Whether the text inserted should be highlighted

### \[slot\] void KComboBox::setCurrentItem(const QString &*item*, bool *insert* = false, int *index* = -1) {#setCurrentItem}

Selects the first item that matches `item`.

If there is no such item, it is inserted at position `index` if `insert` is true. Otherwise, no item is selected.

### void KComboBox::setEditUrl(const QUrl &*url*) {#setEditUrl}

Sets `url` into the edit field of the combo box.

It uses [QUrl::toDisplayString](https://doc.qt.io/qt-6/qurl.html#toDisplayString)() so that the url is properly decoded for displaying.

### void KComboBox::setEditable(bool *editable*) {#setEditable}

Reimplemented so that setEditable(true) creates a [KLineEdit](klineedit.md) instead of [QLineEdit](https://doc.qt.io/qt-6/qlineedit.html).

Note that [QComboBox::setEditable](https://doc.qt.io/qt-6/qcombobox.html#editable-prop) is not virtual, so do not use a [KComboBox](kcombobox.md) in a [QComboBox](https://doc.qt.io/qt-6/qcombobox.html) pointer.

### \[virtual\] void KComboBox::setLineEdit(*QLineEdit \**) {#setLineEdit}

Reimplemented for internal reasons. API remains unaffected. Note that [QComboBox::setLineEdit](https://doc.qt.io/qt-6/qcombobox.html#setLineEdit) is not virtual in Qt4, do not use a [KComboBox](kcombobox.md) in a [QComboBox](https://doc.qt.io/qt-6/qcombobox.html) pointer.

NOTE: Only editable combo boxes can have a line editor. As such any attempt to assign a line edit to a non-editable combo box will simply be ignored.

### void KComboBox::setTrapReturnKey(bool *trap*) {#setTrapReturnKey}

By default, [KComboBox](kcombobox.md) recognizes Key\_Return and Key\_Enter and emits the [returnPressed](kcombobox.md#returnPressed)(const [QString](https://doc.qt.io/qt-6/qstring.html) &) signal, but it also lets the event pass, for example causing a dialog's default button to be called.

Call this method with `trap` set to true to make [KComboBox](kcombobox.md) stop these events. The signals will still be emitted of course.

> **Note:** This only affects editable combo boxes.

> **Note:** Setter function for property [trapReturnKey](kcombobox.md#trapReturnKey-prop).

*See also* [trapReturnKey](kcombobox.md#trapReturnKey)(), setTrapReturnKey()

### \[signal\] void KComboBox::substringCompletion(*const QString &*) {#substringCompletion}

Emitted when the shortcut for substring completion is pressed.

### \[signal\] void KComboBox::textRotation(*KCompletionBase::KeyBindingType*) {#textRotation}

Emitted when the text rotation key bindings are pressed.

The argument indicates which key binding was pressed. In this case this can be either one of four values: PrevCompletionMatch, NextCompletionMatch, RotateUp or RotateDown.

Note that this signal is *not* emitted if the completion mode is set to CompletionNone.

*See also* [KCompletionBase::setKeyBinding](kcompletionbase.md#setKeyBinding)(), for, details

### bool KComboBox::trapReturnKey() const {#trapReturnKey}

Returns `true` if Key\_Return or Key\_Enter input events will be stopped or `false` if they will be propagated.

> **Note:** Getter function for property [trapReturnKey](kcombobox.md#trapReturnKey-prop).

*See also* [setTrapReturnKey](kcombobox.md#setTrapReturnKey)()

### bool KComboBox::urlDropsEnabled() const {#urlDropsEnabled}

Returns `true` when decoded URL drops are enabled
