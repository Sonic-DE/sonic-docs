---
title: "KModifierKeyInfo Class"
description: "Get information about the state of the keyboard's modifier keys."
---

# KModifierKeyInfo Class

Get information about the state of the keyboard's modifier keys. [More...](#details)

- **Header:** `#include <KModifierKeyInfo>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS GuiAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::GuiAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kmodifierkeyinfo-members.md)

## Public Functions

- [KModifierKeyInfo(QObject \*parent = nullptr)](#KModifierKeyInfo)
- [bool isButtonPressed(Qt::MouseButton button) const](#isButtonPressed)
- [bool isKeyLatched(Qt::Key key) const](#isKeyLatched)
- [bool isKeyLocked(Qt::Key key) const](#isKeyLocked)
- [bool isKeyPressed(Qt::Key key) const](#isKeyPressed)
- [const QList\<Qt::Key\> knownKeys() const](#knownKeys)
- [bool knowsKey(Qt::Key key) const](#knowsKey)
- [bool setKeyLatched(Qt::Key key, bool latched)](#setKeyLatched)
- [bool setKeyLocked(Qt::Key key, bool locked)](#setKeyLocked)

## Signals

- [void buttonPressed(Qt::MouseButton button, bool pressed)](#buttonPressed)
- [void keyAdded(Qt::Key key)](#keyAdded)
- [void keyLatched(Qt::Key key, bool latched)](#keyLatched)
- [void keyLocked(Qt::Key key, bool locked)](#keyLocked)
- [void keyPressed(Qt::Key key, bool pressed)](#keyPressed)
- [void keyRemoved(Qt::Key key)](#keyRemoved)

## Detailed Description {#details}

This class provides cross-platform information about the state of the keyboard's modifier keys and the mouse buttons and allows to change the state as well.

It recognizes two states a key can be in:

- locked: eg. caps-locked (a.k.a. toggled)
- latched the key is temporarily locked but will be unlocked upon the next keypress.

An application can either query the states synchronously ([isKeyLatched](kmodifierkeyinfo.md#isKeyLatched)(), [isKeyLocked](kmodifierkeyinfo.md#isKeyLocked)()) or connect to [KModifierKeyInfo](kmodifierkeyinfo.md)'s signals to be notified about changes ([keyLatched](kmodifierkeyinfo.md#keyLatched)(), [keyLocked](kmodifierkeyinfo.md#keyLocked)()).

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KModifierKeyInfo::KModifierKeyInfo(QObject \**parent* = nullptr) {#KModifierKeyInfo}

Default constructor

### \[signal\] void KModifierKeyInfo::buttonPressed(Qt::MouseButton *button*, bool *pressed*) {#buttonPressed}

This signal is emitted whenever the pressed state of a mouse button changes (mouse button press or release).

`button` The mouse button that changed state

`pressed` `true` if the mouse button is now pressed, `false` if is released.

### bool KModifierKeyInfo::isButtonPressed(Qt::MouseButton *button*) const {#isButtonPressed}

Synchronously check if a mouse button is pressed.

`button` The mouse button to check

Returns `true` if the mouse button is pressed, `false` if the mouse button is not pressed or its state is unknown.

### bool KModifierKeyInfo::isKeyLatched(Qt::Key *key*) const {#isKeyLatched}

Synchronously check if a key is latched.

`key` The key to check

Returns `true` if the key is latched, `false` if the key is not latched or unknown.

*See also* [isKeyPressed](kmodifierkeyinfo.md#isKeyPressed), [isKeyLocked](kmodifierkeyinfo.md#isKeyLocked), [keyLatched](kmodifierkeyinfo.md#keyLatched)

### bool KModifierKeyInfo::isKeyLocked(Qt::Key *key*) const {#isKeyLocked}

Synchronously check if a key is locked.

`key` The key to check

Returns `true` if the key is locked, `false` if the key is not locked or unknown.

*See also* [isKeyPressed](kmodifierkeyinfo.md#isKeyPressed), [isKeyLatched](kmodifierkeyinfo.md#isKeyLatched), [keyLocked](kmodifierkeyinfo.md#keyLocked)

### bool KModifierKeyInfo::isKeyPressed(Qt::Key *key*) const {#isKeyPressed}

Synchronously check if a key is pressed.

`key` The key to check

Returns `true` if the key is pressed, `false` if the key is not pressed or unknown.

*See also* [isKeyLatched](kmodifierkeyinfo.md#isKeyLatched), [isKeyLocked](kmodifierkeyinfo.md#isKeyLocked), [keyPressed](kmodifierkeyinfo.md#keyPressed)

### \[signal\] void KModifierKeyInfo::keyAdded(Qt::Key *key*) {#keyAdded}

This signal is emitted whenever a new modifier is found due to the keyboard mapping changing.

`key` The key that was discovered

### \[signal\] void KModifierKeyInfo::keyLatched(Qt::Key *key*, bool *latched*) {#keyLatched}

This signal is emitted whenever the latched state of a key changes.

`key` The key that changed state

`latched` `true` if the key is now latched, `false` if it isn't

*See also* [setKeyLatched](kmodifierkeyinfo.md#setKeyLatched)()

### \[signal\] void KModifierKeyInfo::keyLocked(Qt::Key *key*, bool *locked*) {#keyLocked}

This signal is emitted whenever the locked state of a key changes.

`key` The key that changed state

`locked` `true` if the key is now locked, `false` if it isn't

*See also* [setKeyLocked](kmodifierkeyinfo.md#setKeyLocked)()

### \[signal\] void KModifierKeyInfo::keyPressed(Qt::Key *key*, bool *pressed*) {#keyPressed}

This signal is emitted whenever the pressed state of a key changes (key press or key release).

`key` The key that changed state

`pressed` `true` if the key is now pressed, `false` if is released.

### \[signal\] void KModifierKeyInfo::keyRemoved(Qt::Key *key*) {#keyRemoved}

This signal is emitted whenever a previously known modifier no longer exists due to the keyboard mapping changing.

`key` The key that vanished

### const QList\<Qt::Key\> KModifierKeyInfo::knownKeys() const {#knownKeys}

Get a list of known keys.

Returns list of known keys of which states will be reported.

### bool KModifierKeyInfo::knowsKey(Qt::Key *key*) const {#knowsKey}

Check if a key is known by the underlying window system and can be queried.

`key` The key to check

Returns `true` if the key is available, `false` if it is unknown

### bool KModifierKeyInfo::setKeyLatched(Qt::Key *key*, bool *latched*) {#setKeyLatched}

Set the latched state of a key.

`key` The key to latch

`latched` true to latch the key, false to unlatch it.

Returns `false` if the key is unknown. `true` doesn't guarantee you the operation worked.

*See also* [keyLatched](kmodifierkeyinfo.md#keyLatched)()

### bool KModifierKeyInfo::setKeyLocked(Qt::Key *key*, bool *locked*) {#setKeyLocked}

Set the locked state of a key.

`key` The key to lock

`locked` true to lock the key, false to unlock it.

Return `false` if the key is unknown. `true` doesn't guarantee you the operation worked.

*See also* [keyLocked](kmodifierkeyinfo.md#keyLocked)()
