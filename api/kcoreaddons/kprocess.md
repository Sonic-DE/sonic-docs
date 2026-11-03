---
title: "KProcess Class"
description: "Child process invocation, monitoring and control."
---

# KProcess Class

Child process invocation, monitoring and control. [More...](#details)

- **Header:** `#include <KProcess>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`
- **Inherits:** [QProcess](https://doc.qt.io/qt-6/qprocess.html)

[List of all members, including inherited members](kprocess-members.md)

## Public Types

- [enum KProcess::OutputChannelMode](#OutputChannelMode-enum)

## Public Functions

- [KProcess(QObject \*parent = nullptr)](#KProcess)
- [void clearEnvironment()](#clearEnvironment)
- [void clearProgram()](#clearProgram)
- [int execute(int msecs = -1)](#execute)
- [KProcess::OutputChannelMode outputChannelMode() const](#outputChannelMode)
- [QStringList program() const](#program)
- [void setEnv(const QString &name, const QString &value, bool overwrite = true)](#setEnv)
- [void setNextOpenMode(QIODevice::OpenMode mode)](#setNextOpenMode)
- [void setOutputChannelMode(KProcess::OutputChannelMode mode)](#setOutputChannelMode)
- [void setProgram(const QString &exe, const QStringList &args = QStringList())](#setProgram)
- [void setProgram(const QStringList &argv)](#setProgram-1)
- [void setShellCommand(const QString &cmd)](#setShellCommand)
- [void start()](#start)
- [int startDetached()](#startDetached)
- [void unsetEnv(const QString &name)](#unsetEnv)
- [KProcess &KProcess::operator\<\<(const QString &arg)](#operator-lt-lt)
- [KProcess &KProcess::operator\<\<(const QStringList &args)](#operator-lt-lt-1)

## Static Public Members

- [int execute(const QStringList &argv, int msecs = -1)](#execute-1)
- [int execute(const QString &exe, const QStringList &args = QStringList(), int msecs = -1)](#execute-2)
- [int startDetached(const QStringList &argv)](#startDetached-1)
- [int startDetached(const QString &exe, const QStringList &args = QStringList())](#startDetached-2)

## Detailed Description {#details}

This class extends [QProcess](https://doc.qt.io/qt-6/qprocess.html) by some useful functionality, overrides some defaults with saner values and wraps parts of the API into a more accessible one. Only use [KProcess](kprocess.md) if you need the extra features, otherwise [QProcess](https://doc.qt.io/qt-6/qprocess.html) is the preferred way of spawning child processes.

## Member Type Documentation {#member-type-documentation}

### enum KProcess::OutputChannelMode {#OutputChannelMode-enum}

Modes in which the output channels can be opened.

| Constant | Value | Description |
| --- | --- | --- |
| `KProcess::SeparateChannels` | `QProcess::SeparateChannels` | Standard output and standard error are handled by [KProcess](kprocess.md) as separate channels |
| `KProcess::MergedChannels` | `QProcess::MergedChannels` | Standard output and standard error are handled by [KProcess](kprocess.md) as one channel |
| `KProcess::ForwardedChannels` | `QProcess::ForwardedChannels` | Both standard output and standard error are forwarded to the parent process' respective channel |
| `KProcess::OnlyStdoutChannel` | `QProcess::ForwardedErrorChannel` | Only standard output is handled; standard error is forwarded |
| `KProcess::OnlyStderrChannel` | `QProcess::ForwardedOutputChannel` | Only standard error is handled; standard output is forwarded |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KProcess::KProcess(QObject \**parent* = nullptr) {#KProcess}

Constructor

### void KProcess::clearEnvironment() {#clearEnvironment}

Empties the process' environment.

Note that LD\_LIBRARY\_PATH/DYLD\_LIBRARY\_PATH is automatically added on \*NIX.

This function must be called before starting the process.

### void KProcess::clearProgram() {#clearProgram}

Clear the program and command line argument list.

### int KProcess::execute(int *msecs* = -1) {#execute}

Start the process, wait for it to finish, and return the exit code.

This method is roughly equivalent to the sequence:

```cpp
start();
waitForFinished(msecs);
return exitCode();
```

Unlike the other execute() variants this method is not static, so the process can be parametrized properly and talked to.

`msecs` time to wait for process to exit before killing it

Returns -2 if the process could not be started, -1 if it crashed, otherwise its exit code

### \[static\] int KProcess::execute(const QStringList &*argv*, int *msecs* = -1) {#execute-1}

`argv` the program to execute and the command line arguments for the program, one per list element

`msecs` time to wait for process to exit before killing it

Returns -2 if the process could not be started, -1 if it crashed, otherwise its exit code

This is an overloaded function.

### \[static\] int KProcess::execute(const QString &*exe*, const QStringList &*args* = QStringList(), int *msecs* = -1) {#execute-2}

`exe` the program to execute

`args` the command line arguments for the program, one per list element

`msecs` time to wait for process to exit before killing it

Returns -2 if the process could not be started, -1 if it crashed, otherwise its exit code

This is an overloaded function.

### KProcess::OutputChannelMode KProcess::outputChannelMode() const {#outputChannelMode}

Query how the output channels of the child process are handled.

Returns the output channel handling mode

*See also* [setOutputChannelMode](kprocess.md#setOutputChannelMode)()

### QStringList KProcess::program() const {#program}

Obtain the currently set program and arguments.

Returns a list, the first element being the program, the remaining ones being command line arguments to the program.

*See also* [setProgram](kprocess.md#setProgram)()

### void KProcess::setEnv(const QString &*name*, const QString &*value*, bool *overwrite* = true) {#setEnv}

Adds the variable `name` to the process' environment.

This function must be called before starting the process.

`name` the name of the environment variable

`value` the new value for the environment variable

`overwrite` if `false` and the environment variable is already set, the old value will be preserved

### void KProcess::setNextOpenMode(QIODevice::OpenMode *mode*) {#setNextOpenMode}

Set the [QIODevice](https://doc.qt.io/qt-6/qiodevice.html) open mode the process will be opened in.

This function must be called before starting the process, obviously.

`mode` the open mode. Note that this mode is automatically "reduced" according to the channel modes and redirections.

The default is QIODevice::ReadWrite.

### void KProcess::setOutputChannelMode(KProcess::OutputChannelMode *mode*) {#setOutputChannelMode}

Set how to handle the output channels of the child process.

The default is [ForwardedChannels](kprocess.md#OutputChannelMode-enum), which is unlike in [QProcess](https://doc.qt.io/qt-6/qprocess.html). Do not request more than you actually handle, as this output is simply lost otherwise.

This function must be called before starting the process.

`mode` the output channel handling mode

*See also* [outputChannelMode](kprocess.md#outputChannelMode)()

### void KProcess::setProgram(const QString &*exe*, const QStringList &*args* = QStringList()) {#setProgram}

Set the program and the command line arguments.

This function must be called before starting the process, obviously.

`exe` the program to execute

`args` the command line arguments for the program, one per list element

*See also* [program](kprocess.md#program)()

### void KProcess::setProgram(const QStringList &*argv*) {#setProgram-1}

`argv` the program to execute and the command line arguments for the program, one per list element

This is an overloaded function.

### void KProcess::setShellCommand(const QString &*cmd*) {#setShellCommand}

Set a command to execute through a shell (a POSIX sh on \*NIX and cmd.exe on Windows).

Using this for anything but user-supplied commands is usually a bad idea, as the command's syntax depends on the platform. Redirections including pipes, etc. are better handled by the respective functions provided by [QProcess](https://doc.qt.io/qt-6/qprocess.html).

If [KProcess](kprocess.md) determines that the command does not really need a shell, it will transparently execute it without one for performance reasons.

This function must be called before starting the process, obviously.

`cmd` the command to execute through a shell.

The caller must make sure that all filenames etc. are properly quoted when passed as argument. Failure to do so often results in serious security holes. See [KShell::quoteArg](kshell.md#quoteArg)().

### void KProcess::start() {#start}

Start the process.

*See also* QProcess::start(const QString &, const QStringList &, OpenMode)

### int KProcess::startDetached() {#startDetached}

Start the process and detach from it. See [QProcess::startDetached](https://doc.qt.io/qt-6/qprocess.html#startDetached)() for details.

Unlike the other startDetached() variants this method is not static, so the process can be parametrized properly.

> **Note:** Currently, only the [setProgram](kprocess.md#setProgram)()/[setShellCommand](kprocess.md#setShellCommand)() and [setWorkingDirectory](https://doc.qt.io/qt-6/qprocess.html#setWorkingDirectory)() parametrizations are supported.

The [KProcess](kprocess.md) object may be re-used immediately after calling this function.

Returns the PID of the started process or 0 on error

### \[static\] int KProcess::startDetached(const QStringList &*argv*) {#startDetached-1}

`argv` the program to start and the command line arguments for the program, one per list element

Returns the PID of the started process or 0 on error

This is an overloaded function.

### \[static\] int KProcess::startDetached(const QString &*exe*, const QStringList &*args* = QStringList()) {#startDetached-2}

`exe` the program to start

`args` the command line arguments for the program, one per list element

Returns the PID of the started process or 0 on error

This is an overloaded function.

### void KProcess::unsetEnv(const QString &*name*) {#unsetEnv}

Removes the variable `name` from the process' environment.

This function must be called before starting the process.

`name` the name of the environment variable

### KProcess &KProcess::operator\<\<(const QString &*arg*) {#operator-lt-lt}

Append an element to the command line argument list for this process.

If no executable is set yet, it will be set instead.

For example, doing an "ls -l /usr/local/bin" can be achieved by:

```cpp
KProcess p;
p << "ls" << "-l" << "/usr/local/bin";
...
```

This function must be called before starting the process, obviously.

`arg` the argument to add

Returns a reference to this [KProcess](kprocess.md)

### KProcess &KProcess::operator\<\<(const QStringList &*args*) {#operator-lt-lt-1}

`args` the arguments to add

Returns a reference to this [KProcess](kprocess.md)

This is an overloaded function.
