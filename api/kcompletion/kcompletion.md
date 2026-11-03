---
title: "KCompletion Class"
description: "A generic class for completing QStrings."
---

# KCompletion Class

A generic class for completing QStrings. [More...](#details)

- **Header:** `#include <KCompletion>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Completion)`  
  `target_link_libraries(mytarget PRIVATE KF6::Completion)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kcompletion-members.md)  
[Deprecated members](kcompletion-obsolete.md)

## Public Types

- [enum KCompletion::CompOrder](#CompOrder-enum)
- [enum KCompletion::CompletionMode](#CompletionMode-enum)

## Properties

- [ignoreCase : bool](#ignoreCase-prop)
- [items : QStringList](#items-prop)
- [order : CompOrder](#order-prop)

## Public Functions

- [KCompletion()](#KCompletion)
- [QStringList allMatches()](#allMatches)
- [QStringList allMatches(const QString &string)](#allMatches-1)
- [KCompletionMatches allWeightedMatches()](#allWeightedMatches)
- [KCompletionMatches allWeightedMatches(const QString &string)](#allWeightedMatches-1)
- [KCompletion::CompletionMode completionMode() const](#completionMode)
- [bool hasMultipleMatches() const](#hasMultipleMatches)
- [bool ignoreCase() const](#ignoreCase)
- [bool isEmpty() const](#isEmpty)
- [QStringList items() const](#items)
- [const QString &lastMatch() const](#lastMatch)
- [KCompletion::CompOrder order() const](#order)
- [void setCompletionMode(KCompletion::CompletionMode mode)](#setCompletionMode)
- [void setIgnoreCase(bool ignoreCase)](#setIgnoreCase)
- [void setOrder(KCompletion::CompOrder order)](#setOrder)
- [bool shouldAutoSuggest() const](#shouldAutoSuggest)
- [QStringList substringCompletion(const QString &string) const](#substringCompletion)

## Public Slots

- [void addItem(const QString &item)](#addItem)
- [void addItem(const QString &item, uint weight)](#addItem-1)
- [void clear()](#clear)
- [void insertItems(const QStringList &items)](#insertItems)
- [QString makeCompletion(const QString &string)](#makeCompletion)
- [QString nextMatch()](#nextMatch)
- [QString previousMatch()](#previousMatch)
- [void removeItem(const QString &item)](#removeItem)
- [void setItems(const QStringList &itemList)](#setItems)

## Signals

- [void match(const QString &item)](#match)
- [void matches(const QStringList &matchlist)](#matches)
- [void multipleMatches()](#multipleMatches)

## Protected Functions

- [void postProcessMatch(QString \*match) const](#postProcessMatch)
- [void postProcessMatches(KCompletionMatches \*matches) const](#postProcessMatches)
- [void postProcessMatches(QStringList \*matchList) const](#postProcessMatches-1)
- [void setShouldAutoSuggest(bool shouldAutosuggest)](#setShouldAutoSuggest)
- [void setSorterFunction(KCompletion::SorterFunction sortFunc)](#setSorterFunction)

## Detailed Description {#details}

This class offers easy use of "auto completion", "manual completion" or "shell completion" on [QString](https://doc.qt.io/qt-6/qstring.html) objects. A common use is completing filenames or URLs (see KUrlCompletion()). But it is not limited to URL-completion – everything should be completable! The user should be able to complete email addresses, telephone numbers, commands, SQL queries... Every time your program knows what the user can type into an edit field, you should offer completion. With [KCompletion](kcompletion.md), this is very easy, and if you are using a line edit widget ([KLineEdit](klineedit.md)), it is even easier. Basically, you tell a [KCompletion](kcompletion.md) object what strings should be completable and, whenever completion should be invoked, you call [makeCompletion](kcompletion.md#makeCompletion)(). [KLineEdit](klineedit.md) and (an editable) [KComboBox](kcombobox.md) even do this automatically for you.

[KCompletion](kcompletion.md) offers the completed string via the signal [match](kcompletion.md#match)() and all matching strings (when the result is ambiguous) via the method [allMatches](kcompletion.md#allMatches)().

Notice: auto completion, shell completion and manual completion work slightly differently:

- auto completion always returns a complete item as match. When more than one matching item is available, it will deliver just the first one (depending on sorting order). Iterating over all matches is possible via [nextMatch](kcompletion.md#nextMatch)() and [previousMatch](kcompletion.md#previousMatch)().
- popup completion works in the same way, the only difference being that the completed items are not put into the edit widget, but into a separate popup box.
- manual completion works the same way as auto completion, except that it is not invoked automatically while the user is typing, but only when the user presses a special key. The difference of manual and auto completion is therefore only visible in UI classes. [KCompletion](kcompletion.md) needs to know whether to deliver partial matches (shell completion) or whole matches (auto/manual completion), therefore [KCompletion::CompletionMan](kcompletion.md#CompletionMode-enum) and [KCompletion::CompletionAuto](kcompletion.md#CompletionMode-enum) have the exact same effect in [KCompletion](kcompletion.md).
- shell completion works like "tab completion" in a shell: when multiple matches are available, the longest possible string of all matches is returned (i.e. only a partial item). Iterating over all matching items (complete, not partial) is possible via [nextMatch](kcompletion.md#nextMatch)() and [previousMatch](kcompletion.md#previousMatch)().

As an application programmer, you do not normally have to worry about the different completion modes; [KCompletion](kcompletion.md) handles that for you, according to the setting [setCompletionMode](kcompletion.md#setCompletionMode)(). The default setting is globally configured by the user and read from [completionMode](kcompletion.md#completionMode)().

A short example:

```cpp
KCompletion completion;
completion.setOrder(KCompletion::Sorted);
completion.addItem("pfeiffer@kde.org");
completion.addItem("coolo@kde.org");
completion.addItem("carpdjih@sp.zrz.tu-berlin.de");
completion.addItem("carp\cs.tu-berlin.de");

cout << completion.makeCompletion("ca").latin1() << endl;
```

In shell-completion mode, this will be "carp"; in auto-completion mode it will be "carp\\cs.tu-berlin.de", as that is alphabetically smaller. If [setOrder](kcompletion.md#setOrder) was set to Insertion, "carpdjih@sp.zrz.tu-berlin.de" would be completed in auto-completion mode, as that was inserted before "carp\\cs.tu-berlin.de".

You can dynamically update the completable items by removing and adding them whenever you want. For advanced usage, you could even use multiple [KCompletion](kcompletion.md) objects. E.g. imagine an editor like kwrite with multiple open files. You could store items of each file in a different [KCompletion](kcompletion.md) object, so that you know (and tell the user) where a completion comes from.

> **Note:** [KCompletion](kcompletion.md) does not work with strings that contain 0x0 characters (unicode null), as this is used internally as a delimiter.

You may inherit from [KCompletion](kcompletion.md) and override [makeCompletion](kcompletion.md#makeCompletion)() in special cases (like reading directories or urls and then supplying the contents to [KCompletion](kcompletion.md), as KUrlCompletion does), but this is usually not necessary.

## Member Type Documentation {#member-type-documentation}

### enum KCompletion::CompOrder {#CompOrder-enum}

Constants that represent the order in which [KCompletion](kcompletion.md) performs completion lookups.

| Constant | Value | Description |
| --- | --- | --- |
| `KCompletion::Sorted` | `0` | Use alphabetically sorted order or custom sorter logic. |
| `KCompletion::Insertion` | `1` | Use order of insertion. |
| `KCompletion::Weighted` | `2` | Use weighted order |

### enum KCompletion::CompletionMode {#CompletionMode-enum}

This enum describes the completion mode used for by the [KCompletion](kcompletion.md) class.

| Constant | Value | Description |
| --- | --- | --- |
| `KCompletion::CompletionNone` | `1` | No completion is used. |
| `KCompletion::CompletionAuto` | `2` | Text is automatically filled in whenever possible. |
| `KCompletion::CompletionMan` | `3` | Same as automatic, but shortest match is used for completion. |
| `KCompletion::CompletionShell` | `4` | Completes text much in the same way as a typical \*nix shell would. |
| `KCompletion::CompletionPopup` | `5` | Lists all possible matches in a popup list box to choose from. |
| `KCompletion::CompletionPopupAuto` | `6` | Lists all possible matches in a popup list box to choose from, and automatically fills the result whenever possible. |

## Property Documentation {#property-documentation}

### ignoreCase : bool {#ignoreCase-prop}

**Access functions:**

- `bool` **[ignoreCase](kcompletion.md#ignoreCase)**() const
- virtual `void` **[setIgnoreCase](kcompletion.md#setIgnoreCase)**(`bool` *ignoreCase*)

### items : QStringList {#items-prop}

**Access functions:**

- `QStringList` **[items](kcompletion.md#items)**() const
- virtual `void` **[setItems](kcompletion.md#setItems)**(const `QStringList` &*itemList*)

### order : CompOrder {#order-prop}

**Access functions:**

- `KCompletion::CompOrder` **[order](kcompletion.md#order)**() const
- virtual `void` **[setOrder](kcompletion.md#setOrder)**(`KCompletion::CompOrder` *order*)

## Member Function Documentation {#member-function-documentation}

### KCompletion::KCompletion() {#KCompletion}

Constructor, nothing special here :)

### \[slot\] void KCompletion::addItem(const QString &*item*) {#addItem}

Adds an item to the list of available completions. Resets the current item state ([previousMatch](kcompletion.md#previousMatch)() and [nextMatch](kcompletion.md#nextMatch)() won't work the next time they are called).

`item` the item to add

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kCompletion, qOverload<const QString &>(&KCompletion::addItem));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kCompletion, [receiver = kCompletion](const QString &item) { receiver->addItem(item); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).

### \[slot\] void KCompletion::addItem(const QString &*item*, uint *weight*) {#addItem-1}

Adds an item to the list of available completions. Resets the current item state ([previousMatch](kcompletion.md#previousMatch)() and [nextMatch](kcompletion.md#nextMatch)() won't work the next time they are called).

Sets the weight of the item to `weight` or adds it to the current weight if the item is already available. The weight has to be greater than 1 to take effect (default weight is 1).

`item` the item to add

`weight` the weight of the item, default is 1

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kCompletion, qOverload<const QString &, uint>(&KCompletion::addItem));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kCompletion, [receiver = kCompletion](const QString &item, uint weight) { receiver->addItem(item, weight); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).

### QStringList KCompletion::allMatches() {#allMatches}

Returns a list of all items matching the last completed string. It might take some time if you have a lot of items.

*See also* [substringCompletion](kcompletion.md#substringCompletion)

### QStringList KCompletion::allMatches(const QString &*string*) {#allMatches-1}

Returns a list of all items matching `string`.

### KCompletionMatches KCompletion::allWeightedMatches() {#allWeightedMatches}

Returns a list of all items matching the last completed string. It might take some time if you have a lot of items. The matches are returned as [KCompletionMatches](kcompletionmatches.md), which also keeps the weight of the matches, allowing you to modify some matches or merge them with matches from another call to allWeightedMatches(), and sort the matches after that in order to have the matches ordered correctly.

*See also* [substringCompletion](kcompletion.md#substringCompletion)

### KCompletionMatches KCompletion::allWeightedMatches(const QString &*string*) {#allWeightedMatches-1}

Returns a list of all items matching `string`.

### \[virtual slot\] void KCompletion::clear() {#clear}

Removes all inserted items.

### KCompletion::CompletionMode KCompletion::completionMode() const {#completionMode}

Returns the current completion mode, default is [CompletionPopup](kcompletion.md#CompletionMode-enum)

*See also* [setCompletionMode](kcompletion.md#setCompletionMode), [CompletionMode](kcompletion.md#CompletionMode-enum)

### bool KCompletion::hasMultipleMatches() const {#hasMultipleMatches}

Returns `true` when more than one match is found.

*See also* [multipleMatches](kcompletion.md#multipleMatches)

### bool KCompletion::ignoreCase() const {#ignoreCase}

Returns whether [KCompletion](kcompletion.md) acts case insensitively or not.

Default is `false` (case sensitive).

> **Note:** Getter function for property [ignoreCase](kcompletion.md#ignoreCase-prop).

*See also* [setIgnoreCase](kcompletion.md#setIgnoreCase)

### \[slot\] void KCompletion::insertItems(const QStringList &*items*) {#insertItems}

Inserts `items` into the list of possible completions.

It does the same as [setItems](kcompletion.md#setItems)(), but without calling [clear](kcompletion.md#clear)() before.

`items` the items to insert

### bool KCompletion::isEmpty() const {#isEmpty}

Returns `true` if the completion object contains no entries.

### QStringList KCompletion::items() const {#items}

Returns a list of all items inserted into [KCompletion](kcompletion.md). This is useful if you need to save the state of a [KCompletion](kcompletion.md) object and restore it later.

> **Note:** When [order](kcompletion.md#order)() == Weighted, then every item in the stringlist has its weight appended, delimited by a colon. E.g. an item "www.kde.org" might look like "www.kde.org:4", where 4 is the weight. This is necessary so that you can save the items along with its weighting on disk and load them back with [setItems](kcompletion.md#setItems)(), restoring its weight as well. If you really don't want the appended weightings, call [setOrder](kcompletion.md#setOrder)( [KCompletion::Insertion](kcompletion.md#CompOrder-enum) ) before calling items().

> **Note:** Getter function for property [items](kcompletion.md#items-prop).

*See also* [setItems](kcompletion.md#setItems)

### \[virtual\] const QString &KCompletion::lastMatch() const {#lastMatch}

Returns the last match. Might be useful if you need to check whether a completion is different from the last one.

QString() is returned when there is no last match.

### \[virtual slot\] QString KCompletion::makeCompletion(const QString &*string*) {#makeCompletion}

Attempts to find an item in the list of available completions that begins with `string`. Will either return the first matching item (if there is more than one match) or QString(), if no match is found.

In the latter case, a sound will be emitted, depending on soundsEnabled(). If a match is found, it will be emitted via the signal [match](kcompletion.md#match)().

If this is called twice or more with the same string while no items were added or removed in the meantime, all available completions will be emitted via the signal [matches](kcompletion.md#matches)(). This happens only in shell-completion mode.

`string` the string to complete

Returns the matching item, or QString() if there is no matching item.

*See also* [substringCompletion](kcompletion.md#substringCompletion)

### \[signal\] void KCompletion::match(const QString &*item*) {#match}

This signal is emitted when a match is found.

In particular, [makeCompletion](kcompletion.md#makeCompletion)(), [previousMatch](kcompletion.md#previousMatch)() and [nextMatch](kcompletion.md#nextMatch)() all emit this signal; [makeCompletion](kcompletion.md#makeCompletion)() will only emit it when a match is found, but the other methods will always emit it (and so may emit it with an empty string).

`item` the matching item, or QString() if there were no more matching items.

### \[signal\] void KCompletion::matches(const QStringList &*matchlist*) {#matches}

This signal is emitted by [makeCompletion](kcompletion.md#makeCompletion)() in shell-completion mode when the same string is passed to [makeCompletion](kcompletion.md#makeCompletion)() multiple times in a row.

`matchlist` the list of all matching items

### \[signal\] void KCompletion::multipleMatches() {#multipleMatches}

This signal is emitted when calling [makeCompletion](kcompletion.md#makeCompletion)() and more than one matching item is found.

*See also* [hasMultipleMatches](kcompletion.md#hasMultipleMatches)

### \[slot\] QString KCompletion::nextMatch() {#nextMatch}

Returns the next item from the list of matching items.

When reaching the last item, the list is rotated, so it will return the first match and a sound is emitted (depending on soundsEnabled()).

Returns the next item from the list of matching items. When there is no match, QString() is returned and a sound is emitted.

### KCompletion::CompOrder KCompletion::order() const {#order}

Returns the completion order.

> **Note:** Getter function for property [order](kcompletion.md#order-prop).

*See also* [setOrder](kcompletion.md#setOrder)

### \[virtual protected\] void KCompletion::postProcessMatch(QString \**match*) const {#postProcessMatch}

This method is called after a completion is found and before the matching string is emitted. You can override this method to modify the string that will be emitted. This is necessary e.g. in KUrlCompletion(), where files with spaces in their names are shown escaped ("filename with spaces"), but stored unescaped inside [KCompletion](kcompletion.md). Never delete that pointer!

Default implementation does nothing.

`match` the match to process

*See also* [postProcessMatches](kcompletion.md#postProcessMatches)

### \[virtual protected\] void KCompletion::postProcessMatches(KCompletionMatches \**matches*) const {#postProcessMatches}

This method is called before a list of all available completions is emitted via \#[matches](kcompletion.md#matches)(). You can override this method to modify the found items before \#[match](kcompletion.md#match)() or \#[matches](kcompletion.md#matches)() are emitted. Never delete that pointer!

Default implementation does nothing.

`matches` the matches to process

*See also* [postProcessMatch](kcompletion.md#postProcessMatch)

### \[virtual protected\] void KCompletion::postProcessMatches(QStringList \**matchList*) const {#postProcessMatches-1}

This method is called before a list of all available completions is emitted via [matches](kcompletion.md#matches)(). You can override this method to modify the found items before [match](kcompletion.md#match)() or [matches](kcompletion.md#matches)() are emitted. Never delete that pointer!

Default implementation does nothing.

`matchList` the matches to process

*See also* [postProcessMatch](kcompletion.md#postProcessMatch)

### \[slot\] QString KCompletion::previousMatch() {#previousMatch}

Returns the next item from the list of matching items.

When reaching the beginning, the list is rotated so it will return the last match and a sound is emitted (depending on soundsEnabled()).

Returns the next item from the list of matching items. When there is no match, QString() is returned and a sound is emitted.

### \[slot\] void KCompletion::removeItem(const QString &*item*) {#removeItem}

Removes an item from the list of available completions. Resets the current item state ([previousMatch](kcompletion.md#previousMatch)() and [nextMatch](kcompletion.md#nextMatch)() won't work the next time they are called).

`item` the item to remove

### \[virtual\] void KCompletion::setCompletionMode(KCompletion::CompletionMode *mode*) {#setCompletionMode}

Sets the completion mode.

`mode` the completion mode

*See also* [completionMode](kcompletion.md#completionMode)(), [CompletionMode](kcompletion.md#CompletionMode-enum)

### \[virtual\] void KCompletion::setIgnoreCase(bool *ignoreCase*) {#setIgnoreCase}

Setting this to true makes [KCompletion](kcompletion.md) behave case insensitively.

E.g. [makeCompletion](kcompletion.md#makeCompletion)("CA"); might return "carp\\cs.tu-berlin.de".

Default is false (case sensitive).

`ignoreCase` true to ignore the case

> **Note:** Setter function for property [ignoreCase](kcompletion.md#ignoreCase-prop).

*See also* [ignoreCase](kcompletion.md#ignoreCase)

### \[virtual slot\] void KCompletion::setItems(const QStringList &*itemList*) {#setItems}

Sets the list of items available for completion. Removes all previous items.

> **Note:** When [order](kcompletion.md#order)() == Weighted, then the weighting is looked up for every item in the stringlist. Every item should have ":number" appended, where number is an unsigned integer, specifying the weighting. If you don't like this, call [setOrder](kcompletion.md#setOrder)([KCompletion::Insertion](kcompletion.md#CompOrder-enum)) before calling setItems().

`itemList` the list of items that are available for completion

> **Note:** Setter function for property [items](kcompletion.md#items-prop).

*See also* [items](kcompletion.md#items)

### \[virtual\] void KCompletion::setOrder(KCompletion::CompOrder *order*) {#setOrder}

[KCompletion](kcompletion.md) offers three different ways in which it offers its items:

- in the order of insertion
- sorted alphabetically
- weighted

Choosing weighted makes [KCompletion](kcompletion.md) perform an implicit weighting based on how often an item is inserted. Imagine a web browser with a location bar, where the user enters URLs. The more often a URL is entered, the higher priority it gets.

> **Note:** Setting the order to sorted only affects new inserted items, already existing items will stay in the current order. So you probably want to call setOrder(Sorted) before inserting items if you want everything sorted.

Default is insertion order.

`order` the new order

> **Note:** Setter function for property [order](kcompletion.md#order-prop).

*See also* [order](kcompletion.md#order)

### \[protected\] void KCompletion::setShouldAutoSuggest(bool *shouldAutosuggest*) {#setShouldAutoSuggest}

Deriving classes may set this property and control whether the auto-suggestion should be displayed for the last completion operation performed.

Applies for [CompletionPopupAuto](kcompletion.md#CompletionMode-enum) and [CompletionAuto](kcompletion.md#CompletionMode-enum) modes.

*See also* [shouldAutoSuggest](kcompletion.md#shouldAutoSuggest)()

### \[protected\] void KCompletion::setSorterFunction(KCompletion::SorterFunction *sortFunc*) {#setSorterFunction}

Sets a custom function to be used to sort the matches. Can be set to nullptr to use the default sorting logic.

Applies for [CompOrder::Sorted](kcompletion.md#CompOrder-enum) mode.

### bool KCompletion::shouldAutoSuggest() const {#shouldAutoSuggest}

Informs the caller if they should display the auto-suggestion for the last completion operation performed.

Applies for [CompletionPopupAuto](kcompletion.md#CompletionMode-enum) and [CompletionAuto](kcompletion.md#CompletionMode-enum) modes.

Defaults to `true`, but deriving classes may set it to false in special cases via "[setShouldAutoSuggest](kcompletion.md#setShouldAutoSuggest)".

Returns `true` if auto-suggestion should be displayed for the last completion operation performed.

*See also* [setShouldAutoSuggest](kcompletion.md#setShouldAutoSuggest)()

### QStringList KCompletion::substringCompletion(const QString &*string*) const {#substringCompletion}

Returns a list of all completion items that contain the given `string`. `string` the string to complete

Returns a list of items which contain `text` as a substring, i.e. not necessarily at the beginning.

*See also* [makeCompletion](kcompletion.md#makeCompletion)
