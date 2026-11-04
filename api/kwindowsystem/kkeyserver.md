---
title: "KKeyServer Namespace"
description: "A collection of functions for the conversion of key presses and their modifiers from the window system specific format to the generic format and vice-versa."
---

# KKeyServer Namespace

A collection of functions for the conversion of key presses and their modifiers from the window system specific format to the generic format and vice-versa. [More...](#details)

- **Header:** `#include <KKeyServer>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KWindowSystem)`  
  `target_link_libraries(mytarget PRIVATE KF6::KWindowSystem)`

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### uint KKeyServer::accelModMaskX() {#accelModMaskX}

Returns bitwise OR'ed mask containing Shift, Ctrl, Alt, and Win (if available).

*See also* [modXShift](kkeyserver.md#modXShift)(), [modXLock](kkeyserver.md#modXLock)(), [modXCtrl](kkeyserver.md#modXCtrl)(), [modXAlt](kkeyserver.md#modXAlt)(), [modXNumLock](kkeyserver.md#modXNumLock)(), modXWin(), [modXScrollLock](kkeyserver.md#modXScrollLock)()

### bool KKeyServer::initializeMods() {#initializeMods}

Initialises the values to return for the mod\*() functions below. Called automatically by those functions if not already initialized.

### bool KKeyServer::isShiftAsModifierAllowed(int *keyQt*) {#isShiftAsModifierAllowed}

Test if the shift modifier should be recorded for a given key.

For example, if shift+5 produces '%' Qt wants ctrl+shift+5 recorded as ctrl+% and in that case this function would return false.

### QList\<int\> KKeyServer::keyQtToCodeXs(int *keyQt*) {#keyQtToCodeXs}

Extracts the codes from the given Qt key.

`keyQt` the qt key code

`return` the codes; empty if unsuccessful

### bool KKeyServer::keyQtToModX(int *keyQt*, uint \**mod*) {#keyQtToModX}

Extracts the modifiers from the given Qt key and converts them in a mask of X11 modifiers.

`keyQt` the qt key code

`mod` if successful, the modifiers will be written here

Returns true if successful, false otherwise

### QList\<int\> KKeyServer::keyQtToSymXs(int *keyQt*) {#keyQtToSymXs}

Extracts the symbols from the given Qt key and converts it to an X11 symbol + modifiers.

`keyQt` the qt key code

Returns the symbols; emtpy if unsuccessful

### bool KKeyServer::keyboardHasMetaKey() {#keyboardHasMetaKey}

Returns true if the current keyboard layout supports the Meta key. Specifically, whether the Super or Meta keys are assigned to an X modifier. Returns true if the keyboard has a Meta key

*See also* [modXMeta](kkeyserver.md#modXMeta)()

### QString KKeyServer::modToStringUser(uint *mod*) {#modToStringUser}

Converts the mask of ORed KKey::ModFlag modifiers to a user-readable string.

`mod` the mask of ORed KKey::ModFlag modifiers

Returns the user-readable string (in English)

### uint KKeyServer::modXAlt() {#modXAlt}

Returns the X11 Alt (Mod1) modifier mask/flag.

*See also* [accelModMaskX](kkeyserver.md#accelModMaskX)()

### uint KKeyServer::modXCtrl() {#modXCtrl}

Returns the X11 Ctrl modifier mask/flag.

*See also* [accelModMaskX](kkeyserver.md#accelModMaskX)()

### uint KKeyServer::modXLock() {#modXLock}

Returns the X11 Lock modifier mask/flag.

*See also* [accelModMaskX](kkeyserver.md#accelModMaskX)()

### uint KKeyServer::modXMeta() {#modXMeta}

Returns the X11 Win (Mod3) modifier mask/flag.

*See also* keyboardHasWinKey(), [accelModMaskX](kkeyserver.md#accelModMaskX)()

### uint KKeyServer::modXModeSwitch() {#modXModeSwitch}

Returns the X11 Mode\_switch modifier mask/flag.

*See also* [accelModMaskX](kkeyserver.md#accelModMaskX)()

### uint KKeyServer::modXNumLock() {#modXNumLock}

Returns the X11 NumLock modifier mask/flag.

*See also* [accelModMaskX](kkeyserver.md#accelModMaskX)()

### uint KKeyServer::modXScrollLock() {#modXScrollLock}

Returns the X11 ScrollLock modifier mask/flag.

*See also* [accelModMaskX](kkeyserver.md#accelModMaskX)()

### uint KKeyServer::modXShift() {#modXShift}

Returns the X11 Shift modifier mask/flag.

*See also* [accelModMaskX](kkeyserver.md#accelModMaskX)()

### bool KKeyServer::modXToQt(uint *modX*, int \**modQt*) {#modXToQt}

Converts the mask of ORed X11 modifiers to a mask of ORed Qt key code modifiers.

`modX` the mask of X11 modifiers

`modQt` the mask of Qt key code modifiers will be written here if successful

Returns true if successful, false otherwise

### bool KKeyServer::symXModXToKeyQt(uint32\_t *keySym*, uint16\_t *modX*, int \**keyQt*) {#symXModXToKeyQt}

Converts the given symbol and modifier combination to a Qt key code.

`keySym` the X key symbol

`modX` the mask of X11 modifiers

`keyQt` if successful, the qt key code will be written here

Returns true if successful, false otherwise

### bool KKeyServer::xEventToQt(XEvent \**e*, int \**keyModQt*) {#xEventToQt}

Converts an X keypress event into a Qt key + modifier code

`e` the X11 keypress event

`keyModQt` the Qt keycode and mask of Qt key code modifiers will be written here if successful

Returns true if successful, false otherwise

### bool KKeyServer::xcbKeyPressEventToQt(xcb\_generic\_event\_t \**e*, int \**keyModQt*) {#xcbKeyPressEventToQt}

Converts an XCB keypress event into a Qt key + modifier code

`e` the XCB keypress event

`keyModQt` the Qt keycode and mask of Qt key code modifiers will be written here if successful

Returns true if successful, false otherwise

### bool KKeyServer::xcbKeyPressEventToQt(xcb\_key\_press\_event\_t \**e*, int \**keyModQt*) {#xcbKeyPressEventToQt-1}

Overloaded method for convenience.
