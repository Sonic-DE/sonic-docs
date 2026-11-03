---
title: "KDESu::Client Class"
description: "A client class to access kdesud, the KDE su daemon. This class was introduced in Qt 6.0."
---

# KDESu::Client Class

A client class to access kdesud, the KDE su daemon. This class was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <KDESu/Client>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Su)`  
  `target_link_libraries(mytarget PRIVATE KF6::Su)`

[List of all members, including inherited members](kdesu-client-members.md)

## Public Functions

- [Client()](#Client)
- [int delCommand(const QByteArray &command, const QByteArray &user)](#delCommand)
- [int delGroup(const QByteArray &group)](#delGroup)
- [int delVar(const QByteArray &key)](#delVar)
- [int delVars(const QByteArray &special\_key)](#delVars)
- [int exec(const QByteArray &command, const QByteArray &user, const QByteArray &options = nullptr, const QList\<QByteArray\> &env = QList\<QByteArray\>())](#exec)
- [int exitCode()](#exitCode)
- [bool findGroup(const QByteArray &group)](#findGroup)
- [QList\<QByteArray\> getKeys(const QByteArray &group)](#getKeys)
- [QByteArray getVar(const QByteArray &key)](#getVar)
- [int ping()](#ping)
- [int setHost(const QByteArray &host)](#setHost)
- [int setPass(const char \*pass, int timeout)](#setPass)
- [int setPriority(int priority)](#setPriority)
- [int setScheduler(int scheduler)](#setScheduler)
- [int setVar(const QByteArray &key, const QByteArray &value, int timeout = 0, const QByteArray &group = nullptr)](#setVar)
- [int startServer()](#startServer)
- [int stopServer()](#stopServer)

## Detailed Description {#details}

Kdesud can assist in password caching in two ways:

For high security passwords, like for su and ssh, it executes the password requesting command for you. It feeds the password to the command, without ever returning it to you, the user. See exec, [setPass](kdesu-client.md#setPass), [delCommand](kdesu-client.md#delCommand).

For lower security passwords, like web and ftp passwords, it can act as a persistent storage for string variables. These variables are returned to the user. See [setVar](kdesu-client.md#setVar), [delVar](kdesu-client.md#delVar), [delGroup](kdesu-client.md#delGroup).

Porting from KF5 to KF6:

The class KDESu::KDEsuClient was renamed to [KDESu::Client](kdesu-client.md).

## Member Function Documentation {#member-function-documentation}

### Client::Client() {#Client}

### int Client::delCommand(const QByteArray &*command*, const QByteArray &*user*) {#delCommand}

Remove a password for a user/command.

`command` The command.

`user` The user.

Return zero on success, -1 on an error

### int Client::delGroup(const QByteArray &*group*) {#delGroup}

Delete all persistent variables in a group.

`group` the group name. See [setVar](kdesu-client.md#setVar).

### int Client::delVar(const QByteArray &*key*) {#delVar}

Delete a persistent variable.

`key` The name of the variable.

Returns zero on success, -1 on failure.

### int Client::delVars(const QByteArray &*special\_key*) {#delVars}

Delete all persistent variables with the given key.

A specicalized variant of [delVar](kdesu-client.md#delVar)([QByteArray](https://doc.qt.io/qt-6/qbytearray.html)) that removes all subsets of the cached variables given by `key`. In order for all cached variables related to this key to be deleted properly, the value given to the `group` argument when the [setVar](kdesu-client.md#setVar) function was called, must be a subset of the argument given here and the key

> **Note:** Simply supplying the group key here WILL not necessarily work. If you only have a group key, then use [delGroup](kdesu-client.md#delGroup) instead.

`special_key` the name of the variable.

Returns zero on success, -1 on failure.

### int Client::exec(const QByteArray &*command*, const QByteArray &*user*, const QByteArray &*options* = nullptr, const QList\<QByteArray\> &*env* = QList\<QByteArray\>()) {#exec}

Lets kdesud execute a command. If the daemon does not have a password for this command, this will fail and you need to call [setPass](kdesu-client.md#setPass)().

`command` The command to execute.

`user` The user to run the command as.

`options` Extra options.

`env` Extra environment variables.

Returns Zero on success, -1 on failure.

### int Client::exitCode() {#exitCode}

Wait for the last command to exit and return the exit code.

Returns the exit code of last command, -1 on failure.

### bool Client::findGroup(const QByteArray &*group*) {#findGroup}

Returns true if the specified group exists is cached.

`group` the group key

Returns true if the group is found

### QList\<QByteArray\> Client::getKeys(const QByteArray &*group*) {#getKeys}

Gets all the keys that are membes of the given group.

`group` the group name of the variables.

Returns a list of the keys in the group.

### QByteArray Client::getVar(const QByteArray &*key*) {#getVar}

Get a persistent variable.

`key` The name of the variable.

Returns its value.

### int Client::ping() {#ping}

Ping kdesud. This can be used for diagnostics.

Returns zero on success, -1 on failure

### int Client::setHost(const QByteArray &*host*) {#setHost}

Set the target host (optional).

### int Client::setPass(const char \**pass*, int *timeout*) {#setPass}

Set root's password, lasts one session.

`pass` Root's password.

`timeout` The time that a password will live.

Returns zero on success, -1 on failure.

### int Client::setPriority(int *priority*) {#setPriority}

Set the desired priority (optional), see [StubProcess](kdesu-stubprocess.md).

### int Client::setScheduler(int *scheduler*) {#setScheduler}

Set the desired scheduler (optional), see [StubProcess](kdesu-stubprocess.md).

### int Client::setVar(const QByteArray &*key*, const QByteArray &*value*, int *timeout* = 0, const QByteArray &*group* = nullptr) {#setVar}

Set a persistent variable.

`key` The name of the variable.

`value` Its value.

`timeout` The timeout in seconds for this key. Zero means no timeout.

`group` Make the key part of a group. See [delGroup](kdesu-client.md#delGroup).

Return zero on success, -1 on failure.

### int Client::startServer() {#startServer}

Try to start up kdesud

### int Client::stopServer() {#stopServer}

Stop the daemon.
