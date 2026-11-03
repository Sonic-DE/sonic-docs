---
title: "KTextEditor::Document Class"
description: "A KParts derived class representing a text document."
---

# KTextEditor::Document Class

A [KParts](../kparts/kparts-module.md) derived class representing a text document. [More...](#details)

- **Header:** `#include <KTextEditor/Document>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextEditor)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextEditor)`
- **Inherits:** [KParts::ReadWritePart](../kparts/kparts-readwritepart.md)

[List of all members, including inherited members](ktexteditor-document-members.md)  
[Deprecated members](ktexteditor-document-obsolete.md)

## Public Types

- [enum Document::MarkChangeAction](#MarkChangeAction-enum)
- [enum Document::MarkTypes](#MarkTypes-enum)
- [enum Document::ModifiedOnDiskReason](#ModifiedOnDiskReason-enum)

## Public Functions

- [void addMark(int line, uint markType)](#addMark)
- [KTextEditor::AnnotationModel \*annotationModel() const](#annotationModel)
- [QChar characterAt(KTextEditor::Cursor position) const](#characterAt)
- [QByteArray checksum() const](#checksum)
- [bool clear()](#clear)
- [void clearMark(int line)](#clearMark)
- [void clearMarks()](#clearMarks)
- [QStringList configKeys() const](#configKeys)
- [QVariant configValue(const QString &key)](#configValue)
- [KTextEditor::View \*createView(QWidget \*parent, KTextEditor::MainWindow \*mainWindow = nullptr)](#createView)
- [qsizetype cursorToOffset(KTextEditor::Cursor c) const](#cursorToOffset) (since 6.0)
- [KSyntaxHighlighting::Theme::TextStyle defaultStyleAt(KTextEditor::Cursor position) const](#defaultStyleAt)
- [void discardDataRecovery()](#discardDataRecovery)
- [KTextEditor::Cursor documentEnd() const](#documentEnd)
- [QString documentName() const](#documentName)
- [KTextEditor::Range documentRange() const](#documentRange)
- [bool documentReload()](#documentReload)
- [bool documentSave()](#documentSave)
- [bool documentSaveAs()](#documentSaveAs)
- [uint editableMarks() const](#editableMarks)
- [QStringList embeddedHighlightingModes() const](#embeddedHighlightingModes)
- [QString encoding() const](#encoding)
- [KTextEditor::Cursor endOfLine(int line) const](#endOfLine)
- [QUrl getSaveFileUrl(const QString &dialogTitle, QWidget \*dialogParent = nullptr)](#getSaveFileUrl) (since 6.25)
- [QString highlightingMode() const](#highlightingMode)
- [QString highlightingModeAt(KTextEditor::Cursor position)](#highlightingModeAt)
- [QString highlightingModeSection(int index) const](#highlightingModeSection)
- [QStringList highlightingModes() const](#highlightingModes)
- [bool insertLine(int line, const QString &text)](#insertLine)
- [bool insertLines(int line, const QStringList &text)](#insertLines)
- [bool insertText(KTextEditor::Cursor position, const QString &text, bool block = false)](#insertText)
- [bool insertText(KTextEditor::Cursor position, const QStringList &text, bool block = false)](#insertText-1)
- [bool isDataRecoveryAvailable() const](#isDataRecoveryAvailable)
- [bool isEditingTransactionRunning() const](#isEditingTransactionRunning)
- [bool isEmpty() const](#isEmpty)
- [bool isLineModified(int line) const](#isLineModified)
- [bool isLineSaved(int line) const](#isLineSaved)
- [bool isLineTouched(int line) const](#isLineTouched)
- [bool isValidTextPosition(KTextEditor::Cursor cursor) const](#isValidTextPosition)
- [qint64 lastSavedRevision() const](#lastSavedRevision)
- [QString line(int line) const](#line)
- [int lineLength(int line) const](#lineLength)
- [int lines() const](#lines)
- [void lockRevision(qint64 revision)](#lockRevision)
- [uint mark(int line)](#mark)
- [QString markDescription(KTextEditor::Document::MarkTypes mark) const](#markDescription)
- [QIcon markIcon(KTextEditor::Document::MarkTypes markType) const](#markIcon)
- [const QHash\<int, KTextEditor::Mark \*\> &marks()](#marks)
- [QString mimeType()](#mimeType)
- [QString mode() const](#mode)
- [QString modeSection(int index) const](#modeSection)
- [QStringList modes() const](#modes)
- [KTextEditor::MovingCursor \*newMovingCursor(KTextEditor::Cursor position, KTextEditor::MovingCursor::InsertBehavior insertBehavior = MovingCursor::MoveOnInsert)](#newMovingCursor)
- [KTextEditor::MovingRange \*newMovingRange(KTextEditor::Range range, MovingRange::InsertBehaviors insertBehaviors = MovingRange::DoNotExpand, KTextEditor::MovingRange::EmptyBehavior emptyBehavior = MovingRange::AllowEmpty)](#newMovingRange)
- [KTextEditor::Cursor offsetToCursor(qsizetype offset) const](#offsetToCursor) (since 6.0)
- [bool openingError() const](#openingError)
- [bool postMessage(KTextEditor::Message \*message)](#postMessage)
- [bool print()](#print)
- [void printPreview()](#printPreview)
- [void readSessionConfig(const KConfigGroup &config, const QSet\<QString\> &flags = QSet\<QString\>())](#readSessionConfig)
- [void recoverData()](#recoverData)
- [bool removeLine(int line)](#removeLine)
- [void removeMark(int line, uint markType)](#removeMark)
- [bool removeText(KTextEditor::Range range, bool block = false)](#removeText)
- [bool replaceText(KTextEditor::Range range, const QString &text, bool block = false)](#replaceText)
- [bool replaceText(KTextEditor::Range range, const QStringList &text, bool block = false)](#replaceText-1)
- [qint64 revision() const](#revision)
- [QList\<KTextEditor::Range\> searchText(KTextEditor::Range range, const QString &pattern, const KTextEditor::SearchOptions options = Default) const](#searchText)
- [void setAnnotationModel(KTextEditor::AnnotationModel \*model)](#setAnnotationModel)
- [void setConfigValue(const QString &key, const QVariant &value)](#setConfigValue)
- [void setEditableMarks(uint markMask)](#setEditableMarks)
- [bool setEncoding(const QString &encoding)](#setEncoding)
- [bool setHighlightingMode(const QString &name)](#setHighlightingMode)
- [void setMark(int line, uint markType)](#setMark)
- [void setMarkDescription(KTextEditor::Document::MarkTypes mark, const QString &text)](#setMarkDescription)
- [void setMarkIcon(KTextEditor::Document::MarkTypes markType, const QIcon &icon)](#setMarkIcon)
- [bool setMode(const QString &name)](#setMode)
- [void setModifiedOnDisk(KTextEditor::Document::ModifiedOnDiskReason reason)](#setModifiedOnDisk)
- [void setModifiedOnDiskWarning(bool on)](#setModifiedOnDiskWarning)
- [bool setText(const QString &text)](#setText)
- [bool setText(const QStringList &text)](#setText-1)
- [QString text() const](#text)
- [QString text(KTextEditor::Range range, bool block = false) const](#text-1)
- [QStringList textLines(KTextEditor::Range range, bool block = false) const](#textLines)
- [qsizetype totalCharacters() const](#totalCharacters)
- [void transformCursor(KTextEditor::Cursor &cursor, KTextEditor::MovingCursor::InsertBehavior insertBehavior, qint64 fromRevision, qint64 toRevision = -1)](#transformCursor)
- [void transformCursor(int &line, int &column, KTextEditor::MovingCursor::InsertBehavior insertBehavior, qint64 fromRevision, qint64 toRevision = -1)](#transformCursor-1)
- [void transformRange(KTextEditor::Range &range, KTextEditor::MovingRange::InsertBehaviors insertBehaviors, KTextEditor::MovingRange::EmptyBehavior emptyBehavior, qint64 fromRevision, qint64 toRevision = -1)](#transformRange)
- [void unlockRevision(qint64 revision)](#unlockRevision)
- [QList\<KTextEditor::View \*\> views() const](#views)
- [QString wordAt(KTextEditor::Cursor cursor) const](#wordAt)
- [KTextEditor::Range wordRangeAt(KTextEditor::Cursor cursor) const](#wordRangeAt)
- [void writeSessionConfig(KConfigGroup &config, const QSet\<QString\> &flags = QSet\<QString\>())](#writeSessionConfig)

## Signals

- [void aboutToClose(KTextEditor::Document \*document)](#aboutToClose)
- [void aboutToInvalidateMovingInterfaceContent(KTextEditor::Document \*document)](#aboutToInvalidateMovingInterfaceContent)
- [void aboutToReload(KTextEditor::Document \*document)](#aboutToReload)
- [void aboutToSave(KTextEditor::Document \*document)](#aboutToSave)
- [void configChanged(KTextEditor::Document \*document)](#configChanged)
- [void documentNameChanged(KTextEditor::Document \*document)](#documentNameChanged)
- [void documentSavedOrUploaded(KTextEditor::Document \*document, bool saveAs)](#documentSavedOrUploaded)
- [void documentUrlChanged(KTextEditor::Document \*document)](#documentUrlChanged)
- [void editingFinished(KTextEditor::Document \*document)](#editingFinished)
- [void editingStarted(KTextEditor::Document \*document)](#editingStarted)
- [void highlightingModeChanged(KTextEditor::Document \*document)](#highlightingModeChanged)
- [void lineUnwrapped(KTextEditor::Document \*document, int line)](#lineUnwrapped)
- [void lineWrapped(KTextEditor::Document \*document, KTextEditor::Cursor position)](#lineWrapped)
- [void markChanged(KTextEditor::Document \*document, KTextEditor::Mark mark, KTextEditor::Document::MarkChangeAction action)](#markChanged)
- [void markClicked(KTextEditor::Document \*document, KTextEditor::Mark mark, bool &handled)](#markClicked)
- [void markContextMenuRequested(KTextEditor::Document \*document, KTextEditor::Mark mark, QPoint pos, bool &handled)](#markContextMenuRequested)
- [void markToolTipRequested(KTextEditor::Document \*document, KTextEditor::Mark mark, QPoint position, bool &handled)](#markToolTipRequested)
- [void marksChanged(KTextEditor::Document \*document)](#marksChanged)
- [void modeChanged(KTextEditor::Document \*document)](#modeChanged)
- [void modifiedChanged(KTextEditor::Document \*document)](#modifiedChanged)
- [void modifiedOnDisk(KTextEditor::Document \*document, bool isModified, KTextEditor::Document::ModifiedOnDiskReason reason)](#modifiedOnDisk)
- [void readWriteChanged(KTextEditor::Document \*document)](#readWriteChanged)
- [void reloaded(KTextEditor::Document \*document)](#reloaded)
- [void textChanged(KTextEditor::Document \*document)](#textChanged)
- [void textInserted(KTextEditor::Document \*document, KTextEditor::Cursor position, const QString &text)](#textInserted)
- [void textRemoved(KTextEditor::Document \*document, KTextEditor::Range range, const QString &text)](#textRemoved)
- [void viewCreated(KTextEditor::Document \*document, KTextEditor::View \*view)](#viewCreated)

## Static Public Members

- [int reservedMarkersCount()](#reservedMarkersCount)

## Protected Functions

- [Document(KTextEditor::DocumentPrivate \*impl, const KPluginMetaData &data, QObject \*parent)](#Document)

## Detailed Description {#details}

### Introduction {#introduction}

The Document class represents a pure text document providing methods to modify the content and create views. A document can have any number of views, each view representing the same content, i.e. all views are synchronized. Support for text selection is handled by a View and text format attributes by the Attribute class.

To load a document call KParts::ReadOnlyPart::openUrl(). To reload a document from a file call [documentReload](ktexteditor-document.md#documentReload)(), to save the document call [documentSave](ktexteditor-document.md#documentSave)() or [documentSaveAs](ktexteditor-document.md#documentSaveAs)(). Whenever the modified state of the document changes the signal [modifiedChanged](ktexteditor-document.md#modifiedChanged)() is emitted. Check the modified state with KParts::ReadWritePart::isModified(). Further signals are [documentUrlChanged](ktexteditor-document.md#documentUrlChanged)(). The encoding can be specified with [setEncoding](ktexteditor-document.md#setEncoding)(), however this will only take effect on file reload and file save.

### Text Manipulation {#text-manipulation}

Get the whole content with [text](ktexteditor-document.md#text)() and set new content with [setText](ktexteditor-document.md#setText)(). Call [insertText](ktexteditor-document.md#insertText)() or [insertLine](ktexteditor-document.md#insertLine)() to insert new text or [removeText](ktexteditor-document.md#removeText)() and [removeLine](ktexteditor-document.md#removeLine)() to remove content. Whenever the document's content changed the signal [textChanged](ktexteditor-document.md#textChanged)() is emitted. Additional signals are [textInserted](ktexteditor-document.md#textInserted)() and [textRemoved](ktexteditor-document.md#textRemoved)(). Note, that the first line in the document is line 0.

A Document provides full undo/redo history. Text manipulation actions can be grouped together to one undo/redo action by using an the class [EditingTransaction](ktexteditor-document-editingtransaction.md). You can stack multiple [EditingTransaction](ktexteditor-document-editingtransaction.md)%s. Internally, the Document has a reference counter. If this reference counter is increased the first time (by creating an instance of [EditingTransaction](ktexteditor-document-editingtransaction.md)), the signal [editingStarted](ktexteditor-document.md#editingStarted)() is emitted. Only when the internal reference counter reaches zero again, the signal [editingFinished](ktexteditor-document.md#editingFinished)() and optionally the signal [textChanged](ktexteditor-document.md#textChanged)() are emitted. Whether an editing transaction is currently active can be checked by calling [isEditingTransactionRunning](ktexteditor-document.md#isEditingTransactionRunning)().

> **Note:** The signal [editingFinished](ktexteditor-document.md#editingFinished)() is always emitted when the last instance of [EditingTransaction](ktexteditor-document-editingtransaction.md) is destroyed. Contrary, the signal [textChanged](ktexteditor-document.md#textChanged)() is emitted only if text changed. Hence, [textChanged](ktexteditor-document.md#textChanged)() is more accurate with respect to changes in the Document.

Every text editing transaction is also available through the signals [lineWrapped](ktexteditor-document.md#lineWrapped)(), [lineUnwrapped](ktexteditor-document.md#lineUnwrapped)(), [textInserted](ktexteditor-document.md#textInserted)() and [textRemoved](ktexteditor-document.md#textRemoved)(). However, these signals should be used with care. Please be aware of the following warning:

> **Warning:** Never change the Document's contents when edit actions are active, i.e. in between of (foreign) editing transactions. In case you violate this, the currently active edit action may perform edits that lead to undefined behavior.

### Document Views {#document-views}

A View displays the document's content. As already mentioned, a document can have any number of views, all synchronized. Get a list of all views with [views](ktexteditor-document.md#views)(). Create a new view with [createView](ktexteditor-document.md#createView)(). Every time a new view is created the signal [viewCreated](ktexteditor-document.md#viewCreated)() is emitted.

### Read-Only Mode {#read-only-mode}

A Document may be in read-only mode, for instance due to missing file permissions. The read-only mode can be checked with [isReadWrite](../kparts/kparts-readwritepart.md#isReadWrite)(). Further, the signal [readWriteChanged](ktexteditor-document.md#readWriteChanged)() is emitted whenever the state changes either to read-only mode or to read/write mode. The read-only mode can be controlled with [setReadWrite](../kparts/kparts-readwritepart.md#setReadWrite)().

### Notifications in Documents and Views {#notifications-in-documents-and-views}

A Document has the ability to show a Message to the user in a View. The Message then is shown either the specified View if [Message::setView](ktexteditor-message.md#setView)() was called, or in all View%s of the Document.

To post a message just create a new Message and send it with [postMessage](ktexteditor-document.md#postMessage)(). Further information is available in the API documentation of [KTextEditor::Message](ktexteditor-message.md).

### Crash Recovery for Documents {#crash-recovery-for-documents}

When the system or the application using the editor component crashed with unsaved changes in the Document, the View notifies the user about the lost data and asks, whether the data should be recovered.

This Document gives you control over the data recovery process. Use [isDataRecoveryAvailable](ktexteditor-document.md#isDataRecoveryAvailable)() to check for lost data. If you do not want the editor component to handle the data recovery process automatically, you can either trigger the data recovery by calling [recoverData](ktexteditor-document.md#recoverData)() or discard it through [discardDataRecovery](ktexteditor-document.md#discardDataRecovery)().

### Document Moving Interface {#document-moving-interface}

Document Moving Interface allows you to create [MovingRange](ktexteditor-movingrange.md) and [MovingCursor](ktexteditor-movingcursor.md). A Moving Range or Cursor is a special type of range/cursor because it automatically moves on text insertion or removal. Additionally, one can use the moving ranges to change the color of a particular word or give it a different attribute such as bold. Use [newMovingCursor](ktexteditor-document.md#newMovingCursor)() to create a new moving cursor and [newMovingRange](ktexteditor-document.md#newMovingRange)() to create a new moving range.

Upon destruction or reload, a document will invalidate all its moving ranges. You can connect to [aboutToInvalidateMovingInterfaceContent](ktexteditor-document.md#aboutToInvalidateMovingInterfaceContent)() signals to know when that is going to happen and delete the cached ranges accordingly.

### Document Config {#document-config}

Config provides methods to access and modify the low level config information for a given Document. [KTextEditor::Document](ktexteditor-document.md) has support for the following config keys:

| Key | Type | Description |
| --- | --- | --- |
| backup-on-save-local | \[bool\] | enable/disable backup when saving local files |
| backup-on-save-remote | \[bool\] | enable/disable backup when saving remote files |
| backup-on-save-suffix | \[string\] | set the suffix for file backups, e.g. "~" |
| backup-on-save-prefix | \[string\] | set the prefix for file backups, e.g. "." |
| replace-tabs | \[bool\] | whether to replace tabs |
| indent-pasted-text | \[bool\] | whether to indent pasted text |
| tab-width | \[int\] | read/set the width for tabs |
| indent-width | \[int\] | read/set the indentation width |
| on-the-fly-spellcheck | \[bool\] | enable/disable on the fly spellcheck |

### External modification extension interface for the Document. {#external-modification-extension-interface-for-the-document}

The class ModificationInterface provides methods to handle modifications of all opened files caused by external programs. Whenever the modified-on-disk state changes the signal [modifiedOnDisk](ktexteditor-document.md#modifiedOnDisk)() is emitted along with a [ModifiedOnDiskReason](ktexteditor-document.md#ModifiedOnDiskReason-enum). Set the state by calling [setModifiedOnDisk](ktexteditor-document.md#setModifiedOnDisk)(). Whether the Editor should show warning dialogs to inform the user about external modified files can be controlled with [setModifiedOnDiskWarning](ktexteditor-document.md#setModifiedOnDiskWarning)(). The slot [modifiedOnDisk](ktexteditor-document.md#modifiedOnDisk)() is called to ask the user what to do whenever a file was modified.

### Mark Interface {#mark-interface}

The Mark Interface provides methods to enable and disable marks in a Document, a marked line can be visualized for example with a shaded background color and/or a pixmap in the iconborder of the Document's View. There are a number of predefined mark types, specified in [reservedMarkersCount](ktexteditor-document.md#reservedMarkersCount)(). Additionally it is possible to add custom marks and set custom pixmaps.

Get all marks in the document by calling [marks](ktexteditor-document.md#marks)(). Use [clearMarks](ktexteditor-document.md#clearMarks)() to remove all marks in the entire document. A single mark can be retrieved with [mark](ktexteditor-document.md#mark)(). To remove all marks from a line call [clearMark](ktexteditor-document.md#clearMark)(). To add and remove marks from a given line use [addMark](ktexteditor-document.md#addMark)() and [removeMark](ktexteditor-document.md#removeMark)(). It is also possible to replace all marks with [setMark](ktexteditor-document.md#setMark)(), i.e. [setMark](ktexteditor-document.md#setMark)() is the same as a call of [clearMark](ktexteditor-document.md#clearMark)() followed by [addMark](ktexteditor-document.md#addMark)(). The signals [marksChanged](ktexteditor-document.md#marksChanged)() and [markChanged](ktexteditor-document.md#markChanged)() are emitted whenever a line's marks changed.

> **Note:** A mark type is represented as an *uint*. An *uint* can have several mark types combined (see above: logical OR). That means for all functions/signals with an *uint* parameter, e.g. [setMark](ktexteditor-document.md#setMark)(), [removeMark](ktexteditor-document.md#removeMark)(), etc, the *uint* may contain *multiple* marks, i.e. you can add and remove multiple marks *simultaneously*.

All marks that should be editable by the user can be specified with a mark mask via [setEditableMarks](ktexteditor-document.md#setEditableMarks)(). To set a description and pixmap of a mark type call [setMarkDescription](ktexteditor-document.md#setMarkDescription)() and setMarkPixmap().

### Annotation Interface {#annotation-interface}

The Annotation Interface is designed to provide line annotation information for a document. This interface provides means to associate a document with a annotation model, which provides some annotation information for each line in the document.

Setting a model for a Document makes the model data available for all views. If you only want to provide annotations in exactly one view, you can use the AnnotationViewInterface directly. See the AnnotationViewInterface for further details. To summarize, the two use cases are:

1. Show annotations in all views. This means you set an AnnotationModel with this interface, and then call setAnnotationBorderVisible() for each view.
2. Show annotations only in one view. This means to *not* use this interface. Instead, use the AnnotationViewInterface, which inherits this interface. This means you set a model for the specific View.

If you set a model to the Document *and* the View, the View's model has higher priority.

More information about interfaces for the document can be found in kte\_group\_doc\_extensions.

*See also* [KParts::ReadWritePart](../kparts/kparts-readwritepart.md), [KTextEditor::Editor](ktexteditor-index.md), [KTextEditor::View](ktexteditor-index.md), [KTextEditor::MarkInterface](ktexteditor-index.md)

## Member Type Documentation {#member-type-documentation}

### enum Document::MarkChangeAction {#MarkChangeAction-enum}

Possible actions on a mark.

| Constant | Value | Description |
| --- | --- | --- |
| `KTextEditor::Document::MarkAdded` | `0` | A mark was added. |
| `KTextEditor::Document::MarkRemoved` | `1` | A mark was removed. |

*See also* [markChanged](ktexteditor-document.md#markChanged)()

### enum Document::MarkTypes {#MarkTypes-enum}

Predefined mark types.

| Constant | Value |   |
| --- | --- | --- |
| `KTextEditor::Document::Bookmark` | `markType01` |   |
| `KTextEditor::Document::BreakpointActive` | `markType02` |   |
| `KTextEditor::Document::BreakpointReached` | `markType03` |   |
| `KTextEditor::Document::BreakpointDisabled` | `markType04` |   |
| `KTextEditor::Document::Execution` | `markType05` |   |
| `KTextEditor::Document::Warning` | `markType06` |   |
| `KTextEditor::Document::Error` | `markType07` |   |
| `KTextEditor::Document::SearchMatch` | `markType32` | To add a new standard mark type, edit this interface and document the type. |

### enum Document::ModifiedOnDiskReason {#ModifiedOnDiskReason-enum}

Reasons why a document is modified on disk.

| Constant | Value | Description |
| --- | --- | --- |
| `KTextEditor::Document::OnDiskUnmodified` | `0` | Not modified |
| `KTextEditor::Document::OnDiskModified` | `1` | The file was modified on disk |
| `KTextEditor::Document::OnDiskCreated` | `2` | The file was created on disk |
| `KTextEditor::Document::OnDiskDeleted` | `3` | The file was deleted or moved on disk |

## Member Function Documentation {#member-function-documentation}

### \[protected\] Document::Document(KTextEditor::DocumentPrivate \**impl*, const KPluginMetaData &*data*, QObject \**parent*) {#Document}

Constructor.

Create a new document with `parent`.

Pass it the internal implementation to store a d-pointer.

`impl` is the metadata pointer to use

`data` is TODO

`parent` is the parent object

*See also* [KTextEditor::EditorPrivate::createDocument()](ktexteditor-index.md)

### \[signal\] void Document::aboutToClose(KTextEditor::Document \**document*) {#aboutToClose}

Warn anyone listening that the current document is about to close. At this point all of the information is still accessible, such as the text, cursors and ranges.

Any modifications made to the document at this point will be lost.

`document` is the document being closed

### \[signal\] void Document::aboutToInvalidateMovingInterfaceContent(KTextEditor::Document \**document*) {#aboutToInvalidateMovingInterfaceContent}

This signal is emitted before the ranges of a document are invalidated and the revisions are deleted as the document is cleared (for example on load/reload). While this signal is emitted, the old document content is still valid and accessible before the clear.

`document` is the document which the interface belongs to which will invalidate its data

### \[signal\] void Document::aboutToReload(KTextEditor::Document \**document*) {#aboutToReload}

Warn anyone listening that the current document is about to reload. At this point all of the information is still accessible, such as the text, cursors and ranges.

Any modifications made to the document at this point will be lost.

`document` is the document being reloaded

### \[signal\] void Document::aboutToSave(KTextEditor::Document \**document*) {#aboutToSave}

Emitted just before the document will be saved Any modifications made to the document at this point will get stored on disk.

`document` is the document that was reloaded.

### \[pure virtual\] void Document::addMark(int *line*, uint *markType*) {#addMark}

Add marks of type `markType` to `line`. Existing marks on this line are preserved. If the mark `markType` already is set, nothing happens.

`line` is the line number

`markType` is the mark type

*See also* [removeMark](ktexteditor-document.md#removeMark)(), [setMark](ktexteditor-document.md#setMark)()

### \[pure virtual\] KTextEditor::AnnotationModel \*Document::annotationModel() const {#annotationModel}

Returns the current AnnotationModel or 0 if there's none set

*See also* [setAnnotationModel](ktexteditor-document.md#setAnnotationModel)()

### \[pure virtual\] QChar Document::characterAt(KTextEditor::Cursor *position*) const {#characterAt}

Get the character at a cursor position.

`position` is the location of the character to retrieve

Returns the requested character, or QChar() for invalid cursors.

*See also* [setText](ktexteditor-document.md#setText)()

### \[pure virtual\] QByteArray Document::checksum() const {#checksum}

Get the git hash of the Document's contents on disk. The returned hash equals the git hash of the file written to disk. If the document is a remote document, the checksum may not be available. In this case, [QByteArray::isNull](https://doc.qt.io/qt-6/qbytearray.html#isNull)() returns *true*.

git hash is defined as:

sha1("blob " + filesize + "\\0" + filecontent)

Returns the git hash of the document

### \[pure virtual\] bool Document::clear() {#clear}

Remove the whole content of the document. Returns *true* on success, otherwise *false*

*See also* [removeText](ktexteditor-document.md#removeText)(), [removeLine](ktexteditor-document.md#removeLine)()

### \[pure virtual\] void Document::clearMark(int *line*) {#clearMark}

Clear all marks set in the `line`.

`line` is the line number

*See also* [KTextEditor::DocumentPrivate::clearMarks()](ktexteditor-index.md), [removeMark](ktexteditor-document.md#removeMark)(), [addMark](ktexteditor-document.md#addMark)()

### \[pure virtual\] void Document::clearMarks() {#clearMarks}

Clear all marks in the entire document.

TODO: dominik: add argument unit mask = 0

*See also* [clearMark](ktexteditor-document.md#clearMark)(), [removeMark](ktexteditor-document.md#removeMark)()

### \[signal\] void Document::configChanged(KTextEditor::Document \**document*) {#configChanged}

This signal is emitted whenever the current document configuration is changed.

`document` is the document reporting the configuration change

### \[pure virtual\] QStringList Document::configKeys() const {#configKeys}

Get a list of all available keys.

### \[pure virtual\] QVariant Document::configValue(const QString &*key*) {#configValue}

Get a value for the `key`.

*See also* [setConfigValue](ktexteditor-document.md#setConfigValue)()

### \[pure virtual\] KTextEditor::View \*Document::createView(QWidget \**parent*, KTextEditor::MainWindow \**mainWindow* = nullptr) {#createView}

Create a new view attached to `parent`.

`parent` is the parent widget

`mainWindow` is the main window responsible for this view, if any

Returns the new view

### \[pure virtual, since 6.0\] qsizetype Document::cursorToOffset(KTextEditor::Cursor *c*) const {#cursorToOffset}

Returns the offset for the given cursor position.

> **Note:** It will return -1 if the cursor was invalid or out of bounds.

`c` is the cursor position

This function was introduced in Qt 6.0.

### \[pure virtual\] KSyntaxHighlighting::Theme::TextStyle Document::defaultStyleAt(KTextEditor::Cursor *position*) const {#defaultStyleAt}

Get the default style of the character located at `position`. If `position` is not a valid text position, the default style KSyntaxHighlighting::Theme::TextStyle::Normal is returned.

> **Note:** Further information about the colors of default styles depend on the currently chosen schema. Since each View may have a different color schema, the color information can be obtained through [View::defaultStyleAttribute](ktexteditor-view.md#defaultStyleAttribute)() and [View::lineAttributes](ktexteditor-view.md#lineAttributes)().

`position` is the cursor position

Returns default style, see enum KSyntaxHighlighting::Theme::TextStyle

*See also* [KTextEditor::ViewPrivate::defaultStyleAttribute()](ktexteditor-index.md), [KTextEditor::ViewPrivate::lineAttributes()](ktexteditor-index.md)

### \[pure virtual\] void Document::discardDataRecovery() {#discardDataRecovery}

If recover data is available, calling discardDataRecovery() will discard the recover data and the recover data is lost. If [isDataRecoveryAvailable](ktexteditor-document.md#isDataRecoveryAvailable)() returns *false*, calling this function does nothing.

*See also* [isDataRecoveryAvailable](ktexteditor-document.md#isDataRecoveryAvailable)(), [recoverData](ktexteditor-document.md#recoverData)()

### \[pure virtual\] KTextEditor::Cursor Document::documentEnd() const {#documentEnd}

End position of the document. Returns The last column on the last line of the document

### \[pure virtual\] QString Document::documentName() const {#documentName}

Get this document's name. The editor part should provide some meaningful name, like some unique "Untitled XYZ" for the document - *without* URL or basename for documents with url. Returns readable document name

### \[signal\] void Document::documentNameChanged(KTextEditor::Document \**document*) {#documentNameChanged}

This signal is emitted whenever the `document` name changes.

`document` is document which changed its name

*See also* [documentName](ktexteditor-document.md#documentName)()

### KTextEditor::Range Document::documentRange() const {#documentRange}

A Range which encompasses the whole document. Returns A range from the start to the end of the document

### \[pure virtual\] bool Document::documentReload() {#documentReload}

Reload the current file. The user will be prompted by the part on changes and more and can cancel this action if it can harm. Returns *true* if the reload has been done, otherwise *false*. If the document has no url set, it will just return *false*.

### \[pure virtual\] bool Document::documentSave() {#documentSave}

Save the current file. The user will be asked for a filename if needed and more. Returns *true* on success, i.e. the save has been done, otherwise *false*

### \[pure virtual\] bool Document::documentSaveAs() {#documentSaveAs}

Save the current file to another location. The user will be asked for a filename and more. Returns *true* on success, i.e. the save has been done, otherwise *false*

### \[signal\] void Document::documentSavedOrUploaded(KTextEditor::Document \**document*, bool *saveAs*) {#documentSavedOrUploaded}

This signal should be emitted after a document has been saved to disk or for remote files uploaded.

`document` is the document being saved or uploaded

`saveAs` should be set to true if the operation is a save as operation

### \[signal\] void Document::documentUrlChanged(KTextEditor::Document \**document*) {#documentUrlChanged}

This signal is emitted whenever the `document` URL changes.

`document` is the document which changed its URL

*See also* KParts::ReadOnlyPart::url()

### \[pure virtual\] uint Document::editableMarks() const {#editableMarks}

Get which marks can be toggled by the user. The returned value is a mark mask containing all editable marks combined with a logical OR. Returns mark mask containing all editable marks

*See also* [setEditableMarks](ktexteditor-document.md#setEditableMarks)()

### \[signal\] void Document::editingFinished(KTextEditor::Document \**document*) {#editingFinished}

Emitted when an editing transaction has finished.

> **Note:** This signal is emitted also for editing actions that maybe do not modify the `document` contents (think of having an empty [EditingTransaction](ktexteditor-document-editingtransaction.md)). If you want to get notified only after text really changed, connect to the signal [textChanged](ktexteditor-document.md#textChanged)().

`document` is the document which emitted this signal

*See also* [textChanged](ktexteditor-document.md#textChanged)()

### \[signal\] void Document::editingStarted(KTextEditor::Document \**document*) {#editingStarted}

Emitted when an editing transaction has started.

`document` is the document which emitted this signal

### \[pure virtual\] QStringList Document::embeddedHighlightingModes() const {#embeddedHighlightingModes}

Get all available highlighting modes for the current document.

Each document can be highlighted using an arbitrary number of highlighting contexts. This method will return the names for each of the used modes.

Example: The "PHP (HTML)" mode includes the highlighting for PHP, HTML, CSS and JavaScript.

Returns Returns a list of embedded highlighting modes for the current Document.

*See also* [KTextEditor::Document::highlightingMode()](ktexteditor-index.md)

### \[pure virtual\] QString Document::encoding() const {#encoding}

Get the current chosen encoding. The return value is an empty string, if the document uses the default encoding of the editor and no own special encoding. Returns current encoding of the document

*See also* [setEncoding](ktexteditor-document.md#setEncoding)()

### KTextEditor::Cursor Document::endOfLine(int *line*) const {#endOfLine}

Get the end cursor position of line `line`.

`line` is the line number

*See also* [lineLength](ktexteditor-document.md#lineLength)(), [line](ktexteditor-document.md#line)()

### \[since 6.25\] QUrl Document::getSaveFileUrl(const QString &*dialogTitle*, QWidget \**dialogParent* = nullptr) {#getSaveFileUrl}

Wrapper around [QFileDialog::getSaveFileUrl](https://doc.qt.io/qt-6/qfiledialog.html#getSaveFileUrl), will use proper dialogParent by default and try it's best to find a good directory as start. It also includes additional MIME types based on the document's format and highlighter.

`dialogTitle` is the title for the dialog, for example "Save Document As" `dialogParent` the parent window for the dialog. When nullptr, it will try to determine a proper parent.

Returns the URL to save to or an empty URL if aborted.

This function was introduced in Qt 6.25.

### \[pure virtual\] QString Document::highlightingMode() const {#highlightingMode}

Return the name of the currently used mode Returns name of the used mode

*See also* [highlightingModes](ktexteditor-document.md#highlightingModes)(), [setHighlightingMode](ktexteditor-document.md#setHighlightingMode)()

### \[pure virtual\] QString Document::highlightingModeAt(KTextEditor::Cursor *position*) {#highlightingModeAt}

Get the highlight mode used at a given position in the document.

Retrieve the name of the applied highlight mode at a given `position` in the current document.

Calling this might trigger re-highlighting up to the given line. Therefore this is not const.

*See also* [highlightingModes](ktexteditor-document.md#highlightingModes)()

### \[signal\] void Document::highlightingModeChanged(KTextEditor::Document \**document*) {#highlightingModeChanged}

Emitted when the current document's highlighting mode changes.

`document` is the document reporting the highlighting mode change

*See also* [setHighlightingMode](ktexteditor-document.md#setHighlightingMode)()

### \[pure virtual\] QString Document::highlightingModeSection(int *index*) const {#highlightingModeSection}

Returns the name of the section for a highlight given its index in the highlight list (as returned by highlightModes()).

You can use this function to build a tree of the highlight names, organized in sections.

`index` is the index of the highlight in the list returned by [modes](ktexteditor-document.md#modes)()

### \[pure virtual\] QStringList Document::highlightingModes() const {#highlightingModes}

Returns a list of the names of all possible modes

*See also* [highlightingMode](ktexteditor-document.md#highlightingMode)(), [setHighlightingMode](ktexteditor-document.md#setHighlightingMode)()

### \[pure virtual\] bool Document::insertLine(int *line*, const QString &*text*) {#insertLine}

Insert line(s) at the given line number. The newline character '\\n' is treated as line delimiter, so it is possible to insert multiple lines. To append lines at the end of the document, use

```cpp
insertLine( lines(), text )
```

`line` is where to insert the text

`text` is the text to insert

Returns *true* on success, otherwise *false*

*See also* [insertText](ktexteditor-document.md#insertText)()

### \[pure virtual\] bool Document::insertLines(int *line*, const QStringList &*text*) {#insertLines}

Insert line(s) at the given line number. The newline character '\\n' is treated as line delimiter, so it is possible to insert multiple lines. To append lines at the end of the document, use

```cpp
insertLine( lines(), text )
```

`line` is where to insert the text

`text` is the text to insert

Returns *true* on success, otherwise *false*

*See also* [insertText](ktexteditor-document.md#insertText)()

### \[pure virtual\] bool Document::insertText(KTextEditor::Cursor *position*, const QString &*text*, bool *block* = false) {#insertText}

Insert `text` at `position`.

`position` is where to insert the text

`text` is the text to insert

`block` if true, insert this text as a visual block of text rather than a linear sequence

Returns *true* on success, otherwise *false*

*See also* [setText](ktexteditor-document.md#setText)(), [removeText](ktexteditor-document.md#removeText)()

### \[pure virtual\] bool Document::insertText(KTextEditor::Cursor *position*, const QStringList &*text*, bool *block* = false) {#insertText-1}

Insert `text` at `position`.

`position` is where to insert the text

`text` is the text to insert

`block` if true, insert this text as a visual block of text rather than a linear sequence

Returns *true* on success, otherwise *false*

*See also* [setText](ktexteditor-document.md#setText)(), [removeText](ktexteditor-document.md#removeText)()

### \[pure virtual\] bool Document::isDataRecoveryAvailable() const {#isDataRecoveryAvailable}

Returns whether a recovery is available for the current document.

*See also* [recoverData](ktexteditor-document.md#recoverData)(), [discardDataRecovery](ktexteditor-document.md#discardDataRecovery)()

### \[pure virtual\] bool Document::isEditingTransactionRunning() const {#isEditingTransactionRunning}

Returns true if an editing transaction is currently running.

*See also* [EditingTransaction](ktexteditor-document-editingtransaction.md)

### \[virtual\] bool Document::isEmpty() const {#isEmpty}

Returns if the document is empty.

### \[pure virtual\] bool Document::isLineModified(int *line*) const {#isLineModified}

Check whether `line` currently contains unsaved data. If `line` contains unsaved data, *true* is returned, otherwise *false*. When the user saves the file, a modified line turns into a *saved* line. In this case isLineModified() returns *false* and in its stead [isLineSaved](ktexteditor-document.md#isLineSaved)() returns *true*.

`line` is line number

*See also* [isLineSaved](ktexteditor-document.md#isLineSaved)(), [isLineTouched](ktexteditor-document.md#isLineTouched)()

### \[pure virtual\] bool Document::isLineSaved(int *line*) const {#isLineSaved}

Check whether `line` currently contains only saved text. Saved text in this case implies that a line was touched at some point by the user and then then changes were either undone or the user saved the file.

In case `line` was touched and currently contains only saved data, *true* is returned, otherwise *false*.

`line` is the line number

*See also* [isLineModified](ktexteditor-document.md#isLineModified)(), [isLineTouched](ktexteditor-document.md#isLineTouched)()

### \[pure virtual\] bool Document::isLineTouched(int *line*) const {#isLineTouched}

Returns true if a line was touched since the file was opened. This equals the statement [isLineModified](ktexteditor-document.md#isLineModified)() \|\| [isLineSaved](ktexteditor-document.md#isLineSaved)().

`line` is the line number

*See also* [isLineModified](ktexteditor-document.md#isLineModified)(), [isLineSaved](ktexteditor-document.md#isLineSaved)()

### \[pure virtual\] bool Document::isValidTextPosition(KTextEditor::Cursor *cursor*) const {#isValidTextPosition}

Get whether `cursor` is a valid text position. A cursor position at (line, column) is valid, if

- line \>= 0 and line \< [lines](ktexteditor-document.md#lines)() holds, and
- column \>= 0 and column \<= [lineLength](ktexteditor-document.md#lineLength)(column).

The text position `cursor` is also invalid if it is inside a Unicode surrogate. Therefore, use this function when iterating over the characters of a line.

`cursor` is the cursor position to check for validity

Returns true, if `cursor` is a valid text position, otherwise false

### \[pure virtual\] qint64 Document::lastSavedRevision() const {#lastSavedRevision}

Last revision the buffer got successful saved Returns last revision buffer got saved, -1 if none

### \[pure virtual\] QString Document::line(int *line*) const {#line}

Get a single text line.

`line` is the requested line

Returns the requested line, or "" for invalid line numbers

*See also* [text](ktexteditor-document.md#text)(), [lineLength](ktexteditor-document.md#lineLength)()

### \[pure virtual\] int Document::lineLength(int *line*) const {#lineLength}

Get the length of a given line in characters.

`line` is the line number

Returns the number of characters in the line or -1 if the line was invalid

*See also* [line](ktexteditor-document.md#line)()

### \[signal\] void Document::lineUnwrapped(KTextEditor::Document \**document*, int *line*) {#lineUnwrapped}

Emitted when A line is unwrapped.

`document` is the document which emitted this signal

`line` line is where the unwrap occurred

### \[signal\] void Document::lineWrapped(KTextEditor::Document \**document*, KTextEditor::Cursor *position*) {#lineWrapped}

Emitted when a line of text is wrapped.

`document` is the document which emitted this signal

`position` is the where the wrap occurred

### \[pure virtual\] int Document::lines() const {#lines}

Returns the current number of lines in the document

### \[pure virtual\] void Document::lockRevision(qint64 *revision*) {#lockRevision}

Lock a revision, this will keep it around until released again. But all revisions will always be cleared on buffer [clear](ktexteditor-document.md#clear)() (and therefor load())

`revision` is the revision to lock

### \[pure virtual\] uint Document::mark(int *line*) {#mark}

Get all marks set on the `line`.

`line` is the line number

Returns a *uint* representing of the marks set in `line` concatenated by logical OR

*See also* [setMark](ktexteditor-document.md#setMark)(), [addMark](ktexteditor-document.md#addMark)(), [removeMark](ktexteditor-document.md#removeMark)()

### \[signal\] void Document::markChanged(KTextEditor::Document \**document*, KTextEditor::Mark *mark*, KTextEditor::Document::MarkChangeAction *action*) {#markChanged}

The `document` emits this signal whenever the `mark` changes.

`document` is the document which emitted the signal

`mark` is the changed mark

`action` is the action (either removed or added)

*See also* [marksChanged](ktexteditor-document.md#marksChanged)()

### \[signal\] void Document::markClicked(KTextEditor::Document \**document*, KTextEditor::Mark *mark*, bool &*handled*) {#markClicked}

The `document` emits this signal whenever the `mark` is left-clicked.

`document` is the document which emitted the signal

`mark` is the mark that was right-clicked

`handled` is set this to 'true' if this event was handled externally, and kate should not handle the left click.

### \[signal\] void Document::markContextMenuRequested(KTextEditor::Document \**document*, KTextEditor::Mark *mark*, QPoint *pos*, bool &*handled*) {#markContextMenuRequested}

The `document` emits this signal whenever the `mark` is right-clicked to show a context menu. The receiver may show an own context menu instead of the kate internal one.

`document` is the document which emitted the signal

`mark` is the mark that was right-clicked

`pos` is the position where the menu should be started

`handled` is set this to 'true' if this event was handled externally, and kate should not create it's own context menu.

### \[pure virtual\] QString Document::markDescription(KTextEditor::Document::MarkTypes *mark*) const {#markDescription}

Get the `mark`'s description to text.

`mark` is the mark

Returns text of the given `mark` or QString(), if the entry does not exist

*See also* [setMarkDescription](ktexteditor-document.md#setMarkDescription)()

### \[pure virtual\] QIcon Document::markIcon(KTextEditor::Document::MarkTypes *markType*) const {#markIcon}

Returns a mark type's icon.

`markType` is the mark type. If the icon does not exist the resulting is null (check with QIcon::isNull()).

*See also* [setMarkIcon](ktexteditor-document.md#setMarkIcon)(), [setMarkDescription](ktexteditor-document.md#setMarkDescription)()

### \[signal\] void Document::markToolTipRequested(KTextEditor::Document \**document*, KTextEditor::Mark *mark*, QPoint *position*, bool &*handled*) {#markToolTipRequested}

The `document` emits this signal whenever the `mark` is hovered using the mouse, and the receiver may show a tooltip.

`document` is the document which emitted the signal

`mark` is the mark that was hovered

`position` is the mouse position during the hovering

`handled` set this to 'true' if this event was handled externally

### \[pure virtual\] const QHash\<int, KTextEditor::Mark \*\> &Document::marks() {#marks}

Get a hash holding all marks in the document. The hash key for a mark is its line. Returns a hash holding all marks in the document

KF6 TODO: Change Mark\* to Mark. No need for pointer here.

### \[signal\] void Document::marksChanged(KTextEditor::Document \**document*) {#marksChanged}

The `document` emits this signal whenever a mark mask changed.

`document` is document which emitted this signal

*See also* [markChanged](ktexteditor-document.md#markChanged)()

### \[pure virtual\] QString Document::mimeType() {#mimeType}

Returns this document's mimetype.

### \[pure virtual\] QString Document::mode() const {#mode}

Return the name of the currently used mode Returns name of the used mode

*See also* [modes](ktexteditor-document.md#modes)(), [setMode](ktexteditor-document.md#setMode)()

### \[signal\] void Document::modeChanged(KTextEditor::Document \**document*) {#modeChanged}

Emitted when the current document's mode changes.

`document` is the document reporting the mode change

*See also* [setMode](ktexteditor-document.md#setMode)()

### \[pure virtual\] QString Document::modeSection(int *index*) const {#modeSection}

Returns the name of the section for a mode given its index in the highlight list (as returned by [modes](ktexteditor-document.md#modes)()).

You can use this function to build a tree of the mode names, organized in sections.

`index` is the index of the highlight in the list returned by [modes](ktexteditor-document.md#modes)()

### \[pure virtual\] QStringList Document::modes() const {#modes}

Returns a list of the names of all possible modes

*See also* [mode](ktexteditor-document.md#mode)(), [setMode](ktexteditor-document.md#setMode)()

### \[signal\] void Document::modifiedChanged(KTextEditor::Document \**document*) {#modifiedChanged}

This signal is emitted whenever the `document`'s buffer changed from either state *unmodified* to *modified* or vice versa.

`document` is the document which changed its modified state

*See also* KParts::ReadWritePart::isModified(), KParts::ReadWritePart::setModified()

### \[signal\] void Document::modifiedOnDisk(KTextEditor::Document \**document*, bool *isModified*, KTextEditor::Document::ModifiedOnDiskReason *reason*) {#modifiedOnDisk}

This signal is emitted whenever the `document` changed its modified-on-disk state.

`document` is the Document object that represents the file on disk

`isModified` if *true*, the file was modified rather than created or deleted

`reason` is the reason why the signal was emitted

*See also* [setModifiedOnDisk](ktexteditor-document.md#setModifiedOnDisk)()

### \[pure virtual\] KTextEditor::MovingCursor \*Document::newMovingCursor(KTextEditor::Cursor *position*, KTextEditor::MovingCursor::InsertBehavior *insertBehavior* = MovingCursor::MoveOnInsert) {#newMovingCursor}

Create a new moving cursor for this document.

`position` is the position of the new moving cursor

`insertBehavior` describes the insertion behavior

Returns new moving cursor for the document

### \[pure virtual\] KTextEditor::MovingRange \*Document::newMovingRange(KTextEditor::Range *range*, MovingRange::InsertBehaviors *insertBehaviors* = MovingRange::DoNotExpand, KTextEditor::MovingRange::EmptyBehavior *emptyBehavior* = MovingRange::AllowEmpty) {#newMovingRange}

Create a new moving range for this document. Ownership of the range that is returned belongs to the caller

`range` range of the moving range to create

`insertBehaviors` insertion behaviors

`emptyBehavior` behavior on becoming empty

Returns new moving range for the document

### \[pure virtual, since 6.0\] KTextEditor::Cursor Document::offsetToCursor(qsizetype *offset*) const {#offsetToCursor}

Returns the cursor position for a given `offset`

> **Note:** It will return an invalid cursor(-1, -1) if offset is invalid.

This function was introduced in Qt 6.0.

### bool Document::openingError() const {#openingError}

True, eg if the file for opening could not be read This doesn't have to handle the KPart job canceled cases. Returns was there some problem loading the file?

### \[pure virtual\] bool Document::postMessage(KTextEditor::Message \**message*) {#postMessage}

Post `message` to the Document and its View%s. If multiple Message%s are posted, the one with the highest priority is shown first.

Usually, you can simply forget the pointer, as the Message is deleted automatically, once it is processed or the document gets closed.

If the Document does not have a View yet, the Message is queued and shown, once a View for the Document is created.

`message` the message to show

Returns true, if `message` was posted. false, if message == 0.

### \[pure virtual\] bool Document::print() {#print}

Print the document. This should result in showing the print dialog.

Returns true if document was printed

### \[pure virtual\] void Document::printPreview() {#printPreview}

Shows the print preview dialog/

### \[pure virtual\] void Document::readSessionConfig(const KConfigGroup &*config*, const QSet\<QString\> &*flags* = QSet\<QString\>()) {#readSessionConfig}

Read session settings from the given `config`.

Known flags:

| Flag | Description |
| --- | --- |
| "SkipUrl" | Do not save/restore the file |
| "SkipMode" | Do not save/restore the mode |
| "SkipHighlighting" | Do not save/restore the highlighting |
| "SkipEncoding"i | Do not save/restore the encoding |

`config` is the [KConfigGroup](../kconfigcore/kconfiggroup.md) to read the session settings from

`flags` are optional settings to read (any combination of the flags from the Known Flags list). Unknown flags are ignored.

*See also* [writeSessionConfig](ktexteditor-document.md#writeSessionConfig)()

### \[signal\] void Document::readWriteChanged(KTextEditor::Document \**document*) {#readWriteChanged}

This signal is emitted whenever the readWrite state of a document changes.

`document` is the document whose read/write property changed

*See also* KParts::ReadWritePart::setReadWrite()

### \[pure virtual\] void Document::recoverData() {#recoverData}

If recover data is available, calling recoverData() will trigger the recovery of the data. If [isDataRecoveryAvailable](ktexteditor-document.md#isDataRecoveryAvailable)() returns *false*, calling this function does nothing.

*See also* [isDataRecoveryAvailable](ktexteditor-document.md#isDataRecoveryAvailable)(), [discardDataRecovery](ktexteditor-document.md#discardDataRecovery)()

### \[signal\] void Document::reloaded(KTextEditor::Document \**document*) {#reloaded}

Emitted after the current document was reloaded. At this point, some information might have been invalidated, like for example the editing history.

`document` is the document that was reloaded.

### \[pure virtual\] bool Document::removeLine(int *line*) {#removeLine}

Remove `line` from the document.

`line` is the line to remove

Returns *true* on success, otherwise *false*

*See also* [removeText](ktexteditor-document.md#removeText)(), [clear](ktexteditor-document.md#clear)()

### \[pure virtual\] void Document::removeMark(int *line*, uint *markType*) {#removeMark}

Remove the mark mask of type `markType` from `line`.

`line` is the line number

`markType` is the mark type to be removed

*See also* [clearMark](ktexteditor-document.md#clearMark)()

### \[pure virtual\] bool Document::removeText(KTextEditor::Range *range*, bool *block* = false) {#removeText}

Remove the text specified in `range`.

`range` is the range of text to remove

`block` if true, remove a text block on the basis of columns, rather than everything inside `range`

Returns *true* on success, otherwise *false*

*See also* [setText](ktexteditor-document.md#setText)(), [insertText](ktexteditor-document.md#insertText)()

### \[virtual\] bool Document::replaceText(KTextEditor::Range *range*, const QString &*text*, bool *block* = false) {#replaceText}

Replace text from `range` with specified `text`.

`range` is the range of text to replace

`text` is the replacement text

`block` if true, replace text as a visual block of text rather than a linear sequence

Returns *true* on success, otherwise *false*

*See also* [setText](ktexteditor-document.md#setText)(), [removeText](ktexteditor-document.md#removeText)(), [insertText](ktexteditor-document.md#insertText)()

### \[virtual\] bool Document::replaceText(KTextEditor::Range *range*, const QStringList &*text*, bool *block* = false) {#replaceText-1}

Replace text from `range` with specified `text`.

`range` is the range of text to replace

`text` is the replacement text

`block` if true, replace text as a visual block of text rather than a linear sequence

Returns *true* on success, otherwise *false*

*See also* [setText](ktexteditor-document.md#setText)(), [removeText](ktexteditor-document.md#removeText)(), [insertText](ktexteditor-document.md#insertText)()

### \[static\] int Document::reservedMarkersCount() {#reservedMarkersCount}

Get the number of predefined mark types we have so far.

> **Note:** FIXME: If you change this you have to make sure katepart supports the new size! Returns number of reserved marker types

### \[pure virtual\] qint64 Document::revision() const {#revision}

Current revision Returns current revision

### QList\<KTextEditor::Range\> Document::searchText(KTextEditor::Range *range*, const QString &*pattern*, const KTextEditor::SearchOptions *options* = Default) const {#searchText}

Searches the given input range for a text pattern.

Searches for a text pattern within the given input range. The kind of search performed depends on the `options` used. Use this function for plaintext searches as well as regular expression searches. If no match is found the first (and only) element in the vector return is the invalid range. When searching for regular expressions, the first element holds the range of the full match, the subsequent elements hold the ranges of the capturing parentheses.

`range` is the range to search in

`pattern` is the text pattern to search for

`options` defines the search options

Returns List of ranges (length \>=1)

**Author:** Sebastian Pipping \<webmaster@hartwork.org\>

### \[pure virtual\] void Document::setAnnotationModel(KTextEditor::AnnotationModel \**model*) {#setAnnotationModel}

Sets a new AnnotationModel for this document to provide annotation information for each line.

`model` is the new AnnotationModel

*See also* [annotationModel](ktexteditor-document.md#annotationModel)()

### \[pure virtual\] void Document::setConfigValue(const QString &*key*, const QVariant &*value*) {#setConfigValue}

Set a the `key`'s value to `value`.

*See also* [configValue](ktexteditor-document.md#configValue)()

### \[pure virtual\] void Document::setEditableMarks(uint *markMask*) {#setEditableMarks}

Set the mark mask the user is allowed to toggle to `markMask`. I.e. concatenate all editable marks with a logical OR. If the user should be able to add a bookmark and set a breakpoint with the context menu in the icon pane, you have to call

```cpp
// iface is of Type KTextEditor::MarkInterface*
// only make bookmark and breakpoint editable
iface->setEditableMarks( MarkInterface::Bookmark |
                         MarkInterface::BreakpointActive );

// or preserve last settings, and add bookmark and breakpoint
iface->setEditableMarks( iface->editableMarks() |
                         MarkInterface::Bookmark |
                         MarkInterface::BreakpointActive );
```

`markMask` is the mark bitmask

*See also* [editableMarks](ktexteditor-document.md#editableMarks)(), setMarkPixmap(), [setMarkDescription](ktexteditor-document.md#setMarkDescription)()

### \[pure virtual\] bool Document::setEncoding(const QString &*encoding*) {#setEncoding}

Set the encoding for this document. This encoding will be used while loading and saving files, it will *not* affect the already existing content of the document, e.g. if the file has already been opened without the correct encoding, this will *not* fix it, you would for example need to trigger a reload for this.

`encoding` is new encoding for the document, the name must be accepted by [QStringDecoder](https://doc.qt.io/qt-6/qstringdecoder.html)/[QStringEncoder](https://doc.qt.io/qt-6/qstringencoder.html), if an empty encoding name is given, the part should fallback to its own default encoding, e.g. the system encoding or the global user settings

Returns *true* on success, or *false*, if the encoding could not be set.

*See also* [encoding](ktexteditor-document.md#encoding)()

### \[pure virtual\] bool Document::setHighlightingMode(const QString &*name*) {#setHighlightingMode}

Set the current highlighting mode of the document by giving its name.

`name` is the name of the highlighting mode to use for this document

Returns *true* on success, otherwise *false*

*See also* [highlightingMode](ktexteditor-document.md#highlightingMode)(), [highlightingModes](ktexteditor-document.md#highlightingModes)(), [highlightingModeChanged](ktexteditor-document.md#highlightingModeChanged)()

### \[pure virtual\] void Document::setMark(int *line*, uint *markType*) {#setMark}

Set the `line`'s mark types to `markType`. If `line` already contains a mark of the given type it has no effect. All other marks are deleted before the mark is set. You can achieve the same by calling

```cpp
clearMark(line);
addMark(line, markType);
```

`line` is the line number

`markType` is the mark type

*See also* [clearMark](ktexteditor-document.md#clearMark)(), [addMark](ktexteditor-document.md#addMark)(), [mark](ktexteditor-document.md#mark)()

### \[pure virtual\] void Document::setMarkDescription(KTextEditor::Document::MarkTypes *mark*, const QString &*text*) {#setMarkDescription}

Set the `mark`'s description to `text`.

`mark` is the mark to describe

`text` is the mark's new description

*See also* [markDescription](ktexteditor-document.md#markDescription)(), setMarkPixmap()

### \[pure virtual\] void Document::setMarkIcon(KTextEditor::Document::MarkTypes *markType*, const QIcon &*icon*) {#setMarkIcon}

Set a mark's icon to `icon`.

`markType` is the mark type to which the icon will be attached

`icon` is the new icon

*See also* [markIcon](ktexteditor-document.md#markIcon)(), [setMarkDescription](ktexteditor-document.md#setMarkDescription)()

### \[pure virtual\] bool Document::setMode(const QString &*name*) {#setMode}

Set the current mode of the document by giving its name.

`name` is the name of the mode to use for this document

Returns *true* on success, otherwise *false*

*See also* [mode](ktexteditor-document.md#mode)(), [modes](ktexteditor-document.md#modes)(), [modeChanged](ktexteditor-document.md#modeChanged)()

### \[pure virtual\] void Document::setModifiedOnDisk(KTextEditor::Document::ModifiedOnDiskReason *reason*) {#setModifiedOnDisk}

Sets the document's modified-on-disk state to `reason`. [KTextEditor](ktexteditor-module.md) implementations should emit the signal [modifiedOnDisk](ktexteditor-document.md#modifiedOnDisk)() along with the reason. When the document is in a clean state again the reason should be [ModifiedOnDiskReason::OnDiskUnmodified](ktexteditor-document.md#ModifiedOnDiskReason-enum).

`reason` is the modified-on-disk reason.

*See also* [ModifiedOnDiskReason](ktexteditor-document.md#ModifiedOnDiskReason-enum), [modifiedOnDisk](ktexteditor-document.md#modifiedOnDisk)()

### \[pure virtual\] void Document::setModifiedOnDiskWarning(bool *on*) {#setModifiedOnDiskWarning}

Controls whether the editor should show a warning dialog whenever a file was modified on disk.

`on` true, the editor should show a warning dialog for files modified on disk

### \[pure virtual\] bool Document::setText(const QString &*text*) {#setText}

Set the given text as new document content.

`text` is the new document text

Returns *true* on success, otherwise *false*

*See also* [text](ktexteditor-document.md#text)()

### \[pure virtual\] bool Document::setText(const QStringList &*text*) {#setText-1}

Set the given text as new document content.

`text` is the new document text

Returns *true* on success, otherwise *false*

*See also* [text](ktexteditor-document.md#text)()

### \[pure virtual\] QString Document::text() const {#text}

Get the document content. Returns the complete document content

*See also* [setText](ktexteditor-document.md#setText)()

### \[pure virtual\] QString Document::text(KTextEditor::Range *range*, bool *block* = false) const {#text-1}

Get the document content within the given `range`.

`range` is the range of text to retrieve

`block` Set this to *true* to receive text in a visual block, rather than everything inside `range`.

Returns the requested text part, or QString() for invalid ranges.

*See also* [setText](ktexteditor-document.md#setText)()

### \[signal\] void Document::textChanged(KTextEditor::Document \**document*) {#textChanged}

Emitted when text is changed in a document.

`document` is the document which emitted this signal

*See also* [text](ktexteditor-document.md#text)(), textLine()

### \[signal\] void Document::textInserted(KTextEditor::Document \**document*, KTextEditor::Cursor *position*, const QString &*text*) {#textInserted}

Emitted when text is inserted into a document.

`document` is the document which emitted this signal

`position` is where the insertion occurred

`text` is the inserted text

### \[pure virtual\] QStringList Document::textLines(KTextEditor::Range *range*, bool *block* = false) const {#textLines}

Get the document content within the given `range`.

`range` is the range of text to retrieve

`block` Set this to *true* to receive text in a visual block, rather than everything inside `range`.

Returns the requested text lines, or QStringList() for invalid ranges. no end of line termination is included.

*See also* [setText](ktexteditor-document.md#setText)()

### \[signal\] void Document::textRemoved(KTextEditor::Document \**document*, KTextEditor::Range *range*, const QString &*text*) {#textRemoved}

Emitted when text is removed from a document.

`document` is the document which emitted this signal

`range` is where the removal occurred

`text` is the removed text

### \[pure virtual\] qsizetype Document::totalCharacters() const {#totalCharacters}

Get the count of characters in the document. A TAB character counts as only one character. Returns the number of characters in the document

*See also* [lines](ktexteditor-document.md#lines)()

### \[pure virtual\] void Document::transformCursor(KTextEditor::Cursor &*cursor*, KTextEditor::MovingCursor::InsertBehavior *insertBehavior*, qint64 *fromRevision*, qint64 *toRevision* = -1) {#transformCursor}

Transform a cursor from one revision to an other.

`cursor` is the cursor to transform

`insertBehavior` is the behavior of this cursor on insert of text at its position

`fromRevision` is the first revision to transform

`toRevision` is the last revision to transform (default of -1 is current revision)

### \[pure virtual\] void Document::transformCursor(int &*line*, int &*column*, KTextEditor::MovingCursor::InsertBehavior *insertBehavior*, qint64 *fromRevision*, qint64 *toRevision* = -1) {#transformCursor-1}

Transform a cursor from one revision to an other.

`line` is the line number of the cursor to transform

`column` is the column number of the cursor to transform

`insertBehavior` is the behavior of this cursor on insert of text at its position

`fromRevision` is the first revision to transform

`toRevision` is the last revision to transform (default of -1 is current revision)

### \[pure virtual\] void Document::transformRange(KTextEditor::Range &*range*, KTextEditor::MovingRange::InsertBehaviors *insertBehaviors*, KTextEditor::MovingRange::EmptyBehavior *emptyBehavior*, qint64 *fromRevision*, qint64 *toRevision* = -1) {#transformRange}

Transform a range from one revision to an other.

`range` is the range to transform

`insertBehaviors` is the behavior of this range on insert of text at its position

`emptyBehavior` is the behavior on becoming empty

`fromRevision` is the first revision to transform

`toRevision` is the last revision to transform (default of -1 is current revision)

### \[pure virtual\] void Document::unlockRevision(qint64 *revision*) {#unlockRevision}

Release a revision.

`revision` is the revision to release

### \[signal\] void Document::viewCreated(KTextEditor::Document \**document*, KTextEditor::View \**view*) {#viewCreated}

This signal is emitted whenever the `document` creates a new `view`. It should be called for every view to help applications / plugins to attach to the `view`.

> **Note:** This signal should be emitted after the view constructor is completed, e.g. in the [createView](ktexteditor-document.md#createView)() method.

`document` is the document for which a new view is created

`view` is the new view

*See also* [createView](ktexteditor-document.md#createView)()

### \[pure virtual\] QList\<KTextEditor::View \*\> Document::views() const {#views}

Returns the views pre-casted to [KTextEditor::View](ktexteditor-view.md)%s

### \[pure virtual\] QString Document::wordAt(KTextEditor::Cursor *cursor*) const {#wordAt}

Get the word at the text position `cursor`. The returned word is defined by the word boundaries to the left and right starting at `cursor`. The algorithm takes highlighting information into account, e.g. a dash ('-') in C++ is interpreted as word boundary, whereas e.g. CSS allows identifiers with dash ('-').

If `cursor` is not a valid text position or if there is no word under the requested position `cursor`, an empty string is returned.

`cursor` is the cursor position for the word

Returns the word under the cursor or an empty string if there is no word.

*See also* [wordRangeAt](ktexteditor-document.md#wordRangeAt)(), [characterAt](ktexteditor-document.md#characterAt)()

### \[pure virtual\] KTextEditor::Range Document::wordRangeAt(KTextEditor::Cursor *cursor*) const {#wordRangeAt}

Get the text range for the word located under the text position `cursor`. The returned word is defined by the word boundaries to the left and right starting at `cursor`. The algorithm takes highlighting information into account, e.g. a dash ('-') in C++ is interpreted as word boundary, whereas e.g. CSS allows identifiers with dash ('-').

If `cursor` is not a valid text position or if there is no word under the requested position `cursor`, an invalid text range is returned. If the text range is valid, it is *always* on a single line.

`cursor` is the cursor position for the word

Returns the Range spanning the word under the cursor or an invalid range if there is no word.

*See also* [wordAt](ktexteditor-document.md#wordAt)(), [characterAt](ktexteditor-document.md#characterAt)(), [KTextEditor::Range::isValid()](ktexteditor-index.md)

### \[pure virtual\] void Document::writeSessionConfig(KConfigGroup &*config*, const QSet\<QString\> &*flags* = QSet\<QString\>()) {#writeSessionConfig}

Write session settings to the `config`. See [readSessionConfig](ktexteditor-document.md#readSessionConfig)() for more details about available `flags`.

`config` is the [KConfigGroup](../kconfigcore/kconfiggroup.md) to write the session settings to

`flags` are optional settings to write from the Known Flags list documented in [readSessionConfig](ktexteditor-document.md#readSessionConfig)(). Unknown flags are ignored.

*See also* [readSessionConfig](ktexteditor-document.md#readSessionConfig)()

## Related Non-Members {#related-non-members}

### enum SearchOption {#SearchOption-enum}

**flags KTextEditor::SearchOptions**

Search flags for use with [Document::searchText](ktexteditor-document.md#searchText)().

| Constant | Value | Description |
| --- | --- | --- |
| `KTextEditor::Document::Default` | `0` | Search for a case-sensitive plaintext pattern, without processing of escape sequences, with "whole words" off, in forward direction, within a non-block-mode text range. |
| `KTextEditor::Document::Regex` | `1 << 1` | Treats the pattern as a regular expression |
| `KTextEditor::Document::CaseInsensitive` | `1 << 4` | Ignores case, e.g. "a" matches "A" |
| `KTextEditor::Document::Backwards` | `1 << 5` | Searches in backward direction |
| `KTextEditor::Document::EscapeSequences` | `1 << 10` | Plaintext mode: processes escape sequences |
| `KTextEditor::Document::WholeWords` | `1 << 11` | Plaintext mode: searches whole words only, e.g. **not** "amp" in "example" |

The `SearchOptions` type is a typedef for `QFlags<SearchOption>. `It stores an OR combination of `SearchOption` values.
