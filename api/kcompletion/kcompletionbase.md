---
title: "KCompletionBase Class"
description: "An abstract base class for adding a completion feature into widgets."
---

# KCompletionBase Class

An abstract base class for adding a completion feature into widgets. [More...](#details)

- **Header:** `#include <KCompletionBase>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Completion)`  
  `target_link_libraries(mytarget PRIVATE KF6::Completion)`
- **Inherited By:** [KComboBox](kcombobox.md) and [KLineEdit](klineedit.md)

[List of all members, including inherited members](kcompletionbase-members.md)

## Public Types

- [KCompletionBase::KeyBindingMap](#KeyBindingMap-typedef)
- [enum KCompletionBase::KeyBindingType](#KeyBindingType-enum)

## Public Functions

- [KCompletionBase()](#KCompletionBase)
- [KCompletion \*compObj() const](#compObj)
- [KCompletion::CompletionMode completionMode() const](#completionMode)
- [KCompletion \*completionObject(bool handleSignals = true)](#completionObject)
- [bool emitSignals() const](#emitSignals)
- [bool handleSignals() const](#handleSignals)
- [bool isCompletionObjectAutoDeleted() const](#isCompletionObjectAutoDeleted)
- [QList\<QKeySequence\> keyBinding(KCompletionBase::KeyBindingType item) const](#keyBinding)
- [void setAutoDeleteCompletionObject(bool autoDelete)](#setAutoDeleteCompletionObject)
- [void setCompletedItems(const QStringList &items, bool autoSuggest = true)](#setCompletedItems)
- [void setCompletedText(const QString &text)](#setCompletedText)
- [void setCompletionMode(KCompletion::CompletionMode mode)](#setCompletionMode)
- [void setCompletionObject(KCompletion \*completionObject, bool handleSignals = true)](#setCompletionObject)
- [void setEmitSignals(bool emitRotationSignals)](#setEmitSignals)
- [void setEnableSignals(bool enable)](#setEnableSignals)
- [void setHandleSignals(bool handle)](#setHandleSignals)
- [bool setKeyBinding(KCompletionBase::KeyBindingType item, const QList\<QKeySequence\> &key)](#setKeyBinding)
- [void useGlobalKeyBindings()](#useGlobalKeyBindings)

## Protected Functions

- [KCompletionBase \*delegate() const](#delegate)
- [KCompletionBase::KeyBindingMap keyBindingMap() const](#keyBindingMap)
- [void setDelegate(KCompletionBase \*delegate)](#setDelegate)
- [void setKeyBindingMap(KCompletionBase::KeyBindingMap keyBindingMap)](#setKeyBindingMap)

## Detailed Description {#details}

This is a convenience class that provides the basic functions needed to add text completion support into widgets. All that is required is an implementation for the pure virtual function [setCompletedText](kcompletionbase.md#setCompletedText)(). Refer to [KLineEdit](klineedit.md) or [KComboBox](kcombobox.md) to see how easily such support can be added using this as a base class.

## Member Type Documentation {#member-type-documentation}

### KCompletionBase::KeyBindingMap {#KeyBindingMap-typedef}

Map for the key binding types mentioned above.

### enum KCompletionBase::KeyBindingType {#KeyBindingType-enum}

Constants that represent the items whose shortcut key binding is programmable. The default key bindings for these items are defined in KStandardShortcut.

| Constant | Value | Description |
| --- | --- | --- |
| `KCompletionBase::TextCompletion` | `0` | Text completion (by default Ctrl-E). |
| `KCompletionBase::PrevCompletionMatch` | `1` | Switch to previous completion (by default Ctrl-Up). |
| `KCompletionBase::NextCompletionMatch` | `2` | Switch to next completion (by default Ctrl-Down). |
| `KCompletionBase::SubstringCompletion` | `3` | Substring completion (by default Ctrl-T). |

## Member Function Documentation {#member-function-documentation}

### KCompletionBase::KCompletionBase() {#KCompletionBase}

Default constructor.

### KCompletion \*KCompletionBase::compObj() const {#compObj}

Returns a pointer to the completion object.

This method is only different from [completionObject](kcompletionbase.md#completionObject)() in that it does not create a new [KCompletion](kcompletion-module.md) object even if the internal pointer is `nullptr`. Use this method to get the pointer to a completion object when inheriting so that you will not inadvertently create it.

Returns the completion object or `nullptr` if one does not exist.

### KCompletion::CompletionMode KCompletionBase::completionMode() const {#completionMode}

Returns the current completion mode.

*See also* [setCompletionMode](kcompletionbase.md#setCompletionMode)()

### KCompletion \*KCompletionBase::completionObject(bool *handleSignals* = true) {#completionObject}

Returns a pointer to the current completion object.

If the completion object does not exist, it is automatically created and by default handles all the completion signals internally unless [handleSignals](kcompletionbase.md#handleSignals) is set to `false`. It is also automatically destroyed when the destructor is called. You can change this default behavior using the [setAutoDeleteCompletionObject](kcompletionbase.md#setAutoDeleteCompletionObject) and [setHandleSignals](kcompletionbase.md#setHandleSignals) member functions.

See also [compObj](kcompletionbase.md#compObj).

`handleSignals` if true, handles completion signals internally.

*See also* [setCompletionObject](kcompletionbase.md#setCompletionObject)()

### \[protected\] KCompletionBase \*KCompletionBase::delegate() const {#delegate}

Returns the delegation object, or `nullptr` if there is none

*See also* [setDelegate](kcompletionbase.md#setDelegate)()

### bool KCompletionBase::emitSignals() const {#emitSignals}

Returns `true` if the object emits the signals.

*See also* [setEmitSignals](kcompletionbase.md#setEmitSignals)()

### bool KCompletionBase::handleSignals() const {#handleSignals}

Returns `true` if the object handles the signals.

*See also* [setHandleSignals](kcompletionbase.md#setHandleSignals)()

### bool KCompletionBase::isCompletionObjectAutoDeleted() const {#isCompletionObjectAutoDeleted}

Returns true if the completion object is deleted upon this widget's destruction.

See [setCompletionObject](kcompletionbase.md#setCompletionObject)() and enableCompletion() for details.

Returns `true` if the completion object will be deleted automatically

### QList\<QKeySequence\> KCompletionBase::keyBinding(KCompletionBase::KeyBindingType *item*) const {#keyBinding}

Returns the key binding used for the specified item.

This method returns the key binding used to activate the feature given by `item`. If the binding contains modifier key(s), the sum of the modifier key and the actual key code is returned.

`item` the item to check

Returns the key binding used for the feature given by `item`.

*See also* [setKeyBinding](kcompletionbase.md#setKeyBinding)

### \[protected\] KCompletionBase::KeyBindingMap KCompletionBase::keyBindingMap() const {#keyBindingMap}

Returns a key binding map.

This method is the same as getKeyBinding(), except that it returns the whole keymap containing the key bindings.

Returns the key binding used for the feature given by `item`.

*See also* [setKeyBindingMap](kcompletionbase.md#setKeyBindingMap)()

### void KCompletionBase::setAutoDeleteCompletionObject(bool *autoDelete*) {#setAutoDeleteCompletionObject}

Sets the completion object when this widget's destructor is called.

If the argument is set to `true`, the completion object is deleted when this widget's destructor is called.

`autoDelete` if `true`, delete completion object on destruction.

### \[pure virtual\] void KCompletionBase::setCompletedItems(const QStringList &*items*, bool *autoSuggest* = true) {#setCompletedItems}

A pure virtual function that must be implemented by all inheriting classes.

`items` the list of completed items

`autoSuggest` if `true`, the first element of `items` is automatically completed (i.e. preselected).

### \[pure virtual\] void KCompletionBase::setCompletedText(const QString &*text*) {#setCompletedText}

A pure virtual function that must be implemented by all inheriting classes.

This function is intended to allow external completion implementations to set completed text appropriately. It is mostly relevant when the completion mode is set to CompletionAuto and CompletionManual modes. See KCompletionBase::setCompletedText. Does nothing in CompletionPopup mode, as all available matches will be shown in the popup.

`text` the completed text to be set in the widget.

### \[virtual\] void KCompletionBase::setCompletionMode(KCompletion::CompletionMode *mode*) {#setCompletionMode}

Sets the type of completion to be used.

`mode` Completion type

*See also* [completionMode](kcompletionbase.md#completionMode)()

### \[virtual\] void KCompletionBase::setCompletionObject(KCompletion \**completionObject*, bool *handleSignals* = true) {#setCompletionObject}

Sets up the completion object to be used.

This method assigns the completion object and sets it up to automatically handle the completion and rotation signals internally. You should use this function if you want to share one completion object among your widgets or need to use a customized completion object.

The object assigned through this method is not deleted when this object's destructor is invoked unless you explicitly call [setAutoDeleteCompletionObject](kcompletionbase.md#setAutoDeleteCompletionObject) after calling this method. Be sure to set the bool argument to false, if you want to handle the completion signals yourself.

`completionObject` a [KCompletion](kcompletion-module.md) or a derived child object.

`handleCompletionSignals` if `true`, handles completion signals internally.

*See also* [completionObject](kcompletionbase.md#completionObject)()

### \[protected\] void KCompletionBase::setDelegate(KCompletionBase \**delegate*) {#setDelegate}

Sets or removes the delegation object. If a delegation object is set, all function calls will be forwarded to the delegation object. `delegate` the delegation object, or `nullptr` to remove it

*See also* [delegate](kcompletionbase.md#delegate)()

### void KCompletionBase::setEmitSignals(bool *emitRotationSignals*) {#setEmitSignals}

Sets whether the object emits rotation signals.

`emitRotationSignals` if `false`, disables the emission of rotation signals.

*See also* [emitSignals](kcompletionbase.md#emitSignals)()

### void KCompletionBase::setEnableSignals(bool *enable*) {#setEnableSignals}

Sets the widget's ability to emit text completion and rotation signals.

Invoking this function with `enable` set to `false` will cause the completion and rotation signals not to be emitted. However, unlike setting the completion object to `nullptr` using [setCompletionObject](kcompletionbase.md#setCompletionObject), disabling the emission of the signals through this method does not affect the current completion object.

There is no need to invoke this function by default. When a completion object is created through [completionObject](kcompletionbase.md#completionObject) or [setCompletionObject](kcompletionbase.md#setCompletionObject), these signals are set to emit automatically. Also note that disabling this signals will not necessarily interfere with the objects' ability to handle these events internally. See [setHandleSignals](kcompletionbase.md#setHandleSignals).

`enable` if false, disables the emission of completion and rotation signals.

### \[virtual\] void KCompletionBase::setHandleSignals(bool *handle*) {#setHandleSignals}

Enables this object to handle completion and rotation events internally.

This function simply assigns a boolean value that indicates whether it should handle rotation and completion events or not. Note that this does not stop the object from emitting signals when these events occur.

`handle` if true, it handles completion and rotation internally.

*See also* [handleSignals](kcompletionbase.md#handleSignals)()

### bool KCompletionBase::setKeyBinding(KCompletionBase::KeyBindingType *item*, const QList\<QKeySequence\> &*key*) {#setKeyBinding}

Sets the key binding to be used for manual text completion, text rotation in a history list as well as a completion list.

When the keys set by this function are pressed, a signal defined by the inheriting widget will be activated. If the default value or 0 is specified by the second parameter, then the key binding as defined in the global setting should be used. This method returns false when `key` is negative or the supplied key binding conflicts with another one set for another feature.

> **Note:** To use a modifier key (Shift, Ctrl, Alt) as part of the key binding simply `sum` up the values of the modifier and the actual key. For example, to use CTRL+E, supply `"Qt::CtrlButton | Qt::Key_E"` as the second argument to this function.

`item` the feature whose key binding needs to be set:

- [TextCompletion](kcompletionbase.md#KeyBindingType-enum) the manual completion key binding.
- [PrevCompletionMatch](kcompletionbase.md#KeyBindingType-enum) the previous match key for multiple completion.
- [NextCompletionMatch](kcompletionbase.md#KeyBindingType-enum) the next match key for for multiple completion.
- [SubstringCompletion](kcompletionbase.md#KeyBindingType-enum) the key for substring completion

`key` key binding used to rotate down in a list.

Returns `true` if key binding is successfully set.

*See also* [keyBinding](kcompletionbase.md#keyBinding)

### \[protected\] void KCompletionBase::setKeyBindingMap(KCompletionBase::KeyBindingMap *keyBindingMap*) {#setKeyBindingMap}

Sets the keymap.

`keyBindingMap`

*See also* [keyBindingMap](kcompletionbase.md#keyBindingMap)()

### void KCompletionBase::useGlobalKeyBindings() {#useGlobalKeyBindings}

Sets this object to use global values for key bindings.

This method changes the values of the key bindings for rotation and completion features to the default values provided in KStandardShortcut.

> **Note:** By default, inheriting widgets should use the global key bindings so that there is no need to call this method.
