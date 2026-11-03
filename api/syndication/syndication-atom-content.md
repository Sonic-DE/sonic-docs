---
title: "Syndication::Atom::Content Class"
description: "The content element either contains or links the content of an entry."
---

# Syndication::Atom::Content Class

The content element either contains or links the content of an entry. [More...](#details)

- **Header:** `#include <Syndication/Atom/Content>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`
- **Inherits:** [Syndication::ElementWrapper](syndication-elementwrapper.md)

[List of all members, including inherited members](syndication-atom-content-members.md)

## Public Types

- [enum Content::Format](#Format-enum)

## Public Functions

- [Content()](#Content)
- [Content(const QDomElement &element)](#Content-1)
- [Content(const Syndication::Atom::Content &other)](#Content-2)
- [QByteArray asByteArray() const](#asByteArray)
- [QString asString() const](#asString)
- [QString debugInfo() const](#debugInfo)
- [Syndication::Atom::Content::Format format() const](#format)
- [bool isBinary() const](#isBinary)
- [bool isContained() const](#isContained)
- [bool isEscapedHTML() const](#isEscapedHTML)
- [bool isPlainText() const](#isPlainText)
- [bool isXML() const](#isXML)
- [QString src() const](#src)
- [QString type() const](#type)
- [Syndication::Atom::Content &Content::operator=(const Syndication::Atom::Content &other)](#operator-eq)

## Static Public Members

- [Syndication::Atom::Content::Format mapTypeToFormat(const QString &type, const QString &src = QString())](#mapTypeToFormat)

## Detailed Description {#details}

The content is usually plain text or HTML, but arbitrary XML or binary content are also possible. If [isContained](syndication-atom-content.md#isContained)() is false, the content is not contained in the feed source, but linked.

## Member Type Documentation {#member-type-documentation}

### enum Content::Format {#Format-enum}

format of the content.

| Constant | Value | Description |
| --- | --- | --- |
| `Syndication::Atom::Content::PlainText` | `0` | the content is plain text (i.e. "\<", "\>" etc. are text, not markup |
| `Syndication::Atom::Content::EscapedHTML` | `1` | the content is escaped HTML, (i.e., "\<", "\>" etc. are markup) |
| `Syndication::Atom::Content::XML` | `2` | the content is embedded XML |
| `Syndication::Atom::Content::Binary` | `3` | the content is base64-encoded binary content |

## Member Function Documentation {#member-function-documentation}

### Content::Content() {#Content}

creates a null content object.

### \[explicit\] Content::Content(const QDomElement &*element*) {#Content-1}

creates a Content object wrapping an atom:content element.

`element` a DOM element, should be a atom:content element (although not enforced), otherwise this object will not parse anything useful

### Content::Content(const Syndication::Atom::Content &*other*) {#Content-2}

creates a copy of another Content object

`other` the content object to copy

### QByteArray Content::asByteArray() const {#asByteArray}

Returns byte array containing the embedded binary data, or an empty array if the content is not in binary format

### QString Content::asString() const {#asString}

returns the content as string. If the content format is Text, the returned string contains the text as HTML. If the content is embedded XML, the XML is returned as string.

Returns a string representation of the content, or a null string if the content is either binary content or not contained but linked (see [isContained](syndication-atom-content.md#isContained)())

### QString Content::debugInfo() const {#debugInfo}

returns a description of the content object for debugging purposes

### Syndication::Atom::Content::Format Content::format() const {#format}

returns the content format

### bool Content::isBinary() const {#isBinary}

returns whether the content is binary content or not. Use [asByteArray](syndication-atom-content.md#asByteArray)() to access it.

### bool Content::isContained() const {#isContained}

returns whether the content is contained in the feed source, or not. If it is not contained, [src](syndication-atom-content.md#src)() provides a URL to the content.

### bool Content::isEscapedHTML() const {#isEscapedHTML}

returns whether the content is escaped HTML or not Use [asString](syndication-atom-content.md#asString)() to access it

### bool Content::isPlainText() const {#isPlainText}

returns whether the content is plain text or not. Use [asString](syndication-atom-content.md#asString)() to access it.

### bool Content::isXML() const {#isXML}

returns whether the content is embedded XML. Use [element](syndication-elementwrapper.md#element)() to access the DOM tree, or [asString](syndication-atom-content.md#asString)() to get the XML as string.

### \[static\] Syndication::Atom::Content::Format Content::mapTypeToFormat(const QString &*type*, const QString &*src* = QString()) {#mapTypeToFormat}

maps a mimetype to Format enum according to the Atom 1.0 specification

`type` a valid mimetype, or one of "text", "html", "xhtml"

`src` content source, see [src](syndication-atom-content.md#src)() for details.

### QString Content::src() const {#src}

If src() is set, the content of this entry is not contained in the feed source, but available on the net. src() then contains a URL (more precise: IRI reference) linking to remote content. If src is provided, [type](syndication-atom-content.md#type)() should contain a mimetype, instead of "text", "html" or "xhtml".

Returns a null string if the content is contained in the feed source, or a URL linking to the remote content

### QString Content::type() const {#type}

the type of the content. This is either "text" (plain text), "html" (escaped HTML), "xhtml" (embedded XHTML) or a mime type

Returns the content type. If no type is specified, "text" (the default) is returned.

### Syndication::Atom::Content &Content::operator=(const Syndication::Atom::Content &*other*) {#operator-eq}

assigns another content objecct

`other` the Content object to assign
