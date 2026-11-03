---
title: "KTextEditor::Editor Class"
description: "Accessor interface for the KTextEditor framework."
---

# KTextEditor::Editor Class

Accessor interface for the [KTextEditor](ktexteditor-module.md) framework. [More...](#details)

- **Header:** `#include <KTextEditor/Editor>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextEditor)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextEditor)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](ktexteditor-editor-members.md)

## Public Functions

- [const KAboutData &aboutData() const](#aboutData)
- [void addVariableExpansion(const QList\<QWidget \*\> &widgets, const QStringList &variables = QStringList()) const](#addVariableExpansion)
- [KTextEditor::Application \*application() const](#application)
- [QStringList commandList() const](#commandList)
- [QList\<KTextEditor::Command \*\> commands() const](#commands)
- [void configDialog(QWidget \*parent)](#configDialog)
- [KTextEditor::ConfigPage \*configPage(int number, QWidget \*parent)](#configPage)
- [int configPages() const](#configPages)
- [KTextEditor::Document \*createDocument(QObject \*parent)](#createDocument)
- [QString defaultEncoding() const](#defaultEncoding)
- [QList\<KTextEditor::Document \*\> documents()](#documents)
- [QString expandText(const QString &text, KTextEditor::View \*view) const](#expandText) (since 6.0)
- [bool expandVariable(const QString &variable, KTextEditor::View \*view, QString &output) const](#expandVariable)
- [QFont font() const](#font)
- [KTextEditor::Command \*queryCommand(const QString &cmd) const](#queryCommand)
- [bool registerVariableMatch(const QString &name, const QString &description, KTextEditor::Editor::ExpandFunction expansionFunc)](#registerVariableMatch)
- [bool registerVariablePrefix(const QString &prefix, const QString &description, KTextEditor::Editor::ExpandFunction expansionFunc)](#registerVariablePrefix)
- [const KSyntaxHighlighting::Repository &repository() const](#repository)
- [void setApplication(KTextEditor::Application \*application)](#setApplication)
- [KSyntaxHighlighting::Theme theme() const](#theme)
- [bool unregisterVariable(const QString &variableName)](#unregisterVariable) (since 6.0)

## Signals

- [void configChanged(KTextEditor::Editor \*editor)](#configChanged)
- [void documentCreated(KTextEditor::Editor \*editor, KTextEditor::Document \*document)](#documentCreated)
- [void repositoryReloaded(KTextEditor::Editor \*editor)](#repositoryReloaded)

## Static Public Members

- [KTextEditor::Editor \*instance()](#instance)

## Protected Functions

- [Editor(KTextEditor::EditorPrivate \*impl)](#Editor)
- [~Editor()](#dtor.Editor)

## Detailed Description {#details}

### Introduction {#introduction}

The Editor part can either be accessed through the static accessor [Editor::instance](ktexteditor-editor.md#instance)() or through the [KParts](../kparts/kparts-module.md) component model (see kte\_design\_part). The Editor singleton provides general information and configuration methods for the Editor, for example KAboutData by using [aboutData](ktexteditor-editor.md#aboutData)().

The Editor has a list of all opened documents. Get this list with [documents](ktexteditor-editor.md#documents)(). To create a new Document call [createDocument](ktexteditor-editor.md#createDocument)(). The signal [documentCreated](ktexteditor-editor.md#documentCreated)() is emitted whenever the Editor created a new document.

### Configuration {#configuration}

The config dialog can be shown with [configDialog](ktexteditor-editor.md#configDialog)(). Instead of using the config dialog, the config pages can also be embedded into the application's config dialog. To do this, [configPages](ktexteditor-editor.md#configPages)() returns the number of config pages that exist and [configPage](ktexteditor-editor.md#configPage)() returns the requested page. The configuration are saved automatically by the Editor.

> **Note:** It is recommended to embed the config pages into the main application's config dialog instead of using a separate config dialog, if the config dialog does not look cluttered then. This way, all settings are grouped together in one place.

### Command Line Commands {#command-line-commands}

With Commands it is possible to add new commands to the command line. These Command%s then are added to all document View%s. Common use cases include commands like *find* or setting document variables. The list of all registered commands can be obtained either through [commandList](ktexteditor-editor.md#commandList)() or through [commands](ktexteditor-editor.md#commands)(). Further, a specific command can be obtained through [queryCommand](ktexteditor-editor.md#queryCommand)(). For further information, read the Command API documentation.

*See also* [KTextEditor::Document](ktexteditor-index.md), [KTextEditor::ConfigPage](ktexteditor-index.md), [KTextEditor::Command](ktexteditor-index.md)

## Member Function Documentation {#member-function-documentation}

### \[protected\] Editor::Editor(KTextEditor::EditorPrivate \**impl*) {#Editor}

Constructor.

Create the Editor object and pass it the internal implementation to store a d-pointer.

`impl` d-pointer to use

### \[override virtual noexcept protected\] Editor::~Editor() {#dtor.Editor}

Virtual destructor.

### \[pure virtual\] const KAboutData &Editor::aboutData() const {#aboutData}

Get the about data of this Editor part. Returns about data

### void Editor::addVariableExpansion(const QList\<QWidget \*\> &*widgets*, const QStringList &*variables* = QStringList()) const {#addVariableExpansion}

Adds a QAction to the widget in `widgets` that whenever focus is gained. When the action is invoked, a non-modal dialog is shown that lists all `variables`. If `variables` is non-empty, then only the variables in `variables` are listed.

The supported QWidgets in the `widgets` argument currently are:

- [QLineEdit](https://doc.qt.io/qt-6/qlineedit.html)
- [QTextEdit](https://doc.qt.io/qt-6/qtextedit.html)

### \[pure virtual\] KTextEditor::Application \*Editor::application() const {#application}

Current hosting application, if any set. Returns current application object or a dummy interface that allows you to call the functions will never return a nullptr

*See also* [setApplication](ktexteditor-editor.md#setApplication)()

### \[pure virtual\] QStringList Editor::commandList() const {#commandList}

Get a list of available command line strings. Returns command line strings

*See also* [commands](ktexteditor-editor.md#commands)()

### \[pure virtual\] QList\<KTextEditor::Command \*\> Editor::commands() const {#commands}

Get a list of all registered commands. Returns list of all commands

*See also* [queryCommand](ktexteditor-editor.md#queryCommand)(), [commandList](ktexteditor-editor.md#commandList)()

### \[signal\] void Editor::configChanged(KTextEditor::Editor \**editor*) {#configChanged}

This signal is emitted whenever the editor configuration is changed.

`editor` is the editor whose config has changed

### \[pure virtual\] void Editor::configDialog(QWidget \**parent*) {#configDialog}

Show the editor's config dialog. Changes will be applied to the editor and the configuration changes are saved.

> **Note:** Instead of using the config dialog, the config pages can be embedded into your own config dialog by using [configPages](ktexteditor-editor.md#configPages)() and [configPage](ktexteditor-editor.md#configPage)().

`parent` is parent widget

### \[pure virtual\] KTextEditor::ConfigPage \*Editor::configPage(int *number*, QWidget \**parent*) {#configPage}

Get the config page with the `number`, config pages from 0 to [configPages](ktexteditor-editor.md#configPages)()-1 are available if [configPages](ktexteditor-editor.md#configPages)() \> 0. Configuration changes done over this widget are automatically saved.

`number` is the config page index

`parent` is the parent widget for the config page

Returns created config page or NULL, if the number is out of bounds

*See also* [configPages](ktexteditor-editor.md#configPages)()

### \[pure virtual\] int Editor::configPages() const {#configPages}

Get the number of available config pages. If a number \< 1 is returned, it does not support config pages. Returns number of config pages

*See also* [configPage](ktexteditor-editor.md#configPage)()

### \[pure virtual\] KTextEditor::Document \*Editor::createDocument(QObject \**parent*) {#createDocument}

Create a new document object with `parent`.

For each created document, the signal [documentCreated](ktexteditor-editor.md#documentCreated)() is emitted.

`parent` is the document's parent object

Returns new [KTextEditor::Document](ktexteditor-document.md) object

*See also* [documents](ktexteditor-editor.md#documents)(), [documentCreated](ktexteditor-editor.md#documentCreated)()

### QString Editor::defaultEncoding() const {#defaultEncoding}

Get the current default encoding for this Editor part. Returns default encoding

### \[signal\] void Editor::documentCreated(KTextEditor::Editor \**editor*, KTextEditor::Document \**document*) {#documentCreated}

The `editor` emits this signal whenever a `document` was successfully created.

`editor` is a pointer to the Editor singleton which created the new document

`document` is the newly created document instance

*See also* [createDocument](ktexteditor-editor.md#createDocument)()

### \[pure virtual\] QList\<KTextEditor::Document \*\> Editor::documents() {#documents}

Get a list of all documents of this editor. Returns list of all existing documents

*See also* [createDocument](ktexteditor-editor.md#createDocument)()

### \[since 6.0\] QString Editor::expandText(const QString &*text*, KTextEditor::View \**view*) const {#expandText}

Expands arbitrary `text` that may contain arbitrary many variables. On success, the expanded text is written to `output`.

Returns the expanded text.

This function was introduced in Qt 6.0.

### bool Editor::expandVariable(const QString &*variable*, KTextEditor::View \**view*, QString &*output*) const {#expandVariable}

Expands a single `variable`, writing the expanded value to `output`.

Returns true on success, otherwise false.

### QFont Editor::font() const {#font}

Get the current global editor font. Might change during runtime, [configChanged](ktexteditor-editor.md#configChanged)() will be emitted in that cases. Individual views might have set different fonts, can be queried with the "font" key via

Returns current global font for all views

*See also* [KTextEditor::ConfigInterface::configValue()](ktexteditor-index.md)

### \[static\] KTextEditor::Editor \*Editor::instance() {#instance}

Accessor to get the Editor instance.

> **Note:** This object will stay alive until [QCoreApplication](https://doc.qt.io/qt-6/qcoreapplication.html) terminates. You shall not delete it yourself. There is only ONE Editor instance of this per process.

Returns Editor controller, after initial construction, will live until [QCoreApplication](https://doc.qt.io/qt-6/qcoreapplication.html) is terminating.

### \[pure virtual\] KTextEditor::Command \*Editor::queryCommand(const QString &*cmd*) const {#queryCommand}

Query for the command `cmd`. If the command `cmd` does not exist the return value is NULL.

`cmd` is the name of command to query for

Returns the found command or NULL if no such command exists

### bool Editor::registerVariableMatch(const QString &*name*, const QString &*description*, KTextEditor::Editor::ExpandFunction *expansionFunc*) {#registerVariableMatch}

Registers a variable called `name` for exact matches. For instance, a variable called "CurrentDocument:Path" could be registered which then expands to the path the current document.

Returns true on success, false if the variable could not be registered, e.g. because it already was registered previously.

### bool Editor::registerVariablePrefix(const QString &*prefix*, const QString &*description*, KTextEditor::Editor::ExpandFunction *expansionFunc*) {#registerVariablePrefix}

Registers a variable for arbitrary text that matches the specified `prefix`. For instance, a variable called "ENV:" could be registered which then expands arbitrary environment variables, e.g. ENV:HOME would expand to the user's home directory.

> **Note:** A colon ':' is used as separator for the prefix and the text after the colon that should be evaluated.

Returns true on success, false if a prefix could not be registered, e.g. because it already was registered previously.

### const KSyntaxHighlighting::Repository &Editor::repository() const {#repository}

Get read-only access to the syntax highlighting repository the editor uses. Might be reloaded during runtime, [repositoryReloaded](ktexteditor-editor.md#repositoryReloaded)() will be emitted in that cases.

Returns syntax repository used by the editor

### \[signal\] void Editor::repositoryReloaded(KTextEditor::Editor \**editor*) {#repositoryReloaded}

This signal is emitted whenever the editor syntax repository is reloaded. Can be used to e.g. re-instantiate syntax definitions that got invalidated by the repository reload.

`editor` is the editor whose repository was reloaded

### \[pure virtual\] void Editor::setApplication(KTextEditor::Application \**application*) {#setApplication}

Set the global application object. This will allow the editor component to access the hosting application.

`application` is the application object (if the argument is a nullptr, this will reset the application back to a dummy interface)

*See also* [application](ktexteditor-editor.md#application)()

### KSyntaxHighlighting::Theme Editor::theme() const {#theme}

Get the current global theme. Might change during runtime, [configChanged](ktexteditor-editor.md#configChanged)() will be emitted in that cases. Individual views might have set different themes,

Returns current global theme for all views

*See also* [KTextEditor::View::theme()](ktexteditor-index.md)

### \[since 6.0\] bool Editor::unregisterVariable(const QString &*variableName*) {#unregisterVariable}

Unregisters a variable that was previously registered with [registerVariableMatch](ktexteditor-editor.md#registerVariableMatch)() or [registerVariablePrefix](ktexteditor-editor.md#registerVariablePrefix)().

`variableName` is the variable's name

Returns true if the variable was successfully unregistered, and false if the variable did not exist.

This function was introduced in Qt 6.0.
