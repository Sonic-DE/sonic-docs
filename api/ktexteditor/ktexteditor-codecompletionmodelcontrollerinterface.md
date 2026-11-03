---
title: "KTextEditor::CodeCompletionModelControllerInterface Class"
description: "Controller interface for a CodeCompletionModel instance."
---

# KTextEditor::CodeCompletionModelControllerInterface Class

Controller interface for a [CodeCompletionModel](ktexteditor-codecompletionmodel.md) instance. [More...](#details)

- **Header:** `#include <KTextEditor/CodeCompletionModelControllerInterface>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextEditor)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextEditor)`
- **Group:** CodeCompletionModelControllerInterface is part of kte\_group\_ccmodel\_extensions

[List of all members, including inherited members](ktexteditor-codecompletionmodelcontrollerinterface-members.md)

## Public Types

- [enum CodeCompletionModelControllerInterface::MatchReaction](#MatchReaction-enum)

## Public Functions

- [CodeCompletionModelControllerInterface()](#CodeCompletionModelControllerInterface)
- [void aborted(KTextEditor::View \*view)](#aborted)
- [KTextEditor::Range completionRange(KTextEditor::View \*view, const KTextEditor::Cursor &position)](#completionRange)
- [QString filterString(KTextEditor::View \*view, const KTextEditor::Range &range, const KTextEditor::Cursor &position)](#filterString)
- [KTextEditor::CodeCompletionModelControllerInterface::MatchReaction matchingItem(const QModelIndex &matched)](#matchingItem)
- [bool shouldAbortCompletion(KTextEditor::View \*view, const KTextEditor::Range &range, const QString &currentCompletion)](#shouldAbortCompletion)
- [bool shouldExecute(const QModelIndex &selected, QChar inserted)](#shouldExecute)
- [bool shouldHideItemsWithEqualNames() const](#shouldHideItemsWithEqualNames)
- [bool shouldStartCompletion(KTextEditor::View \*view, const QString &insertedText, bool userInsertion, const KTextEditor::Cursor &position)](#shouldStartCompletion)
- [KTextEditor::Range updateCompletionRange(KTextEditor::View \*view, const KTextEditor::Range &range)](#updateCompletionRange)

## Detailed Description {#details}

The [CodeCompletionModelControllerInterface](ktexteditor-codecompletionmodelcontrollerinterface.md) gives a [CodeCompletionModel](ktexteditor-codecompletionmodel.md) better control over the completion.

By implementing methods defined in this interface you can:

- control when automatic completion should start - see [shouldStartCompletion](ktexteditor-codecompletionmodelcontrollerinterface.md#shouldStartCompletion)()
- define a custom completion range (that will be replaced when the completion is executed) - see [completionRange](ktexteditor-codecompletionmodelcontrollerinterface.md#completionRange)()
- dynamically modify the completion range during completion -see [updateCompletionRange](ktexteditor-codecompletionmodelcontrollerinterface.md#updateCompletionRange)()
- specify the string used for filtering the completion - see [filterString](ktexteditor-codecompletionmodelcontrollerinterface.md#filterString)()
- control when completion should stop - see [shouldAbortCompletion](ktexteditor-codecompletionmodelcontrollerinterface.md#shouldAbortCompletion)()

When the interface is not implemented, or no methods are overridden the default behaviour is used, which will be correct in many situations.

Implementing the Interface To use this class implement it in your [CodeCompletionModel](ktexteditor-codecompletionmodel.md).

```cpp
class MyCodeCompletion : public KTextEditor::CodeCompletionTestModel,
                 public KTextEditor::CodeCompletionModelControllerInterface
{
  Q_OBJECT
  Q_INTERFACES(KTextEditor::CodeCompletionModelControllerInterface)
public:
  KTextEditor::Range completionRange(KTextEditor::View* view, const KTextEditor::Cursor &position);
};
```

**Author:** Joseph Wenninger

*See also* [CodeCompletionModel](ktexteditor-codecompletionmodel.md)

## Member Type Documentation {#member-type-documentation}

### enum CodeCompletionModelControllerInterface::MatchReaction {#MatchReaction-enum}

| Constant | Value |   |
| --- | --- | --- |
| `KTextEditor::CodeCompletionModelControllerInterface::None` | `0` |   |
| `KTextEditor::CodeCompletionModelControllerInterface::HideListIfAutomaticInvocation` | `1` | If this is returned, the completion-list is hidden if it was invoked automatically |
| `KTextEditor::CodeCompletionModelControllerInterface::ForExtension` | `0xffff` |   |

## Member Function Documentation {#member-function-documentation}

### CodeCompletionModelControllerInterface::CodeCompletionModelControllerInterface() {#CodeCompletionModelControllerInterface}

### \[virtual\] void CodeCompletionModelControllerInterface::aborted(KTextEditor::View \**view*) {#aborted}

Notification that completion for this model has been aborted.

`view` is the view in which the completion for this model was aborted

### \[virtual\] KTextEditor::Range CodeCompletionModelControllerInterface::completionRange(KTextEditor::View \**view*, const KTextEditor::Cursor &*position*) {#completionRange}

This function returns the completion range that will be used for the current completion.

This range will be used for filtering the completion list and will get replaced when executing the completion

The default implementation will work for most languages that don't have special chars in identifiers. Since 5.83 the default implementation takes into account the wordCompletionRemoveTail configuration option, if that option is enabled the whole word the cursor is inside is replaced with the completion, however if it's disabled only the text on the left of the cursor will be replaced with the completion.

`view` is the view to generate completions for

`position` is the current cursor position

Returns the completion range

### \[virtual\] QString CodeCompletionModelControllerInterface::filterString(KTextEditor::View \**view*, const KTextEditor::Range &*range*, const KTextEditor::Cursor &*position*) {#filterString}

This function returns the filter-text used for the current completion. Can return an empty string to disable filtering.

The default implementation will return the text from `range` start to the cursor `position`.

`view` is the view to generate completions for

`range` is the completion range

`position` is the current cursor position

Returns the string used for filtering the completion list

### \[virtual\] KTextEditor::CodeCompletionModelControllerInterface::MatchReaction CodeCompletionModelControllerInterface::matchingItem(const QModelIndex &*matched*) {#matchingItem}

Called whenever an item in the completion-list perfectly matches the current filter text.

`matched` is the index that is matched

Returns Whether the completion-list should be hidden on this event. The default-implementation always returns [HideListIfAutomaticInvocation](ktexteditor-codecompletionmodelcontrollerinterface.md#MatchReaction-enum)

### \[virtual\] bool CodeCompletionModelControllerInterface::shouldAbortCompletion(KTextEditor::View \**view*, const KTextEditor::Range &*range*, const QString &*currentCompletion*) {#shouldAbortCompletion}

This function decides if the completion should be aborted. Called after every change to the range (eg. when user entered text)

The default implementation will return true when any special character was entered, or when the range is empty.

`view` is the view to generate completions for

`range` is the completion range

`currentCompletion` is the text typed so far

Returns *true*, if the completion should be aborted, otherwise *false*

### \[virtual\] bool CodeCompletionModelControllerInterface::shouldExecute(const QModelIndex &*selected*, QChar *inserted*) {#shouldExecute}

When an item within this model is currently selected in the completion-list, and the user inserted the given character, should the completion-item be executed? This can be used to execute items from other inputs than the return-key. For example a function item could be executed by typing '(', or variable items by typing '.'.

`selected` is the currently selected index

`inserted` is the character that was inserted by tue user

### \[virtual\] bool CodeCompletionModelControllerInterface::shouldHideItemsWithEqualNames() const {#shouldHideItemsWithEqualNames}

When multiple completion models are used at the same time, it may happen that multiple models add items with the same name to the list. This option allows to hide items from this completion model when another model with higher priority contains items with the same name. Returns Whether items of this completion model should be hidden if another completion model has items with the same name

### \[virtual\] bool CodeCompletionModelControllerInterface::shouldStartCompletion(KTextEditor::View \**view*, const QString &*insertedText*, bool *userInsertion*, const KTextEditor::Cursor &*position*) {#shouldStartCompletion}

This function decides if the automatic completion should be started when the user entered some text.

The default implementation will return true if the last character in

`insertedText` is a letter, a number, '.', '\_' or '\>'

`view` is the view to generate completions for

`insertedText` is the text that was inserted by the user

`userInsertion` is true if the text was inserted by the user using typing. If false, it may have been inserted for example by code-completion.

`position` is the current cursor position

Returns *true*, if the completion should be started, otherwise *false*

### \[virtual\] KTextEditor::Range CodeCompletionModelControllerInterface::updateCompletionRange(KTextEditor::View \**view*, const KTextEditor::Range &*range*) {#updateCompletionRange}

This function lets the CompletionModel dynamically modify the range. Called after every change to the range (eg. when user entered text)

The default implementation does nothing.

`view` is the view to generate completions for

`range` are reference to the current range

Returns the modified range
