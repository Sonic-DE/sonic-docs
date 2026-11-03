---
title: "KUrlCompletion Class"
description: "Completion of a single URL."
---

# KUrlCompletion Class

Completion of a single URL. [More...](#details)

- **Header:** `#include <KUrlCompletion>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherited By:** [KShellCompletion](kshellcompletion.md)

[List of all members, including inherited members](kurlcompletion-members.md)

## Public Types

- [enum KUrlCompletion::Mode](#Mode-enum)

## Public Functions

- [KUrlCompletion()](#KUrlCompletion)
- [KUrlCompletion(KUrlCompletion::Mode)](#KUrlCompletion-1)
- [QUrl dir() const](#dir)
- [bool isRunning() const](#isRunning)
- [QString makeCompletion(const QString &text)](#makeCompletion)
- [QStringList mimeTypeFilters() const](#mimeTypeFilters)
- [KUrlCompletion::Mode mode() const](#mode)
- [bool replaceEnv() const](#replaceEnv)
- [bool replaceHome() const](#replaceHome)
- [QString replacedPath(const QString &text) const](#replacedPath)
- [void setDir(const QUrl &dir)](#setDir)
- [void setMimeTypeFilters(const QStringList &mimeTypes)](#setMimeTypeFilters)
- [void setMode(KUrlCompletion::Mode mode)](#setMode)
- [void setReplaceEnv(bool replace)](#setReplaceEnv)
- [void setReplaceHome(bool replace)](#setReplaceHome)
- [void stop()](#stop)

## Detailed Description {#details}

This class does completion of URLs including user directories (~user) and environment variables. Remote URLs are passed to KIO.

## Member Type Documentation {#member-type-documentation}

### enum KUrlCompletion::Mode {#Mode-enum}

Determines how completion is done.

| Constant | Value | Description |
| --- | --- | --- |
| `KUrlCompletion::ExeCompletion` | `1` | executables in $PATH or with full path. |
| `KUrlCompletion::FileCompletion` | `2` | all files with full path or in [dir](kurlcompletion.md#dir)(), URLs are listed using KIO. |
| `KUrlCompletion::DirCompletion` | `3` | Same as FileCompletion but only returns directories. |

## Member Function Documentation {#member-function-documentation}

### KUrlCompletion::KUrlCompletion() {#KUrlCompletion}

Constructs a [KUrlCompletion](kurlcompletion.md) object in [FileCompletion](kurlcompletion.md#Mode-enum) mode.

### KUrlCompletion::KUrlCompletion(*KUrlCompletion::Mode*) {#KUrlCompletion-1}

This overloaded constructor allows you to set the Mode to [ExeCompletion](kurlcompletion.md#Mode-enum) or [FileCompletion](kurlcompletion.md#Mode-enum) without using [setMode](kurlcompletion.md#setMode). Default is [FileCompletion](kurlcompletion.md#Mode-enum).

### \[virtual\] QUrl KUrlCompletion::dir() const {#dir}

Returns the current directory, as it was given in [setDir](kurlcompletion.md#setDir), as a URL (use [QUrl::toLocalFile](https://doc.qt.io/qt-6/qurl.html#toLocalFile) for local paths)

*See also* [setDir](kurlcompletion.md#setDir)()

### \[virtual\] bool KUrlCompletion::isRunning() const {#isRunning}

Check whether asynchronous completion is in progress.

### \[override virtual\] QString KUrlCompletion::makeCompletion(const QString &*text*) {#makeCompletion}

Finds completions to the given text.

Remote URLs are listed with KIO. For performance reasons, local files are listed with KIO only if KURLCOMPLETION\_LOCAL\_KIO is set. The completion is done asynchronously if KIO is used.

Returns the first match for user, environment, and local dir completion and QString() for asynchronous completion (KIO or threaded).

`text` the text to complete

Returns the first match, or QString() if not found

### QStringList KUrlCompletion::mimeTypeFilters() const {#mimeTypeFilters}

Returns the MIME type filters for the file dialog.

*See also* [setMimeTypeFilters](kurlcompletion.md#setMimeTypeFilters)(), [QFileDialog::mimeTypeFilters](https://doc.qt.io/qt-6/qfiledialog.html#mimeTypeFilters)()

### \[virtual\] KUrlCompletion::Mode KUrlCompletion::mode() const {#mode}

Returns the completion mode: exe or file completion (default [FileCompletion](kurlcompletion.md#Mode-enum)).

*See also* [setMode](kurlcompletion.md#setMode)()

### \[virtual\] bool KUrlCompletion::replaceEnv() const {#replaceEnv}

Checks whether environment variables are completed and whether they are replaced internally while finding completions.

Default is enabled.

Returns true if environment variables will be replaced

*See also* [setReplaceEnv](kurlcompletion.md#setReplaceEnv)()

### \[virtual\] bool KUrlCompletion::replaceHome() const {#replaceHome}

Returns whether ~username is completed and whether ~username is replaced internally with the user's home directory while finding completions. Default is enabled.

Returns true to replace tilde with the home directory

*See also* [setReplaceHome](kurlcompletion.md#setReplaceHome)()

### QString KUrlCompletion::replacedPath(const QString &*text*) const {#replacedPath}

Replaces username and/or environment variables, depending on the current settings and returns the filtered url. Only works with local files, i.e. returns back the original string for non-local urls.

`text` the text to process

Returns the path or URL resulting from this operation. If you want to convert it to a [QUrl](https://doc.qt.io/qt-6/qurl.html), use [QUrl::fromUserInput](https://doc.qt.io/qt-6/qurl.html#fromUserInput).

### \[virtual\] void KUrlCompletion::setDir(const QUrl &*dir*) {#setDir}

Sets the current directory (used as base for completion). Default = $HOME.

`dir` the current directory, as a URL (use [QUrl::fromLocalFile](https://doc.qt.io/qt-6/qurl.html#fromLocalFile) for local paths)

*See also* [dir](kurlcompletion.md#dir)()

### void KUrlCompletion::setMimeTypeFilters(const QStringList &*mimeTypes*) {#setMimeTypeFilters}

Sets the MIME type filters for the file dialog.

*See also* [mimeTypeFilters](kurlcompletion.md#mimeTypeFilters)(), [QFileDialog::setMimeTypeFilters](https://doc.qt.io/qt-6/qfiledialog.html#setMimeTypeFilters)()

### \[virtual\] void KUrlCompletion::setMode(KUrlCompletion::Mode *mode*) {#setMode}

Changes the completion mode: exe or file completion

`mode` the new completion mode

*See also* [mode](kurlcompletion.md#mode)()

### \[virtual\] void KUrlCompletion::setReplaceEnv(bool *replace*) {#setReplaceEnv}

Enables/disables completion and replacement (internally) of environment variables in URLs. Default is enabled.

`replace` true to replace environment variables

*See also* [replaceEnv](kurlcompletion.md#replaceEnv)()

### \[virtual\] void KUrlCompletion::setReplaceHome(bool *replace*) {#setReplaceHome}

Enables/disables completion of ~username and replacement (internally) of ~username with the user's home directory. Default is enabled.

`replace` true to replace tilde with the home directory

*See also* [replaceHome](kurlcompletion.md#replaceHome)()

### \[virtual\] void KUrlCompletion::stop() {#stop}

Stops asynchronous completion.
