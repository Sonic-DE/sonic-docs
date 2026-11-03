---
title: "Syndication Namespace"
description: "RSS/Atom parser library."
---

# Syndication Namespace

RSS/Atom parser library. [More...](#details)

- Header: Syndication/Global
- CMake: find\_package(KF6 REQUIRED COMPONENTS Syndication) target\_link\_libraries(mytarget PRIVATE KF6::Syndication)

## Detailed Description {#details}

## Namespaces {#namespaces}

### namespace Syndication::Atom

(Atom 0.3 documents are converted by the parser)

## Classes {#classes}

### class [AbstractParser](syndication-abstractparser.md)

Interface for all parsers.

### class [Category](syndication-category.md)

A category for categorizing items or whole feeds.

### class [DataRetriever](syndication-dataretriever.md)

Abstract baseclass for all data retriever classes.

### class [DocumentSource](syndication-documentsource.md)

Represents the source of a syndication document, as read from the downloaded file.

### class [DocumentVisitor](syndication-documentvisitor.md)

Visitor interface, following the Visitor design pattern.

### class [ElementWrapper](syndication-elementwrapper.md)

A wrapper for XML elements.

### class [Enclosure](syndication-enclosure.md)

An enclosure describes a (media) file available on the net.

### class [Feed](syndication-feed.md)

This class represents a feed document ("Channel" in RSS, "Feed" in Atom).

### class [Image](syndication-image.md)

This class represents an image file on the web.

### class [Item](syndication-item.md)

An item from a news feed.

### class [Loader](syndication-loader.md)

This class is the preferred way of loading feed sources.

### class [Mapper](syndication-mapper.md)

A mapper maps an [SpecificDocument](syndication-specificdocument.md) to something else.

### class [ParserCollection](syndication-parsercollection.md)

A collection of format-specific parser implementations.

### class [Person](syndication-person.md)

Person objects hold information about a person, such as the author of the content syndicated in the feed.

### class [SpecificDocument](syndication-specificdocument.md)

Document interface for format-specific feed documents as parsed from a document source (see [DocumentSource](syndication-documentsource.md)).

### class [SpecificItem](syndication-specificitem.md)

Interface for all format-specific item-like classes, such as RSS2/RDF items, and Atom entries.

### class [SpecificItemVisitor](syndication-specificitemvisitor.md)

Visitor interface, following the Visitor design pattern.

## Type Documentation {#type-documentation}

### enum Syndication::DateFormat {#DateFormat-enum}

date formats supported by date parsers

| Constant | Value | Description |
| --- | --- | --- |
| `Syndication::ISODate` | `0` | ISO 8601 extended format. (date: "2003-12-13",datetime: "2003-12-13T18:30:02.25", datetime with timezone: "2003-12-13T18:30:02.25+01:00") |
| `Syndication::RFCDate` | `1` | RFC 822. (e.g. "Sat, 07 Sep 2002 00:00:01 GMT") |

### enum Syndication::ErrorCode {#ErrorCode-enum}

error code indicating fetching or parsing errors

| Constant | Value | Description |
| --- | --- | --- |
| `Syndication::Success` | `0` | No error occurred, feed was fetched and parsed successfully |
| `Syndication::Aborted` | `1` | File downloading/parsing was aborted by the user |
| `Syndication::Timeout` | `2` | File download timed out |
| `Syndication::UnknownHost` | `3` | The hostname couldn't get resolved to an IP address |
| `Syndication::FileNotFound` | `4` | The host was contacted successfully, but reported a 404 error |
| `Syndication::OtherRetrieverError` | `5` | Retriever error not covered by the error codes above. This is returned if a custom [DataRetriever](syndication-dataretriever.md) was used. See the retriever-specific status byte for more information on the occurred error. |
| `Syndication::InvalidXml` | `6` | The XML is invalid. This is returned if no parser accepts the source and the DOM document can't be parsed. It is not returned if the source is not valid XML but a (non-XML) parser accepts it. |
| `Syndication::XmlNotAccepted` | `7` | The source is valid XML, but no parser accepted it. |
| `Syndication::InvalidFormat` | `8` | The source was accepted by a parser, but the actual parsing failed. As our parser implementations currently do not validate the source ("parse what you can get"), this code will be rarely seen. |

## Function Documentation {#function-documentation}

### QString Syndication::commentApiNamespace() {#commentApiNamespace}

wellformedweb.org's RSS namespace for comment functionality "http://wellformedweb.org/CommentAPI/"

### QString Syndication::contentNameSpace() {#contentNameSpace}

### QString Syndication::convertNewlines(const QString &*str*) {#convertNewlines}

replaces newlines ("\\n") by \<br/\>

`str` string to convert

### QString Syndication::dublinCoreNamespace() {#dublinCoreNamespace}

### QString Syndication::escapeSpecialCharacters(const QString &*str*) {#escapeSpecialCharacters}

replaces the characters \<, \>, &, ", ' with &lt; &gt; &amp;, &quot; &apos;.

`str` the string to escape

### QString Syndication::htmlToPlainText(const QString &*html*) {#htmlToPlainText}

converts a HTML string to plain text

`html` string in HTML format

Returns stripped text

### bool Syndication::isHtml(const QString &*str*) {#isHtml}

guesses whether a string contains plain text or HTML

`str` the string in unknown format

Returns `true` if the heuristic thinks it's HTML, `false` if thinks it is plain text

### QString Syndication::itunesNamespace() {#itunesNamespace}

### QString Syndication::normalize(const QString &*str*) {#normalize}

Ensures HTML formatting for a string.

guesses via [isHtml](syndication.md#isHtml)() if `str` contains HTML or plain text, and returns [plainTextToHtml](syndication.md#plainTextToHtml)(str) if it thinks it is plain text, or the unmodified `str` otherwise.

`str` a string with unknown content Returns string as HTML (as long as the heuristics work)

### QString Syndication::normalize(const QString &*str*, bool *isCDATA*, bool *containsMarkup*) {#normalize-1}

normalizes a string based on feed-wide properties of tag content. It is based on the assumption that all items in a feed encode their title/description content in the same way (CDATA or not, plain text vs. HTML). isCDATA and containsMarkup are determined once by the feed, and then passed to this method.

The returned string contains HTML, with special characters \<, \>, &, ", and ' escaped, and all other entities resolved. Whitespace is collapsed, relevant whitespace is replaced by respective HTML tags (\<br/\>).

`str` a string

`isCDATA` whether the feed uses CDATA for the tag `str` was read from

`containsMarkup` whether the feed uses HTML markup in the tag `str` was read from.

Returns string as HTML (as long as the heuristics work)

### Syndication::FeedPtr Syndication::parse(const Syndication::DocumentSource &*src*, const QString &*formatHint* = QString()) {#parse}

parses a document from a source and returns a new Feed object wrapping the feed content.

Shortcut for [parserCollection](syndication.md#parserCollection)()-\>parse().

See [ParserCollection::parse](syndication-parsercollection.md#parse)() for more details.

`src` the document source to parse

`formatHint` an optional hint which format to test first

### uint Syndication::parseDate(const QString &*str*, Syndication::DateFormat *hint* = RFCDate) {#parseDate}

parses a date string in ISO (see [parseISODate](syndication.md#parseISODate)()) or RFC 822 (see [parseRFCDate](syndication.md#parseRFCDate)()) format.

It tries both parsers and returns the first valid parsing result found (or 0 otherwise).

To speed up parsing, you can give a hint which format you expect. The method will try the corresponding parser first then.

`str` a date string

`hint` the expected format

Returns parsed date in seconds since epoch, 0 if no date could be parsed from the string.

### uint Syndication::parseISODate(const QString &*str*) {#parseISODate}

parses a date string in ISO 8601 extended format. (date: "2003-12-13",datetime: "2003-12-13T18:30:02.25", datetime with timezone: "2003-12-13T18:30:02.25+01:00")

`str` a string in ISO 8601 format

Returns parsed date in seconds since epoch, 0 if no date could be parsed from the string.

### uint Syndication::parseRFCDate(const QString &*str*) {#parseRFCDate}

parses a date string as defined in RFC 822. (Sat, 07 Sep 2002 00:00:01 GMT)

`str` a string in RFC 822 format

Returns parsed date in seconds since epoch, 0 if no date could be parsed from the string.

### Syndication::ParserCollection\<Syndication::Feed\> \*Syndication::parserCollection() {#parserCollection}

The default [ParserCollection](syndication-parsercollection.md) instance parsing a [DocumentSource](syndication-documentsource.md) into a Feed object.

Use this to parse a local file or a otherwise manually created [DocumentSource](syndication-documentsource.md) object.

To retrieve a feed from the web, use Loader instead.

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

### Syndication::PersonPtr Syndication::personFromString(const QString &*str*) {#personFromString}

Parses a person object from a string by identifying name and email address in the string. Currently detected variants are: "foo@bar.com", "Foo", "Foo \<foo@bar.com\>", "foo@bar.com (Foo)".

`str` the string to parse the person from.

Returns a Person object containing the parsed information.

### QString Syndication::plainTextToHtml(const QString &*plainText*) {#plainTextToHtml}

converts a plain text string to HTML

`plainText` a string in plain text.

### QString Syndication::resolveEntities(const QString &*str*) {#resolveEntities}

resolves entities to respective unicode chars.

`str` a string

### QString Syndication::slashNamespace() {#slashNamespace}

"slash" namespace http://purl.org/rss/1.0/modules/slash/

### bool Syndication::stringContainsMarkup(const QString &*str*) {#stringContainsMarkup}

guesses whether a string contains (HTML) markup or not. This implements not an exact check for valid HTML markup, but a simple (and relatively fast) heuristic.

`str` the string that might or might not contain markup

Returns `true` if the heuristic thinks it contains markup, `false` if thinks it is markup-free plain text

### QString Syndication::xhtmlNamespace() {#xhtmlNamespace}

### QString Syndication::xmlNamespace() {#xmlNamespace}
