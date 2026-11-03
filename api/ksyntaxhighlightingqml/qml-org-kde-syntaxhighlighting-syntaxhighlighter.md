---
title: "SyntaxHighlighter QML Type"
description: "Add syntax highlighting to QML text fields."
---

# SyntaxHighlighter QML Type

Add syntax highlighting to QML text fields. [More...](#details)

- Import Statement: import org.kde.syntaxhighlighting

## Detailed Description {#details}

Syntax highlighting may be added to a text field by specifying a [textEdit](qml-org-kde-syntaxhighlighting-syntaxhighlighter.md#textEdit-prop) id and a [definition](qml-org-kde-syntaxhighlighting-syntaxhighlighter.md#definition-prop).

The list of available definitions can be seen on the [Kate website](https://kate-editor.org/syntax/).

You can learn more about syntax highlighting definitions on the [syntax-highlighting repository](https://invent.kde.org/frameworks/syntax-highlighting).

A custom [repository](qml-org-kde-syntaxhighlighting-syntaxhighlighter.md#repository-prop) containing syntax highlighting definitions may be set. See [KSyntaxHighlighting::Repository](../ksyntaxhighlighting/ksyntaxhighlighting-repository.md) for details.

A custom [theme](qml-org-kde-syntaxhighlighting-syntaxhighlighter.md#theme-prop) for the highlighting definitions may be set. The list of available themes can be seen on the [repository's data/themes/ folder](https://invent.kde.org/frameworks/syntax-highlighting/-/tree/master/data/themes). The name to be used should match the name specified in the JSON metadata, and is case sensitive. For example:

```cpp
{
  "metadata": {
    "name": "GitHub Dark"
  }
}
```

Basic usage:

```qml
import org.kde.syntaxhighlighting

// ...

SyntaxHighlighter {
    textEdit: sourceTextArea
    definition: "INI Files"
    theme: Repository.theme("GitHub Dark")
}
```

For more complex uses, the syntax definition might not be fixed but depend on input data (for example, derived from its mimetype or file name), or a user selection. In the C++ API this is enabled by the [KSyntaxHighlighting::Repository](../ksyntaxhighlighting/ksyntaxhighlighting-repository.md) class, which is available in QML as a singleton object.

The following example shows how to use this for a simple syntax selection combobox:

```qml
ComboBox {
   model: Repository.definitions
   displayText: currentValue.translatedName + " (" + currentValue.translatedSection + ")"
   textRole: "translatedName"
   onCurrentIndexChanged: myHighlighter.definition = currentValue
}
```

Handling color themes is also possible, similarly to syntax definitions. Themes can be listed, their properties can be accessed and they can be set by theme object or name on the highlighter. Like in the C++ API it's also possible to just ask for the light or dark default theme.

More examples can be seen in the [repository's examples/ folder](https://invent.kde.org/frameworks/syntax-highlighting/-/tree/master/examples).

## Property Documentation {#property-documentation}

### definition : variant {#definition-prop}

The syntax highlighting definition to be used.

*See also* [Available Syntax Highlighting language names](https://kate-editor.org/syntax/)

### repository : Repository {#repository-prop}

The repository from where syntax highlighting definitions will be pulled.

Defaults to the default repository provided by the [KSyntaxHighlighting](../ksyntaxhighlighting/ksyntaxhighlighting-module.md) framework.

The selected repository can be accessed via the Repository singleton, which exposes the API from [KSyntaxHighlighting::Repository](../ksyntaxhighlighting/ksyntaxhighlighting-repository.md).

The most commonly accessed API is:

- Repository.definitions
- Repository.definition
- Repository.definitionForName()
- Repository.definitionForFileName()
- Repository.themes
- Repository.theme
- Repository.defaultTheme()
- Repository.DefaultTheme

*See also* [QML Example](https://invent.kde.org/frameworks/syntax-highlighting/-/blob/master/examples/qml/example.qml)

### textEdit : QtObject {#textEdit-prop}

The id of the text edit component that will have syntax highlighting.

### theme : variant {#theme-prop}

The theme to be used for the syntax highlighting.

The theme name to be used should match the name specified in the JSON metadata, and is case sensitive.

The Repository singleton exposes the API from [KSyntaxHighlighting::Repository](../ksyntaxhighlighting/ksyntaxhighlighting-repository.md) that is necessary to manage themes in your application:

- Repository.themes
- Repository.theme
- Repository.defaultTheme()
- Repository.DefaultTheme
