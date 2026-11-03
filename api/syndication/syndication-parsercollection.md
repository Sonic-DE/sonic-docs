---
title: "Syndication::ParserCollection Class"
description: "A collection of format-specific parser implementations."
---

# Syndication::ParserCollection Class

A collection of format-specific parser implementations. [More...](#details)

- **Header:** `#include <Syndication/ParserCollection>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`

[List of all members, including inherited members](syndication-parsercollection-members.md)

## Public Functions

- [void changeMapper(const QString &format, Syndication::Mapper\<T\> \*mapper)](#changeMapper)
- [Syndication::ErrorCode lastError() const](#lastError)
- [QSharedPointer\<T\> parse(const Syndication::DocumentSource &source, const QString &formatHint = QString())](#parse)
- [bool registerParser(Syndication::AbstractParser \*parser, Syndication::Mapper\<T\> \*mapper)](#registerParser)

## Detailed Description {#details}

To parse a feed source, pass it to the [parse](syndication-parsercollection.md#parse)() method of this class.

In most cases, you should use the global singleton instance Syndication::parserCollection().

When loading the source from the web, use Loader instead of using this class directly.

Example code:

```cpp
...
QFile someFile(somePath);
...
DocumentSource src(someFile.readAll());
someFile.close();

FeedPtr feed = parserCollection()->parse(src);

if (feed)
{
    QString title = feed->title();
    QList<ItemPtr> items = feed->items();
    ...
}
```

The template parameter T is the abstraction class parsed documents should be mapped to. If you want to use your own abstraction MyFeed, implement [ParserCollection](syndication-parsercollection.md)\<MyFeed\> (Note that you have to provide mapper implementations for every feed format then).

## Member Function Documentation {#member-function-documentation}

### \[pure virtual\] void ParserCollection::changeMapper(const QString &*format*, Syndication::Mapper\<T\> \**mapper*) {#changeMapper}

Changes the specific format to abstraction mapping for a parser.

`format` the format string of the parser whose mapping should be changed. See [AbstractParser::format](syndication-abstractparser.md#format).

`mapper` Mapper implementation doing the mapping from the format specific representation to abstraction of type T.

### \[pure virtual\] Syndication::ErrorCode ParserCollection::lastError() const {#lastError}

Returns the error code of the last [parse](syndication-parsercollection.md#parse)() call, or Success if [parse](syndication-parsercollection.md#parse)() was successful or not yet called at all.

### \[pure virtual\] QSharedPointer\<T\> ParserCollection::parse(const Syndication::DocumentSource &*source*, const QString &*formatHint* = QString()) {#parse}

tries to parse a given source with the parsers registered. The source is passed to the first parser that accepts it.

`source` The source to be parsed

`formatHint` An optional hint which parser to test first. If there is a parser with the given hint as format string (e.g., "rss2", "atom", "rdf"...), it is asked first to accept the source. This can avoid unnecessary [AbstractParser::accept](syndication-abstractparser.md#accept)() checks and speed up parsing. See also [AbstractParser::format](syndication-abstractparser.md#format)().

Returns the feed document parsed from the source, or NULL if no parser accepted the source.

### \[pure virtual\] bool ParserCollection::registerParser(Syndication::AbstractParser \**parser*, Syndication::Mapper\<T\> \**mapper*) {#registerParser}

Adds a parser and corresponding mapper to the collection.

[AbstractParser::format](syndication-abstractparser.md#format)() must be unique in the collection. If there is already a parser with the same format string, the parser isn't added.

> **Note:** ownership for both `parser` and `mapper` is taken by the implementation, so don't delete them in your code!

`parser` The parser to be registered

`mapper` the mapper that should be used for building the abstraction

Returns whether the parser was successfully registered or not.
