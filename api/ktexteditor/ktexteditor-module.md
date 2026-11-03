---
title: "KTextEditor C++ Classes"
description: "KTextEditor is a full text editor component."
---

# KTextEditor C++ Classes

[KTextEditor](ktexteditor-module.md) is a full text editor component. [More...](#details)

## Namespaces {#namespaces}

- [KTextEditor](ktexteditor.md)

## Classes {#classes}

- [KTextEditor::Application](ktexteditor-application.md): This class allows the application that embeds the KTextEditor component to allow it access to application wide information and interactions.
- [KTextEditor::Attribute](ktexteditor-attribute.md): A class which provides customized text decorations.
- [KTextEditor::CodeCompletionModel](ktexteditor-codecompletionmodel.md): An item model for providing code completion, and meta information for enhanced presentation.
- [KTextEditor::CodeCompletionModelControllerInterface](ktexteditor-codecompletionmodelcontrollerinterface.md): Controller interface for a CodeCompletionModel instance.
- [KTextEditor::Command](ktexteditor-command.md): An Editor command line command.
- [KTextEditor::ConfigPage](ktexteditor-configpage.md): Config page interface for the Editor and Plugin%s.
- [KTextEditor::Cursor](ktexteditor-cursor.md): The Cursor represents a position in a Document.
- [KTextEditor::Document](ktexteditor-document.md): A KParts derived class representing a text document.
- [KTextEditor::Document::EditingTransaction](ktexteditor-document-editingtransaction.md): Editing transaction support.
- [KTextEditor::DocumentCursor](ktexteditor-documentcursor.md): A Cursor which is bound to a specific Document.
- [KTextEditor::Editor](ktexteditor-editor.md): Accessor interface for the KTextEditor framework.
- [KTextEditor::LineRange](ktexteditor-linerange.md): An object representing lines from a start line to an end line.
- [KTextEditor::MainWindow](ktexteditor-mainwindow.md): This class allows the application that embeds the KTextEditor component to allow it to access parts of its main window.
- [KTextEditor::Message](ktexteditor-message.md): This class holds a Message to display in Views.
- [KTextEditor::MovingCursor](ktexteditor-movingcursor.md): A Cursor which is bound to a specific Document, and maintains its position.
- [KTextEditor::MovingRange](ktexteditor-movingrange.md): A range that is bound to a specific Document, and maintains its position.
- [KTextEditor::MovingRangeFeedback](ktexteditor-movingrangefeedback.md): A class which provides notifications of state changes to a MovingRange.
- [KTextEditor::Range](ktexteditor-range.md): An object representing a section of text, from one Cursor to another.
- [KTextEditor::View](ktexteditor-view.md): A text widget with KXMLGUIClient that represents a Document.

## Detailed Description {#details}

[KTextEditor](ktexteditor-module.md) provides a powerful text editor component that you can embed in your application, either as a KPart or using the KF6::TextEditor library (if you need more control).

The text editor component contains many useful features, from syntax highlighting and automatic indentation to advanced scripting support, making it suitable for everything from a simple embedded text-file editor to an advanced IDE.
