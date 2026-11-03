---
title: "KActionCollection Class"
description: "A container for a set of QAction objects."
---

# KActionCollection Class

A container for a set of [QAction](https://doc.qt.io/qt-6/qaction.html) objects. [More...](#details)

- **Header:** `#include <KActionCollection>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS XmlGui)`  
  `target_link_libraries(mytarget PRIVATE KF6::XmlGui)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kactioncollection-members.md)

## Properties

- [configGroup : QString](#configGroup-prop)
- [configIsGlobal : bool](#configIsGlobal-prop)

## Public Functions

- [KActionCollection(QObject \*parent, const QString &cName = QString())](#KActionCollection)
- [~KActionCollection()](#dtor.KActionCollection)
- [QAction \*action(const QString &name) const](#action)
- [QAction \*action(int index) const](#action-1)
- [const QList\<QActionGroup \*\> actionGroups() const](#actionGroups)
- [QList\<QAction \*\> actions() const](#actions)
- [const QList\<QAction \*\> actionsWithoutGroup() const](#actionsWithoutGroup)
- [template \<typename ActionType\> ActionType \*add(const QString &name, const QObject \*receiver = nullptr, const char \*member = nullptr)](#add)
- [template \<
    typename ActionType,
    typename Receiver,
    typename Func
\>
ActionType \*add(const QString &name, const Receiver \*receiver, Func slot)](#add-1)
- [QAction \*addAction(KStandardActions::StandardAction actionType)](#addAction) (since 6.9)
- [QAction \*addAction(KStandardActions::StandardAction actionType, const QString &name)](#addAction-1) (since 6.15)
- [QAction \*addAction(const QString &name, QAction \*action)](#addAction-2)
- [QAction \*addAction(KStandardAction::StandardAction actionType, const QObject \*receiver = nullptr, const char \*member = nullptr)](#addAction-3)
- [template \<typename Receiver, typename Func\> QAction \*addAction(KStandardActions::StandardAction actionType, const Receiver \*receiver, Func slot)](#addAction-4) (since 6.3)
- [QAction \*addAction(const QString &name, const QObject \*receiver = nullptr, const char \*member = nullptr)](#addAction-5)
- [template \<typename Receiver, typename Func\> QAction \*addAction(const QString &name, const Receiver \*receiver, Func slot)](#addAction-6)
- [QAction \*addAction(KStandardAction::StandardAction actionType, const QString &name, const QObject \*receiver = nullptr, const char \*member = nullptr)](#addAction-7)
- [template \<typename Receiver, typename Func\> QAction \*addAction(KStandardAction::StandardAction actionType, const QString &name, const Receiver \*receiver, Func slot)](#addAction-8)
- [template \<typename Receiver, typename Func\> QAction \*addAction(KStandardActions::StandardAction actionType, const QString &name, const Receiver \*receiver, Func slot)](#addAction-9) (since 6.3)
- [void addActions(const QList\<QAction \*\> &actions)](#addActions)
- [void addAssociatedWidget(QWidget \*widget)](#addAssociatedWidget)
- [void associateWidget(QWidget \*widget) const](#associateWidget)
- [QList\<QWidget \*\> associatedWidgets() const](#associatedWidgets)
- [void clear()](#clear)
- [void clearAssociatedWidgets()](#clearAssociatedWidgets)
- [QString componentDisplayName() const](#componentDisplayName)
- [QString componentName() const](#componentName)
- [QString configGroup() const](#configGroup)
- [bool configIsGlobal() const](#configIsGlobal)
- [int count() const](#count)
- [void exportGlobalShortcuts(KConfigGroup \*config, bool writeDefaults = false) const](#exportGlobalShortcuts)
- [void importGlobalShortcuts(KConfigGroup \*config)](#importGlobalShortcuts)
- [bool isEmpty() const](#isEmpty)
- [const KXMLGUIClient \*parentGUIClient() const](#parentGUIClient)
- [void readSettings(KConfigGroup \*config = nullptr)](#readSettings)
- [void removeAction(QAction \*action)](#removeAction)
- [void removeAssociatedWidget(QWidget \*widget)](#removeAssociatedWidget)
- [void setComponentDisplayName(const QString &displayName)](#setComponentDisplayName)
- [void setComponentName(const QString &componentName)](#setComponentName)
- [void setConfigGlobal(bool global)](#setConfigGlobal)
- [void setConfigGroup(const QString &group)](#setConfigGroup)
- [QAction \*takeAction(QAction \*action)](#takeAction)
- [void writeSettings(KConfigGroup \*config = nullptr, bool writeDefaults = false, QAction \*oneAction = nullptr) const](#writeSettings)

## Signals

- [void actionHovered(QAction \*action)](#actionHovered)
- [void actionTriggered(QAction \*action)](#actionTriggered)
- [void changed()](#changed)
- [void inserted(QAction \*action)](#inserted)

## Static Public Members

- [const QList\<KActionCollection \*\> &allCollections()](#allCollections)
- [QKeySequence defaultShortcut(QAction \*action)](#defaultShortcut)
- [QList\<QKeySequence\> defaultShortcuts(QAction \*action)](#defaultShortcuts)
- [bool isShortcutsConfigurable(QAction \*action)](#isShortcutsConfigurable)
- [void setDefaultShortcut(QAction \*action, const QKeySequence &shortcut)](#setDefaultShortcut)
- [void setDefaultShortcuts(QAction \*action, const QList\<QKeySequence\> &shortcuts)](#setDefaultShortcuts)
- [void setShortcutsConfigurable(QAction \*action, bool configurable)](#setShortcutsConfigurable)

## Detailed Description {#details}

[KActionCollection](kactioncollection.md) manages a set of [QAction](https://doc.qt.io/qt-6/qaction.html) objects. It allows them to be grouped for organized presentation of configuration to the user, saving + loading of configuration, and optionally for automatic plugging into specified widget(s).

Additionally, [KActionCollection](kactioncollection.md) provides several convenience functions for locating named actions, and actions grouped by [QActionGroup](https://doc.qt.io/qt-6/qactiongroup.html).

> **Note:** If you create your own action collection and need to assign shortcuts to the actions within, you have to call [associateWidget](kactioncollection.md#associateWidget)() or [addAssociatedWidget](kactioncollection.md#addAssociatedWidget)() to have them working.

## Property Documentation {#property-documentation}

### configGroup : QString {#configGroup-prop}

**Access functions:**

- `QString` **[configGroup](kactioncollection.md#configGroup)**() const
- `void` **[setConfigGroup](kactioncollection.md#setConfigGroup)**(const `QString` &*group*)

### configIsGlobal : bool {#configIsGlobal-prop}

**Access functions:**

- `bool` **[configIsGlobal](kactioncollection.md#configIsGlobal)**() const
- `void` **[setConfigGlobal](kactioncollection.md#setConfigGlobal)**(`bool` *global*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KActionCollection::KActionCollection(QObject \**parent*, const QString &*cName* = QString()) {#KActionCollection}

Constructor.

Allows specification of a component name other than the default application name, where needed (remember to call [setComponentDisplayName](kactioncollection.md#setComponentDisplayName)() too).

### \[override virtual noexcept\] KActionCollection::~KActionCollection() {#dtor.KActionCollection}

Destructor.

### \[invokable\] QAction \*KActionCollection::action(const QString &*name*) const {#action}

Get an action with the given `name` from the action collection.

This won't return the action for the menus defined using a "\<Menu\>" tag in XMLGUI files (e.g. "\<Menu name="menuId"\>" in "applicationNameui.rc").

To access menu actions defined like this, use for example...

```cpp
qobject_cast<QMenu *>(guiFactory()->container("menuId", this));
```

...after having called setupGUI() or createGUI().

Returns a pointer to the [QAction](https://doc.qt.io/qt-6/qaction.html) in the collection that matches the parameters or null if nothing matches.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### QAction \*KActionCollection::action(int *index*) const {#action-1}

Returns the [QAction](https://doc.qt.io/qt-6/qaction.html)\* at position `index` in the action collection.

This is equivalent to [actions](kactioncollection.md#actions)().value(index).

### const QList\<QActionGroup \*\> KActionCollection::actionGroups() const {#actionGroups}

Returns the list of all QActionGroups associated with actions in this action collection.

### \[signal\] void KActionCollection::actionHovered(QAction \**action*) {#actionHovered}

Indicates that `action` was hovered.

### \[signal\] void KActionCollection::actionTriggered(QAction \**action*) {#actionTriggered}

Indicates that `action` was triggered.

### QList\<QAction \*\> KActionCollection::actions() const {#actions}

Returns the list of QActions that belong to this action collection.

The list is guaranteed to be in the same order the action were put into the collection.

### const QList\<QAction \*\> KActionCollection::actionsWithoutGroup() const {#actionsWithoutGroup}

Returns the list of QActions without an [QAction::actionGroup](https://doc.qt.io/qt-6/qaction.html#actionGroup)() that belong to this action collection.

### template \<typename ActionType\> ActionType \*KActionCollection::add(const QString &*name*, const QObject \**receiver* = nullptr, const char \**member* = nullptr) {#add}

Creates a new action under the given name, adds it to the collection, and connects the action's triggered(bool) signal to the specified receiver/member.

The receiver slot may accept either a bool or no parameters at all (i.e. slotTriggered(bool) or slotTriggered() ). The type of the action is specified by the template parameter ActionType.

> **Note:** KDE prior to 4.2 connected the triggered() signal instead of the triggered(bool) signal.

The [KActionCollection](kactioncollection.md) takes ownership of the action object.

`name` The internal name of the action (e.g. "file-open").

`receiver` The [QObject](https://doc.qt.io/qt-6/qobject.html) to connect the triggered(bool) signal to. Leave nullptr if no connection is desired.

`member` The SLOT to connect the triggered(bool) signal to. Leave nullptr if no connection is desired.

Returns new action of the given type ActionType.

*See also* [addAction](kactioncollection.md#addAction)()

### template \< typename ActionType, typename Receiver, typename Func \> ActionType \*KActionCollection::add(const QString &*name*, const Receiver \**receiver*, Func *slot*) {#add-1}

This is the same as add(const [QString](https://doc.qt.io/qt-6/qstring.html) &name, const [QObject](https://doc.qt.io/qt-6/qobject.html) \*receiver, const char \*member) but using new style connect syntax.

`name` The internal name of the action (e.g. "file-open").

`receiver` The [QObject](https://doc.qt.io/qt-6/qobject.html) to connect the triggered(bool) signal to.

`slot` The slot or lambda to connect the triggered(bool) signal to.

Returns new action of the given type ActionType.

*See also* [add](kactioncollection.md#add)(const QString &, const QObject \*, const char \*)

### \[since 6.9\] QAction \*KActionCollection::addAction(KStandardActions::StandardAction *actionType*) {#addAction}

Creates a new standard action and adds it to the collection. The newly created action is also returned.

The action can be retrieved later from the collection by its standard name as per KStandardAction::stdName.

The [KActionCollection](kactioncollection.md) takes ownership of the action object.

`actionType` The standard action type of the action to create.

Returns new action of the given type ActionType.

This function was introduced in Qt 6.9.

### \[since 6.15\] QAction \*KActionCollection::addAction(KStandardActions::StandardAction *actionType*, const QString &*name*) {#addAction-1}

Creates a new standard action and adds it to the collection.

The newly created action is also returned.

`actionType` The standard action type of the action to create.

`name` The name by which the action be retrieved again from the collection.

Returns new action of the given type ActionType.

This function was introduced in Qt 6.15.

### \[invokable\] QAction \*KActionCollection::addAction(const QString &*name*, QAction \**action*) {#addAction-2}

Add an `action` under the given `name` to the collection.

Inserting an action that was previously inserted under a different name will replace the old entry, i.e. the action will not be available under the old name anymore but only under the new one.

Inserting an action under a name that is already used for another action will replace the other action in the collection (but will not delete it).

If [KAuthorized::authorizeAction](../kconfigcore/kauthorized.md#authorizeAction)() reports that the action is not authorized, it will be disabled and hidden.

The ownership of the action object is not transferred. If the action is destroyed it will be removed automatically from the [KActionCollection](kactioncollection.md).

`name` The name by which the action be retrieved again from the collection.

`action` The action to add.

Returns the same as the action given as parameter. This is just for convenience (chaining calls) and consistency with the other [addAction](kactioncollection.md#addAction) methods, you can also simply ignore the return value.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### QAction \*KActionCollection::addAction(KStandardAction::StandardAction *actionType*, const QObject \**receiver* = nullptr, const char \**member* = nullptr) {#addAction-3}

Creates a new standard action, adds it to the collection and connects the action's triggered(bool) signal to the specified receiver/member. The newly created action is also returned.

> **Note:** Using [KStandardAction::OpenRecent](../kconfigwidgets/kstandardaction.md#StandardAction-enum) will cause a different signal than triggered(bool) to be used, see [KStandardAction](../kconfigwidgets/kstandardaction.md) for more information.

The action can be retrieved later from the collection by its standard name as per KStandardAction::stdName.

The [KActionCollection](kactioncollection.md) takes ownership of the action object.

`actionType` The standard action type of the action to create.

`receiver` The [QObject](https://doc.qt.io/qt-6/qobject.html) to connect the triggered(bool) signal to. Leave nullptr if no connection is desired.

`member` The SLOT to connect the triggered(bool) signal to. Leave nullptr if no connection is desired.

Returns new action of the given type ActionType.

### \[since 6.3\] template \<typename Receiver, typename Func\> QAction \*KActionCollection::addAction(KStandardActions::StandardAction *actionType*, const Receiver \**receiver*, Func *slot*) {#addAction-4}

Creates a new standard action, adds it to the collection and connects the action's triggered(bool) signal to the specified receiver/member. The newly created action is also returned.

> **Note:** Using [KStandardAction::OpenRecent](../kconfigwidgets/kstandardaction.md#StandardAction-enum) will cause a different signal than triggered(bool) to be used, see [KStandardAction](../kconfigwidgets/kstandardaction.md) for more information.

The action can be retrieved later from the collection by its standard name as per KStandardAction::stdName.

The [KActionCollection](kactioncollection.md) takes ownership of the action object.

`actionType` The standard action type of the action to create.

`receiver` The [QObject](https://doc.qt.io/qt-6/qobject.html) to connect the triggered(bool) signal to. Leave nullptr if no connection is desired.

`slot` The slot or lambda to connect the triggered(bool) signal to.

Returns new action of the given type ActionType.

This function was introduced in Qt 6.3.

### QAction \*KActionCollection::addAction(const QString &*name*, const QObject \**receiver* = nullptr, const char \**member* = nullptr) {#addAction-5}

Creates a new action under the given name to the collection and connects the action's triggered(bool) signal to the specified receiver/member. The newly created action is returned.

> **Note:** KDE prior to 4.2 used the triggered() signal instead of the triggered(bool) signal.

Inserting an action that was previously inserted under a different name will replace the old entry, i.e. the action will not be available under the old name anymore but only under the new one.

Inserting an action under a name that is already used for another action will replace the other action in the collection.

The [KActionCollection](kactioncollection.md) takes ownership of the action object.

`name` The name by which the action be retrieved again from the collection.

`receiver` The [QObject](https://doc.qt.io/qt-6/qobject.html) to connect the triggered(bool) signal to. Leave nullptr if no connection is desired.

`member` The SLOT to connect the triggered(bool) signal to. Leave nullptr if no connection is desired.

Returns new action of the given type ActionType.

### template \<typename Receiver, typename Func\> QAction \*KActionCollection::addAction(const QString &*name*, const Receiver \**receiver*, Func *slot*) {#addAction-6}

This is the same as [addAction](kactioncollection.md#addAction)(const [QString](https://doc.qt.io/qt-6/qstring.html) &name, const [QObject](https://doc.qt.io/qt-6/qobject.html) \*receiver, const char \*member) but using new style connect syntax.

`name` The internal name of the action (e.g. "file-open").

`receiver` The [QObject](https://doc.qt.io/qt-6/qobject.html) to connect the triggered(bool) signal to.

`slot` The slot or lambda to connect the triggered(bool) signal to.

Returns new action of the given type ActionType.

*See also* [addAction](kactioncollection.md#addAction-5)(const QString &, const QObject \*, const char \*)

### QAction \*KActionCollection::addAction(KStandardAction::StandardAction *actionType*, const QString &*name*, const QObject \**receiver* = nullptr, const char \**member* = nullptr) {#addAction-7}

Creates a new standard action, adds to the collection under the given name and connects the action's triggered(bool) signal to the specified receiver/member. The newly created action is also returned.

> **Note:** Using [KStandardAction::OpenRecent](../kconfigwidgets/kstandardaction.md#StandardAction-enum) will cause a different signal than triggered(bool) to be used, see [KStandardAction](../kconfigwidgets/kstandardaction.md) for more information.

The action can be retrieved later from the collection by the specified name.

The [KActionCollection](kactioncollection.md) takes ownership of the action object.

`actionType` The standard action type of the action to create.

`name` The name by which the action be retrieved again from the collection.

`receiver` The [QObject](https://doc.qt.io/qt-6/qobject.html) to connect the triggered(bool) signal to. Leave nullptr if no connection is desired.

`member` The SLOT to connect the triggered(bool) signal to. Leave nullptr if no connection is desired.

Returns new action of the given type ActionType.

### template \<typename Receiver, typename Func\> QAction \*KActionCollection::addAction(KStandardAction::StandardAction *actionType*, const QString &*name*, const Receiver \**receiver*, Func *slot*) {#addAction-8}

This is the same as [addAction](kactioncollection.md#addAction)([KStandardAction::StandardAction](../kconfigwidgets/kstandardaction.md#StandardAction-enum) actionType, const [QString](https://doc.qt.io/qt-6/qstring.html) &name, const [QObject](https://doc.qt.io/qt-6/qobject.html) \*receiver, const char \*member) but using new style connect syntax.

`actionType` The standard action type of the action to create.

`name` The name by which the action be retrieved again from the collection.

`receiver` The [QObject](https://doc.qt.io/qt-6/qobject.html) to connect the triggered(bool) signal to.

`slot` The slot or lambda to connect the triggered(bool) signal to.

Returns new action of the given type ActionType.

*See also* [addAction](kactioncollection.md#addAction-7)(KStandardAction::StandardAction, const QString &, const QObject \*, const char \*)

### \[since 6.3\] template \<typename Receiver, typename Func\> QAction \*KActionCollection::addAction(KStandardActions::StandardAction *actionType*, const QString &*name*, const Receiver \**receiver*, Func *slot*) {#addAction-9}

This is the same as [addAction](kactioncollection.md#addAction)([KStandardAction::StandardAction](../kconfigwidgets/kstandardaction.md#StandardAction-enum) actionType, const [QString](https://doc.qt.io/qt-6/qstring.html) &name, const Receiver \*receiver, Func slot) but using [KStandardActions](../kconfiggui/kstandardactions.md) from [KConfigGui](../kconfiggui/kconfiggui-module.md).

`actionType` The standard action type of the action to create.

`name` The name by which the action be retrieved again from the collection.

`receiver` The [QObject](https://doc.qt.io/qt-6/qobject.html) to connect the triggered(bool) signal to.

`slot` The slot or lambda to connect the triggered(bool) signal to.

Returns new action of the given type ActionType.

This function was introduced in Qt 6.3.

### void KActionCollection::addActions(const QList\<QAction \*\> &*actions*) {#addActions}

Adds a list of `actions` to the collection.

The objectName of the actions is used as their internal name in the collection.

The ownership of the action objects is not transferred. If the action is destroyed it will be removed automatically from the [KActionCollection](kactioncollection.md).

Uses [addAction](kactioncollection.md#addAction)(const [QString](https://doc.qt.io/qt-6/qstring.html)&, [QAction](https://doc.qt.io/qt-6/qaction.html)\*).

*See also* [addAction](kactioncollection.md#addAction)()

### void KActionCollection::addAssociatedWidget(QWidget \**widget*) {#addAssociatedWidget}

Associate all actions in this collection to the given `widget`, including any actions added after this association is made.

This does not change the action's shortcut context, so if you need to have the actions only trigger when the widget has focus, you'll need to set the shortcut context on each action to [Qt::WidgetShortcut](https://doc.qt.io/qt-6/qt.html#ShortcutContext-enum) (or better still, [Qt::WidgetWithChildrenShortcut](https://doc.qt.io/qt-6/qt.html#ShortcutContext-enum) with Qt 4.4+)

### \[static\] const QList\<KActionCollection \*\> &KActionCollection::allCollections() {#allCollections}

Access the list of all action collections in existence for this app.

### void KActionCollection::associateWidget(QWidget \**widget*) const {#associateWidget}

Associate all actions in this collection to the given `widget`.

Unlike [addAssociatedWidget](kactioncollection.md#addAssociatedWidget)(), this method only adds all current actions in the collection to the given widget. Any action added after this call will not be added to the given widget automatically.

So this is just a shortcut for a foreach loop and a widget-\>[addAction](kactioncollection.md#addAction) call.

### QList\<QWidget \*\> KActionCollection::associatedWidgets() const {#associatedWidgets}

Return a list of all associated widgets.

### \[signal\] void KActionCollection::changed() {#changed}

Emitted when an action has been inserted into, or removed from, this action collection.

### void KActionCollection::clear() {#clear}

Clears the entire action collection, deleting all actions.

### void KActionCollection::clearAssociatedWidgets() {#clearAssociatedWidgets}

Clear all associated widgets and remove the actions from those widgets.

### QString KActionCollection::componentDisplayName() const {#componentDisplayName}

The display name for the associated component.

*See also* [setComponentDisplayName](kactioncollection.md#setComponentDisplayName)()

### QString KActionCollection::componentName() const {#componentName}

The component name with which this class is associated.

*See also* [setComponentName](kactioncollection.md#setComponentName)()

### QString KActionCollection::configGroup() const {#configGroup}

Returns the [KConfig](../kconfigcore/kconfig.md) group with which settings will be loaded and saved.

> **Note:** Getter function for property [configGroup](kactioncollection.md#configGroup-prop).

*See also* [setConfigGroup](kactioncollection.md#setConfigGroup)()

### bool KActionCollection::configIsGlobal() const {#configIsGlobal}

Returns whether this action collection's configuration should be global to KDE ( `true` ), or specific to the application ( `false` ).

> **Note:** Getter function for property [configIsGlobal](kactioncollection.md#configIsGlobal-prop).

### int KActionCollection::count() const {#count}

The number of actions in the collection.

This is equivalent to [actions](kactioncollection.md#actions)().count().

### \[static\] QKeySequence KActionCollection::defaultShortcut(QAction \**action*) {#defaultShortcut}

Returns the default primary shortcut for the given `action`.

*See also* [setDefaultShortcut](kactioncollection.md#setDefaultShortcut)()

### \[static\] QList\<QKeySequence\> KActionCollection::defaultShortcuts(QAction \**action*) {#defaultShortcuts}

Returns the default shortcuts for the given `action`.

*See also* [setDefaultShortcuts](kactioncollection.md#setDefaultShortcuts)()

### void KActionCollection::exportGlobalShortcuts(KConfigGroup \**config*, bool *writeDefaults* = false) const {#exportGlobalShortcuts}

Export the current configurable global key associations to `config`.

If `writeDefaults` is set to true, default settings will also be written.

### void KActionCollection::importGlobalShortcuts(KConfigGroup \**config*) {#importGlobalShortcuts}

Import all configurable global key associations from `config`.

### \[signal\] void KActionCollection::inserted(QAction \**action*) {#inserted}

Indicates that `action` was inserted into this action collection.

### bool KActionCollection::isEmpty() const {#isEmpty}

Returns whether the action collection is empty or not.

### \[static\] bool KActionCollection::isShortcutsConfigurable(QAction \**action*) {#isShortcutsConfigurable}

Returns true if the given `action` shortcuts may be configured by the user.

### const KXMLGUIClient \*KActionCollection::parentGUIClient() const {#parentGUIClient}

The parent [KXMLGUIClient](kxmlguiclient.md), or null if not available.

### void KActionCollection::readSettings(KConfigGroup \**config* = nullptr) {#readSettings}

Read all key associations from `config`.

If `config` is zero, read all key associations from the application's configuration file [KSharedConfig::openConfig](../kconfigcore/ksharedconfig.md#openConfig)(), in the group set by [setConfigGroup](kactioncollection.md#setConfigGroup)().

### void KActionCollection::removeAction(QAction \**action*) {#removeAction}

Removes an `action` from the collection and deletes it.

### void KActionCollection::removeAssociatedWidget(QWidget \**widget*) {#removeAssociatedWidget}

Remove an association between all actions in this collection and the given `widget`, i.e. remove those actions from the widget, and stop associating newly added actions as well.

### void KActionCollection::setComponentDisplayName(const QString &*displayName*) {#setComponentDisplayName}

Set the component `displayName` associated with this action collection.

This can be done, for example, for the toolbar editor.

[KXMLGUIClient::setComponentName](kxmlguiclient.md#setComponentName) takes care of calling this.

*See also* [componentDisplayName](kactioncollection.md#componentDisplayName)()

### void KActionCollection::setComponentName(const QString &*componentName*) {#setComponentName}

Sets the `componentName` associated with this action collection.

> **Warning:** Don't call this method on a [KActionCollection](kactioncollection.md) that contains actions. This is not supported.

`componentName` The name which is to be associated with this action collection, or QString() to indicate the app name. This is used to load/save settings into XML files. [KXMLGUIClient::setComponentName](kxmlguiclient.md#setComponentName) takes care of calling this.

*See also* [componentName](kactioncollection.md#componentName)()

### void KActionCollection::setConfigGlobal(bool *global*) {#setConfigGlobal}

Set whether this action collection's configuration should be `global` to KDE ( `true` ), or specific to the application ( `false` ).

> **Note:** Setter function for property [configIsGlobal](kactioncollection.md#configIsGlobal-prop).

### void KActionCollection::setConfigGroup(const QString &*group*) {#setConfigGroup}

Sets `group` as the [KConfig](../kconfigcore/kconfig.md) group with which settings will be loaded and saved.

> **Note:** Setter function for property [configGroup](kactioncollection.md#configGroup-prop).

*See also* [configGroup](kactioncollection.md#configGroup)()

### \[static\] void KActionCollection::setDefaultShortcut(QAction \**action*, const QKeySequence &*shortcut*) {#setDefaultShortcut}

Sets the default `shortcut` for the given `action`.

Since 5.2, this also calls action-\>setShortcut(shortcut), i.e. the default shortcut is made active initially.

*See also* [defaultShortcut](kactioncollection.md#defaultShortcut)()

### \[static invokable\] void KActionCollection::setDefaultShortcuts(QAction \**action*, const QList\<QKeySequence\> &*shortcuts*) {#setDefaultShortcuts}

\*

Sets the default `shortcuts` in their specified shortcutContext() \* for the given `action`. \* \* Since 5.2, this also calls action-\>setShortcuts(shortcuts), \* i.e. the default shortcut is made active initially.

\*

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [defaultShortcuts](kactioncollection.md#defaultShortcuts)()

### \[static\] void KActionCollection::setShortcutsConfigurable(QAction \**action*, bool *configurable*) {#setShortcutsConfigurable}

Sets whether the `action` shortcuts may be `configurable` by the user.

*See also* [isShortcutsConfigurable](kactioncollection.md#isShortcutsConfigurable)()

### QAction \*KActionCollection::takeAction(QAction \**action*) {#takeAction}

Removes an `action` from the collection.

The ownership of the action object is not changed.

### void KActionCollection::writeSettings(KConfigGroup \**config* = nullptr, bool *writeDefaults* = false, QAction \**oneAction* = nullptr) const {#writeSettings}

Write the current configurable key associations to `config`. What the function does if `config` is zero depends. If this action collection belongs to a [KXMLGUIClient](kxmlguiclient.md) the setting are saved to the kxmlgui definition file. If not the settings are written to the applications config file.

> **Note:** `oneAction` and `writeDefaults` have no meaning for the kxmlgui configuration file.

`config` Config object to save to, or null.

`writeDefaults` set to true to write settings which are already at defaults.

`oneAction` pass an action here if you just want to save the values for one action, eg. if you know that action is the only one which has changed.
