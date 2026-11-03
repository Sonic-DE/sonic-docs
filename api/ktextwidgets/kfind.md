---
title: "KFind Class"
description: "A generic implementation of the \"find\" function."
---

# KFind Class

A generic implementation of the "find" function. [More...](#details)

- **Header:** `#include <KFind>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextWidgets)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)
- **Inherited By:** [KReplace](kreplace.md)

[List of all members, including inherited members](kfind-members.md)

## Public Types

- [enum KFind::Options](#Options-enum)
- [enum KFind::Result](#Result-enum)

## Public Functions

- [KFind(const QString &pattern, long options, QWidget \*parent)](#KFind)
- [KFind(const QString &pattern, long options, QWidget \*parent, QWidget \*findDialog)](#KFind-1)
- [void closeFindNextDialog()](#closeFindNextDialog)
- [void displayFinalDialog() const](#displayFinalDialog)
- [KFind::Result find()](#find)
- [QDialog \*findNextDialog(bool create = false)](#findNextDialog)
- [int index() const](#index)
- [bool needData() const](#needData)
- [int numMatches() const](#numMatches)
- [long options() const](#options)
- [QString pattern() const](#pattern)
- [void resetCounts()](#resetCounts)
- [void setData(const QString &data, int startPos = -1)](#setData)
- [void setData(int id, const QString &data, int startPos = -1)](#setData-1)
- [void setOptions(long options)](#setOptions)
- [void setPattern(const QString &pattern)](#setPattern)
- [bool shouldRestart(bool forceAsking = false, bool showNumMatches = true) const](#shouldRestart)
- [bool validateMatch(const QString &text, int index, int matchedlength)](#validateMatch)

## Signals

- [void dialogClosed()](#dialogClosed)
- [void optionsChanged()](#optionsChanged)
- [void textFound(const QString &text, int matchingIndex, int matchedLength)](#textFound)
- [void textFoundAtId(int id, int matchingIndex, int matchedLength)](#textFoundAtId)

## Static Public Members

- [int find(const QString &text, const QString &pattern, int index, long options, int \*matchedLength, QRegularExpressionMatch \*rmatch)](#find-1)

## Detailed Description {#details}

**Detail**:

This class includes prompt handling etc. Also provides some static functions which can be used to create custom behavior instead of using the class directly.

**Example**:

To use the class to implement a complete find feature:

In the slot connected to the find action, after using [KFindDialog](kfinddialog.md):

```cpp
// This creates a find-next-prompt dialog if needed.
m_find = new KFind(pattern, options, this);

// Connect textFound() signal to code which handles highlighting of found text.
connect(m_find, &KFind::textFound, this, [this](const QString &text, int matchingIndex, int matchedLength) {
    slotHighlight(text, matchingIndex, matchedLength);
}));
// Connect findNext signal - called when pressing the button in the dialog
connect(m_find, SIGNAL(findNext()),
        this, SLOT(slotFindNext()));
