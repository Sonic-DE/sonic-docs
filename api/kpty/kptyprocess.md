---
title: "KPtyProcess Class"
description: "This class extends KProcess by support for PTYs (pseudo TTYs)."
---

# KPtyProcess Class

This class extends [KProcess](../kcoreaddons/kprocess.md) by support for PTYs (pseudo TTYs). [More...](#details)

- **Header:** `#include <KPtyProcess>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Pty)`  
  `target_link_libraries(mytarget PRIVATE KF6::Pty)`
- **Inherits:** [KProcess](../kcoreaddons/kprocess.md)

[List of all members, including inherited members](kptyprocess-members.md)

## Public Types

- [enum KPtyProcess::PtyChannelFlag](#PtyChannelFlag-enum)

## Public Functions

- [KPtyProcess(QObject \*parent = nullptr)](#KPtyProcess)
- [KPtyProcess(int ptyMasterFd, QObject \*parent = nullptr)](#KPtyProcess-1)
- [bool isUseUtmp() const](#isUseUtmp)
- [KPtyDevice \*pty() const](#pty)
- [KPtyProcess::PtyChannels ptyChannels() const](#ptyChannels)
- [void setPtyChannels(KPtyProcess::PtyChannels channels)](#setPtyChannels)
- [void setUseUtmp(bool value)](#setUseUtmp)

## Detailed Description {#details}

The PTY is opened as soon as the class is instantiated. Verify that it was opened successfully by checking that [pty](kptyprocess.md#pty)()-\>masterFd() is not -1.

The PTY is always made the process' controlling TTY. Utmp registration and connecting the stdio handles to the PTY are optional.

No attempt to integrate with [QProcess](https://doc.qt.io/qt-6/qprocess.html)' waitFor\*() functions was made, for it is impossible. Note that [execute](../kcoreaddons/kprocess.md#execute)() does not work with the PTY, too. Use the PTY device's waitFor\*() functions or use it asynchronously.

> **Note:** If you inherit from this class and use [setChildProcessModifier](https://doc.qt.io/qt-6/qprocess.html#setChildProcessModifier)() in the derived class, you must call the [childProcessModifier](https://doc.qt.io/qt-6/qprocess.html#childProcessModifier)() of [KPtyProcess](kptyprocess.md) first (using [setChildProcessModifier](https://doc.qt.io/qt-6/qprocess.html#setChildProcessModifier)() in the derived class will "overwrite" the [childProcessModifier](https://doc.qt.io/qt-6/qprocess.html#childProcessModifier)() std::function that was previously set by [KPtyProcess](kptyprocess.md)).

For example:

```cpp
class MyProcess : public KPtyProcess
{
    MyProcess()
    {
        auto parentChildProcModifier = KPtyProcess::childProcessModifier();
        setChildProcessModifier([parentChildProcModifier]() {
            // First call the parent class modifier function
            if (parentChildProcModifier) {
                parentChildProcModifier();
            }
            // Then whatever extra code you need to run
            ....
            ....
        });
    }
```

## Member Type Documentation {#member-type-documentation}

### enum KPtyProcess::PtyChannelFlag {#PtyChannelFlag-enum}

**flags KPtyProcess::PtyChannels**

| Constant | Value | Description |
| --- | --- | --- |
| `KPtyProcess::NoChannels` | `0` | The PTY is not connected to any channel |
| `KPtyProcess::StdinChannel` | `1` | Connect PTY to stdin |
| `KPtyProcess::StdoutChannel` | `2` | Connect PTY to stdout |
| `KPtyProcess::StderrChannel` | `4` | Connect PTY to stderr |
| `KPtyProcess::AllOutputChannels` | `6` | Connect PTY to all output channels |
| `KPtyProcess::AllChannels` | `7` | Connect PTY to all channels |

The `PtyChannels` type is a typedef for `QFlags<PtyChannelFlag>. `It stores an OR combination of `PtyChannelFlag` values.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KPtyProcess::KPtyProcess(QObject \**parent* = nullptr) {#KPtyProcess}

Constructor

### KPtyProcess::KPtyProcess(int *ptyMasterFd*, QObject \**parent* = nullptr) {#KPtyProcess-1}

Construct a process using an open pty master.

`ptyMasterFd` an open pty master file descriptor. The process does not take ownership of the descriptor; it will not be automatically closed at any point.

### bool KPtyProcess::isUseUtmp() const {#isUseUtmp}

Get whether to register the process as a TTY login in utmp.

Returns whether to register in utmp

### KPtyDevice \*KPtyProcess::pty() const {#pty}

Get the PTY device of this process.

Returns the PTY device

### KPtyProcess::PtyChannels KPtyProcess::ptyChannels() const {#ptyChannels}

Query to which channels the PTY is assigned.

Returns the output channel handling mode

*See also* [setPtyChannels](kptyprocess.md#setPtyChannels)()

### void KPtyProcess::setPtyChannels(KPtyProcess::PtyChannels *channels*) {#setPtyChannels}

Set to which channels the PTY should be assigned.

This function must be called before starting the process.

`channels` the output channel handling mode

*See also* [ptyChannels](kptyprocess.md#ptyChannels)()

### void KPtyProcess::setUseUtmp(bool *value*) {#setUseUtmp}

Set whether to register the process as a TTY login in utmp.

Utmp is disabled by default. It should enabled for interactively fed processes, like terminal emulations.

This function must be called before starting the process.

`value` whether to register in utmp.

*See also* [isUseUtmp](kptyprocess.md#isUseUtmp)()
