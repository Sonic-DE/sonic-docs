---
title: "KGlobalAccel Class"
description: "Configurable global shortcut support."
---

# KGlobalAccel Class

Configurable global shortcut support. [More...](#details)

- **Header:** `#include <KGlobalAccel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS GlobalAccel)`  
  `target_link_libraries(mytarget PRIVATE KF6::GlobalAccel)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kglobalaccel-members.md)

## Public Types

- [enum KGlobalAccel::GlobalShortcutLoading](#GlobalShortcutLoading-enum)
- [enum KGlobalAccel::MatchType](#MatchType-enum)
- [enum KGlobalAccel::actionIdFields](#actionIdFields-enum)

## Public Functions

- [QList\<QKeySequence\> defaultShortcut(const QAction \*action) const](#defaultShortcut)
- [QList\<QKeySequence\> globalShortcut(const QString &componentName, const QString &actionId) const](#globalShortcut)
- [bool hasShortcut(const QAction \*action) const](#hasShortcut)
- [void removeAllShortcuts(QAction \*action)](#removeAllShortcuts)
- [bool setDefaultShortcut(QAction \*action, const QList\<QKeySequence\> &shortcut, KGlobalAccel::GlobalShortcutLoading loadFlag = Autoloading)](#setDefaultShortcut)
- [bool setShortcut(QAction \*action, const QList\<QKeySequence\> &shortcut, KGlobalAccel::GlobalShortcutLoading loadFlag = Autoloading)](#setShortcut)
- [QList\<QKeySequence\> shortcut(const QAction \*action) const](#shortcut)

## Signals

- [void globalShortcutActiveChanged(QAction \*action, bool active)](#globalShortcutActiveChanged)
- [void globalShortcutChanged(QAction \*action, const QKeySequence &seq)](#globalShortcutChanged)

## Static Public Members

- [bool cleanComponent(const QString &componentUnique)](#cleanComponent)
- [QList\<KGlobalShortcutInfo\> globalShortcutsByKey(const QKeySequence &seq, KGlobalAccel::MatchType type = Equal)](#globalShortcutsByKey)
- [bool isComponentActive(const QString &componentName)](#isComponentActive)
- [bool isGlobalShortcutAvailable(const QKeySequence &seq, const QString &component = QString())](#isGlobalShortcutAvailable)
- [bool promptStealShortcutSystemwide(QWidget \*parent, const QList\<KGlobalShortcutInfo\> &shortcuts, const QKeySequence &seq)](#promptStealShortcutSystemwide)
- [KGlobalAccel \*self()](#self)
- [bool setGlobalShortcut(QAction \*action, const QKeySequence &shortcut)](#setGlobalShortcut)
- [bool setGlobalShortcut(QAction \*action, const QList\<QKeySequence\> &shortcuts)](#setGlobalShortcut-1)
- [bool setInverseShortcutActions(QAction \*forwardAction, QAction \*backwardAction)](#setInverseShortcutActions) (since 6.27)
- [void stealShortcutSystemwide(const QKeySequence &seq)](#stealShortcutSystemwide)

## Detailed Description {#details}

[KGlobalAccel](kglobalaccel.md) allows you to have global accelerators that are independent of the focused window. Unlike regular shortcuts, the application's window does not need focus for them to be activated.

Here's an example how to register the Meta + E global shortcut:

```cpp
QAction *action = new QAction();
action->setObjectName(QStringLiteral("actionId"));
action->setText(QStringLiteral("human readable name"));
KGlobalAccel::self()->setDefaultShortcut(action, QList<QKeySequence>() << (Qt::META | Qt::Key_E));
KGlobalAccel::self()->setShortcut(action, QList<QKeySequence>() << (Qt::META | Qt::Key_E));
connect(action, &QAction::triggered, []() {
    qDebug() << "global shortcut trigerred";
});
```

*See also* [KKeySequenceRecorder](../kguiaddons/kkeysequencerecorder.md)

## Member Type Documentation {#member-type-documentation}

### enum KGlobalAccel::GlobalShortcutLoading {#GlobalShortcutLoading-enum}

An enum about global shortcut setter semantics

| Constant | Value | Description |
| --- | --- | --- |
| `KGlobalAccel::Autoloading` | `0x0` | Look up the action in global settings (using its main component's name and text()) and set the shortcut as saved there. |
| `KGlobalAccel::NoAutoloading` | `0x4` | Prevent autoloading of saved global shortcut for action. |

*See also* [setGlobalShortcut](kglobalaccel.md#setGlobalShortcut)()

### enum KGlobalAccel::MatchType {#MatchType-enum}

Keysequence match semantics.

Assuming we have an Emacs-style shortcut, for example (Alt+B, Alt+F, Alt+G) already assigned, how a new shortcut is compared depends on which value of the enum is used.

| Constant | Value | Description |
| --- | --- | --- |
| `KGlobalAccel::Equal` | `0` | Exact matching: (Alt+B, Alt+F, Alt+G) |
| `KGlobalAccel::Shadows` | `1` | Sequence shadowing: (Alt+B, Alt+F), (Alt+F, Alt+G) |
| `KGlobalAccel::Shadowed` | `2` | Sequence being shadowed: (Alt+B, Alt+F, Alt+G, \<any key\>), (\<any key\>, Alt+B, Alt+F, Alt+G) |

### enum KGlobalAccel::actionIdFields {#actionIdFields-enum}

Index for actionId QStringLists

| Constant | Value | Description |
| --- | --- | --- |
| `KGlobalAccel::ComponentUnique` | `0` | Components Unique Name (ID). |
| `KGlobalAccel::ActionUnique` | `1` | Actions Unique Name (ID). |
| `KGlobalAccel::ComponentFriendly` | `2` | Components Friendly Translated Name |
| `KGlobalAccel::ActionFriendly` | `3` | Actions Friendly Translated Name |

## Member Function Documentation {#member-function-documentation}

### \[static\] bool KGlobalAccel::cleanComponent(const QString &*componentUnique*) {#cleanComponent}

Clean the shortcuts for component `componentUnique`.

If the component is not active all global shortcut registrations are purged and the component is removed completely.

If the component is active all global shortcut registrations not in use will be purged. If there is no shortcut registration left the component is purged too.

If a purged component or shortcut is activated the next time it will reregister itself. All you probably will lose on wrong usage are the user's set shortcuts.

If you make sure your component is running and all global shortcuts it has are active this function can be used to clean up the registry.

Handle with care!

If the method return `true` at least one shortcut was purged so handle all previously acquired information with care.

### QList\<QKeySequence\> KGlobalAccel::defaultShortcut(const QAction \**action*) const {#defaultShortcut}

Get the global default shortcut for this `action`, if one exists. Global shortcuts allow your actions to respond to accellerators independently of the focused window. Unlike regular shortcuts, the application's window does not need focus for them to be activated.

*See also* [setDefaultShortcut](kglobalaccel.md#setDefaultShortcut)()

### QList\<QKeySequence\> KGlobalAccel::globalShortcut(const QString &*componentName*, const QString &*actionId*) const {#globalShortcut}

Retrieves the shortcut as defined in global settings by `componentName` (e.g. "kwin") and `actionId` (e.g. "Kill Window").

*See also* [setGlobalShortcut](kglobalaccel.md#setGlobalShortcut)()

### \[signal\] void KGlobalAccel::globalShortcutActiveChanged(QAction \**action*, bool *active*) {#globalShortcutActiveChanged}

Emitted when a global shortcut for the given `action` is activated or deactivated.

The global shorcut will be activated when the keys are pressed and deactivated when the keys are released. `active` indicates whether the global shortcut is active.

### \[signal\] void KGlobalAccel::globalShortcutChanged(QAction \**action*, const QKeySequence &*seq*) {#globalShortcutChanged}

Emitted when the global shortcut is changed. A global shortcut is subject to be changed by the global shortcuts kcm.

`action` specifies the action for which the changed shortcut was registered.

`seq` indicates the key sequence that corresponds to the changed shortcut.

*See also* [setGlobalShortcut](kglobalaccel.md#setGlobalShortcut)(), [setDefaultShortcut](kglobalaccel.md#setDefaultShortcut)()

### \[static\] QList\<KGlobalShortcutInfo\> KGlobalAccel::globalShortcutsByKey(const QKeySequence &*seq*, KGlobalAccel::MatchType *type* = Equal) {#globalShortcutsByKey}

Returns a list of global shortcuts registered for the shortcut `seq` using the given matching `type`.

If the list contains more that one entry it means the component that registered the shortcuts uses global shortcut contexts. All returned shortcuts belong to the same component.

### bool KGlobalAccel::hasShortcut(const QAction \**action*) const {#hasShortcut}

Returns true if a shortcut or a default shortcut has been registered for the given `action`.

### \[static\] bool KGlobalAccel::isComponentActive(const QString &*componentName*) {#isComponentActive}

Returns `true` if the component with the given `componentName` exists; otherwise returns `false`.

### \[static\] bool KGlobalAccel::isGlobalShortcutAvailable(const QKeySequence &*seq*, const QString &*component* = QString()) {#isGlobalShortcutAvailable}

Returns `true` if the shortcut `seq` is available for the `component`; otherwise returns `false`.

The component is only of interest if the current application uses global shortcut contexts. In that case a global shortcut by `component` in an inactive global shortcut contexts does not block the `seq` for us.

### \[static\] bool KGlobalAccel::promptStealShortcutSystemwide(QWidget \**parent*, const QList\<KGlobalShortcutInfo\> &*shortcuts*, const QKeySequence &*seq*) {#promptStealShortcutSystemwide}

Show a messagebox to inform the user that a global shortcut is already occupied, and ask to take it away from its current action(s). This is GUI only, so nothing will be actually changed.

Returns `true` if user confirms that it is okay to re-assign the global shorcut; otherwise returns `false`.

*See also* [stealShortcutSystemwide](kglobalaccel.md#stealShortcutSystemwide)()

### void KGlobalAccel::removeAllShortcuts(QAction \**action*) {#removeAllShortcuts}

Unregister and remove all defined global shortcuts for the given `action`.

### \[static\] KGlobalAccel \*KGlobalAccel::self() {#self}

Returns (and creates if necessary) the singleton instance

### bool KGlobalAccel::setDefaultShortcut(QAction \**action*, const QList\<QKeySequence\> &*shortcut*, KGlobalAccel::GlobalShortcutLoading *loadFlag* = Autoloading) {#setDefaultShortcut}

Assign a default global `shortcut` for a given `action`.

For more information about global shortcuts and `loadFlag`, see [setShortcut](kglobalaccel.md#setShortcut)().

Upon shortcut change the [globalShortcutChanged](kglobalaccel.md#globalShortcutChanged)() will be triggered so other applications get notified.

Returns `true` if the shortcut has been set successfully; otherwise returns `false`.

*See also* [defaultShortcut](kglobalaccel.md#defaultShortcut)(), [globalShortcutChanged](kglobalaccel.md#globalShortcutChanged)()

### \[static\] bool KGlobalAccel::setGlobalShortcut(QAction \**action*, const QKeySequence &*shortcut*) {#setGlobalShortcut}

Sets both active and default `shortcut` for the given `action`.

This method is suited for the case that only one shortcut is to be configured.

If more control for loading the shortcuts is needed use the variants offering more control.

Returns `true` if the shortcut has been set successfully; otherwise returns `false`.

*See also* [globalShortcut](kglobalaccel.md#globalShortcut)(), [setShortcut](kglobalaccel.md#setShortcut)(), [setDefaultShortcut](kglobalaccel.md#setDefaultShortcut)()

### \[static\] bool KGlobalAccel::setGlobalShortcut(QAction \**action*, const QList\<QKeySequence\> &*shortcuts*) {#setGlobalShortcut-1}

Sets both active and default `shortcuts` for the given `action`.

If more control for loading the shortcuts is needed use the variants offering more control.

Returns `true` if the shortcut has been set successfully; otherwise returns `false`.

*See also* [setShortcut](kglobalaccel.md#setShortcut)(), [setDefaultShortcut](kglobalaccel.md#setDefaultShortcut)()

### \[static, since 6.27\] bool KGlobalAccel::setInverseShortcutActions(QAction \**forwardAction*, QAction \**backwardAction*) {#setInverseShortcutActions}

Designates `forwardAction` and `backwardAction` as inverse actions of each other.

Both actions must have been set with `setDefaultShortcut()` or `setGlobalShortcut()` before calling this function. Their component name (e.g. "kwin") must be the same.

When configuring a shortcut for one of these two actions, the settings application should prompt the user to also (re)assign or modify a similar shortcut for its inverse action.

Both actions may be shown as a pair in shortcut lists.

Returns `true` if the shortcut has been set successfully; otherwise returns `false`.

This function was introduced in Qt 6.27.

*See also* [setShortcut](kglobalaccel.md#setShortcut)(), [setDefaultShortcut](kglobalaccel.md#setDefaultShortcut)(), [setGlobalShortcut](kglobalaccel.md#setGlobalShortcut)()

### bool KGlobalAccel::setShortcut(QAction \**action*, const QList\<QKeySequence\> &*shortcut*, KGlobalAccel::GlobalShortcutLoading *loadFlag* = Autoloading) {#setShortcut}

Assign a global shortcut for the given action.

Global shortcuts allow an action to respond to key shortcuts independently of the focused window, i.e. the action will trigger if the keys were pressed no matter where in the X session.

The action must have a per main component unique action-\>[objectName](https://doc.qt.io/qt-6/qobject.html#objectName-prop)() to enable cross-application bookkeeping. If the action-\>[objectName](https://doc.qt.io/qt-6/qobject.html#objectName-prop)() is empty this method will do nothing and will return false.

It is mandatory that the action-\>[objectName](https://doc.qt.io/qt-6/qobject.html#objectName-prop)() doesn't change once the shortcut has been successfully registered.

> **Note:** KActionCollection::insert(name, action) will set action's objectName to name so you often don't have to set an objectName explicitly.

When an action, identified by main component name and [objectName](https://doc.qt.io/qt-6/qobject.html#objectName-prop)(), is assigned a global shortcut for the first time on a KDE installation the assignment will be saved. The shortcut will then be restored every time [setGlobalShortcut](kglobalaccel.md#setGlobalShortcut)() is called with `loadFlag` == Autoloading.

If you actually want to change the global shortcut you have to set `loadFlag` to [NoAutoloading](kglobalaccel.md#GlobalShortcutLoading-enum). The new shortcut will be automatically saved again.

`action` specifies the action for which the shortcut will be assigned.

`shortcut` specifies the global shortcut(s) to assign. Will be ignored unless `loadFlag` is set to [NoAutoloading](kglobalaccel.md#GlobalShortcutLoading-enum) or this is the first time ever you call this method (see above).

If `loadFlag` is [KGlobalAccel::Autoloading](kglobalaccel.md#GlobalShortcutLoading-enum), assign the global shortcut this action has previously had if any. That way user preferences and changes made to avoid clashes will be conserved. If [KGlobalAccel::NoAutoloading](kglobalaccel.md#GlobalShortcutLoading-enum) the given shortcut will be assigned without looking up old values. You should only do this if the user wants to change the shortcut or if you have another very good reason. Key combinations that clash with other shortcuts will be dropped.

> **Note:** the default shortcut will never be influenced by autoloading - it will be set as given.

*See also* [shortcut](kglobalaccel.md#shortcut)(), [globalShortcutChanged](kglobalaccel.md#globalShortcutChanged)()

### QList\<QKeySequence\> KGlobalAccel::shortcut(const QAction \**action*) const {#shortcut}

Get the global shortcut for this `action`, if one exists. Global shortcuts allow your actions to respond to accellerators independently of the focused window. Unlike regular shortcuts, the application's window does not need focus for them to be activated.

> **Note:** that this method only works together with [setShortcut](kglobalaccel.md#setShortcut)() because the action pointer is used to retrieve the result. If you would like to retrieve the shortcut as stored in the global settings, use the [globalShortcut](kglobalaccel.md#globalShortcut)(componentName, actionId) instead.

*See also* [setShortcut](kglobalaccel.md#setShortcut)()

### \[static\] void KGlobalAccel::stealShortcutSystemwide(const QKeySequence &*seq*) {#stealShortcutSystemwide}

Take away the given shortcut `seq` from the named action it belongs to. This applies to all actions with global shortcuts in any KDE application.

*See also* [promptStealShortcutSystemwide](kglobalaccel.md#promptStealShortcutSystemwide)()
