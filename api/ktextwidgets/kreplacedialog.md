---
title: "KReplaceDialog Class"
description: "A generic \"replace\" dialog."
---

# KReplaceDialog Class

A generic "replace" dialog. [More...](#details)

- **Header:** `#include <KReplaceDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextWidgets)`
- **Inherits:** [KFindDialog](kfinddialog.md)

[List of all members, including inherited members](kreplacedialog-members.md)

## Public Types

- [enum KReplaceDialog::Options](#Options-enum)

## Public Functions

- [KReplaceDialog(QWidget \*parent = nullptr, long options = 0, const QStringList &findStrings = QStringList(), const QStringList &replaceStrings = QStringList(), bool hasSelection = true)](#KReplaceDialog)
- [long options() const](#options)
- [QWidget \*replaceExtension() const](#replaceExtension)
- [QString replacement() const](#replacement)
- [QStringList replacementHistory() const](#replacementHistory)
- [void setOptions(long options)](#setOptions)
- [void setReplacementHistory(const QStringList &history)](#setReplacementHistory)

## Detailed Description {#details}

**Detail**:

This widget inherits from [KFindDialog](kfinddialog.md) and implements the following additional functionalities: a replacement string object and an area for a user-defined widget to extend the dialog.

**Example**:

To use the basic replace dialog:

```cpp

```

To use your own extensions:

```cpp

```

## Member Type Documentation {#member-type-documentation}

### enum KReplaceDialog::Options {#Options-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KReplaceDialog::PromptOnReplace` | `256` | Should the user be prompted before the replace operation? |
| `KReplaceDialog::BackReference` | `512` | Use a back reference in the regular expression. |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KReplaceDialog::KReplaceDialog(QWidget \**parent* = nullptr, long *options* = 0, const QStringList &*findStrings* = QStringList(), const QStringList &*replaceStrings* = QStringList(), bool *hasSelection* = true) {#KReplaceDialog}

Construct a replace dialog.read-only or rather select-only combo box with a parent object and a name.

`parent` The parent object of this widget

`options` A bitfield of the Options to be enabled.

`findStrings` A [QStringList](https://doc.qt.io/qt-6/qstringlist.html) to insert in the combo box of text to find

`replaceStrings` A [QStringList](https://doc.qt.io/qt-6/qstringlist.html) to insert in the combo box of text to replace with

`hasSelection` Whether a selection exists

### long KReplaceDialog::options() const {#options}

Returns the state of the options. Disabled options may be returned in an indeterminate state.

*See also* [setOptions](kreplacedialog.md#setOptions)

### QWidget \*KReplaceDialog::replaceExtension() const {#replaceExtension}

Returns an empty widget which the user may fill with additional UI elements as required. The widget occupies the width of the dialog, and is positioned immediately the regular expression support widgets for the replacement string.

### QString KReplaceDialog::replacement() const {#replacement}

Returns the replacement string.

### QStringList KReplaceDialog::replacementHistory() const {#replacementHistory}

Returns the list of history items.

*See also* [setReplacementHistory](kreplacedialog.md#setReplacementHistory)

### void KReplaceDialog::setOptions(long *options*) {#setOptions}

Set the options which are enabled.

`options` The setting of the Options.

*See also* [options](kreplacedialog.md#options)()

### void KReplaceDialog::setReplacementHistory(const QStringList &*history*) {#setReplacementHistory}

Provide the list of strings to be displayed as the `history` of replacement strings. The history might get truncated if it is too long.

*See also* [replacementHistory](kreplacedialog.md#replacementHistory)
