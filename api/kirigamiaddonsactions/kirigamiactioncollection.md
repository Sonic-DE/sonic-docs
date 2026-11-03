---
title: "KirigamiActionCollection Class"
description: "The C++ counterpart of the ActionCollection QML type."
---

# KirigamiActionCollection Class

The C++ counterpart of the [ActionCollection](qml-org-kde-kirigamiaddons-actions-actioncollection.md) QML type. [More...](#details)

- **Header:** `#include <KirigamiActionCollection>`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kirigamiactioncollection-members.md)

## Properties

- [\[read-only\] actions : QQmlListProperty\<ActionData\>](#actions-prop)
- [application : AbstractKirigamiApplication\*](#application-prop)
- [configGroup : QString](#configGroup-prop)
- [configIsGlobal : bool](#configIsGlobal-prop)
- [\[read-only\] menus : QQmlListProperty\<ActionMenu\>](#menus-prop)
- [name : QString](#name-prop)
- [text : QString](#text-prop)

## Public Functions

- [KirigamiActionCollection(QObject \*parent = nullptr, const QString &cName = QString())](#KirigamiActionCollection)
- [~KirigamiActionCollection()](#dtor.KirigamiActionCollection)
- [QAction \*action(const QString &name) const](#action)
- [QAction \*action(int index) const](#action-1)
- [const QList\<QActionGroup \*\> actionGroups() const](#actionGroups)
- [QList\<QAction \*\> actions() const](#actions)
- [const QList\<QAction \*\> actionsWithoutGroup() const](#actionsWithoutGroup)
- [template \<
    typename ActionType,
    typename Receiver,
    typename Func
\>
typename std::enable\_if\<!std::is\_convertible\<Func, const char \*\>::value, ActionType\>::type \*add(const QString &name, const Receiver \*receiver, Func slot)](#add)
- [QAction \*addAction(const QString &name, QAction \*action)](#addAction)
- [template \<typename Receiver, typename Func\> typename std::enable\_if\<!std::is\_convertible\<Func, const char \*\>::value, QAction\>::type \*addAction(const QString &name, const Receiver \*receiver, Func slot)](#addAction-1)
- [template \<typename Receiver, typename Func\> typename std::enable\_if\<!std::is\_convertible\<Func, const char \*\>::value, QAction\>::type \*addAction(KStandardActions::StandardAction actionType, const QString &name, const Receiver \*receiver, Func slot)](#addAction-2)
- [void addActions(const QList\<QAction \*\> &actions)](#addActions)
- [void clear()](#clear)
- [QString componentDisplayName() const](#componentDisplayName)
- [QString componentName() const](#componentName)
- [QString configGroup() const](#configGroup)
- [bool configIsGlobal() const](#configIsGlobal)
- [int count() const](#count)
- [bool isEmpty() const](#isEmpty)
- [void readSettings(KConfigGroup \*config = nullptr)](#readSettings)
- [void removeAction(QAction \*action)](#removeAction)
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
- [void menusChanged()](#menusChanged)

## Static Public Members

- [const QList\<KirigamiActionCollection \*\> &allCollections()](#allCollections)
- [QKeySequence defaultShortcut(QAction \*action)](#defaultShortcut)
- [QList\<QKeySequence\> defaultShortcuts(QAction \*action)](#defaultShortcuts)
- [bool isShortcutsConfigurable(QAction \*action)](#isShortcutsConfigurable)
- [void setDefaultShortcut(QAction \*action, const QKeySequence &shortcut)](#setDefaultShortcut)
- [void setDefaultShortcuts(QAction \*action, const QList\<QKeySequence\> &shortcuts)](#setDefaultShortcuts)
- [void setShortcutsConfigurable(QAction \*action, bool configurable)](#setShortcutsConfigurable)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### \[read-only\] actions : QQmlListProperty\<ActionData\> {#actions-prop}

**Access functions:**

- `QQmlListProperty`\<`ActionData`\> **qmlActions**()

**Notifier signal:**

- `void` **actionsChanged**()

### application : AbstractKirigamiApplication\* {#application-prop}

**Access functions:**

- `AbstractKirigamiApplication` \***application**() const
- `void` **setApplication**(`AbstractKirigamiApplication` \**application*)

**Notifier signal:**

- `void` **applicationChanged**()

### configGroup : QString {#configGroup-prop}

**Access functions:**

- `QString` **[configGroup](kirigamiactioncollection.md#configGroup)**() const
- `void` **[setConfigGroup](kirigamiactioncollection.md#setConfigGroup)**(const `QString` &*group*)

### configIsGlobal : bool {#configIsGlobal-prop}

**Access functions:**

- `bool` **[configIsGlobal](kirigamiactioncollection.md#configIsGlobal)**() const
- `void` **[setConfigGlobal](kirigamiactioncollection.md#setConfigGlobal)**(`bool` *global*)

### \[read-only\] menus : QQmlListProperty\<ActionMenu\> {#menus-prop}

**Access functions:**

- `QQmlListProperty`\<`ActionMenu`\> **menus**()

**Notifier signal:**

- `void` **[menusChanged](kirigamiactioncollection.md#menusChanged)**()

### name : QString {#name-prop}

**Access functions:**

- `QString` **name**() const
- `void` **setName**(const `QString` &*name*)

**Notifier signal:**

- `void` **nameChanged**()

### text : QString {#text-prop}

**Access functions:**

- `QString` **text**() const
- `void` **setText**(const `QString` &*text*)

**Notifier signal:**

- `void` **textChanged**()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KirigamiActionCollection::KirigamiActionCollection(QObject \**parent* = nullptr, const QString &*cName* = QString()) {#KirigamiActionCollection}

Constructor.

Allows specification of a component name other than the default application name, where needed (remember to call [setComponentDisplayName](kirigamiactioncollection.md#setComponentDisplayName)() too).

`parent` the parent object. `cName` the component name, or the default application name if empty.

### \[override virtual noexcept\] KirigamiActionCollection::~KirigamiActionCollection() {#dtor.KirigamiActionCollection}

Destructor.

### \[invokable\] QAction \*KirigamiActionCollection::action(const QString &*name*) const {#action}

Get the action with the given `name` from the action collection.

This won't return the action for the menus defined using a "\<Menu\>" tag in XMLGUI files (e.g. "\<Menu name="menuId"\>" in "applicationNameui.rc"). To access menu actions defined like this, use e.g.

```cpp
qobject_cast<QMenu *>(guiFactory()->container("menuId", this));
```

after having called setupGUI() or createGUI().

`name` Name of the [QAction](https://doc.qt.io/qt-6/qaction.html)

Returns A pointer to the [QAction](https://doc.qt.io/qt-6/qaction.html) in the collection which matches the parameters or null if nothing matches.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### QAction \*KirigamiActionCollection::action(int *index*) const {#action-1}

Return the [QAction](https://doc.qt.io/qt-6/qaction.html)\* at position `index` in the action collection.

This is equivalent to [actions](kirigamiactioncollection.md#actions)().value(index);

### const QList\<QActionGroup \*\> KirigamiActionCollection::actionGroups() const {#actionGroups}

Returns the list of all QActionGroups associated with actions in this action collection.

### \[signal\] void KirigamiActionCollection::actionHovered(QAction \**action*) {#actionHovered}

Indicates that `action` was hovered.

### \[signal\] void KirigamiActionCollection::actionTriggered(QAction \**action*) {#actionTriggered}

Indicates that `action` was triggered

### QList\<QAction \*\> KirigamiActionCollection::actions() const {#actions}

Returns the list of QActions which belong to this action collection.

The list is guaranteed to be in the same order the action were put into the collection.

### const QList\<QAction \*\> KirigamiActionCollection::actionsWithoutGroup() const {#actionsWithoutGroup}

Returns the list of QActions without an [QAction::actionGroup](https://doc.qt.io/qt-6/qaction.html#actionGroup)() which belong to this action collection.

### template \< typename ActionType, typename Receiver, typename Func \> typename std::enable\_if\<!std::is\_convertible\<Func, const char \*\>::value, ActionType\>::type \*KirigamiActionCollection::add(const QString &*name*, const Receiver \**receiver*, Func *slot*) {#add}

Creates a new action under the given name, adds it to the collection and connects the action's triggered(bool) signal to the specified receiver/member.

The type of the action is specified by the template parameter ActionType.

The [KirigamiActionCollection](kirigamiactioncollection.md) takes ownership of the action object.

`name` The internal name of the action (e.g. "file-open").

`receiver` The [QObject](https://doc.qt.io/qt-6/qobject.html) to connect the triggered(bool) signal to.

`slot` The slot or lambda to connect the triggered(bool) signal to.

Returns new action of the given type ActionType.

### \[invokable\] QAction \*KirigamiActionCollection::addAction(const QString &*name*, QAction \**action*) {#addAction}

Add an action under the given name to the collection.

Inserting an action that was previously inserted under a different name will replace the old entry, i.e. the action will not be available under the old name anymore but only under the new one.

Inserting an action under a name that is already used for another action will replace the other action in the collection (but will not delete it).

If [KAuthorized::authorizeAction](../kconfigqml/qml-org-kde-config-kauthorized.md#authorizeAction-method)() reports that the action is not authorized, it will be disabled and hidden.

The ownership of the action object is not transferred. If the action is destroyed it will be removed automatically from the [KirigamiActionCollection](kirigamiactioncollection.md).

`name` The name by which the action be retrieved again from the collection.

`action` The action to add.

Returns the same as the action given as parameter. This is just for convenience (chaining calls) and consistency with the other addAction methods, you can also simply ignore the return value.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### template \<typename Receiver, typename Func\> typename std::enable\_if\<!std::is\_convertible\<Func, const char \*\>::value, QAction\>::type \*KirigamiActionCollection::addAction(const QString &*name*, const Receiver \**receiver*, Func *slot*) {#addAction-1}

Creates a new action under the given name to the collection and connects the action's triggered(bool) signal to the specified receiver/member. The newly created action is returned.

`name` The internal name of the action (e.g. "file-open").

`receiver` The [QObject](https://doc.qt.io/qt-6/qobject.html) to connect the triggered(bool) signal to.

`slot` The slot or lambda to connect the triggered(bool) signal to.

Returns new action of the given type ActionType.

### template \<typename Receiver, typename Func\> typename std::enable\_if\<!std::is\_convertible\<Func, const char \*\>::value, QAction\>::type \*KirigamiActionCollection::addAction(KStandardActions::StandardAction *actionType*, const QString &*name*, const Receiver \**receiver*, Func *slot*) {#addAction-2}

Creates a new standard action, adds it to the collection and connects the action's triggered(bool) signal to the specified receiver/member. The newly created action is also returned.

The action can be retrieved later from the collection by its standard name as per KStandardActions::stdName.

The [KirigamiActionCollection](kirigamiactioncollection.md) takes ownership of the action object.

`actionType` The standard action type of the action to create.

`name` The name by which the action be retrieved again from the collection.

`receiver` The [QObject](https://doc.qt.io/qt-6/qobject.html) to connect the triggered(bool) signal to.

`slot` The slot or lambda to connect the triggered(bool) signal to.

Returns new action of the given type ActionType.

### void KirigamiActionCollection::addActions(const QList\<QAction \*\> &*actions*) {#addActions}

Adds a list of actions to the collection.

The objectName of the actions is used as their internal name in the collection.

The ownership of the action objects is not transferred. If the action is destroyed it will be removed automatically from the [KirigamiActionCollection](kirigamiactioncollection.md).

Uses [addAction](kirigamiactioncollection.md#addAction)(const [QString](https://doc.qt.io/qt-6/qstring.html)&, [QAction](https://doc.qt.io/qt-6/qaction.html)\*).

`actions` the list of the actions to add.

*See also* [addAction](kirigamiactioncollection.md#addAction)()

### \[static\] const QList\<KirigamiActionCollection \*\> &KirigamiActionCollection::allCollections() {#allCollections}

Access the list of all action collections in existence for this app

### \[signal\] void KirigamiActionCollection::changed() {#changed}

Emitted when an action has been inserted into, or removed from, this action collection.

### void KirigamiActionCollection::clear() {#clear}

Clears the entire action collection, deleting all actions.

### QString KirigamiActionCollection::componentDisplayName() const {#componentDisplayName}

The display name for the associated component.

*See also* [setComponentDisplayName](kirigamiactioncollection.md#setComponentDisplayName)()

### QString KirigamiActionCollection::componentName() const {#componentName}

The component name with which this class is associated.

*See also* [setComponentName](kirigamiactioncollection.md#setComponentName)()

### QString KirigamiActionCollection::configGroup() const {#configGroup}

Returns the KConfig group with which settings will be loaded and saved.

> **Note:** Getter function for property [configGroup](kirigamiactioncollection.md#configGroup-prop).

*See also* [setConfigGroup](kirigamiactioncollection.md#setConfigGroup)()

### bool KirigamiActionCollection::configIsGlobal() const {#configIsGlobal}

Returns whether this action collection's configuration should be global to KDE ( `true` ), or specific to the application ( `false` ).

> **Note:** Getter function for property [configIsGlobal](kirigamiactioncollection.md#configIsGlobal-prop).

### int KirigamiActionCollection::count() const {#count}

Returns the number of actions in the collection.

This is equivalent to [actions](kirigamiactioncollection.md#actions)().count().

### \[static\] QKeySequence KirigamiActionCollection::defaultShortcut(QAction \**action*) {#defaultShortcut}

Get the default primary shortcut for the given action.

`action` the action for which the default primary shortcut should be returned.

Returns the default primary shortcut of the given action

*See also* [setDefaultShortcut](kirigamiactioncollection.md#setDefaultShortcut)()

### \[static\] QList\<QKeySequence\> KirigamiActionCollection::defaultShortcuts(QAction \**action*) {#defaultShortcuts}

Get the default shortcuts for the given action.

`action` the action for which the default shortcuts should be returned.

Returns the default shortcuts of the given action

*See also* [setDefaultShortcuts](kirigamiactioncollection.md#setDefaultShortcuts)()

### \[signal\] void KirigamiActionCollection::inserted(QAction \**action*) {#inserted}

Indicates that `action` was inserted into this action collection.

### bool KirigamiActionCollection::isEmpty() const {#isEmpty}

Returns whether the action collection is empty or not.

### \[static\] bool KirigamiActionCollection::isShortcutsConfigurable(QAction \**action*) {#isShortcutsConfigurable}

Returns true if the given action's shortcuts may be configured by the user.

`action` the action for the hint should be verified.

### \[signal\] void KirigamiActionCollection::menusChanged() {#menusChanged}

Emitted when the declarative menu tree changes.

> **Note:** Notifier signal for property [menus](kirigamiactioncollection.md#menus-prop).

### void KirigamiActionCollection::readSettings(KConfigGroup \**config* = nullptr) {#readSettings}

Read all key associations from `config`.

If `config` is zero, read all key associations from the application's configuration file KSharedConfig::openConfig(), in the group set by [setConfigGroup](kirigamiactioncollection.md#setConfigGroup)().

### void KirigamiActionCollection::removeAction(QAction \**action*) {#removeAction}

Removes an action from the collection and deletes it. `action` The action to remove.

### void KirigamiActionCollection::setComponentDisplayName(const QString &*displayName*) {#setComponentDisplayName}

Set the component `displayName` associated with this action collection.

(e.g. for the toolbar editor) KXMLGUIClient::setComponentName takes care of calling this.

*See also* [componentDisplayName](kirigamiactioncollection.md#componentDisplayName)()

### void KirigamiActionCollection::setComponentName(const QString &*componentName*) {#setComponentName}

Set the `componentName` associated with this action collection.

> **Warning:** Don't call this method on a [KirigamiActionCollection](kirigamiactioncollection.md) that contains actions. This is not supported.

`componentName` the name which is to be associated with this action collection, or QString() to indicate the app name. This is used to load/save settings into XML files.

KXMLGUIClient::setComponentName takes care of calling this.

*See also* [componentName](kirigamiactioncollection.md#componentName)()

### void KirigamiActionCollection::setConfigGlobal(bool *global*) {#setConfigGlobal}

Set whether this action collection's configuration should be global to KDE ( `true` ), or specific to the application ( `false` ).

`global` whether the configuration should be global to KDE.

> **Note:** Setter function for property [configIsGlobal](kirigamiactioncollection.md#configIsGlobal-prop).

### void KirigamiActionCollection::setConfigGroup(const QString &*group*) {#setConfigGroup}

Sets `group` as the KConfig group with which settings will be loaded and saved.

> **Note:** Setter function for property [configGroup](kirigamiactioncollection.md#configGroup-prop).

*See also* [configGroup](kirigamiactioncollection.md#configGroup)()

### \[static\] void KirigamiActionCollection::setDefaultShortcut(QAction \**action*, const QKeySequence &*shortcut*) {#setDefaultShortcut}

Set the default shortcut for the given action.

`action` the action for which the default shortcut should be set.

`shortcut` the shortcut to use for the given action in its specified shortcutContext()

*See also* [defaultShortcut](kirigamiactioncollection.md#defaultShortcut)()

### \[static invokable\] void KirigamiActionCollection::setDefaultShortcuts(QAction \**action*, const QList\<QKeySequence\> &*shortcuts*) {#setDefaultShortcuts}

Set the default shortcuts for the given action.

`action` the action for which the default shortcut should be set.

`shortcuts` the shortcuts to use for the given action in its specified shortcutContext()

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [defaultShortcuts](kirigamiactioncollection.md#defaultShortcuts)()

### \[static\] void KirigamiActionCollection::setShortcutsConfigurable(QAction \**action*, bool *configurable*) {#setShortcutsConfigurable}

Indicate whether the user may configure the action's shortcuts.

`action` the action for the hint should be verified.

`configurable` set to true if the shortcuts of the given action may be configured by the user, otherwise false.

*See also* [isShortcutsConfigurable](kirigamiactioncollection.md#isShortcutsConfigurable)()

### QAction \*KirigamiActionCollection::takeAction(QAction \**action*) {#takeAction}

Removes an action from the collection.

The ownership of the action object is not changed.

`action` the action to remove.

### void KirigamiActionCollection::writeSettings(KConfigGroup \**config* = nullptr, bool *writeDefaults* = false, QAction \**oneAction* = nullptr) const {#writeSettings}

Write the current configurable key associations to `config`. What the function does if `config` is zero depends. If this action collection belongs to a KXMLGUIClient the setting are saved to the kxmlgui definition file. If not the settings are written to the applications config file.

> **Note:** `oneAction` and `writeDefaults` have no meaning for the kxmlgui configuration file.

`config` Config object to save to, or null (see above)

`writeDefaults` set to true to write settings which are already at defaults.

`oneAction` pass an action here if you just want to save the values for one action, eg. if you know that action is the only one which has changed.