```

Then initialize the variables determining the "current position" (to the cursor, if the option [FromCursor](kfind.md#Options-enum) is set, to the beginning of the selection if the option [SelectedText](kfind.md#Options-enum) is set, and to the beginning of the document otherwise). Initialize the "end of search" variables as well (end of doc or end of selection). Swap begin and end if [FindBackwards](kfind.md#Options-enum). Finally, call slotFindNext();

```cpp
void slotFindNext()
{
    KFind::Result res = KFind::NoMatch;
    while (res == KFind::NoMatch && <position not at end>) {
        if (m_find->needData())
            m_find->setData(<current text fragment>);

        // Let KFind inspect the text fragment, and display a dialog if a match is found
        res = m_find->find();

        if (res == KFind::NoMatch) {
            <Move to the next text fragment, honoring the FindBackwards setting for the direction>
        }
    }

    if (res == KFind::NoMatch) // i.e. at end
        <Call either  m_find->displayFinalDialog(); m_find->deleteLater(); m_find = nullptr;
         or           if (m_find->shouldRestart()) { reinit (w/o FromCursor); m_find->resetCounts(); slotFindNext(); }
                      else { m_find->closeFindNextDialog(); }>
}
```

Don't forget to delete m\_find in the destructor of your class, unless you gave it a parent widget on construction.

This implementation allows to have a "Find Next" action, which resumes the search, even if the user closed the "Find Next" dialog.

A "Find Previous" action can simply switch temporarily the value of [FindBackwards](kfind.md#Options-enum) and call slotFindNext() - and reset the value afterwards.

## Member Type Documentation {#member-type-documentation}

### enum KFind::Options {#Options-enum}

**flags KFind::SearchOptions**

| Constant | Value | Description |
| --- | --- | --- |
| `KFind::WholeWordsOnly` | `1` | Match whole words only. |
| `KFind::FromCursor` | `2` | Start from current cursor position. |
| `KFind::SelectedText` | `4` | Only search selected area. |
| `KFind::CaseSensitive` | `8` | Consider case when matching. |
| `KFind::FindBackwards` | `16` | Go backwards. |
| `KFind::RegularExpression` | `32` | Interpret the pattern as a regular expression. |
| `KFind::FindIncremental` | `64` | Find incremental. |
| `KFind::MinimumUserOption` | `65536` | User options start with this bit |

The `SearchOptions` type is a typedef for `QFlags<Options>. `It stores an OR combination of `Options` values.

### enum KFind::Result {#Result-enum}

| Constant |   |
| --- | --- |
| `KFind::NoMatch` | `0` |
| `KFind::Match` | `1` |

## Member Function Documentation {#member-function-documentation}

### KFind::KFind(const QString &*pattern*, long *options*, QWidget \**parent*) {#KFind}

Only use this constructor if you don't use [KFindDialog](kfinddialog.md), or if you use it as a modal dialog.

### KFind::KFind(const QString &*pattern*, long *options*, QWidget \**parent*, QWidget \**findDialog*) {#KFind-1}

This is the recommended constructor if you also use [KFindDialog](kfinddialog.md) (non-modal). You should pass the pointer to it here, so that when a message box appears it has the right parent. Don't worry about deletion, [KFind](kfind.md) will notice if the find dialog is closed.

### void KFind::closeFindNextDialog() {#closeFindNextDialog}

Close the "find next?" dialog. The application should do this when the last match was hit. If the application deletes the [KFind](kfind.md), then "find previous" won't be possible anymore.

IMPORTANT: you should also call this if you are using a non-modal find dialog, to tell [KFind](kfind.md) not to pop up its own dialog.

### \[signal\] void KFind::dialogClosed() {#dialogClosed}

Emitted when the 'find next' dialog is being closed. Some apps might want to remove the highlighted text when this happens. Apps without support for "Find Next" can also do m\_find-\>[deleteLater](https://doc.qt.io/qt-6/qobject.html#deleteLater)() to terminate the find operation.

### \[virtual\] void KFind::displayFinalDialog() const {#displayFinalDialog}

Displays the final dialog saying "no match was found", if that was the case. Call either this or [shouldRestart](kfind.md#shouldRestart)().

### KFind::Result KFind::find() {#find}

Walk the text fragment (e.g. in a text-processor line or spreadsheet cell ...etc) looking for matches. For each match, emits the [textFound](kfind.md#textFound)() signal and displays the find-again dialog to ask if the user wants to find the same text again.

### \[static\] int KFind::find(const QString &*text*, const QString &*pattern*, int *index*, long *options*, int \**matchedLength*, QRegularExpressionMatch \**rmatch*) {#find-1}

Search `text` for `pattern`. If a match is found, the length of the matched string will be stored in `matchedLength` and the index of the matched string will be returned. If no match is found -1 is returned.

If the [KFind::RegularExpression](kfind.md#Options-enum) flag is set, the `pattern` will be iterpreted as a regular expression (using [QRegularExpression](https://doc.qt.io/qt-6/qregularexpression.html)).

> **Note:** Unicode support is always enabled (by setting the [QRegularExpression::UseUnicodePropertiesOption](https://doc.qt.io/qt-6/qregularexpression.html#PatternOption-enum) flag).

`text` The string to search in

`pattern` The pattern to search for

`index` The index in `text` from which to start the search

`options` The options to use

`matchedLength` If there is a match, its length will be stored in this parameter

`rmatch` If there is a regular expression match (implies that the [KFind::RegularExpression](kfind.md#Options-enum) flag is set) and `rmatch` is not a nullptr the match result will be stored in this [QRegularExpressionMatch](https://doc.qt.io/qt-6/qregularexpressionmatch.html) object

Returns The index at which a match was found otherwise -1

### QDialog \*KFind::findNextDialog(bool *create* = false) {#findNextDialog}

Returns (or creates if `create` is true) the dialog that shows the "find next?" prompt. Usually you don't need to call this. One case where it can be useful, is when the user selects the "Find" menu item while a find operation is under way. In that case, the program may want to call setActiveWindow() on that dialog.

### int KFind::index() const {#index}

Returns the current matching index (or -1). Same as the matchingIndex parameter passed to the [textFound](kfind.md#textFound)() signal. You usually don't need to use this, except maybe when updating the current data, so you need to call [setData](kfind.md#setData)(newData, index()).

### bool KFind::needData() const {#needData}

Returns true if the application must supply a new text fragment It also means the last call returned "[NoMatch](kfind.md#Result-enum)". But by storing this here the application doesn't have to store it in a member variable (between calls to slotFindNext()).

### int KFind::numMatches() const {#numMatches}

Returns the number of matches found (i.e. the number of times the [textFound](kfind.md#textFound)() signal was emitted). If 0, can be used in a dialog box to tell the user "no match was found". The final dialog does so already, unless you used setDisplayFinalDialog(false).

### long KFind::options() const {#options}

Return the current options.

Warning: this is usually the same value as the one passed to the constructor, but options might change \_during\_ the replace operation: e.g. the "All" button resets the PromptOnReplace flag.

*See also* [setOptions](kfind.md#setOptions)(), [KFind::Options](kfind.md#Options-enum)

### \[signal\] void KFind::optionsChanged() {#optionsChanged}

Emitted when the options have changed. This can happen e.g. with "Replace All", or if our 'find next' dialog gets a "find previous" one day.

### QString KFind::pattern() const {#pattern}

Returns the pattern we're currently looking for

*See also* [setPattern](kfind.md#setPattern)()

### \[virtual\] void KFind::resetCounts() {#resetCounts}

Call this to reset the [numMatches](kfind.md#numMatches) count (and the numReplacements count for a [KReplace](kreplace.md)). Can be useful if reusing the same [KReplace](kreplace.md) for different operations, or when restarting from the beginning of the document.

### void KFind::setData(const QString &*data*, int *startPos* = -1) {#setData}

Call this when [needData](kfind.md#needData) returns true, before calling [find](kfind.md#find)().

`data` is the text fragment (line).

`startPos` if set, the index at which the search should start.

Usually `startPos` is only necessary for the very first call to setData, for the 'find in selection' feature. The default value of -1 means "process all the data", i.e. either 0 or data.length()-1 depending on [FindBackwards](kfind.md#Options-enum).

### void KFind::setData(int *id*, const QString &*data*, int *startPos* = -1) {#setData-1}

Call this when [needData](kfind.md#needData) returns true, before calling [find](kfind.md#find)(). The use of ID's is especially useful if you're using the [FindIncremental](kfind.md#Options-enum) option.

`id` the id of the text fragment.

`data` the text fragment (line).

`startPos` if set, the index at which the search should start. This is only necessary for the very first call to [setData](kfind.md#setData) usually, for the 'find in selection' feature. A value of -1 (the default value) means "process all the data", i.e. either 0 or data.length()-1 depending on [FindBackwards](kfind.md#Options-enum).

### \[virtual\] void KFind::setOptions(long *options*) {#setOptions}

Set new `options`. Usually this is used for setting or clearing the [FindBackwards](kfind.md#Options-enum) options.

*See also* [options](kfind.md#options)(), [KFind::Options](kfind.md#Options-enum)

### void KFind::setPattern(const QString &*pattern*) {#setPattern}

Sets the `pattern` to look for

*See also* [pattern](kfind.md#pattern)()

### \[virtual\] bool KFind::shouldRestart(bool *forceAsking* = false, bool *showNumMatches* = true) const {#shouldRestart}

Returns true if we should restart the search from scratch. Can ask the user, or return false (if we already searched the whole document).

`forceAsking` set to true if the user modified the document during the search. In that case it makes sense to restart the search again.

`showNumMatches` set to true if the dialog should show the number of matches. Set to false if the application provides a "find previous" action, in which case the match count will be erroneous when hitting the end, and we could even be hitting the beginning of the document (so not all matches have even been seen).

### \[signal\] void KFind::textFound(const QString &*text*, int *matchingIndex*, int *matchedLength*) {#textFound}

Connect to this signal to implement highlighting of found text during the find operation.

If you've set data with [setData](kfind.md#setData)(id, text), use the [textFoundAtId](kfind.md#textFoundAtId)(int, int, int) signal.

WARNING: If you're using the [FindIncremental](kfind.md#Options-enum) option, the text argument passed by this signal is not necessarily the data last set through [setData](kfind.md#setData)(), but can also be an earlier set data block.

`text` is the text that was found

`matchingIndex` is the index of the start of the matched text

`matchedLength` is the length of the matched text

*See also* [setData](kfind.md#setData)()

### \[signal\] void KFind::textFoundAtId(int *id*, int *matchingIndex*, int *matchedLength*) {#textFoundAtId}

Connect to this signal to implement highlighting of found text during the find operation.

Use this signal if you've set your data with [setData](kfind.md#setData)(id, text), otherwise use the [textFound](kfind.md#textFound)(text, matchingIndex, matchedLength) signal.

WARNING: If you're using the [FindIncremental](kfind.md#Options-enum) option, the `id` passed by this signal is not necessarily the id of the data last set through [setData](kfind.md#setData)(), but can also be of an earlier set data block.

`matchingIndex` is the index of the start of the matched text

`matchedLength` is the length of the matched text

*See also* [setData](kfind.md#setData)()

### \[virtual\] bool KFind::validateMatch(const QString &*text*, int *index*, int *matchedlength*) {#validateMatch}

Virtual method, which allows applications to add extra checks for validating a candidate match. It's only necessary to reimplement this if the find dialog extension has been used to provide additional criteria.

`text` The current text fragment

`index` The starting index where the candidate match was found

`matchedlength` The length of the candidate match

Returns true if the candidate matches.
