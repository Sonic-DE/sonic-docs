---
title: "KParts::ReadWritePart Class"
description: "Base class for an \"editor\" part."
---

# KParts::ReadWritePart Class

Base class for an "editor" part. [More...](#details)

- **Header:** `#include <KParts/ReadWritePart>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Parts)`  
  `target_link_libraries(mytarget PRIVATE KF6::Parts)`
- **Inherits:** [KParts::ReadOnlyPart](kparts-readonlypart.md)

[List of all members, including inherited members](kparts-readwritepart-members.md)

## Public Functions

- [ReadWritePart(QObject \*parent = nullptr, const KPluginMetaData &data = {})](#ReadWritePart)
- [~ReadWritePart()](#dtor.ReadWritePart)
- [bool closeUrl()](#closeUrl)
- [bool closeUrl(bool promptToSave)](#closeUrl-1)
- [bool isModified() const](#isModified)
- [bool isReadWrite() const](#isReadWrite)
- [bool queryClose()](#queryClose)
- [bool saveAs(const QUrl &url)](#saveAs)
- [void setModified(bool modified)](#setModified-1)
- [void setReadWrite(bool readwrite = true)](#setReadWrite)

## Public Slots

- [bool save()](#save)
- [void setModified()](#setModified)
- [bool waitSaveComplete()](#waitSaveComplete)

## Signals

- [void sigQueryClose(bool \*handled, bool \*abortClosing)](#sigQueryClose)

## Protected Functions

- [bool saveFile()](#saveFile)
- [bool saveToUrl()](#saveToUrl)

## Detailed Description {#details}

This class handles network transparency for you. Anything that can open a URL, allow modifications, and save (to the same URL or a different one).

A read-write part can be set to read-only mode, using [setReadWrite](kparts-readwritepart.md#setReadWrite)().

Part writers: Any part inheriting [ReadWritePart](kparts-readwritepart.md) should check [isReadWrite](kparts-readwritepart.md#isReadWrite) before allowing any action that modifies the part. The part probably wants to reimplement [setReadWrite](kparts-readwritepart.md#setReadWrite), disable those actions. Don't forget to call the parent [setReadWrite](kparts-readwritepart.md#setReadWrite).

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ReadWritePart::ReadWritePart(QObject \**parent* = nullptr, const KPluginMetaData &*data* = {}) {#ReadWritePart}

Constructor See parent constructor for instructions.

### \[override virtual noexcept\] ReadWritePart::~ReadWritePart() {#dtor.ReadWritePart}

Destructor Applications using a [ReadWritePart](kparts-readwritepart.md) should make sure, before destroying it, to call [closeUrl](kparts-readwritepart.md#closeUrl)(). In [KMainWindow::queryClose](../kxmlgui/kmainwindow.md#queryClose)(), for instance, they should allow closing only if the return value of [closeUrl](kparts-readwritepart.md#closeUrl)() was true. This allows to cancel.

### \[override virtual\] bool ReadWritePart::closeUrl() {#closeUrl}

Reimplements: [ReadOnlyPart::closeUrl()](kparts-readonlypart.md#closeUrl).

Called when closing the current url (e.g. document), for instance when switching to another url (note that [openUrl](kparts-readonlypart.md#openUrl)() calls it automatically in this case).

If the current URL is not fully loaded yet, aborts loading.

If [isModified](kparts-readwritepart.md#isModified)(), [queryClose](kparts-readwritepart.md#queryClose)() will be called.

Returns false on cancel

### \[virtual\] bool ReadWritePart::closeUrl(bool *promptToSave*) {#closeUrl-1}

Call this method instead of the above if you need control if the save prompt is shown. For example, if you call [queryClose](kparts-readwritepart.md#queryClose)() from [KMainWindow::queryClose](../kxmlgui/kmainwindow.md#queryClose)(), you would not want to prompt again when closing the url.

Equivalent to promptToSave ? [closeUrl](kparts-readwritepart.md#closeUrl)() : [ReadOnlyPart::closeUrl](kparts-readonlypart.md#closeUrl)()

### bool ReadWritePart::isModified() const {#isModified}

Returns true if the document has been modified.

### bool ReadWritePart::isReadWrite() const {#isReadWrite}

Returns true if the part is in read-write mode

### \[virtual\] bool ReadWritePart::queryClose() {#queryClose}

If the document has been modified, ask the user to save changes. This method is meant to be called from [KMainWindow::queryClose](../kxmlgui/kmainwindow.md#queryClose)(). It will also be called from [closeUrl](kparts-readwritepart.md#closeUrl)().

Returns true if [closeUrl](kparts-readwritepart.md#closeUrl)() can be called without the user losing important data, false if the user chooses to cancel.

### \[virtual slot\] bool ReadWritePart::save() {#save}

Save the file in the location from which it was opened. You can connect this to the "save" action. Calls [saveFile](kparts-readwritepart.md#saveFile)() and [saveToUrl](kparts-readwritepart.md#saveToUrl)(), no need to reimplement.

### \[virtual\] bool ReadWritePart::saveAs(const QUrl &*url*) {#saveAs}

Save the file to a new location.

Calls [save](kparts-readwritepart.md#save)(), no need to reimplement

### \[pure virtual protected\] bool ReadWritePart::saveFile() {#saveFile}

Save to a local file. You need to implement it, to save to the local file. The framework takes care of re-uploading afterwards.

Returns true on success, false on failure. On failure the function should inform the user about the problem with an appropriate message box. Standard error messages can be constructed using [KIO::buildErrorString](../kiocore/kio.md#buildErrorString)() in combination with the error codes defined in kio/global.h

### \[virtual protected\] bool ReadWritePart::saveToUrl() {#saveToUrl}

Save the file.

Uploads the file, if `url` is remote. This will emit [started](kparts-readonlypart.md#started)(), and either [completed](kparts-readonlypart.md#completed)() or [canceled](kparts-readonlypart.md#canceled)(), in case you want to provide feedback.

Returns true on success, false on failure.

### \[slot\] void ReadWritePart::setModified() {#setModified}

Call setModified() whenever the contents get modified. This is a slot for convenience, since it simply calls setModified(true), so that you can connect it to a signal, like textChanged().

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         readWritePart, qOverload<>(&ReadWritePart::setModified));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         readWritePart, [receiver = readWritePart]() { receiver->setModified(); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).

*See also* [isModified](kparts-readwritepart.md#isModified)()

### \[virtual\] void ReadWritePart::setModified(bool *modified*) {#setModified-1}

Sets the modified flag of the part.

### \[virtual\] void ReadWritePart::setReadWrite(bool *readwrite* = true) {#setReadWrite}

Changes the behavior of this part to readonly or readwrite.

`readwrite` set to true to enable readwrite mode

*See also* [isReadWrite](kparts-readwritepart.md#isReadWrite)()

### \[signal\] void ReadWritePart::sigQueryClose(bool \**handled*, bool \**abortClosing*) {#sigQueryClose}

set handled to true, if you don't want the default handling set abortClosing to true, if you handled the request, but for any reason don't want to allow closing the document

### \[slot\] bool ReadWritePart::waitSaveComplete() {#waitSaveComplete}

Waits for any pending upload job to finish and returns whether the last [save](kparts-readwritepart.md#save)() action was successful.
