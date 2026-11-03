---
title: "KAuthorized QML Type (Singleton)"
description: "Singleton used for checking whether actions are allowed by a user."
---

# KAuthorized QML Type (Singleton)

Singleton used for checking whether actions are allowed by a user.

- Import Statement: import org.kde.config
- In C++: [KAuthorized](../kconfigcore/kauthorized.md)

> **Note:** **Note:** This type is a QML singleton. There is only one instance of this type in the QML engine.

## Detailed Description {#details}

KDE's Kiosk settings allow to control whether a user is allowed to perform actions such as opening files or running shell commands.

This singleton can be used to implement per-application controls for what the user is allowed to do.

The relevant settings are read from the application's [KSharedConfig](../kconfigcore/ksharedconfig.md) instance, so actions can be disabled on a per-application or global basis (by using the kdeglobals file).

*See also* [Kiosk - Simple configuration management for large deployment](https://develop.kde.org/docs/administration/kiosk/)

## Property Documentation {#property-documentation}

### GenericAction : enumeration {#GenericAction-prop}

Actions pertaining to the KDE Kiosk system that are prepended with "action/".

| Constant | Description |
| --- | --- |
| OPEN\_WITH | If the open-with menu should be shown for files etc. |
| EDITFILETYPE | If mime-type accociations are allowed to be configured |
| OPTIONS\_SHOW\_TOOLBAR | If the toolbar should be displayed in apps |
| SWITCH\_APPLICATION\_LANGUAGE | If an action to switch the app language should be shown |
| BOOKMARKS | If saving bookmarks is allowed |

### GenericRestriction : enumeration {#GenericRestriction-prop}

The enum values lower cased represent the action that is authorized.

For example the [KAuthorized](qml-org-kde-config-kauthorized.md).SHELL\_ACCESS value is converted to the "shell\_access" string.

| Constant | Description |
| --- | --- |
| SHELL\_ACCESS | If the user is authorized to open a shell or execute shell commands |
| GHNS | If the collaborative data sharing framework KNewStuff is authorized GUI behavior |
| LINEEDIT\_REVEAL\_PASSWORD | If typed characters in password fields can be made visible |
| LINEEDIT\_TEXT\_COMPLETION | If line edits should be allowed to display completions |
| MOVABLE\_TOOLBARS | If toolbars of apps should be movable |
| RUN\_DESKTOP\_FILES | If .desktop files should be run as executables when clicked |

## Method Documentation {#method-documentation}

### void authorize(string *action*) {#authorize-method}

Returns whether the user is permitted to perform a certain `action`.

All settings are read from the `[KDE Action Restrictions]` group. For example, if kdeglobals contains

```cpp
[KDE Action Restrictions][$i]
shell_access=false
```

then

```cpp
KAuthorized.authorize("shell_access");
```

will return `false`.

This method is intended for actions that do not necessarily have a one-to-one correspondence with a menu or toolbar item (ie: a QAction in a KXMLGui application). "shell\_access" is an example of such a "generic" action.

The convention for actions like "File-\>New" is to prepend the action name with "action/", for example "action/file\_new". This is what [authorizeAction](qml-org-kde-config-kauthorized.md#authorizeAction-method)() does.

Returns `true` if the action is authorized, `false` otherwise.

*See also* [authorizeAction](qml-org-kde-config-kauthorized.md#authorizeAction-method)(), [GenericRestriction](qml-org-kde-config-kauthorized.md#GenericRestriction-prop)

### void authorize(KAuthorized.GenericRestriction *action*) {#authorize-method-1}

Returns whether the user is permitted to perform a common `action`.

The enum values lower cased represent the action that is passed in to [KAuthorized::authorize](qml-org-kde-config-kauthorized.md#authorize-method)(const [QString](https://doc.qt.io/qt-6/qstring.html) &action).

This function overloads [KAuthorized::authorize(string action)](qml-org-kde-config-kauthorized.md#authorize-method).

### void authorizeAction(string *action*) {#authorizeAction-method}

Returns whether the user is permitted to perform a certain `action`.

This behaves like [authorize](qml-org-kde-config-kauthorized.md#authorize-method)(), except that "action/" is prepended to `action`. So if kdeglobals contains

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

*See also* [authorize](qml-org-kde-config-kauthorized.md#authorize-method)()

### void authorizeAction(KAuthorized.GenericAction *action*) {#authorizeAction-method-1}

This function overloads [KAuthorized::authorize(string action)](qml-org-kde-config-kauthorized.md#authorize-method).

### void authorizeControlModule(string *pluginId*) {#authorizeControlModule-method}

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
