---
title: "KAuthorized Class"
description: "Used for checking whether actions are allowed for a user."
---

# KAuthorized Class

Used for checking whether actions are allowed for a user.

- **Header:** `#include <KAuthorized>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

## Public Types

- [enum KAuthorized::GenericAction](#GenericAction-enum)
- [enum KAuthorized::GenericRestriction](#GenericRestriction-enum)

## Static Public Members

- [bool authorize(const QString &action)](#authorize)
- [bool authorize(KAuthorized::GenericRestriction action)](#authorize-1)
- [bool authorizeAction(const QString &action)](#authorizeAction)
- [bool authorizeAction(KAuthorized::GenericAction action)](#authorizeAction-1)
- [bool authorizeControlModule(const QString &pluginId)](#authorizeControlModule)

## Detailed Description {#details}

The functions in this namespace provide the core of the Kiosk action restriction system; the KIO and KXMLGui frameworks build on this.

KDE's Kiosk settings allow to control whether a user is allowed to perform actions such as opening files or running shell commands.

The relevant settings are read from the application's [KSharedConfig](ksharedconfig.md) instance, so actions can be disabled on a per-application or global basis (by using the kdeglobals file).

## Member Type Documentation {#member-type-documentation}

### enum KAuthorized::GenericAction {#GenericAction-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KAuthorized::OPEN_WITH` | `1` | If the open-with menu should be shown for files etc. |
| `KAuthorized::EDITFILETYPE` | `2` | If mime-type accociations are allowed to be configured |
| `KAuthorized::OPTIONS_SHOW_TOOLBAR` | `3` | If the toolbar should be displayed in apps |
| `KAuthorized::SWITCH_APPLICATION_LANGUAGE` | `4` | If an action to switch the app language should be shown |
| `KAuthorized::BOOKMARKS` | `5` | If saving bookmarks is allowed |

### enum KAuthorized::GenericRestriction {#GenericRestriction-enum}

The enum values lower cased represent the action that is authorized For example the SHELL\_ACCESS value is converted to the "shell\_access" string.

| Constant | Value | Description |
| --- | --- | --- |
| `KAuthorized::SHELL_ACCESS` | `1` | If the user is authorized to open a shell or execute shell commands |
| `KAuthorized::GHNS` | `2` | If the collaborative data sharing framework KNewStuff is authorized GUI behavior |
| `KAuthorized::LINEEDIT_REVEAL_PASSWORD` | `3` | If typed characters in password fields can be made visible |
| `KAuthorized::LINEEDIT_TEXT_COMPLETION` | `4` | If line edits should be allowed to display completions |
| `KAuthorized::MOVABLE_TOOLBARS` | `5` | If toolbars of apps should be movable |
| `KAuthorized::RUN_DESKTOP_FILES` | `6` | If .desktop files should be run as executables when clicked |

## Member Function Documentation {#member-function-documentation}

### \[static invokable\] bool KAuthorized::authorize(const QString &*action*) {#authorize}

Returns whether the user is permitted to perform a certain `action`.

All settings are read from the `[KDE Action Restrictions]` group. For example, if kdeglobals contains

```cpp
[KDE Action Restrictions][$i]
shell_access=false
```

then

```cpp
KAuthorized::authorize("shell_access");
```

will return `false`.

This method is intended for actions that do not necessarily have a one-to-one correspondence with a menu or toolbar item (ie: a QAction in a KXMLGui application). "shell\_access" is an example of such a "generic" action.

The convention for actions like "File-\>New" is to prepend the action name with "action/", for example "action/file\_new". This is what [authorizeAction](kauthorized.md#authorizeAction)() does.

Returns `true` if the action is authorized, `false` otherwise.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [authorizeAction](kauthorized.md#authorizeAction)()

### \[static invokable\] bool KAuthorized::authorize(KAuthorized::GenericRestriction *action*) {#authorize-1}

Returns whether the user is permitted to perform a common `action`.

The enum values lower cased represent the action that is passed in to [KAuthorized::authorize](kauthorized.md#authorize)(const [QString](https://doc.qt.io/qt-6/qstring.html) &action).

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

This function overloads [KAuthorized::authorize(const QString &action)](kauthorized.md#authorize).

### \[static invokable\] bool KAuthorized::authorizeAction(const QString &*action*) {#authorizeAction}

Returns whether the user is permitted to perform a certain `action`.

This behaves like [authorize](kauthorized.md#authorize)(), except that "action/" is prepended to `action`. So if kdeglobals contains

```cpp
[KDE Action Restrictions][$i]
action/file_new=false
```

then

```cpp
KAuthorized::authorizeAction("file_new");
```

will return `false`.

KXMLGui-based applications should not normally need to call this function, as KActionCollection will do it automatically.

Returns `true` if the QAction is authorized, `false` otherwise.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [authorize](kauthorized.md#authorize)()

### \[static invokable\] bool KAuthorized::authorizeAction(KAuthorized::GenericAction *action*) {#authorizeAction-1}

Overload to authorize a common `action`.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

This function overloads [KAuthorized::authorizeAction(const QString &action)](kauthorized.md#authorizeAction).

### \[static invokable\] bool KAuthorized::authorizeControlModule(const QString &*pluginId*) {#authorizeControlModule}

Returns whether the user is permitted to use a certain control module with the given `pluginId`.

All settings are read from the "\[KDE Control Module Restrictions\]" group. For example, if kdeglobals contains

```cpp
[KDE Control Module Restrictions][$i]
kcm_desktop-settings=false
```

then

```cpp
KAuthorized::authorizeControlModule("kcm_desktop-settings");
```

will return `false`.

Returns `true` if access to the module is authorized, `false` otherwise.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.
