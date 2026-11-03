---
title: "KDESu::StubProcess Class"
description: "Chat with kdesu_stub."
---

# KDESu::StubProcess Class

Chat with kdesu\_stub. [More...](#details)

- **Header:** `#include <KDESu/StubProcess>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Su)`  
  `target_link_libraries(mytarget PRIVATE KF6::Su)`
- **Inherits:** [KDESu::PtyProcess](kdesu-ptyprocess.md)
- **Inherited By:** [KDESu::SshProcess](kdesu-sshprocess.md) and [KDESu::SuProcess](kdesu-suprocess.md)

[List of all members, including inherited members](kdesu-stubprocess-members.md)

## Public Types

- [enum StubProcess::Scheduler](#Scheduler-enum)

## Public Functions

- [StubProcess()](#StubProcess)
- [void setCommand(const QByteArray &command)](#setCommand)
- [void setPriority(int prio)](#setPriority)
- [void setScheduler(int sched)](#setScheduler)
- [void setUser(const QByteArray &user)](#setUser)
- [void setXOnly(bool xonly)](#setXOnly)

## Protected Functions

- [int converseStub(int check)](#converseStub)
- [QByteArray display()](#display)
- [QByteArray displayAuth()](#displayAuth)

## Detailed Description {#details}

[StubProcess](kdesu-stubprocess.md) extends [PtyProcess](kdesu-ptyprocess.md) with functionality to chat with kdesu\_stub.

## Member Type Documentation {#member-type-documentation}

### enum StubProcess::Scheduler {#Scheduler-enum}

Different schedulers. SchedNormal is the normal Unix timesharing scheduler, while SchedRealtime is a POSIX.1b realtime scheduler.

| Constant |   |
| --- | --- |
| `KDESu::StubProcess::SchedNormal` | `0` |
| `KDESu::StubProcess::SchedRealtime` | `1` |

## Member Function Documentation {#member-function-documentation}

### StubProcess::StubProcess() {#StubProcess}

### \[protected\] int StubProcess::converseStub(int *check*) {#converseStub}

Exchange all parameters with kdesu\_stub.

### \[virtual protected\] QByteArray StubProcess::display() {#display}

This virtual function can be overloaded when special behavior is desired. By default, it returns the value returned by KCookie.

### \[virtual protected\] QByteArray StubProcess::displayAuth() {#displayAuth}

See display.

### void StubProcess::setCommand(const QByteArray &*command*) {#setCommand}

Set the command.

### void StubProcess::setPriority(int *prio*) {#setPriority}

Set the priority of the process. The priority value must be between 0 and 100, 0 being the lowest priority. This value is mapped to the scheduler and system dependent priority range of the OS.

### void StubProcess::setScheduler(int *sched*) {#setScheduler}

Set the scheduler type.

### void StubProcess::setUser(const QByteArray &*user*) {#setUser}

Set the target user.

### void StubProcess::setXOnly(bool *xonly*) {#setXOnly}

Set to "X only mode": Sycoca is not built and kdeinit is not launched.
