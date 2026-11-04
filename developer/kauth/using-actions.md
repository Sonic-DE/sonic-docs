---
title: Using actions in your applications
description: Write a KAuth helper, register its actions, and call it from your application.
source_url: https://develop.kde.org/docs/features/kauth/using_kauth/
source_authors: [Nicola Gigante, Dario Freddi, Carl Schwan, Alexander Volkov, Chris Holland, Mikhail Zolotukhin, Thiago Sueto]
license: LGPL-2.1-or-later
license_url: https://spdx.org/licenses/LGPL-2.1-or-later.html
checked_against: sonic-frameworks-auth (examples/helper.cpp, examples/client.cpp, KF6AuthMacros.cmake, helpersupport.cpp, backends/dbus/DBusHelperProxy.cpp, policy-gen)
---

# Using actions in your applications

With the [KAuth concepts](introduction.md) and the registration of actions covered, here is how to use KAuth actions in your application.

## Implementing an action helper

The helper is a QObject subclass, and each action is a public slot. `sonic-frameworks-auth` has a complete example in its `examples/` folder. Its helper class is declared like this:

```cpp
#include <KAuth/ActionReply>
#include <KAuth/HelperSupport>

using namespace KAuth;

class MyHelper : public QObject
{
    Q_OBJECT
public Q_SLOTS:
    ActionReply read(const QVariantMap &args);
    ActionReply write(const QVariantMap &args);
    ActionReply longaction(const QVariantMap &args);
};
```

A slot's name is the action name without the helper ID in front (if it is there), with all dots replaced by underscores. Here the helper ID is `org.kde.kf6auth.example`, so the three slots implement the actions `org.kde.kf6auth.example.read`, `org.kde.kf6auth.example.write` and `org.kde.kf6auth.example.longaction`.

The action name doesn't have to start with the helper ID, but it is good practice. To make `MyHelper` also implement an action like `org.foo.datetime.changetime`, which doesn't start with the helper ID, you would write a slot called `org_foo_datetime_changetime()`.

The slot's signature is fixed: it returns an [ActionReply](/docs/api/kauth/kauth-actionreply), which carries results, error codes and custom data back to the application when the action has finished. The return type may also be written as `KAuth::ActionReply`.

Here is the `read()` action, which reads a file:

```cpp
ActionReply MyHelper::read(const QVariantMap &args)
{
    ActionReply reply;
    QString filename = args["filename"].toString();
    QFile file(filename);
    if (!file.open(QIODevice::ReadOnly)) {
        reply = ActionReply::HelperErrorReply();
        reply.setErrorDescription(file.errorString());
        return reply;
    }
    QTextStream stream(&file);
    QString contents;
    stream >> contents;
    reply.addData("contents", contents);
    return reply;
}
```

It first creates a default reply, which reports success. Then it takes the file name from the `QVariantMap` argument that the application set before calling the helper. If it can't open the file, it returns an `ActionReply` reporting that an error happened in the helper, with QFile's error message as its description. Otherwise it reads the file and adds the content to the reply.

The class is compiled into a program of its own, which needs a `main()` function and some setup. You don't write them: the `KAUTH_HELPER_MAIN()` macro does it:

```cpp
KAUTH_HELPER_MAIN("org.kde.kf6auth.example", MyHelper)
```

The first argument is the helper ID. The application uses the same string to say which helper to call, so watch out for typos: nothing can detect them.

The second argument is the helper's class. A complex helper can have many source files, but the macro must appear in one of them.

To install the helper, KAuth provides the CMake function `kauth_install_helper_files()`:

```cmake
add_executable(<helper_target> your sources...)
target_link_libraries(<helper_target> KF6::AuthCore your libraries...)
install(TARGETS <helper_target> DESTINATION ${KAUTH_HELPER_INSTALL_DIR})

kauth_install_helper_files(<helper_target> <helper_id> <user>)
```

The first argument is the CMake target of the helper program, which you build and install yourself (and link against `KF6::AuthCore`). Install it in `${KAUTH_HELPER_INSTALL_DIR}`, or `kauth_install_helper_files()` won't work. The second argument is the helper ID; don't misspell it, and don't quote it. `user` is the user the helper runs as: usually `root`, but some actions need fewer rights, and then you should use the right user (for example `apache` to change Apache's settings).

