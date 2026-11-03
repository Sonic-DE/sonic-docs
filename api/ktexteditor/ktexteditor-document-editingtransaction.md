---
title: "KTextEditor::Document::EditingTransaction Class"
description: "Editing transaction support."
---

# KTextEditor::Document::EditingTransaction Class

Editing transaction support. [More...](#details)

- **Header:** `#include <EditingTransaction>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextEditor)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextEditor)`

[List of all members, including inherited members](ktexteditor-document-editingtransaction-members.md)

## Public Functions

- [EditingTransaction(KTextEditor::Document \*document)](#EditingTransaction)
- [EditingTransaction(const KTextEditor::Document::EditingTransaction &)](#EditingTransaction-1)
- [~EditingTransaction()](#dtor.EditingTransaction)
- [void finish()](#finish)
- [void start()](#start)
- [KTextEditor::Document::EditingTransaction &EditingTransaction::operator=(const KTextEditor::Document::EditingTransaction &)](#operator-eq)

## Detailed Description {#details}

Edit commands during this sequence will be bunched together so that they represent a single undo command in the editor, and so that repaint events do not occur in between.

Your application should *not* return control to the event loop while it has an unterminated (i.e. this object is not destructed) editing sequence (result undefined) - so do all of your work in one go!

Using this class typically looks as follows:

```cpp
void foo() {
    KTextEditor::Document::EditingTransaction transaction(document);
    // now call editing functions
    document->removeText(...)
    document->insertText(...)
}
```

Although usually not required, the [EditingTransaction](ktexteditor-document-editingtransaction.md) additionally allows to manually call [finish](ktexteditor-document-editingtransaction.md#finish)() and [start](ktexteditor-document-editingtransaction.md#start)() in between.

*See also* [editingStarted](ktexteditor-document.md#editingStarted)(), [editingFinished](ktexteditor-document.md#editingFinished)()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] EditingTransaction::EditingTransaction(KTextEditor::Document \**document*) {#EditingTransaction}

Constructs the object and starts an editing transaction by calling [start](ktexteditor-document-editingtransaction.md#start)().

`document` document for the transaction

*See also* [start](ktexteditor-document-editingtransaction.md#start)()

### EditingTransaction::EditingTransaction(*const KTextEditor::Document::EditingTransaction &*) {#EditingTransaction-1}

No copy constructor, don't allow this to be copied.

### \[noexcept\] EditingTransaction::~EditingTransaction() {#dtor.EditingTransaction}

Destructs the object and, if needed, finishes a running editing transaction by calling [finish](ktexteditor-document-editingtransaction.md#finish)().

*See also* [finish](ktexteditor-document-editingtransaction.md#finish)()

### void EditingTransaction::finish() {#finish}

By calling finish(), the editing transaction can be finished already before destruction of this instance.

*See also* [start](ktexteditor-document-editingtransaction.md#start)()

### void EditingTransaction::start() {#start}

By calling start(), the editing transaction can be started again. This function only is of use in combination with [finish](ktexteditor-document-editingtransaction.md#finish)().

*See also* [finish](ktexteditor-document-editingtransaction.md#finish)()

### KTextEditor::Document::EditingTransaction &EditingTransaction::operator=(*const KTextEditor::Document::EditingTransaction &*) {#operator-eq}

No assignment operator, no copying around editing transactions.
