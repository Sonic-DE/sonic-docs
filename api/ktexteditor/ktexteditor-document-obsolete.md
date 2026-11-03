---
title: "Obsolete Members for KTextEditor::Document"
description: "Deprecated members of KTextEditor::Document."
parent: "ktexteditor/ktexteditor-document"
---

# Obsolete Members for KTextEditor::Document

**The following members of class [Document](ktexteditor-document.md) are deprecated.** We strongly advise against using them in new code.

## Signals

- [void aboutToDeleteMovingInterfaceContent(KTextEditor::Document \*document)](#aboutToDeleteMovingInterfaceContent) (deprecated in 6.0)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[signal, deprecated in 6.0\] void Document::aboutToDeleteMovingInterfaceContent(KTextEditor::Document \**document*) {#aboutToDeleteMovingInterfaceContent}

This function is deprecated since 6.0. We strongly advise against using it in new code.

This signal is emitted before the cursors/ranges/revisions of a document are destroyed as the document is deleted.

`document` the document which the interface belongs to which is in the process of being deleted

Not emitted any more. Ownership of the moving interface belongs to the user.
