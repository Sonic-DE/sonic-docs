---
title: "KUrlRequester Class"
description: "A widget to request a filename/url from the user."
---

# KUrlRequester Class

A widget to request a filename/url from the user. [More...](#details)

- **Header:** `#include <KUrlRequester>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)
- **Inherited By:** [KUrlComboRequester](kurlcomborequester.md)

[List of all members, including inherited members](kurlrequester-members.md)  
[Deprecated members](kurlrequester-obsolete.md)

## Properties

- [acceptMode : QFileDialog::AcceptMode](#acceptMode-prop)
- [fileDialogModality : Qt::WindowModality](#fileDialogModality-prop)
- [mode : KFile::Modes](#mode-prop)
- [nameFilters : QStringList](#nameFilters-prop)
- [placeholderText : QString](#placeholderText-prop)
- [text : QString](#text-prop)
- [url : QUrl](#url-prop)

## Public Functions

- [KUrlRequester(QWidget \*parent = nullptr)](#KUrlRequester)
- [KUrlRequester(QWidget \*editWidget, QWidget \*parent)](#KUrlRequester-1)
- [KUrlRequester(const QUrl &url, QWidget \*parent = nullptr)](#KUrlRequester-2)
- [QFileDialog::AcceptMode acceptMode() const](#acceptMode)
- [QPushButton \*button() const](#button)
- [KComboBox \*comboBox() const](#comboBox)
- [KUrlCompletion \*completionObject() const](#completionObject)
- [const KEditListWidget::CustomEditor &customEditor()](#customEditor)
- [Qt::WindowModality fileDialogModality() const](#fileDialogModality)
- [KLineEdit \*lineEdit() const](#lineEdit)
- [QStringList mimeTypeFilters() const](#mimeTypeFilters)
- [KFile::Modes mode() const](#mode)
- [QStringList nameFilters() const](#nameFilters)
- [QString placeholderText() const](#placeholderText)
- [void setAcceptMode(QFileDialog::AcceptMode m)](#setAcceptMode)
- [void setFileDialogModality(Qt::WindowModality modality)](#setFileDialogModality)
- [void setMimeTypeFilters(const QStringList &mimeTypes)](#setMimeTypeFilters)
- [void setMode(KFile::Modes mode)](#setMode)
- [void setNameFilter(const QString &filter)](#setNameFilter)
- [void setNameFilters(const QStringList &filters)](#setNameFilters)
- [void setPlaceholderText(const QString &msg)](#setPlaceholderText)
- [QUrl startDir() const](#startDir)
- [QString text() const](#text)
- [QUrl url() const](#url)

## Public Slots

- [void clear()](#clear)
- [void setStartDir(const QUrl &startDir)](#setStartDir)
- [void setText(const QString &text)](#setText)
- [void setUrl(const QUrl &url)](#setUrl)

## Signals

- [void openFileDialog(KUrlRequester \*)](#openFileDialog)
- [void returnPressed(const QString &text)](#returnPressed)
- [void textChanged(const QString &)](#textChanged)
- [void textEdited(const QString &)](#textEdited)
- [void urlSelected(const QUrl &)](#urlSelected)

## Detailed Description {#details}

This class is a widget showing a lineedit and a button, which invokes a filedialog. File name completion is available in the lineedit.

The default for the filedialog is to ask for one existing local file, i.e. the default mode is '[KFile::File](kfile.md#Mode-enum) \| [KFile::ExistingOnly](kfile.md#Mode-enum) \| [KFile::LocalOnly](kfile.md#Mode-enum)', which you can change by using [setMode](kurlrequester.md#setMode)().

The default filter is "\*", i.e. show all files, which you can change by using [setNameFilters](kurlrequester.md#setNameFilters)() or [setMimeTypeFilters](kurlrequester.md#setMimeTypeFilters)().

By default the start directory is the current working directory, or the last directory where a file has been selected previously, you can change this behavior by calling [setStartDir](kurlrequester.md#setStartDir)().

The default window modality for the file dialog is [Qt::ApplicationModal](https://doc.qt.io/qt-6/qt.html#WindowModality-enum)

## Property Documentation {#property-documentation}

### acceptMode : QFileDialog::AcceptMode {#acceptMode-prop}

**Access functions:**

- `QFileDialog::AcceptMode` **[acceptMode](kurlrequester.md#acceptMode)**() const
- `void` **[setAcceptMode](kurlrequester.md#setAcceptMode)**(`QFileDialog::AcceptMode` *m*)

### fileDialogModality : Qt::WindowModality {#fileDialogModality-prop}

**Access functions:**

- `Qt::WindowModality` **[fileDialogModality](kurlrequester.md#fileDialogModality)**() const
- `void` **[setFileDialogModality](kurlrequester.md#setFileDialogModality)**(`Qt::WindowModality` *modality*)

### mode : KFile::Modes {#mode-prop}

**Access functions:**

- `KFile::Modes` **[mode](kurlrequester.md#mode)**() const
- `void` **[setMode](kurlrequester.md#setMode)**(`KFile::Modes` *mode*)

### nameFilters : QStringList {#nameFilters-prop}

**Access functions:**

- `QStringList` **[nameFilters](kurlrequester.md#nameFilters)**() const
- `void` **[setNameFilters](kurlrequester.md#setNameFilters)**(const `QStringList` &*filters*)

### placeholderText : QString {#placeholderText-prop}

**Access functions:**

- `QString` **[placeholderText](kurlrequester.md#placeholderText)**() const
- `void` **[setPlaceholderText](kurlrequester.md#setPlaceholderText)**(const `QString` &*msg*)

### text : QString {#text-prop}

**Access functions:**

- `QString` **[text](kurlrequester.md#text)**() const
- `void` **[setText](kurlrequester.md#setText)**(const `QString` &*text*)

**Notifier signal:**

- `void` **[textChanged](kurlrequester.md#textChanged)**(*const QString &*)

### url : QUrl {#url-prop}

**Access functions:**

- `QUrl` **[url](kurlrequester.md#url)**() const
- `void` **[setUrl](kurlrequester.md#setUrl)**(const `QUrl` &*url*)

**Notifier signal:**

- `void` **[textChanged](kurlrequester.md#textChanged)**(*const QString &*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KUrlRequester::KUrlRequester(QWidget \**parent* = nullptr) {#KUrlRequester}

Constructs a [KUrlRequester](kurlrequester.md) widget.

### KUrlRequester::KUrlRequester(QWidget \**editWidget*, QWidget \**parent*) {#KUrlRequester-1}

Special constructor, which creates a [KUrlRequester](kurlrequester.md) widget with a custom edit-widget. The edit-widget can be either a KComboBox or a KLineEdit (or inherited thereof). Note: for geometry management reasons, the edit-widget is reparented to have the [KUrlRequester](kurlrequester.md) as parent.

### \[explicit\] KUrlRequester::KUrlRequester(const QUrl &*url*, QWidget \**parent* = nullptr) {#KUrlRequester-2}

Constructs a [KUrlRequester](kurlrequester.md) widget with the initial URL `url`.

### QFileDialog::AcceptMode KUrlRequester::acceptMode() const {#acceptMode}

Returns the current open / save mode

> **Note:** Getter function for property [acceptMode](kurlrequester.md#acceptMode-prop).

*See also* [setAcceptMode](kurlrequester.md#setAcceptMode)(), [QFileDialog::acceptMode](https://doc.qt.io/qt-6/qfiledialog.html#acceptMode-prop)()

### QPushButton \*KUrlRequester::button() const {#button}

Returns a pointer to the pushbutton. It is provided so that you can specify an own pixmap or a text, if you really need to.

### \[slot\] void KUrlRequester::clear() {#clear}

Clears the lineedit/combobox.

### KComboBox \*KUrlRequester::comboBox() const {#comboBox}

Returns a pointer to the combobox, in case you have set one using the special constructor. Returns 0L otherwise.

### KUrlCompletion \*KUrlRequester::completionObject() const {#completionObject}

Returns the [KUrlCompletion](kurlcompletion.md) object used in the lineedit/combobox.

### const KEditListWidget::CustomEditor &KUrlRequester::customEditor() {#customEditor}

Returns an object, suitable for use with KEditListWidget. It allows you to put this [KUrlRequester](kurlrequester.md) into a KEditListWidget. Basically, do it like this:

```cpp
KUrlRequester *req = new KUrlRequester( someWidget );
[...]
KEditListWidget *editListWidget = new KEditListWidget( req->customEditor(), someWidget );
```

### Qt::WindowModality KUrlRequester::fileDialogModality() const {#fileDialogModality}

Returns the window modality of the file dialog set with [setFileDialogModality](kurlrequester.md#setFileDialogModality)

> **Note:** Getter function for property [fileDialogModality](kurlrequester.md#fileDialogModality-prop).

*See also* [setFileDialogModality](kurlrequester.md#setFileDialogModality)()

### KLineEdit \*KUrlRequester::lineEdit() const {#lineEdit}

Returns a pointer to the lineedit, either the default one, or the special one, if you used the special constructor.

It is provided so that you can e.g. set an own completion object (e.g. [KShellCompletion](kshellcompletion.md)) into it.

### QStringList KUrlRequester::mimeTypeFilters() const {#mimeTypeFilters}

Returns the MIME type filters for the file dialog.

*See also* [setMimeTypeFilters](kurlrequester.md#setMimeTypeFilters)(), [QFileDialog::mimeTypeFilters](https://doc.qt.io/qt-6/qfiledialog.html#mimeTypeFilters)()

### KFile::Modes KUrlRequester::mode() const {#mode}

Returns the current mode

> **Note:** Getter function for property [mode](kurlrequester.md#mode-prop).

*See also* [setMode](kurlrequester.md#setMode)(), [QFileDialog::fileMode](https://doc.qt.io/qt-6/qfiledialog.html#fileMode-prop)()

### QStringList KUrlRequester::nameFilters() const {#nameFilters}

Returns the filters for the file dialog.

> **Note:** Getter function for property [nameFilters](kurlrequester.md#nameFilters-prop).

*See also* [setNameFilters](kurlrequester.md#setNameFilters)(), [QFileDialog::nameFilters](https://doc.qt.io/qt-6/qfiledialog.html#nameFilters)()

### \[signal\] void KUrlRequester::openFileDialog(*KUrlRequester \**) {#openFileDialog}

Emitted before the filedialog is going to open. Connect to this signal to "configure" the filedialog, e.g. set the filefilter, the mode, a preview-widget, etc. It's usually not necessary to set a URL for the filedialog, as it will get set properly from the editfield contents.

If you use multiple KUrlRequesters, you can connect all of them to the same slot and use the given [KUrlRequester](kurlrequester.md) pointer to know which one is going to open.

### QString KUrlRequester::placeholderText() const {#placeholderText}

Returns the message set with [setPlaceholderText](kurlrequester.md#setPlaceholderText)

> **Note:** Getter function for property [placeholderText](kurlrequester.md#placeholderText-prop).

*See also* [setPlaceholderText](kurlrequester.md#setPlaceholderText)()

### \[signal\] void KUrlRequester::returnPressed(const QString &*text*) {#returnPressed}

Emitted when return or enter was pressed in the lineedit. The parameter contains the contents of the lineedit.

### void KUrlRequester::setAcceptMode(QFileDialog::AcceptMode *m*) {#setAcceptMode}

Sets the open / save mode of the file dialog.

The default is [QFileDialog::AcceptOpen](https://doc.qt.io/qt-6/qfiledialog.html#AcceptMode-enum).

> **Note:** Setter function for property [acceptMode](kurlrequester.md#acceptMode-prop).

*See also* [acceptMode](kurlrequester.md#acceptMode)(), [QFileDialog::setAcceptMode](https://doc.qt.io/qt-6/qfiledialog.html#acceptMode-prop)()

### void KUrlRequester::setFileDialogModality(Qt::WindowModality *modality*) {#setFileDialogModality}

Set the window modality for the file dialog to `modality` Directory selection dialogs are always modal

The default is [Qt::ApplicationModal](https://doc.qt.io/qt-6/qt.html#WindowModality-enum).

> **Note:** Setter function for property [fileDialogModality](kurlrequester.md#fileDialogModality-prop).

*See also* [fileDialogModality](kurlrequester.md#fileDialogModality)()

### void KUrlRequester::setMimeTypeFilters(const QStringList &*mimeTypes*) {#setMimeTypeFilters}

Sets the MIME type filters for the file dialog.

*See also* [mimeTypeFilters](kurlrequester.md#mimeTypeFilters)(), [QFileDialog::setMimeTypeFilters](https://doc.qt.io/qt-6/qfiledialog.html#setMimeTypeFilters)()

### void KUrlRequester::setMode(KFile::Modes *mode*) {#setMode}

Sets the mode of the file dialog.

The default mode of the file dialog is '[KFile::File](kfile.md#Mode-enum) \| [KFile::ExistingOnly](kfile.md#Mode-enum) \| [KFile::LocalOnly](kfile.md#Mode-enum)', which you can change using this method.

> **Note:** You can only select one file from the file dialog invoked by [KUrlRequester](kurlrequester.md), hence setting [KFile::Files](kfile.md#Mode-enum) doesn't make much sense here.

`mode` an OR'ed combination of [KFile::Modes](kfile.md#Mode-enum) flags

> **Note:** Setter function for property [mode](kurlrequester.md#mode-prop).

*See also* [mode](kurlrequester.md#mode)(), [QFileDialog::setFileMode](https://doc.qt.io/qt-6/qfiledialog.html#fileMode-prop)()

### void KUrlRequester::setNameFilter(const QString &*filter*) {#setNameFilter}

Sets the name `filter` for the file dialog.

*See also* [QFileDialog::setNameFilter](https://doc.qt.io/qt-6/qfiledialog.html#setNameFilter)()

### void KUrlRequester::setNameFilters(const QStringList &*filters*) {#setNameFilters}

Sets the name `filters` for the file dialog.

> **Note:** Setter function for property [nameFilters](kurlrequester.md#nameFilters-prop).

*See also* [nameFilters](kurlrequester.md#nameFilters)(), [QFileDialog::setNameFilters](https://doc.qt.io/qt-6/qfiledialog.html#setNameFilters)()

### void KUrlRequester::setPlaceholderText(const QString &*msg*) {#setPlaceholderText}

This makes the [KUrlRequester](kurlrequester.md) line edit display a grayed-out hinting text as long as the user didn't enter any text. It is often used as indication about the purpose of the line edit.

> **Note:** Setter function for property [placeholderText](kurlrequester.md#placeholderText-prop).

*See also* [placeholderText](kurlrequester.md#placeholderText)()

### \[slot\] void KUrlRequester::setStartDir(const QUrl &*startDir*) {#setStartDir}

Sets the start dir `startDir`.

The start dir is only used when the URL isn't set.

*See also* [startDir](kurlrequester.md#startDir)()

### \[slot\] void KUrlRequester::setText(const QString &*text*) {#setText}

Sets the current text in the lineedit or combobox.

This is used for cases where [KUrlRequester](kurlrequester.md) is used to enter URL-or-something-else, like [KOpenWithDialog](kopenwithdialog.md) where you can type a full command with arguments.

> **Note:** Setter function for property [text](kurlrequester.md#text-prop).

*See also* [text](kurlrequester.md#text)

### \[slot\] void KUrlRequester::setUrl(const QUrl &*url*) {#setUrl}

Sets the url in the lineedit to `url`.

> **Note:** Setter function for property [url](kurlrequester.md#url-prop).

*See also* [url](kurlrequester.md#url)()

### QUrl KUrlRequester::startDir() const {#startDir}

Returns the current start dir

*See also* [setStartDir](kurlrequester.md#setStartDir)()

### QString KUrlRequester::text() const {#text}

Returns the current text in the lineedit or combobox. This does not do the URL expansion that [url](kurlrequester.md#url)() does, it's only provided for cases where [KUrlRequester](kurlrequester.md) is used to enter URL-or-something-else, like [KOpenWithDialog](kopenwithdialog.md) where you can type a full command with arguments.

> **Note:** Getter function for property [text](kurlrequester.md#text-prop).

*See also* [setText](kurlrequester.md#setText)()

### \[signal\] void KUrlRequester::textChanged(*const QString &*) {#textChanged}

Emitted when the text in the lineedit changes. The parameter contains the contents of the lineedit.

> **Note:** Notifier signal for properties [text](kurlrequester.md#text-prop) and [url](kurlrequester.md#url-prop).

### \[signal\] void KUrlRequester::textEdited(*const QString &*) {#textEdited}

Emitted when the text in the lineedit was modified by the user. Unlike [textChanged](kurlrequester.md#textChanged)(), this signal is not emitted when the text is changed programmatically, for example, by calling [setText](kurlrequester.md#setText)().

### QUrl KUrlRequester::url() const {#url}

Returns the current url in the lineedit. May be malformed, if the user entered something weird. For local files, ~user or environment variables are substituted, relative paths will be resolved against [startDir](kurlrequester.md#startDir)()

> **Note:** Getter function for property [url](kurlrequester.md#url-prop).

*See also* [setUrl](kurlrequester.md#setUrl)()

### \[signal\] void KUrlRequester::urlSelected(*const QUrl &*) {#urlSelected}

Emitted when the user changed the URL via the file dialog. The parameter contains the contents of the lineedit.
