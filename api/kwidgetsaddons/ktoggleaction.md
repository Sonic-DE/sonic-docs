---
title: "KToggleAction Class"
description: "Checkbox like action."
---

# KToggleAction Class

Checkbox like action. [More...](#details)

- **Header:** `#include <KToggleAction>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QAction](https://doc.qt.io/qt-6/qaction.html)
- **Inherited By:** [KToggleFullScreenAction](ktogglefullscreenaction.md)

[List of all members, including inherited members](ktoggleaction-members.md)

## Public Functions

- [KToggleAction(QObject \*parent)](#KToggleAction)
- [KToggleAction(const QString &text, QObject \*parent)](#KToggleAction-1)
- [KToggleAction(const QIcon &icon, const QString &text, QObject \*parent)](#KToggleAction-2)
- [void setCheckedState(const KGuiItem &checkedItem)](#setCheckedState)

## Public Slots

- [void slotToggled(bool checked)](#slotToggled)

## Detailed Description {#details}

This action provides two states: checked or not.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KToggleAction::KToggleAction(QObject \**parent*) {#KToggleAction}

Constructs an action with the specified parent.

`parent` The action's parent object.

### KToggleAction::KToggleAction(const QString &*text*, QObject \**parent*) {#KToggleAction-1}

Constructs an action with text; a shortcut may be specified by the ampersand character (e.g. "&Option" creates a shortcut with key *O* )

This is the most common [QAction](https://doc.qt.io/qt-6/qaction.html) used when you do not have a corresponding icon (note that it won't appear in the current version of the "Edit ToolBar" dialog, because an action needs an icon to be plugged in a toolbar...).

`text` The text that will be displayed.

`parent` The action's parent object.

### KToggleAction::KToggleAction(const QIcon &*icon*, const QString &*text*, QObject \**parent*) {#KToggleAction-2}

Constructs an action with text and an icon; a shortcut may be specified by the ampersand character (e.g. "&Option" creates a shortcut with key *O* )

This is the other common [QAction](https://doc.qt.io/qt-6/qaction.html) used. Use it when you do have a corresponding icon.

`icon` The icon to display.

`text` The text that will be displayed.

`parent` The action's parent object.

### void KToggleAction::setCheckedState(const KGuiItem &*checkedItem*) {#setCheckedState}

Defines the text (and icon, tooltip, whatsthis) that should be displayed instead of the normal text, when the action is checked. Note that this does not replace the check box in front of the menu. So you should not use it to replace the text "Show \<foo\>" with "Hide \<foo\>", for example.

If hasIcon(), the icon is kept for the 'checked state', unless `checkedItem` defines an icon explicitly. Same thing for tooltip and whatsthis.

### \[virtual protected slot\] void KToggleAction::slotToggled(bool *checked*) {#slotToggled}
