---
title: KAuth
description: KAuth, privilege elevation for your program.
source_url: https://develop.kde.org/docs/features/kauth/
source_authors: [Nicola Gigante, Dario Freddi, David Edmundson, Carl Schwan, Chris Holland, Mikhail Zolotukhin, Paul Worrall, Thiago Sueto, Tobias Fella]
license: LGPL-2.1-or-later
license_url: https://spdx.org/licenses/LGPL-2.1-or-later.html
checked_against: sonic-frameworks-auth (policy-gen, polkit-1 and mac policy generators, KF6AuthMacros.cmake, ConfigureChecks.cmake)
---

# KAuth

KAuth is part of `sonic-frameworks-auth` (`find_package(KF6 REQUIRED COMPONENTS Auth)`). Its API reference is in [KAuth](/docs/api/kauth/kauth-index).

## Privilege escalation

Sometimes an application needs to do something that requires administrator rights: write a configuration file owned by root, set the system clock, or other administrative tasks.

The obvious solution is to run the whole application as root, but that exposes the user to many security problems. Instead, run the application as a normal user, and authenticate to run only small parts of it as root or another user.

## What KAuth is

KAuth is an authorization framework that wraps lower-level libraries and tools. When you use KAuth, you don't need to care which authorization system the target system uses: KAuth handles that. On Linux, including SonicDE, it uses polkit; on macOS it uses Authorization Services.

KAuth can also run restricted parts of your code with elevated privileges (*helpers*), gives you easy ways to communicate with them, and keeps them secure throughout the authorization process.

## Concepts

A few concepts are needed to use KAuth. Many come from the underlying APIs such as polkit, so if you know those you can skip this section.

- An **action** is a single task that needs authorization. Each action has a unique identifier in reverse domain name syntax, like `org.foo.this.is.an.action`. For example, if your application needs to read a file the user has no rights to, it needs an action like `org.foo.auth.example.read`. Each action should be one single task: then system administrators can fine-tune which users may perform which actions, and the privileged parts of your application stay locked down more securely.

- The **authorization system** is the underlying framework (such as polkit or Authorization Services) KAuth talks to. KAuth aims to keep you from having to know or care about it, but this page mentions it often to explain how KAuth works.

- The **action namespace** is the first part of the action identifier. In `org.foo.auth.example.read`, `org.foo.auth.example` is the action namespace and `read` is the action name. This matters for helpers and `.actions` files.

- **Authorization** is the phase in which the authorization system makes its checks (and possibly asks the user for credentials). It takes place before any action is executed. KAuth handles it: you can start it yourself, but usually you don't need to, because KAuth only executes an action when the authorization system allows it.

- **Authentication** is an optional phase during authorization, when the action's policy requires the user to prove who they are. It is handled entirely by the authorization system, not by KAuth (by design, KAuth can't take over this phase); in SonicDE, the polkit authentication agent (`sonic-polkit-agent`) shows the dialog. It is still useful to know about it.

- **Execution** happens only if authorization succeeded. It may just confirm the successful authorization, or run a function in a helper.

- A **helper** is a separate program running as a privileged user (usually root), which is started for an action that has a helper attached. KAuth handles communication with the helper and starting and stopping it, so you hardly notice that it is a separate program.

## The phases

Say you use KAuth for a privileged operation, and the action requires the user to authenticate (the most common case). Then:

- The user wants to do a privileged task.
- The application creates an action for the task.
- The application asks for the action to be executed.
- From here on, KAuth or the authorization system handles everything:
- *Authorization begins.*
- The system finds that the user must authenticate to be authorized.
- *Authentication begins.*
- The user is asked for their password, fingerprint or similar.
- *Authentication ends.*
- If authentication failed, the action is rejected.
- Otherwise, the system grants the user an explicit authorization.
- *Authorization ends.*
- If authorization failed, the action is rejected.
- Otherwise, the action is executed.
- *Execution begins.*
- The helper is started as root, and the requested code runs.
- Right after starting, the helper checks the authorization again: this is more secure, and some authorization systems only authorize at the beginning of execution. If the caller isn't authorized, the helper stops.
- If the caller is authorized, the helper does the task.
- *Execution ends.*
- The application receives the helper's result.

In your code you only deal with the first steps; KAuth handles the rest.

## Creating actions

For security, authorization systems require actions to be registered when the application is installed, so that the system administrator knows every action that can be authorized. So if you use KAuth, you register new actions with the system.

## Naming actions and namespaces

Authorization systems are strict about action names. KAuth only accepts action identifiers made of **lowercase letters and digits**, separated by dots:

- `org.foo.auth.example.read` **OK**
- `org.Foo.auth.example.read` **not OK**
- `org.foo.auth.example-1.read` **not OK**
- `org.foo.auth.example.readFile` **not OK**
- `org.foo.auth.example.readfile` **OK**

## The .actions file

Actions are registered with an `.actions` file, a standard INI file listing the actions. Its texts can be translated (`Name[de]=…`).

An `.actions` file can contain any number of actions, as long as they **all belong to the same action namespace**. This is very important.

The format is:

```ini
[org.foo.auth.example.action]
Name=Example action
Description=The system is attempting to perform the example action
Policy=auth_admin
Persistence=session
```

- **The group name**: the action identifier.
- **Name**: a human-readable name for the action.
- **Description**: the message shown to the user during authentication, if any.
- **Policy**: the default policy for the action, for the user's active session. One of:
  - `yes`: allowed without authentication
  - `no`: always denied, without authentication
  - `auth_self`: allowed if the user authenticates as themselves
  - `auth_admin`: allowed if the user authenticates as an administrator
- **PolicyInactive**: optional, the same for inactive sessions (for example a session that isn't on the active console). Without it, actions are denied in inactive sessions.
- **Persistence**: optional, only used by the polkit backend, and only when the policy is `auth_admin` or `auth_self`. It makes the authorization granted by authenticating persist:
  - `session`
  - `always`

  With polkit both values have the same effect: KAuth generates polkit's `auth_admin_keep` (or `auth_self_keep`) policy, which keeps the authorization for a short time. Without `Persistence`, the user is asked every time.

## The Domain group

An `.actions` file can have a special group, `[Domain]`, with more information about the action namespace. All its keys are optional:

```ini
[Domain]
Name=The KAuth example series
Icon=kauth-example
URL=https://sonicde.org/
```

- **Name**: usually the name of the application that uses this namespace (polkit's vendor).
- **Icon**: an icon name shared by all the actions.
- **URL**: your organization's home page.

## Registering the actions with CMake

When your actions are defined (any number of them, all in the same namespace, for example `org.foo.auth.example.*`), register them with the system with a KAuth CMake function. If your file is called `org.foo.auth.example.actions`:

```cmake
kauth_install_actions(org.foo.auth.example org.foo.auth.example.actions)
```

The syntax is:

```cmake
kauth_install_actions(<namespace_id> <actions definition file>)
```

where `namespace_id` is the namespace of your actions, here `org.foo.auth.example`. With polkit, this generates a polkit policy file, `<namespace_id>.policy`, and installs it in polkit's actions directory (`KAUTH_POLICY_FILES_INSTALL_DIR`, usually `/usr/share/polkit-1/actions`). On macOS the actions are added to the system's action registry when the project is installed.

Next: [Using actions in your applications](using-actions.md).
