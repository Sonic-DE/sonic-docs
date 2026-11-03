---
title: "KTextEditor::Command Class"
description: "An Editor command line command."
---

# KTextEditor::Command Class

An Editor command line command. [More...](#details)

- **Header:** `#include <KTextEditor/Command>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextEditor)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextEditor)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](ktexteditor-command-members.md)

## Public Functions

- [Command(const QStringList &cmds, QObject \*parent = nullptr)](#Command)
- [~Command()](#dtor.Command)
- [const QStringList &cmds() const](#cmds)
- [KCompletion \*completionObject(KTextEditor::View \*view, const QString &cmdname)](#completionObject)
- [bool exec(KTextEditor::View \*view, const QString &cmd, QString &msg, const KTextEditor::Range &range = KTextEditor::invalid())](#exec)
- [bool help(KTextEditor::View \*view, const QString &cmd, QString &msg)](#help)
- [void processText(KTextEditor::View \*view, const QString &text)](#processText)
- [bool supportsRange(const QString &cmd)](#supportsRange)
- [bool wantsToProcessText(const QString &cmdname)](#wantsToProcessText)

## Detailed Description {#details}

Introduction

The Command class represents a command for the editor command line. A command simply consists of a string, for example `find`. The command auto-registers itself at the Editor. The Editor itself queries the command for a list of accepted strings/commands by calling [cmds](ktexteditor-command.md#cmds)(). If the command gets invoked the function [exec](ktexteditor-command.md#exec)() is called, i.e. you have to implement the `reaction` in [exec](ktexteditor-command.md#exec)(). Whenever the user needs help for a command [help](ktexteditor-command.md#help)() is called.

Command Information

To provide reasonable information about a specific command there are the following accessor functions for a given command string:

- name() returns a label
- description() returns a descriptive text
- category() returns a category into which the command fits.

These getters allow [KTextEditor](ktexteditor-module.md) implementations to plug commands into menus and toolbars, so that a user can assign shortcuts.

Command Completion

The Command optionally can show a completion popup to help the user select a valid entry as first parameter to the Command. To this end, return a valid completion item by reiplementing [completionObject](ktexteditor-command.md#completionObject)().

The returned completion object is deleted automatically once it is not needed anymore. Therefore neither delete the completion object yourself nor return the same completion object twice.

Interactive Commands

In case the Command needs to interactively process the text of the parameters, override [wantsToProcessText](ktexteditor-command.md#wantsToProcessText)() by returning `true` and reimplement [processText](ktexteditor-command.md#processText)().

A typical example of an iterative command would be the incremental search.

*See also* [KTextEditor::CommandInterface](ktexteditor-index.md)

## Member Function Documentation {#member-function-documentation}

### Command::Command(const QStringList &*cmds*, QObject \**parent* = nullptr) {#Command}

Constructor with `parent`. Will register this command for the commands names given in `cmds` at the global editor instance.

### \[override virtual noexcept\] Command::~Command() {#dtor.Command}

Virtual destructor. Will unregister this command at the global editor instance.

### const QStringList &Command::cmds() const {#cmds}

Return a list of strings a command may begin with. This is the same list the command was constructed with. A string is the start part of a pure text which can be handled by this command, i.e. for the command s/sdl/sdf/g the corresponding string is simply `s`, and for char:1212 simply `char`. Returns list of supported commands

### \[virtual\] KCompletion \*Command::completionObject(KTextEditor::View \**view*, const QString &*cmdname*) {#completionObject}

Return a KCompletion object that will substitute the command line default one while typing the first argument of the command cmdname. The text will be added to the command separated by one space character.

Override this method if your command can provide a completion object. The returned completion object is deleted automatically once it is not needed anymore. Therefore neither delete the completion object yourself nor return the same completion object twice.

The default implementation returns a null pointer (`nullptr`).

`view` is the view the command will work on

`cmdname` is the command name associated with this request.

Returns a valid completion object or `nullptr`, if a completion object is not supported

### \[pure virtual\] bool Command::exec(KTextEditor::View \**view*, const QString &*cmd*, QString &*msg*, const KTextEditor::Range &*range* = KTextEditor::Range::invalid()) {#exec}

Execute the command for the given `view` and `cmd` string. Return the success value and a `msg` for status. As example we consider a replace command. The replace command would return the number of replaced strings as `msg`, like "16 replacements made." If an error occurred in the usage it would return `false` and set the `msg` to something like "missing argument." or such.

If a non-invalid `range` is given, the command shall be executed on that range. [supportsRange](ktexteditor-command.md#supportsRange)() tells if the command supports that.

Returns `true` on success, otherwise `false`

### \[pure virtual\] bool Command::help(KTextEditor::View \**view*, const QString &*cmd*, QString &*msg*) {#help}

Shows help for the given `view` and `cmd` string.

If your command has a help text for `cmd` you have to return `true` and set the `msg` to a meaningful text. The help text is embedded by the Editor in a [Qt::RichText](https://doc.qt.io/qt-6/qt.html#TextFormat-enum) enabled widget, e.g. a [QToolTip](https://doc.qt.io/qt-6/qtooltip.html).

Returns `true` if your command has a help text, otherwise `false`

### \[virtual\] void Command::processText(KTextEditor::View \**view*, const QString &*text*) {#processText}

This is called by the command line each time the argument text for the command changed, if [wantsToProcessText](ktexteditor-command.md#wantsToProcessText)() returns `true`.

`view` is the current view

`text` is the current command text typed by the user

*See also* [wantsToProcessText](ktexteditor-command.md#wantsToProcessText)()

### \[virtual\] bool Command::supportsRange(const QString &*cmd*) {#supportsRange}

Find out if a given command can act on a range. This is used for checking if a command should be called when the user also gave a range or if an error should be raised.

`cmd` is the command

Returns `true` if command supports acting on a range of lines, `false` not. The default implementation returns `false`.

### \[virtual\] bool Command::wantsToProcessText(const QString &*cmdname*) {#wantsToProcessText}

Check, whether the command wants to process text interactively for the given command with name cmdname.

If you return true, the command's [processText](ktexteditor-command.md#processText)() method is called whenever the text in the command line changed.

Reimplement this to return true, if your commands wants to process the text while typing.

`cmdname` is the command name associated with this query.

Returns `true`, if your command wants to process text interactively, otherwise `false`

*See also* [processText](ktexteditor-command.md#processText)()
