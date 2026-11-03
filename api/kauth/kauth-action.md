---
title: "KAuth::Action Class"
description: "Class to access, authorize and execute actions."
---

# KAuth::Action Class

Class to access, authorize and execute actions. [More...](#details)

- **Header:** `#include <KAuth/Action>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Auth)`  
  `target_link_libraries(mytarget PRIVATE KF6::AuthCore)`

[List of all members, including inherited members](kauth-action-members.md)

## Public Types

- [enum Action::AuthDetail](#AuthDetail-enum)
- [enum Action::AuthStatus](#AuthStatus-enum)
- [Action::DetailsMap](#DetailsMap-typedef)
- [enum Action::ExecutionMode](#ExecutionMode-enum)

## Public Functions

- [Action()](#Action)
- [Action(const QString &name)](#Action-2)
- [Action(const QString &name, const KAuth::Action::DetailsMap &details)](#Action-3)
- [Action(const KAuth::Action &action)](#Action-1)
- [void addArgument(const QString &key, const QVariant &value)](#addArgument)
- [QVariantMap arguments() const](#arguments)
- [KAuth::Action::DetailsMap detailsV2() const](#detailsV2)
- [KAuth::ExecuteJob \*execute(KAuth::Action::ExecutionMode mode = ExecuteMode)](#execute)
- [bool hasHelper() const](#hasHelper)
- [QString helperId() const](#helperId)
- [bool isValid() const](#isValid)
- [QString name() const](#name)
- [QWindow \*parentWindow() const](#parentWindow) (since 6.0)
- [void setArguments(const QVariantMap &arguments)](#setArguments)
- [void setDetailsV2(const KAuth::Action::DetailsMap &details)](#setDetailsV2)
- [void setHelperId(const QString &id)](#setHelperId)
- [void setName(const QString &name)](#setName)
- [void setParentWindow(QWindow \*parent)](#setParentWindow) (since 6.0)
- [void setTimeout(int timeout)](#setTimeout)
- [void setTimeout(std::chrono::milliseconds msec)](#setTimeout-1)
- [KAuth::Action::AuthStatus status() const](#status)
- [int timeout() const](#timeout)
- [bool Action::operator!=(const KAuth::Action &action) const](#operator-not-eq)
- [bool Action::operator==(const KAuth::Action &action) const](#operator-eq-eq)

## Detailed Description {#details}

This is the main class of the [KAuth](kauth-module.md) API. It provides the interface to manipulate actions. Every action is identified by its name. Every instance of the Action class with the same name refers to the same action.

Once you have an action object you can tell the helper to execute it (asking the user to authenticate if needed) with the [execute](kauth-action.md#execute)() method. The simplest thing to do is to execute a single action synchronously blocking for the reply by calling [KJob::exec](../kcoreaddons/kjob.md#exec)() on the job object returned by [execute](kauth-action.md#execute)().

For asynchronous calls, use KAuth::ExecuteJob::start() instead. It sends the request to the helper and returns immediately. Before doing so you should however connect to at least the [KJob::result](../kcoreaddons/kjob.md#result)([KJob](../kcoreaddons/kjob.md) \*) signal to receive a slot call once the action is done executing.

To use the [execute](kauth-action.md#execute)() method you have to set the default helper's ID using the [setHelperId](kauth-action.md#setHelperId)() static method. Alternatively, you can specify the helperID using the overloaded version of the methods that takes it as a parameter.

Each action object contains a [QVariantMap](https://doc.qt.io/qt-6/qvariant.html#QVariantMap-typedef) object that is passed directly to the helper when the action is executed. You can access this map using the [arguments](kauth-action.md#arguments)() method. You can insert into it any kind of custom data you need to pass to the helper.

```cpp
void MyApp::runAction()
{
    action = KAuth::Action("org.kde.myapp.action");
    KAuth::ExecuteJob *job = action.execute();
    connect(job, &KAuth::ExecuteJob::result, this, &MyApp::actionResult);
    job->start();
}

void MyApp::actionResult(KJob *kjob)
{
    auto job = qobject_cast<KAuth::ExecuteJob *>(kjob);
    qDebug() << job.error() << job.data();
}
```

## Member Type Documentation {#member-type-documentation}

### enum Action::AuthDetail {#AuthDetail-enum}

The backend specific details.

| Constant | Value |   |
| --- | --- | --- |
| `KAuth::Action::AuthDetail::DetailOther` | `0` |   |
| `KAuth::Action::AuthDetail::DetailMessage` | `1` | The message to show in authentication dialog. |

### enum Action::AuthStatus {#AuthStatus-enum}

The values set by authorization methods

| Constant | Value | Description |
| --- | --- | --- |
| `KAuth::Action::DeniedStatus` | `0` | The authorization has been denied by the authorization backend |
| `KAuth::Action::ErrorStatus` | `1` | An error occurred |
| `KAuth::Action::InvalidStatus` | `2` | An invalid action cannot be authorized |
| `KAuth::Action::AuthorizedStatus` | `3` | The authorization has been granted by the authorization backend |
| `KAuth::Action::AuthRequiredStatus` | `4` | The user could obtain the authorization after authentication |
| `KAuth::Action::UserCancelledStatus` | `5` | The user pressed Cancel the authentication dialog. Currently used only on the mac |

### Action::DetailsMap {#DetailsMap-typedef}

Map of details.

### enum Action::ExecutionMode {#ExecutionMode-enum}

| Constant |   |
| --- | --- |
| `KAuth::Action::ExecuteMode` | `0` |
| `KAuth::Action::AuthorizeOnlyMode` | `1` |

## Member Function Documentation {#member-function-documentation}

### Action::Action() {#Action}

Default constructor

This constructor sets the name to the empty string. Such an action is invalid and cannot be authorized nor executed, so you need to call [setName](kauth-action.md#setName)() before you can use the object.

### Action::Action(const QString &*name*) {#Action-2}

This creates a new action object with this name `name` The name of the new action

### Action::Action(const QString &*name*, const KAuth::Action::DetailsMap &*details*) {#Action-3}

This creates a new action object with this name and details `name` The name of the new action `details` The details of the action

*See also* [setDetailsV2](kauth-action.md#setDetailsV2)

### Action::Action(const KAuth::Action &*action*) {#Action-1}

Copy constructor

### void Action::addArgument(const QString &*key*, const QVariant &*value*) {#addArgument}

Convenience method to add an argument.

This method adds the pair `key/value` to the [QVariantMap](https://doc.qt.io/qt-6/qvariant.html#QVariantMap-typedef) used to send custom data to the helper.

Use this method if you don't want to create a new [QVariantMap](https://doc.qt.io/qt-6/qvariant.html#QVariantMap-typedef) only to add a new entry.

`key` The new entry's key

`value` The value of the new entry

### QVariantMap Action::arguments() const {#arguments}

Returns map object used to pass arguments to the helper.

This method returns the variant map that the application can use to pass arbitrary data to the helper when executing the action.

Returns the arguments map that will be passed to the helper.

*See also* [setArguments](kauth-action.md#setArguments)()

### KAuth::Action::DetailsMap Action::detailsV2() const {#detailsV2}

Gets the action's details

The details that will be shown in the authorization dialog, if the backend supports it.

Returns The action's details

*See also* [setDetailsV2](kauth-action.md#setDetailsV2)()

### KAuth::ExecuteJob \*Action::execute(KAuth::Action::ExecutionMode *mode* = ExecuteMode) {#execute}

Get the job object used to execute the action

Returns the [KAuth::ExecuteJob](kauth-executejob.md) object to be used to run the action.

### bool Action::hasHelper() const {#hasHelper}

Checks if the action has an helper

This function can be used to check if an helper will be called upon the execution of an action. Such an helper can be set through [setHelperId](kauth-action.md#setHelperId)(). If this function returns false, upon execution the action will be just authorized.

Returns Whether the action has an helper or not

*See also* [setHelperId](kauth-action.md#setHelperId)

### QString Action::helperId() const {#helperId}

Gets the default helper ID used for actions execution

The helper ID is the string that uniquely identifies the helper in the system. It is the string passed to the KAUTH\_HELPER\_MAIN() macro in the helper source. Because one could have different helpers, you need to specify an helper ID for each execution, or set a default ID by calling [setHelperId](kauth-action.md#setHelperId)(). This method returns the current default value.

Returns the default helper ID.

*See also* [setHelperId](kauth-action.md#setHelperId)()

### bool Action::isValid() const {#isValid}

Returns if the object represents a valid action

Action names have to respect a simple syntax. They have to be all in lowercase characters, separated by dots. Dots can't appear at the beginning and at the end of the name.

In other words, the action name has to match this perl-like regular expression:

```cpp
/^[a-z]+(\.[a-z]+)*$/
```

This method returns `false` if the action name doesn't match the valid syntax.

If the backend supports it, this method also checks if the action is valid and recognized by the backend itself.

> **Note:** This may spawn a nested event loop.

Invalid actions cannot be authorized nor executed. The empty string is not a valid action name, so the default constructor returns an invalid action.

### QString Action::name() const {#name}

Gets the action's name.

This is the unique attribute that identifies an action object. Two action objects with the same name always refer to the same action.

Returns The action name

*See also* [setName](kauth-action.md#setName)()

### \[since 6.0\] QWindow \*Action::parentWindow() const {#parentWindow}

Returns the parent widget for the authentication dialog for this action

Returns a [QWindow](https://doc.qt.io/qt-6/qwindow.html) which will is being used as the dialog's parent

This function was introduced in Qt 6.0.

*See also* [setParentWindow](kauth-action.md#setParentWindow)()

### void Action::setArguments(const QVariantMap &*arguments*) {#setArguments}

Sets the map object used to pass arguments to the helper.

This method sets the variant map that the application can use to pass arbitrary data to the helper when executing the action.

Only non-gui variants are supported.

`arguments` The new arguments map

*See also* [arguments](kauth-action.md#arguments)()

### void Action::setDetailsV2(const KAuth::Action::DetailsMap &*details*) {#setDetailsV2}

Sets the action's details

You can use this function to provide the user more details (if the backend supports it) on the action being authorized in the authorization dialog

`details` the details describing the action. For e.g, "[DetailMessage](kauth-action.md#AuthDetail-enum)" key can be used to give a customized authentication message.

*See also* [detailsV2](kauth-action.md#detailsV2)()

### void Action::setHelperId(const QString &*id*) {#setHelperId}

Sets the default helper ID used for actions execution

This method sets the helper ID which contains the body of this action. If the string is non-empty, the corresponding helper will be fired and the action executed inside the helper. Otherwise, the action will be just authorized.

> **Note:** To unset a previously set helper, just pass an empty string

`id` The default helper ID.

*See also* [hasHelper](kauth-action.md#hasHelper), [helperId](kauth-action.md#helperId)

### void Action::setName(const QString &*name*) {#setName}

Sets the action's name.

It's not common to change the action name after its creation. Usually you set the name with the constructor (and you have to, because there's no default constructor)

*See also* [name](kauth-action.md#name)()

### \[since 6.0\] void Action::setParentWindow(QWindow \**parent*) {#setParentWindow}

Sets a parent window for the authentication dialog

This function is used for explicitly setting a parent window for an eventual authentication dialog required when authorization is triggered. Some backends, in fact, (like polkit-1) need to have a parent explicitly set for displaying the dialog correctly.

> **Note:** If you are using [KAuth](kauth-module.md) through one of KDE's GUI components (KPushButton, KCModule...) you do not need and should not call this function, as it is already done by the component itself.

`parent` A QWidget which will be used as the dialog's parent

This function was introduced in Qt 6.0.

*See also* [parentWindow](kauth-action.md#parentWindow)()

### void Action::setTimeout(int *timeout*) {#setTimeout}

Sets the action's timeout.

The `timeout` of the action in milliseconds -1 means the default D-Bus timeout (usually 25 seconds)

*See also* [timeout](kauth-action.md#timeout)()

### void Action::setTimeout(std::chrono::milliseconds *msec*) {#setTimeout-1}

Convenience overload suporting C++ chrono types. May also be used with chrono literals.

### KAuth::Action::AuthStatus Action::status() const {#status}

Gets information about the authorization status of an action

This methods query the authorization backend to know if the user can try to acquire the authorization for this action. If the result is Action::AuthRequired, the user can try to acquire the authorization by authenticating.

It should not be needed to call this method directly, because the execution methods already take care of all the authorization stuff.

Returns

- Action::Denied if the user doesn't have the authorization to execute the action,
- Action::Authorized if the action can be executed,
- Action::AuthRequired if the user could acquire the authorization after authentication,
- Action::UserCancelled if the user cancels the authentication dialog. Not currently supported by the Polkit backend

### int Action::timeout() const {#timeout}

Gets the action's timeout.

The timeout of the action in milliseconds -1 means the default D-Bus timeout (usually 25 seconds)

Returns The action timeouts

*See also* [setTimeout](kauth-action.md#setTimeout)()

### bool Action::operator!=(const KAuth::Action &*action*) const {#operator-not-eq}

Negated comparison operator

Returns the negation of operator==

`action` the action to compare to

Returns true if the two actions are different and not both invalid

### bool Action::operator==(const KAuth::Action &*action*) const {#operator-eq-eq}

Comparison operator

This comparison operator compares the *names* of this and `action` and returns whether they are the same. It does not care about the arguments stored in the actions. However, if two actions are invalid they'll match as equal, even if the invalid names are different.

Returns true if the two actions are the same or both invalid