The function generates and installs two files: a D-Bus policy that lets the helper register on the system bus (`<helper_id>.conf` in D-Bus's `system.d`), and a D-Bus system service file, so that the system bus starts the helper when it is needed.

The helper doesn't inherit the calling application's environment. If `HOME` isn't set, the helper sets it from the user database.

## Registering the actions

For actions to be authorized, they must be added to the authorization system's policy database. KAuth does that with a CMake function:

```cmake
kauth_install_actions(<helper_id> <actions definition file>)
```

The actions definition file (see [The .actions file](introduction.md#the-actions-file)) lists the actions your code implements and their default security settings. It is an INI file with a group for each action. For the `read()` action:

```ini
[org.kde.kf6auth.example.read]
Name=Read action
Description=Read action description
Policy=auth_admin
Persistence=session
```

`Name` describes the action for whoever reads the file. `Description` is the message shown to the user in the authentication dialog; keep it reasonably short. `Policy` is the default rule the user must meet to be authorized:

- **yes**: always allowed
- **no**: always denied
- **auth_self**: the user must authenticate as themselves
- **auth_admin**: the user must authenticate as an administrator

`Persistence` is optional and says how long an authorization lasts:

- **session**
- **always**

Without it, the user is asked every time.

> **Note:** Only the polkit backend uses `Persistence`.

> **Warning:** With polkit, `session` and `always` mean the same: the authorization is kept for a short time (polkit's `auth_admin_keep`).

## Calling the helper from the application

With the helper ready, the main application calls it. `examples/client.cpp` shows how:

- To refer to an action, create an [Action](/docs/api/kauth/kauth-action) object.
- Each `Action` refers to an action by its identifier.
- Two objects with the same identifier refer to the same action.
- With an `Action` you can authorize and execute the action.
- Executing an action gives you an [ExecuteJob](/docs/api/kauth/kauth-executejob), a normal [KJob](/docs/api/kcoreaddons/kjob) that you can run synchronously or asynchronously.

This code calls the action of the example:

```cpp
QVariantMap args;
args["filename"] = filename;
Action readAction("org.kde.kf6auth.example.read");
readAction.setHelperId("org.kde.kf6auth.example");
readAction.setArguments(args);
ExecuteJob *job = readAction.execute();
if (!job->exec()) {
    qDebug() << "KAuth returned an error code:" << job->error();
} else {
    QString contents = job->data()["contents"].toString();
    qDebug() << "KAuth succeeded. Contents: " << contents;
}
```

It creates the action object with the action's identifier, then puts the file name (of a file the user may not read) into the arguments `QVariantMap`, which the helper's `read()` slot receives. It runs the action synchronously and reads the reply; if it succeeded, the data is in the returned `QVariantMap`. You must set the helper ID on the action explicitly: this is a safety measure against calling a helper by accident, and KAuth actions don't need a helper at all (that is the default).

If your application calls the helper several times, it must do so from the same thread.

## Asynchronous calls, progress and stopping

The example's `org.kde.kf6auth.example.longaction` action takes a long time, so it needs more:

- The helper regularly tells the application how far it has got.
- The application can stop the action, for example when the user cancels it or quits.

The code:

```cpp
ActionReply MyHelper::longaction(const QVariantMap &)
{
    for (int i = 1; i <= 100; i++) {
        if (HelperSupport::isStopped()) {
            break;
        }
        HelperSupport::progressStep(i);
        QThread::usleep(250000);
    }
    return ActionReply::SuccessReply();
}
```

The action only waits in a loop, but it shows the important parts. `HelperSupport::progressStep()` sends the progress to the application.

`progressStep()` has two overloads. The one used here takes an integer, which the application's `ExecuteJob` uses as its percentage (KJob's `percent()` signal). The other takes a `QVariantMap`, which the job passes on unchanged with its `newData()` signal, so you can report any data you like.

The loop ends when `HelperSupport::isStopped()` returns `true`, which happens when the application asks for the action to stop (`ExecuteJob::kill()`). The helper decides whether to obey; if it does, it should return from the slot, *not* exit.

## Debugging helpers

Helper code needs debugging too, so KAuth installs a Qt message handler in the helper: every `qDebug()` and similar call is sent to the application and printed there by Qt's message system, with the same level. If the helper does

```cpp
qDebug() << "I'm in the helper";
```

the *application's* output shows

```text
Debug message from helper: I'm in the helper
```

The level is kept, so `qFatal()` in the helper (not recommended anyway) aborts not only the helper but also the application.

The code examples on this page come from `sonic-frameworks-auth/examples` and are licensed under the LGPL-2.1-or-later.
