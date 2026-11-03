---
title: "KSyntaxHighlighting::Theme Class"
description: "Color theme definition used for highlighting."
---

# KSyntaxHighlighting::Theme Class

Color theme definition used for highlighting. [More...](#details)

- **Header:** `#include <KSyntaxHighlighting/Theme>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KSyntaxHighlighting)`  
  `target_link_libraries(mytarget PRIVATE KF6::KSyntaxHighlighting)`

[List of all members, including inherited members](ksyntaxhighlighting-theme-members.md)

## Public Types

- [enum Theme::EditorColorRole](#EditorColorRole-enum)
- [enum Theme::TextStyle](#TextStyle-enum)

## Properties

- [\[read-only\] name : QString](#name-prop)
- [\[read-only\] translatedName : QString](#translatedName-prop)

## Public Functions

- [Theme()](#Theme)
- [Theme(const KSyntaxHighlighting::Theme &copy)](#Theme-2)
- [QRgb backgroundColor(KSyntaxHighlighting::Theme::TextStyle style) const](#backgroundColor)
- [QRgb editorColor(KSyntaxHighlighting::Theme::EditorColorRole role) const](#editorColor)
- [QString filePath() const](#filePath)
- [bool isBold(KSyntaxHighlighting::Theme::TextStyle style) const](#isBold)
- [bool isItalic(KSyntaxHighlighting::Theme::TextStyle style) const](#isItalic)
- [bool isReadOnly() const](#isReadOnly)
- [bool isStrikeThrough(KSyntaxHighlighting::Theme::TextStyle style) const](#isStrikeThrough)
- [bool isUnderline(KSyntaxHighlighting::Theme::TextStyle style) const](#isUnderline)
- [bool isValid() const](#isValid)
- [QString name() const](#name)
- [QIcon previewIcon() const](#previewIcon) (since 6.28)
- [QRgb selectedBackgroundColor(KSyntaxHighlighting::Theme::TextStyle style) const](#selectedBackgroundColor)
- [QRgb selectedTextColor(KSyntaxHighlighting::Theme::TextStyle style) const](#selectedTextColor)
- [QRgb textColor(KSyntaxHighlighting::Theme::TextStyle style) const](#textColor)
- [QString translatedName() const](#translatedName)
- [KSyntaxHighlighting::Theme &Theme::operator=(const KSyntaxHighlighting::Theme &other)](#operator-eq)

## Detailed Description {#details}

The Theme provides a full color theme for painting the highlighted text. One Theme is defined either as a \*.theme file on disk, or as a file compiled into the SyntaxHighlighting library by using Qt's resource system. Each Theme has a unique [name](ksyntaxhighlighting-theme.md#name)(), including a [translatedName](ksyntaxhighlighting-theme.md#translatedName)() if put into the UI. Themes shipped by default are typically read-only, see [isReadOnly](ksyntaxhighlighting-theme.md#isReadOnly)().

A Theme defines two sets of colors:

- Text colors, including foreground and background colors, colors for selected text, and properties such as bold and italic. These colors are used e.g. by the [SyntaxHighlighter](ksyntaxhighlighting-syntaxhighlighter.md).
- Editor colors, including a background color for the entire editor widget, the line number color, code folding colors, etc.

### Text Colors and the Class Format {#text-colors-and-the-class-format}

The text colors are used for syntax highlighting. // TODO: elaborate more and explain relation to Format class

### theme\_editor\_colors Editor Colors {#theme-editor-colors-editor-colors}

If you want to use the SyntaxHighlighting framework to write your own text editor, you also need to paint the background of the editing widget. In addition, the editor may support showing line numbers, a folding bar, a highlight for the current text line, and similar features. All these colors are defined in terms of the "editor colors" and accessible by calling [editorColor](ksyntaxhighlighting-theme.md#editorColor)() with the desired enum [EditorColorRole](ksyntaxhighlighting-theme.md#EditorColorRole-enum).

### Accessing a Theme {#accessing-a-theme}

All available Theme%s are accessed through the Repository. These themes are typically valid themes. If you create a Theme on your own, [isValid](ksyntaxhighlighting-theme.md#isValid)() will return `false`, and all colors provided by this Theme are in fact invalid and therefore unusable.

*See also* [Format](ksyntaxhighlighting-format.md)

## Member Type Documentation {#member-type-documentation}

### enum Theme::EditorColorRole {#EditorColorRole-enum}

Editor color roles, used to paint line numbers, editor background etc. The colors typically should have good contrast with the colors used in the [TextStyle](ksyntaxhighlighting-theme.md#TextStyle-enum)%s.

| Constant | Value | Description |
| --- | --- | --- |
| `KSyntaxHighlighting::Theme::BackgroundColor` | `0` | Background color for the editing area. |
| `KSyntaxHighlighting::Theme::TextSelection` | `1` | Background color for selected text. |
| `KSyntaxHighlighting::Theme::CurrentLine` | `2` | Background color for the line of the current text cursor. |
| `KSyntaxHighlighting::Theme::SearchHighlight` | `3` | Background color for matching text while searching. |
| `KSyntaxHighlighting::Theme::ReplaceHighlight` | `4` | Background color for replaced text for a search & replace action. |
| `KSyntaxHighlighting::Theme::BracketMatching` | `5` | Background color for matching bracket pairs (including quotes). |
| `KSyntaxHighlighting::Theme::TabMarker` | `6` | Foreground color for visualizing tabs and trailing spaces. |
| `KSyntaxHighlighting::Theme::SpellChecking` | `7` | Color used to underline spell check errors. |
| `KSyntaxHighlighting::Theme::IndentationLine` | `8` | Color used to draw vertical indentation levels, typically a line. |
| `KSyntaxHighlighting::Theme::IconBorder` | `9` | Background color for the icon border. |
| `KSyntaxHighlighting::Theme::CodeFolding` | `10` | Background colors for code folding regions in the text area, as well as code folding indicators in the code folding border. |
| `KSyntaxHighlighting::Theme::LineNumbers` | `11` | Foreground color for drawing the line numbers. This should have a good contrast with the IconBorder background color. |
| `KSyntaxHighlighting::Theme::CurrentLineNumber` | `12` | Foreground color for drawing the current line number. This should have a good contrast with the IconBorder background color. |
| `KSyntaxHighlighting::Theme::WordWrapMarker` | `13` | Color used in the icon border to indicate dynamically wrapped lines. This color should have a good contrast with the IconBorder background color. |
| `KSyntaxHighlighting::Theme::ModifiedLines` | `14` | Color used to draw a vertical line for marking changed lines. |
| `KSyntaxHighlighting::Theme::SavedLines` | `15` | Color used to draw a vertical line for marking saved lines. |
| `KSyntaxHighlighting::Theme::Separator` | `16` | Line color used to draw separator lines, e.g. at column 80 in the text editor area. |
| `KSyntaxHighlighting::Theme::MarkBookmark` | `17` | Background color for bookmarks. |
| `KSyntaxHighlighting::Theme::MarkBreakpointActive` | `18` | Background color for active breakpoints. |
| `KSyntaxHighlighting::Theme::MarkBreakpointReached` | `19` | Background color for a reached breakpoint. |
| `KSyntaxHighlighting::Theme::MarkBreakpointDisabled` | `20` | Background color for inactive (disabled) breakpoints. |
| `KSyntaxHighlighting::Theme::MarkExecution` | `21` | Background color for marking the current execution position. |
| `KSyntaxHighlighting::Theme::MarkWarning` | `22` | Background color for general warning marks. |
| `KSyntaxHighlighting::Theme::MarkError` | `23` | Background color for general error marks. |
| `KSyntaxHighlighting::Theme::TemplateBackground` | `24` | Background color for text templates (snippets). |
| `KSyntaxHighlighting::Theme::TemplatePlaceholder` | `25` | Background color for all editable placeholders in text templates. |
| `KSyntaxHighlighting::Theme::TemplateFocusedPlaceholder` | `26` | Background color for the currently active placeholder in text templates. |
| `KSyntaxHighlighting::Theme::TemplateReadOnlyPlaceholder` | `27` | Background color for read-only placeholders in text templates. |

### enum Theme::TextStyle {#TextStyle-enum}

Default styles that can be referenced from syntax definition XML files. Make sure to choose readable colors with good contrast especially in combination with the [EditorColorRole](ksyntaxhighlighting-theme.md#EditorColorRole-enum)%s.

| Constant | Value | Description |
| --- | --- | --- |
| `KSyntaxHighlighting::Theme::Normal` | `0` | Default text style for normal text and source code without special highlighting. |
| `KSyntaxHighlighting::Theme::Keyword` | `1` | Text style for language keywords. |
| `KSyntaxHighlighting::Theme::Function` | `2` | Text style for function definitions and function calls. |
| `KSyntaxHighlighting::Theme::Variable` | `3` | Text style for variables, if applicable. For instance, variables in PHP typically start with a '$', so all identifiers following the pattern $foo are highlighted as variable. |
| `KSyntaxHighlighting::Theme::ControlFlow` | `4` | Text style for control flow highlighting, such as if, then, else, return, or continue. |
| `KSyntaxHighlighting::Theme::Operator` | `5` | Text style for operators such as +, -, \*, / and :: etc. |
| `KSyntaxHighlighting::Theme::BuiltIn` | `6` | Text style for built-in language classes and functions. |
| `KSyntaxHighlighting::Theme::Extension` | `7` | Text style for well-known extensions, such as Qt or boost. |
| `KSyntaxHighlighting::Theme::Preprocessor` | `8` | Text style for preprocessor statements. |
| `KSyntaxHighlighting::Theme::Attribute` | `9` | Text style for attributes of functions or objects, e.g. @override in Java, or \_\_declspec(...) and \_\_attribute\_\_((...)) in C++. |
| `KSyntaxHighlighting::Theme::Char` | `10` | Text style for single characters such as 'a'. |
| `KSyntaxHighlighting::Theme::SpecialChar` | `11` | Text style for escaped characters in strings, such as "hello\\n". |
| `KSyntaxHighlighting::Theme::String` | `12` | Text style for strings, for instance "hello world". |
| `KSyntaxHighlighting::Theme::VerbatimString` | `13` | Text style for verbatim strings such as HERE docs. |
| `KSyntaxHighlighting::Theme::SpecialString` | `14` | Text style for special strings such as regular expressions in ECMAScript or the LaTeX math mode. |
| `KSyntaxHighlighting::Theme::Import` | `15` | Text style for includes, imports, modules, or LaTeX packages. |
| `KSyntaxHighlighting::Theme::DataType` | `16` | Text style for data types such as int, char, float etc. |
| `KSyntaxHighlighting::Theme::DecVal` | `17` | Text style for decimal values. |
| `KSyntaxHighlighting::Theme::BaseN` | `18` | Text style for numbers with base other than 10. |
| `KSyntaxHighlighting::Theme::Float` | `19` | Text style for floating point numbers. |
| `KSyntaxHighlighting::Theme::Constant` | `20` | Text style for language constants, e.g. True, False, None in Python or nullptr in C/C++. |
| `KSyntaxHighlighting::Theme::Comment` | `21` | Text style for normal comments. |
| `KSyntaxHighlighting::Theme::Documentation` | `22` | Text style for comments that reflect API documentation, such as doxygen comments. |
| `KSyntaxHighlighting::Theme::Annotation` | `23` | Text style for annotations in comments, such as `in` Doxygen or JavaDoc. |
| `KSyntaxHighlighting::Theme::CommentVar` | `24` | Text style that refers to variables in a comment, such as after `<identifier>` in Doxygen or JavaDoc. |
| `KSyntaxHighlighting::Theme::RegionMarker` | `25` | Text style for region markers, typically defined by BEGIN/END. |
| `KSyntaxHighlighting::Theme::Information` | `26` | Text style for information, such as the keyword \\note in Doxygen. |
| `KSyntaxHighlighting::Theme::Warning` | `27` | Text style for warnings, such as the keyword \\warning in Doxygen. |
| `KSyntaxHighlighting::Theme::Alert` | `28` | Text style for comment specials such as TODO and WARNING in comments. |
| `KSyntaxHighlighting::Theme::Error` | `29` | Text style indicating wrong syntax. |
| `KSyntaxHighlighting::Theme::Others` | `30` | Text style for attributes that do not match any of the other default styles. |

## Property Documentation {#property-documentation}

### \[read-only\] name : QString {#name-prop}

**Access functions:**

- `QString` **[name](ksyntaxhighlighting-theme.md#name)**() const

### \[read-only\] translatedName : QString {#translatedName-prop}

**Access functions:**

- `QString` **[translatedName](ksyntaxhighlighting-theme.md#translatedName)**() const

## Member Function Documentation {#member-function-documentation}

### Theme::Theme() {#Theme}

Default constructor, creating an invalid Theme, see [isValid](ksyntaxhighlighting-theme.md#isValid)().

### Theme::Theme(const KSyntaxHighlighting::Theme &*copy*) {#Theme-2}

Copy constructor, sharing the Theme data with `copy`.

### QRgb Theme::backgroundColor(KSyntaxHighlighting::Theme::TextStyle *style*) const {#backgroundColor}

Returns the background color to be used for `style`. `0` is returned for styles that do not specify a background color, use the default background color in that case.

### QRgb Theme::editorColor(KSyntaxHighlighting::Theme::EditorColorRole *role*) const {#editorColor}

Returns the editor color for the requested `role`.

### QString Theme::filePath() const {#filePath}

Returns the full path and file name to this Theme. Themes from the Qt resource return the Qt resource path. Themes from disk return the local path.

If the theme is invalid ([isValid](ksyntaxhighlighting-theme.md#isValid)()), an empty string is returned.

### bool Theme::isBold(KSyntaxHighlighting::Theme::TextStyle *style*) const {#isBold}

Returns whether the given style should be shown in bold.

### bool Theme::isItalic(KSyntaxHighlighting::Theme::TextStyle *style*) const {#isItalic}

Returns whether the given style should be shown in italic.

### bool Theme::isReadOnly() const {#isReadOnly}

Returns `true` if this Theme is read-only.

A Theme is read-only, if the [filePath](ksyntaxhighlighting-theme.md#filePath)() points to a non-writable file. This is typically the case for Themes that are compiled into the executable as resource file, as well as for theme files that are installed in read-only system locations (e.g. /usr/share/).

### bool Theme::isStrikeThrough(KSyntaxHighlighting::Theme::TextStyle *style*) const {#isStrikeThrough}

Returns whether the given style should be shown struck through.

### bool Theme::isUnderline(KSyntaxHighlighting::Theme::TextStyle *style*) const {#isUnderline}

Returns whether the given style should be shown underlined.

### bool Theme::isValid() const {#isValid}

Returns `true` if this is a valid Theme. If the theme is invalid, none of the returned colors are well-defined.

### QString Theme::name() const {#name}

Returns the unique name of this Theme.

> **Note:** Getter function for property [name](ksyntaxhighlighting-theme.md#name-prop).

*See also* [translatedName](ksyntaxhighlighting-theme.md#translatedName)()

### \[since 6.28\] QIcon Theme::previewIcon() const {#previewIcon}

Returns a preview icon for the theme.

This can be used in a theme selection list to give the user an impression of the general look and feel for the theme.

This function was introduced in Qt 6.28.

### QRgb Theme::selectedBackgroundColor(KSyntaxHighlighting::Theme::TextStyle *style*) const {#selectedBackgroundColor}

Returns the background color to be used for selected text for `style`. `0` is returned for styles that do not specify a background color, use the default [backgroundColor](ksyntaxhighlighting-theme.md#backgroundColor)() in that case.

### QRgb Theme::selectedTextColor(KSyntaxHighlighting::Theme::TextStyle *style*) const {#selectedTextColor}

Returns the selected text color to be used for `style`. `0` is returned for styles that do not specify a selected text color, use the default [textColor](ksyntaxhighlighting-theme.md#textColor)() in that case.

### QRgb Theme::textColor(KSyntaxHighlighting::Theme::TextStyle *style*) const {#textColor}

Returns the text color to be used for `style`. `0` is returned for styles that do not specify a text color, use the default text color in that case.

### QString Theme::translatedName() const {#translatedName}

Returns the translated name of this Theme. The translated name can be used in the user interface.

> **Note:** Getter function for property [translatedName](ksyntaxhighlighting-theme.md#translatedName-prop).

### KSyntaxHighlighting::Theme &Theme::operator=(const KSyntaxHighlighting::Theme &*other*) {#operator-eq}

Assignment operator, sharing the Theme data with `other`.
