---
title: "KDualAction Class"
description: "An action which can alternate between two texts/icons when triggered."
---

# KDualAction Class

An action which can alternate between two texts/icons when triggered. [More...](#details)

- **Header:** `#include <KDualAction>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QAction](https://doc.qt.io/qt-6/qaction.html)

[List of all members, including inherited members](kdualaction-members.md)

## Public Functions

- [KDualAction(QObject \*parent)](#KDualAction)
- [KDualAction(const QString &inactiveText, const QString &activeText, QObject \*parent)](#KDualAction-1)
- [KGuiItem activeGuiItem() const](#activeGuiItem)
- [QIcon activeIcon() const](#activeIcon)
- [QString activeText() const](#activeText)
- [QString activeToolTip() const](#activeToolTip)
- [bool autoToggle() const](#autoToggle)
- [KGuiItem inactiveGuiItem() const](#inactiveGuiItem)
- [QIcon inactiveIcon() const](#inactiveIcon)
- [QString inactiveText() const](#inactiveText)
- [QString inactiveToolTip() const](#inactiveToolTip)
- [bool isActive() const](#isActive)
- [void setActiveGuiItem(const KGuiItem &)](#setActiveGuiItem)
- [void setActiveIcon(const QIcon &)](#setActiveIcon)
- [void setActiveText(const QString &)](#setActiveText)
- [void setActiveToolTip(const QString &)](#setActiveToolTip)
- [void setAutoToggle(bool)](#setAutoToggle)
- [void setIconForStates(const QIcon &icon)](#setIconForStates)
- [void setInactiveGuiItem(const KGuiItem &)](#setInactiveGuiItem)
- [void setInactiveIcon(const QIcon &)](#setInactiveIcon)
- [void setInactiveText(const QString &)](#setInactiveText)
- [void setInactiveToolTip(const QString &)](#setInactiveToolTip)

## Public Slots

- [void setActive(bool state)](#setActive)

## Signals

- [void activeChanged(bool)](#activeChanged)
- [void activeChangedByUser(bool)](#activeChangedByUser)

## Detailed Description {#details}

[KDualAction](kdualaction.md) should be used when you want to create an action which alternate between two states when triggered but which should not be rendered as a checkable widget because it is more appropriate to change the text and icon of the action instead.

You should use [KDualAction](kdualaction.md) to implement this kind of actions instead of [KToggleAction](ktoggleaction.md) because [KToggleAction](ktoggleaction.md) is rendered as a checkable widget: this means one of your state will have a checkbox in a menu and will be represented as a sunken button in a toolbar.

Porting from [KToggleAction](ktoggleaction.md) to [KDualAction](kdualaction.md):

1. If you used the [KToggleAction](ktoggleaction.md) constructor which accepts the action text, adjust the constructor: [KDualAction](kdualaction.md) constructor accepts both inactive and active text.

2. Replace connections to the checked(bool) signal with a connection to the [activeChanged](kdualaction.md#activeChanged)(bool) (or [activeChangedByUser](kdualaction.md#activeChangedByUser)(bool))

3. Replace calls to [setChecked](https://doc.qt.io/qt-6/qaction.html#checked-prop)()/[isChecked](https://doc.qt.io/qt-6/qaction.html#checked-prop)() with [setActive](kdualaction.md#setActive)()/[isActive](kdualaction.md#isActive)()

4. Replace calls to setCheckedState(guiItem) with [setActiveGuiItem](kdualaction.md#setActiveGuiItem)(guiItem)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KDualAction::KDualAction(QObject \**parent*) {#KDualAction}

Constructs a [KDualAction](kdualaction.md) with the specified parent. Texts must be set with setTextForState() or setGuiItemForState().

### KDualAction::KDualAction(const QString &*inactiveText*, const QString &*activeText*, QObject \**parent*) {#KDualAction-1}

Constructs a [KDualAction](kdualaction.md) with the specified parent and texts.

### \[signal\] void KDualAction::activeChanged(*bool*) {#activeChanged}

Emitted when the state changes. This signal is emitted when the user trigger the action and when [setActive](kdualaction.md#setActive)() is called.

### \[signal\] void KDualAction::activeChangedByUser(*bool*) {#activeChangedByUser}

Only emitted when the state changes because the user triggered the action.

### KGuiItem KDualAction::activeGuiItem() const {#activeGuiItem}

Gets the [KGuiItem](kguiitem.md) for the active state

*See also* [setActiveGuiItem](kdualaction.md#setActiveGuiItem)()

### QIcon KDualAction::activeIcon() const {#activeIcon}

Gets the icon for the active state

*See also* [setActiveIcon](kdualaction.md#setActiveIcon)()

### QString KDualAction::activeText() const {#activeText}

Gets the text for the active state

*See also* [setActiveText](kdualaction.md#setActiveText)()

### QString KDualAction::activeToolTip() const {#activeToolTip}

Gets the tooltip for the active state

*See also* [setActiveToolTip](kdualaction.md#setActiveToolTip)()

### bool KDualAction::autoToggle() const {#autoToggle}

Returns whether the current action will automatically be changed when the user triggers this action. The default value is true.

*See also* [setAutoToggle](kdualaction.md#setAutoToggle)()

### KGuiItem KDualAction::inactiveGuiItem() const {#inactiveGuiItem}

Gets the [KGuiItem](kguiitem.md) for the inactive state

*See also* [setInactiveGuiItem](kdualaction.md#setInactiveGuiItem)()

### QIcon KDualAction::inactiveIcon() const {#inactiveIcon}

Gets the icon for the inactive state

*See also* [setInactiveIcon](kdualaction.md#setInactiveIcon)()

### QString KDualAction::inactiveText() const {#inactiveText}

Gets the text for the inactive state

*See also* [setInactiveText](kdualaction.md#setInactiveText)()

### QString KDualAction::inactiveToolTip() const {#inactiveToolTip}

Gets the tooltip for the inactive state

*See also* [setInactiveToolTip](kdualaction.md#setInactiveToolTip)()

### bool KDualAction::isActive() const {#isActive}

Returns the action state. The action is inactive by default.

### \[slot\] void KDualAction::setActive(bool *state*) {#setActive}

Sets the action state. [activeChanged](kdualaction.md#activeChanged)() will be emitted but not [activeChangedByUser](kdualaction.md#activeChangedByUser)().

*See also* [isActive](kdualaction.md#isActive)()

### void KDualAction::setActiveGuiItem(*const KGuiItem &*) {#setActiveGuiItem}

Sets the [KGuiItem](kguiitem.md) for the active state

*See also* [activeGuiItem](kdualaction.md#activeGuiItem)()

### void KDualAction::setActiveIcon(*const QIcon &*) {#setActiveIcon}

Sets the icon for the active state

*See also* [activeIcon](kdualaction.md#activeIcon)()

### void KDualAction::setActiveText(*const QString &*) {#setActiveText}

Sets the text for the active state

*See also* [activeText](kdualaction.md#activeText)()

### void KDualAction::setActiveToolTip(*const QString &*) {#setActiveToolTip}

Sets the tooltip for the active state

*See also* [activeToolTip](kdualaction.md#activeToolTip)()

### void KDualAction::setAutoToggle(*bool*) {#setAutoToggle}

Defines whether the current action should automatically be changed when the user triggers this action.

*See also* [autoToggle](kdualaction.md#autoToggle)()

### void KDualAction::setIconForStates(const QIcon &*icon*) {#setIconForStates}

Convenience method to set the icon for both active and inactive states.

### void KDualAction::setInactiveGuiItem(*const KGuiItem &*) {#setInactiveGuiItem}

Sets the [KGuiItem](kguiitem.md) for the inactive state

*See also* [inactiveGuiItem](kdualaction.md#inactiveGuiItem)()

### void KDualAction::setInactiveIcon(*const QIcon &*) {#setInactiveIcon}

Sets the icon for the inactive state

*See also* [inactiveIcon](kdualaction.md#inactiveIcon)()

### void KDualAction::setInactiveText(*const QString &*) {#setInactiveText}

Sets the text for the inactive state

*See also* [inactiveText](kdualaction.md#inactiveText)()

### void KDualAction::setInactiveToolTip(*const QString &*) {#setInactiveToolTip}

Sets the tooltip for the inactive state

*See also* [inactiveToolTip](kdualaction.md#inactiveToolTip)()
