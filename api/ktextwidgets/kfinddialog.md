---
title: "KFindDialog Class"
description: "A generic \"find\" dialog."
---

# KFindDialog Class

A generic "find" dialog. [More...](#details)

- **Header:** `#include <KFindDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextWidgets)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)
- **Inherited By:** [KReplaceDialog](kreplacedialog.md)

[List of all members, including inherited members](kfinddialog-members.md)

## Public Functions

- [KFindDialog(QWidget \*parent = nullptr, long options = 0, const QStringList &findStrings = QStringList(), bool hasSelection = false, bool replaceDialog = false)](#KFindDialog)
- [~KFindDialog()](#dtor.KFindDialog)
- [QWidget \*findExtension() const](#findExtension)
- [QStringList findHistory() const](#findHistory)
- [long options() const](#options)
- [QString pattern() const](#pattern)
- [void setFindHistory(const QStringList &history)](#setFindHistory)
- [void setHasCursor(bool hasCursor)](#setHasCursor)
- [void setHasSelection(bool hasSelection)](#setHasSelection)
- [void setOptions(long options)](#setOptions)
- [void setPattern(const QString &pattern)](#setPattern)
- [void setSupportsBackwardsFind(bool supports)](#setSupportsBackwardsFind)
- [void setSupportsCaseSensitiveFind(bool supports)](#setSupportsCaseSensitiveFind)
- [void setSupportsRegularExpressionFind(bool supports)](#setSupportsRegularExpressionFind)
- [void setSupportsWholeWordsFind(bool supports)](#setSupportsWholeWordsFind)

## Signals

- [void cancelClicked()](#cancelClicked)
- [void okClicked()](#okClicked)
- [void optionsChanged()](#optionsChanged)

## Detailed Description {#details}

**Detail**:

This widget inherits from KDialog and implements the following additional functionalities: a find string object and an area for a user-defined widget to extend the dialog.

**Example**:

To use the basic modal find dialog, and then run the search:

```cpp
KFindDialog dlg(....)
if (dlg.exec() != QDialog::Accepted)
    return;

// proceed with KFind from here
```

To create a non-modal find dialog:

```cpp
if (m_findDialog) {
  m_findDialog->activateWindow();
} else {
  m_findDialog = new KFindDialog(...);
  connect(m_findDialog, &KFindDialog::okClicked, this, [this] {
      m_findDialog->close();
      delete m_find;
      m_find = new KFind(m_findDialog->pattern(), m_findDialog->options(), this);
      // ... see KFind documentation for what else should be done here
  });
}
```

Don't forget to delete and reset m\_findDialog when closed. (But do NOT delete your [KFind](kfind.md) object at that point, it's needed for "Find Next".)

To use your own extensions: see [findExtension](kfinddialog.md#findExtension)().

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KFindDialog::KFindDialog(QWidget \**parent* = nullptr, long *options* = 0, const QStringList &*findStrings* = QStringList(), bool *hasSelection* = false, bool *replaceDialog* = false) {#KFindDialog}

Construct a modal find dialog

`parent` The parent object of this widget.

`options` A bitfield of the Options to be checked.

`findStrings` The find history, see [findHistory](kfinddialog.md#findHistory)()

`hasSelection` Whether a selection exists

### \[override virtual noexcept\] KFindDialog::~KFindDialog() {#dtor.KFindDialog}

Destructor.

### \[signal\] void KFindDialog::cancelClicked() {#cancelClicked}

This signal is sent when the user clicks on Cancel button.

### QWidget \*KFindDialog::findExtension() const {#findExtension}

Returns an empty widget which the user may fill with additional UI elements as required. The widget occupies the width of the dialog, and is positioned immediately below the regular expression support widgets for the pattern string.

### QStringList KFindDialog::findHistory() const {#findHistory}

Returns the list of history items.

*See also* [setFindHistory](kfinddialog.md#setFindHistory)

### \[signal\] void KFindDialog::okClicked() {#okClicked}

This signal is sent when the user clicks on Ok button.

### long KFindDialog::options() const {#options}

Returns the state of the options. Disabled options may be returned in an indeterminate state.

*See also* [setOptions](kfinddialog.md#setOptions)(), [KFind::Options](kfind.md#Options-enum)

### \[signal\] void KFindDialog::optionsChanged() {#optionsChanged}

This signal is sent whenever one of the option checkboxes is toggled. Call [options](kfinddialog.md#options)() to get the new state of the checkboxes.

### QString KFindDialog::pattern() const {#pattern}

Returns the pattern to find.

*See also* [setPattern](kfinddialog.md#setPattern)()

### void KFindDialog::setFindHistory(const QStringList &*history*) {#setFindHistory}

Provide the list of strings to be displayed as the history of find strings. The `history` might get truncated if it is too long.

*See also* [findHistory](kfinddialog.md#findHistory)

### void KFindDialog::setHasCursor(bool *hasCursor*) {#setHasCursor}

Hide/show the 'from cursor' option, depending on whether the application implements a cursor.

`hasCursor` true if the application features a cursor. This is assumed to be the case by default.

### void KFindDialog::setHasSelection(bool *hasSelection*) {#setHasSelection}

Enable/disable the 'search in selection' option, depending on whether there actually is a selection.

`hasSelection` true if a selection exists

### void KFindDialog::setOptions(long *options*) {#setOptions}

Set the options which are checked.

`options` The setting of the Options.

*See also* [options](kfinddialog.md#options)(), [KFind::Options](kfind.md#Options-enum)

### void KFindDialog::setPattern(const QString &*pattern*) {#setPattern}

Sets the `pattern` to find.

*See also* [pattern](kfinddialog.md#pattern)()

### void KFindDialog::setSupportsBackwardsFind(bool *supports*) {#setSupportsBackwardsFind}

Enable/disable the 'Find backwards' option, depending on whether the application supports it.

`supports` true if the application supports backwards find. This is assumed to be the case by default.

### void KFindDialog::setSupportsCaseSensitiveFind(bool *supports*) {#setSupportsCaseSensitiveFind}

Enable/disable the 'Case sensitive' option, depending on whether the application supports it.

`supports` true if the application supports case sensitive find. This is assumed to be the case by default.

### void KFindDialog::setSupportsRegularExpressionFind(bool *supports*) {#setSupportsRegularExpressionFind}

Enable/disable the 'Regular expression' option, depending on whether the application supports it.

`supports` true if the application supports regular expression find. This is assumed to be the case by default.

### void KFindDialog::setSupportsWholeWordsFind(bool *supports*) {#setSupportsWholeWordsFind}

Enable/disable the 'Whole words only' option, depending on whether the application supports it.

`supports` true if the application supports whole words only find. This is assumed to be the case by default.
