---
title: "KDESu::SshProcess Class"
description: "Executes a remote command, using ssh."
---

# KDESu::SshProcess Class

Executes a remote command, using ssh. [More...](#details)

- **Header:** `#include <KDESu/SshProcess>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Su)`  
  `target_link_libraries(mytarget PRIVATE KF6::Su)`
- **Inherits:** [KDESu::StubProcess](kdesu-stubprocess.md)

[List of all members, including inherited members](kdesu-sshprocess-members.md)

## Public Types

- [enum SshProcess::Errors](#Errors-enum)

## Public Functions

- [SshProcess(const QByteArray &host = QByteArray(), const QByteArray &user = QByteArray(), const QByteArray &command = QByteArray())](#SshProcess)
- [int checkInstall(const char \*password)](#checkInstall)
- [int checkNeedPassword()](#checkNeedPassword)
- [QByteArray error() const](#error)
- [int exec(const char \*password, int check = 0)](#exec)
- [QByteArray prompt() const](#prompt)
- [void setHost(const QByteArray &host)](#setHost)
- [void setStub(const QByteArray &stub)](#setStub)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum SshProcess::Errors {#Errors-enum}

| Constant |   |
| --- | --- |
| `KDESu::SshProcess::SshNotFound` | `1` |
| `KDESu::SshProcess::SshNeedsPassword` | `2` |
| `KDESu::SshProcess::SshIncorrectPassword` | `3` |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] SshProcess::SshProcess(const QByteArray &*host* = QByteArray(), const QByteArray &*user* = QByteArray(), const QByteArray &*command* = QByteArray()) {#SshProcess}

### int SshProcess::checkInstall(const char \**password*) {#checkInstall}

Checks if the stub is installed and if the password is correct.

Returns zero if everything is correct, nonzero otherwise.

### int SshProcess::checkNeedPassword() {#checkNeedPassword}

Checks if the current user@host needs a password.

Returns the prompt for the password if a password is required. A null string otherwise.

### QByteArray SshProcess::error() const {#error}

### int SshProcess::exec(const char \**password*, int *check* = 0) {#exec}

Executes the command.

### QByteArray SshProcess::prompt() const {#prompt}

### void SshProcess::setHost(const QByteArray &*host*) {#setHost}

Sets the target host.

### void SshProcess::setStub(const QByteArray &*stub*) {#setStub}

Sets the location of the remote stub.
