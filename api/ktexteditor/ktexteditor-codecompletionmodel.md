---
title: "KTextEditor::CodeCompletionModel Class"
description: "An item model for providing code completion, and meta information for enhanced presentation."
---

# KTextEditor::CodeCompletionModel Class

An item model for providing code completion, and meta information for enhanced presentation. [More...](#details)

- **Header:** `#include <KTextEditor/CodeCompletionModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextEditor)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextEditor)`
- **Inherits:** [QAbstractItemModel](https://doc.qt.io/qt-6/qabstractitemmodel.html)

[List of all members, including inherited members](ktexteditor-codecompletionmodel-members.md)

## Public Types

- [enum CodeCompletionModel::Columns](#Columns-enum)
- [enum CodeCompletionModel::CompletionProperty](#CompletionProperty-enum)
- [enum CodeCompletionModel::ExtraItemDataRoles](#ExtraItemDataRoles-enum)

## Public Functions

- [CodeCompletionModel(QObject \*parent)](#CodeCompletionModel)
- [int columnCount(const QModelIndex &parent = QModelIndex()) const](#columnCount)
- [void completionInvoked(KTextEditor::View \*view, const KTextEditor::Range &range, KTextEditor::CodeCompletionModel::InvocationType invocationType)](#completionInvoked)
- [void executeCompletionItem(KTextEditor::View \*view, const KTextEditor::Range &word, const QModelIndex &index) const](#executeCompletionItem)
- [bool hasGroups() const](#hasGroups)
- [QModelIndex index(int row, int column, const QModelIndex &parent = QModelIndex()) const](#index)
- [QMap\<int, QVariant\> itemData(const QModelIndex &index) const](#itemData)
- [QModelIndex parent(const QModelIndex &index) const](#parent)
- [int rowCount(const QModelIndex &parent = QModelIndex()) const](#rowCount)

## Signals

- [void waitForReset()](#waitForReset)

## Detailed Description {#details}

Introduction

The [CodeCompletionModel](ktexteditor-codecompletionmodel.md) is the actual workhorse to provide code completions in a [KTextEditor::View](ktexteditor-view.md). It is meant to be used in conjunction with the View. The [CodeCompletionModel](ktexteditor-codecompletionmodel.md) is not meant to be used as is. Rather you need to implement a subclass of [CodeCompletionModel](ktexteditor-codecompletionmodel.md) to actually generate completions appropriate for your type of Document.

Implementing a [CodeCompletionModel](ktexteditor-codecompletionmodel.md)

The [CodeCompletionModel](ktexteditor-codecompletionmodel.md) is a [QAbstractItemModel](https://doc.qt.io/qt-6/qabstractitemmodel.html), and can be subclassed in the same way. It provides default implementations of several members, however, so in most cases (if your completions are essentially a non-hierarchical, flat list of matches) you will only need to overload few virtual functions.

Implementing a [CodeCompletionModel](ktexteditor-codecompletionmodel.md) for a flat list

For the simple case of a flat list of completions, you will need to:

- Implement [completionInvoked](ktexteditor-codecompletionmodel.md#completionInvoked)() to actually generate/update the list of completion matches
- implement [itemData](ktexteditor-codecompletionmodel.md#itemData)() (or [QAbstractItemModel::data](https://doc.qt.io/qt-6/qabstractitemmodel.html#data)()) to return the information that should be displayed for each match.
- use setRowCount() to reflect the number of matches.

Columns and roles

TODO document the meaning and usage of the columns and roles used by the

Completion Interface

Using the new [CodeCompletionModel](ktexteditor-codecompletionmodel.md)

To start using your [KTextEditor::View](ktexteditor-view.md) Completion Interface.

ControllerInterface to get more control

To have more control over code completion implement [CodeCompletionModelControllerInterface](ktexteditor-codecompletionmodelcontrollerinterface.md) in your [CodeCompletionModel](ktexteditor-codecompletionmodel.md).

*See also* [KTextEditor::CodeCompletionModelControllerInterface](ktexteditor-index.md)

## Member Type Documentation {#member-type-documentation}

### enum CodeCompletionModel::Columns {#Columns-enum}

| Constant | Value |   |
| --- | --- | --- |
| `KTextEditor::CodeCompletionModel::Prefix` | `0` |   |
| `KTextEditor::CodeCompletionModel::Icon` | `1` | Icon representing the type of completion. We have a separate icon field so that names remain aligned where only some completions have icons, and so that they can be rearranged by the user. |
| `KTextEditor::CodeCompletionModel::Scope` | `2` |   |
| `KTextEditor::CodeCompletionModel::Name` | `3` |   |
| `KTextEditor::CodeCompletionModel::Arguments` | `4` |   |
| `KTextEditor::CodeCompletionModel::Postfix` | `5` |   |

### enum CodeCompletionModel::CompletionProperty {#CompletionProperty-enum}

**flags CodeCompletionModel::CompletionProperties**

| Constant |   |
| --- | --- |
| `KTextEditor::CodeCompletionModel::NoProperty` | `0x0` |
| `KTextEditor::CodeCompletionModel::FirstProperty` | `0x1` |
| `KTextEditor::CodeCompletionModel::Public` | `0x1` |
| `KTextEditor::CodeCompletionModel::Protected` | `0x2` |
| `KTextEditor::CodeCompletionModel::Private` | `0x4` |
| `KTextEditor::CodeCompletionModel::Static` | `0x8` |
| `KTextEditor::CodeCompletionModel::Const` | `0x10` |
| `KTextEditor::CodeCompletionModel::Namespace` | `0x20` |
| `KTextEditor::CodeCompletionModel::Class` | `0x40` |
| `KTextEditor::CodeCompletionModel::Struct` | `0x80` |
| `KTextEditor::CodeCompletionModel::Union` | `0x100` |
| `KTextEditor::CodeCompletionModel::Function` | `0x200` |
| `KTextEditor::CodeCompletionModel::Variable` | `0x400` |
| `KTextEditor::CodeCompletionModel::Enum` | `0x800` |
| `KTextEditor::CodeCompletionModel::Template` | `0x1000` |
| `KTextEditor::CodeCompletionModel::TypeAlias` | `0x2000` |
| `KTextEditor::CodeCompletionModel::Virtual` | `0x4000` |
| `KTextEditor::CodeCompletionModel::Override` | `0x8000` |
| `KTextEditor::CodeCompletionModel::Inline` | `0x10000` |
| `KTextEditor::CodeCompletionModel::Friend` | `0x20000` |
| `KTextEditor::CodeCompletionModel::Signal` | `0x40000` |
| `KTextEditor::CodeCompletionModel::Slot` | `0x80000` |
| `KTextEditor::CodeCompletionModel::LocalScope` | `0x100000` |
| `KTextEditor::CodeCompletionModel::NamespaceScope` | `0x200000` |
| `KTextEditor::CodeCompletionModel::GlobalScope` | `0x400000` |
| `KTextEditor::CodeCompletionModel::LastProperty` | `GlobalScope` |

The `CompletionProperties` type is a typedef for `QFlags<CompletionProperty>. `It stores an OR combination of `CompletionProperty` values.

### enum CodeCompletionModel::ExtraItemDataRoles {#ExtraItemDataRoles-enum}

Meta information is passed through extra {[Qt::ItemDataRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum)}s. This information should be returned when requested on the Name column.

| Constant | Value | Description |
| --- | --- | --- |
| `KTextEditor::CodeCompletionModel::CompletionRole` | `Qt::UserRole` | The model should return a set of [CompletionProperties](ktexteditor-codecompletionmodel.md#CompletionProperty-enum). |
| `KTextEditor::CodeCompletionModel::ScopeIndex` | `Qt::UserRole + 1` | The model should return an index to the scope -1 represents no scope. TODO how to sort scope? |
| `KTextEditor::CodeCompletionModel::MatchQuality` | `Qt::UserRole + 2` | If requested, your model should try to determine whether the completion in question is a suitable match for the context (ie. is accessible, exported, + returns the data type required). The returned data should ideally be matched against the argument-hint context set earlier by SetMatchContext. Return an integer value that should be positive if the completion is suitable, and zero if the completion is not suitable. The value should be between 0 an 10, where 10 means perfect match. Return QVariant::Invalid if you are unable to determine this. |
| `KTextEditor::CodeCompletionModel::SetMatchContext` | `Qt::UserRole + 3` | Is requested before MatchQuality(..) is requested. The item on which this is requested is an argument-hint item When this role is requested, the item should be noted, and whenever MatchQuality is requested, it should be computed by matching the item given with MatchQuality into the context chosen by SetMatchContext. Feel free to ignore this, but ideally you should return QVariant::Invalid to make clear that your model does not support this. |
| `KTextEditor::CodeCompletionModel::HighlightingMethod` | `Qt::UserRole + 4` | Define which highlighting method will be used: - QVariant::Invalid - allows the editor to choose (usually internal highlighting) - QVariant::Integer - highlight as specified by [HighlightMethods](ktexteditor-codecompletionmodel.md#HighlightMethod-enum). |

GroupRole Using this Role, it is possible to greatly optimize the time needed to process very long completion-lists. In the completion-list, the items are usually ordered by some properties like argument-hint depth, inheritance-depth and attributes. Kate usually has to query the completion-models for these values for each item in the completion-list in order to extract the argument-hints and correctly sort the completion-list. However, with a very long completion-list, only a very small fraction of the items is actually visible. By using a tree structure you can give the items in a grouped order to kate, so it does not need to look at each item and query data in order to initially show the completion-list. This is how it works:

- You create a tree-structure for your items
- Every inner node of the tree defines one attribute value that all sub-nodes have in common.
   
   - When the inner node is queried for GroupRole, it should return the "ExtraItemDataRoles" that all sub-nodes have in common
   - When the inner node is then queried for that exact role, it should return that value.
   - No other queries will be done to inner nodes.
- Every leaf node stands for an actual item in the completion list.
- The recommended grouping order is: Argument-hint depth, inheritance depth, attributes. This role can also be used to define completely custom groups, bypassing the editors builtin grouping:
   
   - Return [Qt::DisplayRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum) when GroupRole is requested
   - Return the label text of the group when [Qt::DisplayRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum)
   - Optional: Return an integer sorting-value when InheritanceDepth is requested. This number will be used to determine the order of the groups. The order of the builtin groups is: 1=Best Matches, 100=Local Scope, 200=Public, 300=Protected, 400=Private, 500=Namespace, 600=Global You can pick any arbitrary number to position your group relative to these builtin groups.

UnimportantItemRole Return a nonzero value here to enforce sorting the item at the end of the list.

LastExtraItemDataRole

*See also* ArgumentHintDepth, ExpandingWidget

## enum CodeCompletionModel::HighlightMethod {#HighlightMethod-enum}

**flags CodeCompletionModel::HighlightMethods**

| Constant |   |
| --- | --- |
| `KTextEditor::CodeCompletionModel::NoHighlighting` | `0x0` |
| `KTextEditor::CodeCompletionModel::InternalHighlighting` | `0x1` |
| `KTextEditor::CodeCompletionModel::CustomHighlighting` | `0x2` |

The `HighlightMethods` type is a typedef for `QFlags<HighlightMethod>. `It stores an OR combination of `HighlightMethod` values.

## enum CodeCompletionModel::InvocationType {#InvocationType-enum}

| Constant |   |
| --- | --- |
| `KTextEditor::CodeCompletionModel::AutomaticInvocation` | `0` |
| `KTextEditor::CodeCompletionModel::UserInvocation` | `1` |
| `KTextEditor::CodeCompletionModel::ManualInvocation` | `2` |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] CodeCompletionModel::CodeCompletionModel(QObject \**parent*) {#CodeCompletionModel}

### \[override virtual\] int CodeCompletionModel::columnCount(const QModelIndex &*parent* = QModelIndex()) const {#columnCount}

Reimplements: [QAbstractItemModel::columnCount(const QModelIndex &parent) const](https://doc.qt.io/qt-6/qabstractitemmodel.html#columnCount).

Reimplemented from [QAbstractItemModel::columnCount](https://doc.qt.io/qt-6/qabstractitemmodel.html#columnCount)(). The default implementation returns ColumnCount for all indices.

### \[virtual\] void CodeCompletionModel::completionInvoked(KTextEditor::View \**view*, const KTextEditor::Range &*range*, KTextEditor::CodeCompletionModel::InvocationType *invocationType*) {#completionInvoked}

This function is responsible to generating / updating the list of current completions. The default implementation does nothing.

When implementing this function, remember to call setRowCount() (or implement [rowCount](ktexteditor-codecompletionmodel.md#rowCount)()), and to generate the appropriate change notifications (for instance by calling QAbstractItemModel::reset()).

`view` is the view to generate completions for

`range` is the range of text to generate completions for

`invocationType` describes how the code completion was triggered

### \[virtual\] void CodeCompletionModel::executeCompletionItem(KTextEditor::View \**view*, const KTextEditor::Range &*word*, const QModelIndex &*index*) const {#executeCompletionItem}

This function is responsible for inserting a selected completion into the view. The default implementation replaces the text that the completions were based on with the [Qt::DisplayRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum) of the Name column of the given match.

`view` is the view to insert the completion into

`word` is the Range that the completions are based on (what the user entered so far)

`index` identifies the completion match to insert

### bool CodeCompletionModel::hasGroups() const {#hasGroups}

This function returns true if the model needs grouping, otherwise false. The default is false if not changed via setHasGroups().

### \[override virtual\] QModelIndex CodeCompletionModel::index(int *row*, int *column*, const QModelIndex &*parent* = QModelIndex()) const {#index}

Reimplements: [QAbstractItemModel::index(int row, int column, const QModelIndex &parent) const](https://doc.qt.io/qt-6/qabstractitemmodel.html#index).

Reimplemented from [QAbstractItemModel::index](https://doc.qt.io/qt-6/qabstractitemmodel.html#index)(). The default implementation returns a standard [QModelIndex](https://doc.qt.io/qt-6/qmodelindex.html) as long as the row and column are valid.

### \[override virtual\] QMap\<int, QVariant\> CodeCompletionModel::itemData(const QModelIndex &*index*) const {#itemData}

Reimplements: [QAbstractItemModel::itemData(const QModelIndex &index) const](https://doc.qt.io/qt-6/qabstractitemmodel.html#itemData).

Reimplemented from [QAbstractItemModel::itemData](https://doc.qt.io/qt-6/qabstractitemmodel.html#itemData)(). The default implementation returns a map with the [QAbstractItemModel::data](https://doc.qt.io/qt-6/qabstractitemmodel.html#data)() for all roles that are used by the CodeCompletionInterface. You will need to reimplement either this function or [QAbstractItemModel::data](https://doc.qt.io/qt-6/qabstractitemmodel.html#data)() in your [CodeCompletionModel](ktexteditor-codecompletionmodel.md).

### \[override virtual\] QModelIndex CodeCompletionModel::parent(const QModelIndex &*index*) const {#parent}

Reimplements: [QAbstractItemModel::parent(const QModelIndex &index) const](https://doc.qt.io/qt-6/qabstractitemmodel.html#parent).

Reimplemented from [QAbstractItemModel::parent](https://doc.qt.io/qt-6/qabstractitemmodel.html#parent)(). The default implementation returns an invalid [QModelIndex](https://doc.qt.io/qt-6/qmodelindex.html) for all items. This is appropriate for non-hierarchical / flat lists of completions.

### \[override virtual\] int CodeCompletionModel::rowCount(const QModelIndex &*parent* = QModelIndex()) const {#rowCount}

Reimplements: [QAbstractItemModel::rowCount(const QModelIndex &parent) const](https://doc.qt.io/qt-6/qabstractitemmodel.html#rowCount).

Reimplemented from [QAbstractItemModel::rowCount](https://doc.qt.io/qt-6/qabstractitemmodel.html#rowCount)(). The default implementation returns the value set by setRowCount() for invalid (toplevel) indices, and 0 for all other indices. This is appropriate for non-hierarchical / flat lists of completions

### \[signal\] void CodeCompletionModel::waitForReset() {#waitForReset}

Emit this if the code-completion for this model was invoked, some time is needed in order to get the data, and the model is reset once the data is available.

This only has an effect if emitted from within [completionInvoked](ktexteditor-codecompletionmodel.md#completionInvoked)(..).

This prevents the code-completion list from showing until this model is reset, so there is no annoying flashing in the user-interface resulting from other models supplying their data earlier.

> **Note:** The implementation may choose to show the completion-list anyway after some timeout

> **Warning:** If you emit this, you \_must\_ also reset the model at some point, else the code-completion will be completely broken to the user. Consider that there may always be additional completion-models apart from yours.
