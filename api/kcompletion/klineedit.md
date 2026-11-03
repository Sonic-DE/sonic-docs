---
title: "KLineEdit Class"
description: "An enhanced QLineEdit widget for inputting text."
---

# KLineEdit Class

An enhanced [QLineEdit](https://doc.qt.io/qt-6/qlineedit.html) widget for inputting text. [More...](#details)

- **Header:** `#include <KLineEdit>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Completion)`  
  `target_link_libraries(mytarget PRIVATE KF6::Completion)`
- **Inherits:** [QLineEdit](https://doc.qt.io/qt-6/qlineedit.html) and [KCompletionBase](kcompletionbase.md)

[List of all members, including inherited members](klineedit-members.md)

## Properties

- [squeezedTextEnabled : bool](#squeezedTextEnabled-prop)
- [trapEnterKeyEvent : bool](#trapEnterKeyEvent-prop)

## Public Functions

- [KLineEdit(QWidget \*parent = nullptr)](#KLineEdit)
- [KLineEdit(const QString &string, QWidget \*parent = nullptr)](#KLineEdit-1)
- [QSize clearButtonUsedSize() const](#clearButtonUsedSize)
- [KCompletionBox \*completionBox(bool create = true)](#completionBox)
- [void doCompletion(const QString &text)](#doCompletion)
- [bool isSqueezedTextEnabled() const](#isSqueezedTextEnabled)
- [QString originalText() const](#originalText)
- [void setCompletionBox(KCompletionBox \*box)](#setCompletionBox)
- [void setCompletionModeDisabled(KCompletion::CompletionMode mode, bool disable = true)](#setCompletionModeDisabled)
- [void setSqueezedTextEnabled(bool enable)](#setSqueezedTextEnabled)
- [void setTrapReturnKey(bool trap)](#setTrapReturnKey)
- [void setUrl(const QUrl &url)](#setUrl)
- [bool trapReturnKey() const](#trapReturnKey)
- [bool urlDropsEnabled() const](#urlDropsEnabled)
- [QString userText() const](#userText)

## Public Slots

- [void makeCompletion(const QString &)](#makeCompletion)
- [void rotateText(KCompletionBase::KeyBindingType type)](#rotateText)
- [void setCompletedItems(const QStringList &items, bool autoSuggest = true)](#setCompletedItems)
- [void setReadOnly(bool)](#setReadOnly)
- [void setSqueezedText(const QString &text)](#setSqueezedText)
- [void userCancelled(const QString &cancelText)](#userCancelled)

## Signals

- [void aboutToShowContextMenu(QMenu \*contextMenu)](#aboutToShowContextMenu)
- [void clearButtonClicked()](#clearButtonClicked)
- [void completion(const QString &)](#completion)
- [void completionBoxActivated(const QString &)](#completionBoxActivated)
- [void completionModeChanged(KCompletion::CompletionMode)](#completionModeChanged)
- [void returnKeyPressed(const QString &text)](#returnKeyPressed)
- [void substringCompletion(const QString &)](#substringCompletion)
- [void textRotation(KCompletionBase::KeyBindingType)](#textRotation)

## Protected Functions

- [bool autoSuggest() const](#autoSuggest)
- [void setCompletedText(const QString &, bool)](#setCompletedText)
- [void setUserSelection(bool userSelection)](#setUserSelection)

## Detailed Description {#details}

This widget inherits from [QLineEdit](https://doc.qt.io/qt-6/qlineedit.html) and implements the following additional functionalities:

- a completion object that provides both automatic and manual text completion as well as multiple match iteration features
- configurable key-bindings to activate these features
- a popup-menu item that can be used to allow the user to set text completion modes on the fly based on their preference

To support these features [KLineEdit](klineedit.md) also emits a few more additional signals:

- completion(const [QString](https://doc.qt.io/qt-6/qstring.html) &): this signal can be connected to a slot that will assist the user in filling out the remaining text
- [textRotation](klineedit.md#textRotation)(KeyBindingType): this signal is intended to be used to iterate through the list of all possible matches whenever there is more than one match for the entered text
- [returnKeyPressed](klineedit.md#returnKeyPressed)(const [QString](https://doc.qt.io/qt-6/qstring.html) &): this signal provides the current text in the widget as its argument whenever appropriate (this is in addition to the [QLineEdit::returnPressed](https://doc.qt.io/qt-6/qlineedit.html#returnPressed)() signal which [KLineEdit](klineedit.md) inherits from [QLineEdit](https://doc.qt.io/qt-6/qlineedit.html)).

This widget by default creates a completion object when you invoke the completionObject(bool) member function for the first time or use setCompletionObject([KCompletion](kcompletion-module.md) \*, bool) to assign your own completion object. Additionally, to make this widget more functional, [KLineEdit](klineedit.md) will by default handle the text rotation and completion events internally when a completion object is created through either one of the methods mentioned above. If you do not need this functionality, simply use [KCompletionBase::setHandleSignals](kcompletionbase.md#setHandleSignals)(bool) or set the boolean parameter in the above functions to false.

The default key-bindings for completion and rotation is determined from the global settings in KStandardShortcut. These values, however, can be overridden locally by invoking [KCompletionBase::setKeyBinding](kcompletionbase.md#setKeyBinding)(). The values can easily be reverted back to the default setting, by simply calling [useGlobalKeyBindings](kcompletionbase.md#useGlobalKeyBindings)(). An alternate method would be to default individual key-bindings by using [setKeyBinding](kcompletionbase.md#setKeyBinding)() with the default second argument.

If EchoMode for this widget is set to something other than [QLineEdit::Normal](https://doc.qt.io/qt-6/qlineedit.html#EchoMode-enum), the completion mode will always be defaulted to CompletionNone. This is done purposefully to guard against protected entries, such as passwords, being cached in [KCompletion](kcompletion-module.md)'s list. Hence, if the EchoMode is not [QLineEdit::Normal](https://doc.qt.io/qt-6/qlineedit.html#EchoMode-enum), the completion mode is automatically disabled.

A read-only [KLineEdit](klineedit.md) will have the same background color as a disabled [KLineEdit](klineedit.md), but its foreground color will be the one used for the read-write mode. This differs from [QLineEdit](https://doc.qt.io/qt-6/qlineedit.html)'s implementation and is done to give visual distinction between the three different modes: disabled, read-only, and read-write.

To enable the basic completion feature:

```cpp
KLineEdit *edit = new KLineEdit(this);
KCompletion *comp = edit->completionObject();
// Connect to the Return pressed signal - optional
connect(edit, &KLineEdit::returnKeyPressed, comp, [this](const QString &text) { addItem(text); });
```

To use a customized completion object or your own completion object:

```cpp
KLineEdit *edit = new KLineEdit(this);
KUrlCompletion *comp = new KUrlCompletion();
edit->setCompletionObject(comp);
// Connect to the return pressed signal - optional
connect(edit, &KLineEdit::returnKeyPressed, comp, [this](const QString &text) { addItem(text); });
```

Note if you specify your own completion object you have to either delete it when you don't need it anymore, or you can tell [KLineEdit](klineedit.md) to delete it for you:

```cpp
edit->setAutoDeleteCompletionObject(true);
```

Miscellaneous function calls:

```cpp
// Tell the widget to not handle completion and iteration automatically
edit->setHandleSignals(false);

// Set your own key-bindings for a text completion mode
edit->setKeyBinding(KCompletionBase::TextCompletion, Qt::End);

// Hide the context (popup) menu
edit->setContextMenuPolicy(Qt::NoContextMenu);

// Default the key-bindings back to the default system settings
edit->useGlobalKeyBindings();
```

## Property Documentation {#property-documentation}

### squeezedTextEnabled : bool {#squeezedTextEnabled-prop}

**Access functions:**

- `bool` **[isSqueezedTextEnabled](klineedit.md#isSqueezedTextEnabled)**() const
- `void` **[setSqueezedTextEnabled](klineedit.md#setSqueezedTextEnabled)**(`bool` *enable*)

### trapEnterKeyEvent : bool {#trapEnterKeyEvent-prop}

**Access functions:**

- `bool` **[trapReturnKey](klineedit.md#trapReturnKey)**() const
- `void` **[setTrapReturnKey](klineedit.md#setTrapReturnKey)**(`bool` *trap*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KLineEdit::KLineEdit(QWidget \**parent* = nullptr) {#KLineEdit}

Constructs a line edit `parent` The parent widget of the line edit.

### \[explicit\] KLineEdit::KLineEdit(const QString &*string*, QWidget \**parent* = nullptr) {#KLineEdit-1}

Constructs a [KLineEdit](klineedit.md) object with a default text, a parent, and a name.

`string` Text to be shown in the edit widget. `parent` The parent widget of the line edit.

### \[signal\] void KLineEdit::aboutToShowContextMenu(QMenu \**contextMenu*) {#aboutToShowContextMenu}

Emitted before the context menu is displayed.

The signal allows you to add your own entries into the the context menu that is created on demand.

> **Note:** Do not store the pointer to the [QMenu](https://doc.qt.io/qt-6/qmenu.html) provided through since it is created and deleted on demand.

`contextMenu` the context menu about to be displayed

### \[protected\] bool KLineEdit::autoSuggest() const {#autoSuggest}

Whether in current state text should be auto-suggested

### \[signal\] void KLineEdit::clearButtonClicked() {#clearButtonClicked}

Emitted when the user clicked on the clear button

### QSize KLineEdit::clearButtonUsedSize() const {#clearButtonUsedSize}

Returns the size used by the clear button

### \[signal\] void KLineEdit::completion(*const QString &*) {#completion}

Emitted when the completion key is pressed.

Please note that this signal is *not* emitted if the completion mode is set to CompletionNone or EchoMode is *normal*.

### \[virtual\] KCompletionBox \*KLineEdit::completionBox(bool *create* = true) {#completionBox}

This method will create a completion-box if none is there, yet.

`create` Set this to false if you don't want the box to be created i.e. to test if it is available.

Returns the completion-box, that is used in completion mode CompletionPopup.

*See also* [setCompletionBox](klineedit.md#setCompletionBox)()

### \[signal\] void KLineEdit::completionBoxActivated(*const QString &*) {#completionBoxActivated}

Emitted whenever the completion box is activated.

### \[signal\] void KLineEdit::completionModeChanged(*KCompletion::CompletionMode*) {#completionModeChanged}

Emitted when the user changed the completion mode by using the popupmenu.

### void KLineEdit::doCompletion(const QString &*text*) {#doCompletion}

Do completion now. This is called automatically when typing a key for instance. Emits [completion](klineedit.md#completion)() and/or calls [makeCompletion](klineedit.md#makeCompletion)(), depending on emitSignals and handleSignals.

### bool KLineEdit::isSqueezedTextEnabled() const {#isSqueezedTextEnabled}

Returns `true` if text squeezing is enabled.

This is only valid when the widget is in read-only mode.

> **Note:** Getter function for property [squeezedTextEnabled](klineedit.md#squeezedTextEnabled-prop).

### \[virtual protected slot\] void KLineEdit::makeCompletion(*const QString &*) {#makeCompletion}

Completes the remaining text with a matching one from a given list.

### QString KLineEdit::originalText() const {#originalText}

Returns the original text if text squeezing is enabled. If the widget is not in "read-only" mode, this function returns the same thing as [QLineEdit::text](https://doc.qt.io/qt-6/qlineedit.html#text-prop)().

*See also* [QLineEdit](https://doc.qt.io/qt-6/qlineedit.html)

### \[signal\] void KLineEdit::returnKeyPressed(const QString &*text*) {#returnKeyPressed}

Emitted when the user presses the Return or Enter key.

The argument is the current text. Note that this signal is *not* emitted if the widget's `EchoMode` is set to [QLineEdit::EchoMode](https://doc.qt.io/qt-6/qlineedit.html#EchoMode-enum).

### \[slot\] void KLineEdit::rotateText(KCompletionBase::KeyBindingType *type*) {#rotateText}

Iterates through all possible matches of the completed text or the history list.

This function simply iterates over all possible matches in case multiple matches are found as a result of a text completion request. It will have no effect if only a single match is found.

`type` The key-binding invoked.

### \[override virtual slot\] void KLineEdit::setCompletedItems(const QStringList &*items*, bool *autoSuggest* = true) {#setCompletedItems}

Reimplements: [KCompletionBase::setCompletedItems(const QStringList &items, bool autoSuggest)](kcompletionbase.md#setCompletedItems).

Same as the above function except it allows you to temporarily turn off text completion in CompletionPopupAuto mode.

`items` list of completion matches to be shown in the completion box.

`autoSuggest` true if you want automatic text completion (suggestion) enabled.

### \[virtual protected\] void KLineEdit::setCompletedText(*const QString &*, *bool*) {#setCompletedText}

This function simply sets the lineedit text and highlights the text appropriately if the boolean value is set to `true`.

### void KLineEdit::setCompletionBox(KCompletionBox \**box*) {#setCompletionBox}

Set the completion-box to be used in completion mode CompletionPopup. This will do nothing if a completion-box already exists.

`box` The [KCompletionBox](kcompletionbox.md) to set

*See also* [completionBox](klineedit.md#completionBox)()

### void KLineEdit::setCompletionModeDisabled(KCompletion::CompletionMode *mode*, bool *disable* = true) {#setCompletionModeDisabled}

Disables completion modes by making them non-checkable.

The context menu allows to change the completion mode. This method allows to disable some modes.

### \[virtual slot\] void KLineEdit::setReadOnly(*bool*) {#setReadOnly}

Sets the lineedit to read-only. Similar to [QLineEdit::setReadOnly](https://doc.qt.io/qt-6/qlineedit.html#readOnly-prop) but also takes care of the background color, and the clear button.

### \[slot\] void KLineEdit::setSqueezedText(const QString &*text*) {#setSqueezedText}

Squeezes `text` into the line edit.

This can only be used with read-only line-edits.

### void KLineEdit::setSqueezedTextEnabled(bool *enable*) {#setSqueezedTextEnabled}

Enable text squeezing whenever the supplied text is too long. Only works for "read-only" mode.

Note that once text squeezing is enabled, [QLineEdit::text](https://doc.qt.io/qt-6/qlineedit.html#text-prop)() and [QLineEdit::displayText](https://doc.qt.io/qt-6/qlineedit.html#displayText-prop)() return the squeezed text. If you want the original text, use [originalText](klineedit.md#originalText).

> **Note:** Setter function for property [squeezedTextEnabled](klineedit.md#squeezedTextEnabled-prop).

*See also* [isSqueezedTextEnabled](klineedit.md#isSqueezedTextEnabled)(), [QLineEdit](https://doc.qt.io/qt-6/qlineedit.html)

### void KLineEdit::setTrapReturnKey(bool *trap*) {#setTrapReturnKey}

By default, [KLineEdit](klineedit.md) recognizes `Key_Return` and `Key_Enter` and emits the [returnPressed](https://doc.qt.io/qt-6/qlineedit.html#returnPressed)() signals, but it also lets the event pass, for example causing a dialog's default-button to be called.

Call this method with `trap` = `true` to make [KLineEdit](klineedit.md) stop these events. The signals will still be emitted of course.

> **Note:** Setter function for property [trapEnterKeyEvent](klineedit.md#trapEnterKeyEvent-prop).

*See also* [trapReturnKey](klineedit.md#trapReturnKey)()

### void KLineEdit::setUrl(const QUrl &*url*) {#setUrl}

Sets `url` into the lineedit. It uses [QUrl::toDisplayString](https://doc.qt.io/qt-6/qurl.html#toDisplayString)() so that the url is properly decoded for displaying.

### \[protected\] void KLineEdit::setUserSelection(bool *userSelection*) {#setUserSelection}

Sets the widget in userSelection mode or in automatic completion selection mode. This changes the colors of selections.

### \[signal\] void KLineEdit::substringCompletion(*const QString &*) {#substringCompletion}

Emitted when the shortcut for substring completion is pressed.

### \[signal\] void KLineEdit::textRotation(*KCompletionBase::KeyBindingType*) {#textRotation}

Emitted when the text rotation key-bindings are pressed.

The argument indicates which key-binding was pressed. In [KLineEdit](klineedit.md)'s case this can be either one of two values: PrevCompletionMatch or NextCompletionMatch. See [KCompletionBase::setKeyBinding](kcompletionbase.md#setKeyBinding) for details.

Note that this signal is not emitted if the completion mode is set to CompletionNone or [echoMode](https://doc.qt.io/qt-6/qlineedit.html#echoMode-prop)() is *not* normal.

### bool KLineEdit::trapReturnKey() const {#trapReturnKey}

Returns `true` if keyevents of `Key_Return` or `Key_Enter` will be stopped or if they will be propagated.

> **Note:** Getter function for property [trapEnterKeyEvent](klineedit.md#trapEnterKeyEvent-prop).

*See also* [setTrapReturnKey](klineedit.md#setTrapReturnKey)()

### bool KLineEdit::urlDropsEnabled() const {#urlDropsEnabled}

Returns `true` when decoded URL drops are enabled

### \[protected slot\] void KLineEdit::userCancelled(const QString &*cancelText*) {#userCancelled}

Resets the current displayed text. Call this function to revert a text completion if the user cancels the request. Mostly applies to popup completions.

### QString KLineEdit::userText() const {#userText}

Returns the text as given by the user (i.e. not autocompleted) if the widget has autocompletion disabled, this function returns the same as [QLineEdit::text](https://doc.qt.io/qt-6/qlineedit.html#text-prop)().
