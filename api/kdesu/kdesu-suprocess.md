---
title: "KDESu::SuProcess Class"
description: "Executes a command under elevated privileges, using su."
---

# KDESu::SuProcess Class

Executes a command under elevated privileges, using su. [More...](#details)

- **Header:** `#include <KDESu/SuProcess>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Su)`  
  `target_link_libraries(mytarget PRIVATE KF6::Su)`
- **Inherits:** [KDESu::StubProcess](kdesu-stubprocess.md)

[List of all members, including inherited members](kdesu-suprocess-members.md)

## Public Types

- [enum SuProcess::Errors](#Errors-enum)
- [enum SuProcess::checkMode](#checkMode-enum)

## Public Functions

- [SuProcess(const QByteArray &user = nullptr, const QByteArray &command = nullptr)](#SuProcess)
- [int checkInstall(const char \*password)](#checkInstall)
- [int checkNeedPassword()](#checkNeedPassword)
- [int exec(const char \*password, int check = NoCheck)](#exec)
- [QString superUserCommand()](#superUserCommand)
- [bool useUsersOwnPassword()](#useUsersOwnPassword)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum SuProcess::Errors {#Errors-enum}

| Constant |   |
| --- | --- |
| `KDESu::SuProcess::SuNotFound` | `1` |
| `KDESu::SuProcess::SuNotAllowed` | `2` |
| `KDESu::SuProcess::SuIncorrectPassword` | `3` |

### enum SuProcess::checkMode {#checkMode-enum}

Executes the command. This will wait for the command to finish.

| Constant |   |
| --- | --- |
| `KDESu::SuProcess::NoCheck` | `0` |
| `KDESu::SuProcess::Install` | `1` |
| `KDESu::SuProcess::NeedPassword` | `2` |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] SuProcess::SuProcess(const QByteArray &*user* = nullptr, const QByteArray &*command* = nullptr) {#SuProcess}

### int SuProcess::checkInstall(const char \**password*) {#checkInstall}

Checks if the stub is installed and the password is correct.

Returns zero if everything is correct, nonzero otherwise.

### int SuProcess::checkNeedPassword() {#checkNeedPassword}

Checks if a password is needed.

### int SuProcess::exec(const char \**password*, int *check* = NoCheck) {#exec}

### QString SuProcess::superUserCommand() {#superUserCommand}

Checks what the default super user command is, e.g. sudo, su, etc

Returns the default super user command

### bool SuProcess::useUsersOwnPassword() {#useUsersOwnPassword}

Checks whether or not the user's password is being asked for or another user's password. Due to usage of systems such as sudo, even when attempting to switch to another user one may need to enter their own password.
