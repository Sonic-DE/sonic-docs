---
title: "KDESu::PtyProcess Class"
description: "Synchronous communication with tty programs."
---

# KDESu::PtyProcess Class

Synchronous communication with tty programs. [More...](#details)

- **Header:** `#include <KDESu/PtyProcess>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Su)`  
  `target_link_libraries(mytarget PRIVATE KF6::Su)`
- **Inherited By:** [KDESu::StubProcess](kdesu-stubprocess.md)

[List of all members, including inherited members](kdesu-ptyprocess-members.md)

## Public Types

- [enum PtyProcess::checkPidStatus](#checkPidStatus-enum)

## Public Functions

- [int enableLocalEcho(bool enable = true)](#enableLocalEcho)
- [int exec(const QByteArray &command, const QList\<QByteArray\> &args)](#exec)
- [int fd() const](#fd)
- [int pid() const](#pid)
- [QByteArray readAll(bool block = true)](#readAll)
- [QByteArray readLine(bool block = true)](#readLine)
- [void setEnvironment(const QList\<QByteArray\> &env)](#setEnvironment)
- [void setErase(bool erase)](#setErase)
- [void setExitString(const QByteArray &exit)](#setExitString)
- [void setTerminal(bool terminal)](#setTerminal)
- [void unreadLine(const QByteArray &line, bool addNewline = true)](#unreadLine)
- [int waitForChild()](#waitForChild)
- [int waitSlave()](#waitSlave)
- [void writeLine(const QByteArray &line, bool addNewline = true)](#writeLine)

## Static Public Members

- [bool checkPid(pid\_t pid)](#checkPid)
- [int checkPidExited(pid\_t pid)](#checkPidExited)
- [int waitMS(int fd, int ms)](#waitMS)

## Protected Functions

- [QList\<QByteArray\> environment() const](#environment)

## Detailed Description {#details}

[PtyProcess](kdesu-ptyprocess.md) provides synchronous communication with tty based programs. The communications channel used is a pseudo tty (as opposed to a pipe) This means that programs which require a terminal will work.

## Member Type Documentation {#member-type-documentation}

### enum PtyProcess::checkPidStatus {#checkPidStatus-enum}

Error return values for [checkPidExited](kdesu-ptyprocess.md#checkPidExited)()

| Constant | Value | Description |
| --- | --- | --- |
| `KDESu::PtyProcess::Error` | `-1` | No child |
| `KDESu::PtyProcess::NotExited` | `-2` | Child hasn't exited |
| `KDESu::PtyProcess::Killed` | `-3` | Child terminated by signal |

## Member Function Documentation {#member-function-documentation}

### \[static\] bool PtyProcess::checkPid(pid\_t *pid*) {#checkPid}

Basic check for the existence of `pid`.

Returns true iff `pid` is an extant process, (one you could kill - see man kill(2) for signal 0).

### \[static\] int PtyProcess::checkPidExited(pid\_t *pid*) {#checkPidExited}

Check process exit status for process `pid`.

If child `pid` has exited, return its exit status, (which may be zero).

On error (no child, no exit), return -1.

If child `has` not exited, return -2.

### int PtyProcess::enableLocalEcho(bool *enable* = true) {#enableLocalEcho}

Enables/disables local echo on the pseudo tty.

### \[protected\] QList\<QByteArray\> PtyProcess::environment() const {#environment}

Returns the additional environment variables set by [setEnvironment](kdesu-ptyprocess.md#setEnvironment)()

*See also* [setEnvironment](kdesu-ptyprocess.md#setEnvironment)()

### int PtyProcess::exec(const QByteArray &*command*, const QList\<QByteArray\> &*args*) {#exec}

Forks off and execute a command.

The command's standard in and output are connected to the pseudo tty. They are accessible with [readLine](kdesu-ptyprocess.md#readLine) and [writeLine](kdesu-ptyprocess.md#writeLine).

`command` The command to execute.

`args` The arguments to the command.

Returns 0 on success, -1 on error. errno might give more information then.

### int PtyProcess::fd() const {#fd}

Returns the filedescriptor of the process.

### int PtyProcess::pid() const {#pid}

Returns the pid of the process.

### QByteArray PtyProcess::readAll(bool *block* = true) {#readAll}

Read all available output from the program's standard out.

`block` If no output is in the buffer, should the function block (else it will return an empty [QByteArray](https://doc.qt.io/qt-6/qbytearray.html))?

Returns the output.

### QByteArray PtyProcess::readLine(bool *block* = true) {#readLine}

Reads a line from the program's standard out. Depending on the `block` parameter, this call blocks until something was read.

Note that in some situations this function will return less than a full line of output, but never more. Newline characters are stripped.

`block` Block until a full line is read?

Returns the output string.

### void PtyProcess::setEnvironment(const QList\<QByteArray\> &*env*) {#setEnvironment}

Set additinal environment variables.

*See also* [environment](kdesu-ptyprocess.md#environment)()

### void PtyProcess::setErase(bool *erase*) {#setErase}

Overwrites the password as soon as it is used. Relevant only to some subclasses.

### void PtyProcess::setExitString(const QByteArray &*exit*) {#setExitString}

Sets the exit string. If a line of program output matches this, [waitForChild](kdesu-ptyprocess.md#waitForChild)() will terminate the program and return.

### void PtyProcess::setTerminal(bool *terminal*) {#setTerminal}

Enables/disables terminal output. Relevant only to some subclasses.

### void PtyProcess::unreadLine(const QByteArray &*line*, bool *addNewline* = true) {#unreadLine}

Puts back a line of input.

`line` The line to put back.

`addNewline` Adds a '\\n' to the line.

### int PtyProcess::waitForChild() {#waitForChild}

Waits for the child to exit. See also [setExitString](kdesu-ptyprocess.md#setExitString).

### \[static\] int PtyProcess::waitMS(int *fd*, int *ms*) {#waitMS}

Wait `ms` milliseconds (ie. 1/10th of a second is 100ms), using `fd` as a filedescriptor to wait on.

Returns select(2)'s result, which is -1 on error, 0 on timeout, or positive if there is data on one of the selected fd's.

`ms` must be in the range 0..999 (i.e. the maximum wait duration is 999ms, almost one second).

### int PtyProcess::waitSlave() {#waitSlave}

Waits until the pty has cleared the ECHO flag. This is useful when programs write a password prompt before they disable ECHO. Disabling it might flush any input that was written.

### void PtyProcess::writeLine(const QByteArray &*line*, bool *addNewline* = true) {#writeLine}

Writes a line of text to the program's standard in.

`line` The text to write.

`addNewline` Adds a '\\n' to the line.
