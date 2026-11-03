---
title: "KTextEditor::Application Class"
description: "This class allows the application that embeds the KTextEditor component to allow it access to application wide information and interactions."
---

# KTextEditor::Application Class

This class allows the application that embeds the [KTextEditor](ktexteditor-module.md) component to allow it access to application wide information and interactions. [More...](#details)

- **Header:** `#include <KTextEditor/Application>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextEditor)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextEditor)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](ktexteditor-application-members.md)

## Public Functions

- [Application(QObject \*parent)](#Application)
- [KTextEditor::MainWindow \*activeMainWindow()](#activeMainWindow)
- [bool closeDocument(KTextEditor::Document \*document)](#closeDocument)
- [bool closeDocuments(const QList\<KTextEditor::Document \*\> &documents)](#closeDocuments)
- [QList\<KTextEditor::Document \*\> documents()](#documents)
- [KTextEditor::Document \*findUrl(const QUrl &url)](#findUrl)
- [QList\<KTextEditor::MainWindow \*\> mainWindows()](#mainWindows)
- [KTextEditor::Document \*openUrl(const QUrl &url, const QString &encoding = QString())](#openUrl)
- [KTextEditor::Plugin \*plugin(const QString &name)](#plugin)
- [bool quit()](#quit)

## Signals

- [void documentCreated(KTextEditor::Document \*document)](#documentCreated)
- [void documentDeleted(KTextEditor::Document \*document)](#documentDeleted)
- [void documentWillBeDeleted(KTextEditor::Document \*document)](#documentWillBeDeleted)
- [void pluginCreated(const QString &name, KTextEditor::Plugin \*plugin)](#pluginCreated)
- [void pluginDeleted(const QString &name, KTextEditor::Plugin \*plugin)](#pluginDeleted)

## Detailed Description {#details}

For example the component can get the current active main window of the application.

The application must pass a pointer to the Application object to the setApplication method of the global editor instance and ensure that this object stays valid for the complete lifetime of the editor.

It must not reimplement this class but construct an instance and pass a pointer to a [QObject](https://doc.qt.io/qt-6/qobject.html) that has the required slots to receive the requests.

KTextEditor::Editor::instance()-\>application() will always return a non-nullptr object to avoid the need for nullptr checks before calling the API.

The same holds for [activeMainWindow](ktexteditor-application.md#activeMainWindow)(), even if no main window is around, you will get a non-nullptr interface object that allows to call the functions of the [MainWindow](ktexteditor-mainwindow.md) without needs for a nullptr check around it in the client code.

kte\_plugin\_hosting

## Member Function Documentation {#member-function-documentation}

### Application::Application(QObject \**parent*) {#Application}

Construct an Application wrapper object. The passed parent is both the parent of this [QObject](https://doc.qt.io/qt-6/qobject.html) and the receiver of all interface calls via invokeMethod.

`parent` is the object the calls are relayed to

### KTextEditor::MainWindow \*Application::activeMainWindow() {#activeMainWindow}

Accessor to the active main window. Returns a pointer to the active mainwindow, even if no main window is active you will get a non-nullptr dummy interface that allows you to call interface functions without the need for null checks

### bool Application::closeDocument(KTextEditor::Document \**document*) {#closeDocument}

Close the given document. If the document is modified, user will be asked for confirmation.

`document` is the the document to be closed

Returns *true* on success, otherwise *false*

### bool Application::closeDocuments(const QList\<KTextEditor::Document \*\> &*documents*) {#closeDocuments}

Close a list of documents. If any of them are modified, user will be asked for confirmation. Use this if you want to close multiple documents at once, as the application might be able to group the "do you really want that" dialogs into one.

`documents` is the list of documents to be closed

Returns *true* on success, otherwise *false*

### \[signal\] void Application::documentCreated(KTextEditor::Document \**document*) {#documentCreated}

This signal is emitted when the `document` was created.

`document` document that was created

### \[signal\] void Application::documentDeleted(KTextEditor::Document \**document*) {#documentDeleted}

This signal is emitted when the `document` has been deleted.

> **Warning:** Do not access the data referenced by the pointer, it is already invalid. Use the pointer only to remove mappings in hash or maps

`document` document that is deleted

### \[signal\] void Application::documentWillBeDeleted(KTextEditor::Document \**document*) {#documentWillBeDeleted}

This signal is emitted before a `document` which should be closed is deleted The document is still accessible and usable, but it will be deleted after this signal was send.

`document` document that will be deleted

### QList\<KTextEditor::Document \*\> Application::documents() {#documents}

Get a list of all documents that are managed by the application. This might contain less documents than the editor has in his documents () list. Returns all documents the application manages, might be empty!

### KTextEditor::Document \*Application::findUrl(const QUrl &*url*) {#findUrl}

Get the document with the URL. If multiple documents match the searched url, return the first found one.

`url` is the document's URL

Returns the document with the given `url` or nullptr, if none found

### QList\<KTextEditor::MainWindow \*\> Application::mainWindows() {#mainWindows}

Get a list of all main windows. Returns all main windows, might be empty!

### KTextEditor::Document \*Application::openUrl(const QUrl &*url*, const QString &*encoding* = QString()) {#openUrl}

Open the document URL with the given encoding. If the url is empty, a new empty document will be created

`url` is the document URL

`encoding` is the preferred encoding. If encoding is QString() the encoding will be guessed or the default encoding will be used.

Returns a pointer to the created document

### KTextEditor::Plugin \*Application::plugin(const QString &*name*) {#plugin}

Get a plugin with the specified name.

`name` is the plugin's name

Returns pointer to the plugin if a plugin with `name` is loaded, otherwise nullptr

### \[signal\] void Application::pluginCreated(const QString &*name*, KTextEditor::Plugin \**plugin*) {#pluginCreated}

This signal is emitted when an Plugin was loaded.

`name` is the name of the plugin

`plugin` is the new plugin

### \[signal\] void Application::pluginDeleted(const QString &*name*, KTextEditor::Plugin \**plugin*) {#pluginDeleted}

This signal is emitted when an Plugin got deleted.

`name` is the name of the plugin

`plugin` is the deleted plugin

> **Warning:** Do not access the data referenced by the pointer, it is already invalid. Use the pointer only to remove mappings in hash or maps

### bool Application::quit() {#quit}

Ask app to quit. The app might interact with the user and decide that quitting is not possible and return false.

Returns true if the app could quit
