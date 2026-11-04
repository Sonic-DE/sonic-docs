---
title: "KFuzzyMatcher Namespace"
description: "This namespace contains functions for fuzzy matching a list of strings against a pattern."
---

# KFuzzyMatcher Namespace

This namespace contains functions for fuzzy matching a list of strings against a pattern. [More...](#details)

- **Header:** `#include <KFuzzyMatcher>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`

## Detailed Description {#details}

This code is ported to Qt from lib\_fts: https://github.com/forrestthewoods/lib_fts which tries to replicate SublimeText like fuzzy matching.

> **Note:** All character matches will happen sequentially. That means that this function is not typo tolerant i.e., "gti" will not match "git", but "gt" will. All methods in here are stateless i.e., the input string will not be modified. Also note that strings in all the functions in this namespace will be matched case-insensitively.

Limitations:

- Currently this will match only strings with length \< 256 correctly. This is because we intend on matching a pattern against words / short strings and not paragraphs.
- No more than 256 matches will happen.

If you are using this with [QSortFilterProxyModel](https://doc.qt.io/qt-6/qsortfilterproxymodel.html), you need to override both [QSortFilterProxyModel::lessThan](https://doc.qt.io/qt-6/qsortfilterproxymodel.html#lessThan) and [QSortFilterProxyModel::filterAcceptsRow](https://doc.qt.io/qt-6/qsortfilterproxymodel.html#filterAcceptsRow). A simple example:

```cpp
bool filterAcceptsRow(int sourceRow, const QModelIndex &sourceParent) const override
{
    int score = 0;
    const auto idx = sourceModel()->index(sourceRow, 0, sourceParent);
    const auto actionName = idx.data().toString().splitRef(QLatin1Char(':')).at(1);
    const bool res = kfts::fuzzy_match_sequential(m_pattern, actionName, score);
    // store the score in the source model
    sourceModel()->setData(idx, score, ScoreRole);
    return res;
}

bool lessThan(const QModelIndex &sourceLeft, const QModelIndex &sourceRight) const override
{
    // use the score here to sort
    const int l = sourceLeft.data(ScoreRole).toInt();
    const int r = sourceRight.data(ScoreRole).toInt();
    return l < r;
}
```

Additionally you must not use invalidateFilter() if you go with the above approach. Instead use beginResetModel()/endResetModel():

```cpp
Q_SLOT void setFilterString(const QString &string)
{
    beginResetModel();
    m_pattern = string;
    endResetModel();
}
```

## Classes {#classes}

### struct [KFuzzyMatcher::Range](kfuzzymatcher-range.md)

### struct [KFuzzyMatcher::Result](kfuzzymatcher-result.md)

## Type Documentation {#type-documentation}

### enum KFuzzyMatcher::RangeType {#RangeType-enum}

The type of matches to consider when requesting for ranges.

| Constant | Value | Description |
| --- | --- | --- |
| `KFuzzyMatcher::RangeType::FullyMatched` | `0` | We want ranges only where the pattern fully matches the user supplied string |
| `KFuzzyMatcher::RangeType::All` | `1` | We want ranges for all matches, even if the pattern partially matched the user supplied string |

*See also* [matchedRanges](kfuzzymatcher.md#matchedRanges)

## Function Documentation {#function-documentation}

### KFuzzyMatcher::Result KFuzzyMatcher::match(QStringView *pattern*, QStringView *str*) {#match}

This is the main function which does scored fuzzy matching.

The return value of this function contains Result\#score which should be used to sort the results. Without sorting of the results this function won't be very effective.

If `pattern` is empty, the function will return `true`

`pattern` to search for. For e.g., text entered by a user to filter a list or model

`str` the current string from your list of strings

Returns a Result type with score of this match and whether the match was successful. If there is no match, score is zero. If the match is successful, score must be used to sort the results.

### bool KFuzzyMatcher::matchSimple(QStringView *pattern*, QStringView *str*) {#matchSimple}

Simple fuzzy matching of chars in `pattern` with chars in `str` sequentially. If there is a match, it will return true and false otherwise. There is no scoring. You should use this if score is not important for you and only matching is important.

If `pattern` is empty, the function will return `true`

`pattern` to search for. For e.g., text entered by a user to filter a list

`str` the current string from your list of strings

Returns `true` on sucessful match

### QList\<KFuzzyMatcher::Range\> KFuzzyMatcher::matchedRanges(QStringView *pattern*, QStringView *str*, KFuzzyMatcher::RangeType *type* = RangeType::FullyMatched) {#matchedRanges}

A function which returns the positions + lengths where the `pattern` matched inside the `str`. The resulting ranges can then be utilized to show the user where the matches occurred. Example:

```cpp
String: hello
Pattern: Hlo

Output: [Range{0, 1}, Range{3, 2}]
```

In the above example `"Hlo"` matched inside the string `"hello"` in two places i.e., position 0 and position 3. At position 0 it matched 'h', and at position 3 it matched 'lo'.

The ranges themeselves can't do much so you will have to make the result useful in your own way. Some possible uses can be:

- Transform the result into a vector of `QTextLayout::FormatRange` and then paint them in the view
- Use the result to transform the string into html, for example conver the string from above example to "\<b\>H\</b\>el\<b\>lo\</b\>, and then use `QTextDocument` to paint it into your view.

Example with the first method:

```cpp
auto ranges = KFuzzyMatcher::matchedRanges(pattern, string);
QList<QTextLayout::FormatRange> out;
std::transform(ranges.begin(), ranges.end(), std::back_inserter(out), [](const KFuzzyMatcher::Range &fr){
   return QTextLayout::FormatRange{fr.start, fr.length, QTextCharFormat()};
});

QTextLayout layout(text, font);
layout.beginLayout();
QTextLine line = layout.createLine();
//...
layout.endLayout();

layout.setFormats(layout.formats() + out);
layout.draw(painter, position);
```

If `pattern` is empty, the function will return an empty vector

if `type` is `RangeType::All`, the function will try to get ranges even if the pattern didn't fully match. For example:

```cpp
pattern: "git"
string: "gti"
RangeType: All

Output: [Range{0, 1}, Range{2, 1}]
```

`pattern` to search for. For e.g., text entered by a user to filter a list or model

`str` the current string from your list of strings

`type` whether to consider ranges from full matches only or all matches including partial matches

Returns A vector of ranges containing positions and lengths where the pattern matched. If there was no match, the vector will be empty
