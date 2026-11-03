---
title: "Syndication::ElementWrapper Class"
description: "A wrapper for XML elements."
---

# Syndication::ElementWrapper Class

A wrapper for XML elements. [More...](#details)

- **Header:** `#include <Syndication/ElementWrapper>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`
- **Inherited By:** [Syndication::Atom::Category](syndication-atom-category.md), [Syndication::Atom::Content](syndication-atom-content.md), [Syndication::Atom::Entry](syndication-atom-entry.md), [Syndication::Atom::EntryDocument](syndication-atom-entrydocument.md), [Syndication::Atom::FeedDocument](syndication-atom-feeddocument.md), [Syndication::Atom::Generator](syndication-atom-generator.md), [Syndication::Atom::Link](syndication-atom-link.md), [Syndication::Atom::Person](syndication-atom-person.md), and [Syndication::Atom::Source](syndication-atom-source.md)

[List of all members, including inherited members](syndication-elementwrapper-members.md)

## Public Functions

- [ElementWrapper()](#ElementWrapper)
- [ElementWrapper(const QDomElement &element)](#ElementWrapper-1)
- [ElementWrapper(const Syndication::ElementWrapper &other)](#ElementWrapper-2)
- [QString attribute(const QString &name, const QString &defValue = QString()) const](#attribute)
- [QString attributeNS(const QString &nsURI, const QString &localName, const QString &defValue = QString()) const](#attributeNS)
- [QString childNodesAsXML() const](#childNodesAsXML)
- [QString completeURI(const QString &uri) const](#completeURI)
- [const QDomElement &element() const](#element)
- [QList\<QDomElement\> elementsByTagName(const QString &tagName) const](#elementsByTagName)
- [QList\<QDomElement\> elementsByTagNameNS(const QString &nsURI, const QString &tagName) const](#elementsByTagNameNS)
- [QString extractElementText(const QString &tagName) const](#extractElementText)
- [QString extractElementTextNS(const QString &namespaceURI, const QString &localName) const](#extractElementTextNS)
- [QDomElement firstElementByTagNameNS(const QString &nsURI, const QString &tagName) const](#firstElementByTagNameNS)
- [bool hasAttribute(const QString &name) const](#hasAttribute)
- [bool hasAttributeNS(const QString &nsURI, const QString &localName) const](#hasAttributeNS)
- [bool isNull() const](#isNull)
- [QString text() const](#text)
- [QString xmlBase() const](#xmlBase)
- [QString xmlLang() const](#xmlLang)
- [Syndication::ElementWrapper &ElementWrapper::operator=(const Syndication::ElementWrapper &other)](#operator-eq)
- [bool ElementWrapper::operator==(const Syndication::ElementWrapper &other) const](#operator-eq-eq)

## Static Public Members

- [QString childNodesAsXML(const QDomElement &parent)](#childNodesAsXML-1)

## Detailed Description {#details}

This is the base class for the (lazy) wrappers used in the RSS2 and Atom parsers. The wrapped element can be accessed via [element](syndication-elementwrapper.md#element)(). It also contains several helper functions for XML processing.

## Member Function Documentation {#member-function-documentation}

### ElementWrapper::ElementWrapper() {#ElementWrapper}

Creates a element wrapper wrapping a null element. [isNull](syndication-elementwrapper.md#isNull)() will return `true` for these instances.

### ElementWrapper::ElementWrapper(const QDomElement &*element*) {#ElementWrapper-1}

Creates an element wrapper wrapping the DOM element `element`

`element` the element to wrap

### ElementWrapper::ElementWrapper(const Syndication::ElementWrapper &*other*) {#ElementWrapper-2}

Copy constructor. The instances share the same element.

`other` the element wrapper to copy

### QString ElementWrapper::attribute(const QString &*name*, const QString &*defValue* = QString()) const {#attribute}

Returns the attribute called name.

If the attribute does not exist defValue is returned. (which is a null string by default).

`name` tag name

`defValue` the default value

### QString ElementWrapper::attributeNS(const QString &*nsURI*, const QString &*localName*, const QString &*defValue* = QString()) const {#attributeNS}

Returns the attribute with the local name `localName` and the namespace URI `nsURI`.

If the attribute does not exist `defValue` is returned (which is a null string by default).

`nsURI` namespace URI

`localName` local tag name

`defValue` the default value

### QString ElementWrapper::childNodesAsXML() const {#childNodesAsXML}

Returns the child nodes of the wrapped element as XML.

See childNodesAsXML(const QDomElement& parent) for details

Returns XML serialization of the wrapped element's children

### \[static\] QString ElementWrapper::childNodesAsXML(const QDomElement &*parent*) {#childNodesAsXML-1}

Concatenates the XML representations of all children.

Example: If `parent` is an `xhtml:body` element like

```cpp
<xhtml:body><p>foo</p><blockquote>bar</blockquote></xhtml:body>
```

this function returns

```cpp
<p>foo</p><blockquote>bar</blockquote>
```

namespace and xml:base information are preserved.

`parent` the DOM element whose children should be returned as XML

Returns XML serialization of parent's children

### QString ElementWrapper::completeURI(const QString &*uri*) const {#completeURI}

Completes relative URIs with a prefix specified via xml:base.

Example:

```cpp
xml:base="http://www.foo.org/", uri="announcements/bar.html"
```

is completed to `http://www.foo.org/announcements/bar.html`

See also [xmlBase](syndication-elementwrapper.md#xmlBase)().

`uri` a possibly relative URI

Returns the resolved, absolute URI (using xml:base), if `uri` is a relative, valid URI.

If `uri` is not valid, absolute, or no xml:base is set in the scope of this element, `uri` is returned unmodified.

### const QDomElement &ElementWrapper::element() const {#element}

returns the wrapped resource.

### QList\<QDomElement\> ElementWrapper::elementsByTagName(const QString &*tagName*) const {#elementsByTagName}

Returns all child elements with tag name `tagName`

Contrary to QDomElement::elementsByTagName() only direct descendents are returned.

`tagName` the tag name of the elements to extract

Returns a list of child elements with the given tag name

### QList\<QDomElement\> ElementWrapper::elementsByTagNameNS(const QString &*nsURI*, const QString &*tagName*) const {#elementsByTagNameNS}

Returns all child elements with tag name `tagName` and namespace URI `nsURI`.

Contrary to QDomElement::elementsByTagNameNS() only direct descendents are returned

`nsURI` the namespace URI

`tagName` the local name (local within its namespace) of the element to search for

Returns a list of child elements with the given namespace URI and tag name

### QString ElementWrapper::extractElementText(const QString &*tagName*) const {#extractElementText}

Extracts the text from a child element, ignoring namespaces. For instance, when the wrapped element is `<thisElement>`:

```cpp
<thisElement>
    <title>Hi there</title>
</thisElement>
```

extractElementText("title") will return the text content of `title`, "Hi there".

`tagName` the name of the element to extract

Returns the (trimmed) text content of `tagName`, or a null string if there is no such tag

### QString ElementWrapper::extractElementTextNS(const QString &*namespaceURI*, const QString &*localName*) const {#extractElementTextNS}

Extracts the text from a child element, respecting namespaces. If there is more than one child with the same tag name, the first one is processed.

For instance, when the wrapped element is `<thisElement>`:

```cpp
<thisElement>
    <atom:title>Hi there</atom:title>
</thisElement>
```

```cpp
extractElementText("http://www.w3.org/2005/Atom", "title")
```

will return the text content of `atom:title`, "Hi there". (Assuming that "atom" is defined as "http://www.w3.org/2005/Atom")

`namespaceURI` the namespace URI of the element to extract

`localName` the local name (local within its namespace) of the element to extract

Returns the (trimmed) text content of `localName`, or a null string if there is no such tag

### QDomElement ElementWrapper::firstElementByTagNameNS(const QString &*nsURI*, const QString &*tagName*) const {#firstElementByTagNameNS}

Searches the direct children of the wrapped element for an element with a given namespace and tag name.

`nsURI` the namespace URI

`tagName` the local name (local within its namespace) of the element to search for

Returns the first child element with the given namespace URI and tag name, or a null element if no such element was found.

### bool ElementWrapper::hasAttribute(const QString &*name*) const {#hasAttribute}

Returns `true` if this element has an attribute called `name`; otherwise returns `false`.

`name` the attribute name (without namespace)

### bool ElementWrapper::hasAttributeNS(const QString &*nsURI*, const QString &*localName*) const {#hasAttributeNS}

Returns `true` if this element has an attribute with the local name `localName` and the namespace URI `nsURI`; otherwise returns `false`.

`nsURI` namespace URI

`localName` local attribute name

### bool ElementWrapper::isNull() const {#isNull}

Returns `true` if isNull() is true for the wrapped element, `false` otherwise

### QString ElementWrapper::text() const {#text}

Returns the wrapped element's text or an empty string.

For more information, see QDomElement::text();

### QString ElementWrapper::xmlBase() const {#xmlBase}

Returns the xml:base value to be used for the wrapped element.

The xml:base attribute establishes the base URI for resolving any relative references found in its scope (its own element and all descendants). (See also [completeURI](syndication-elementwrapper.md#completeURI)())

### QString ElementWrapper::xmlLang() const {#xmlLang}

Returns the xml:lang value to be used for the wrapped element.

The xml:lang attribute indicates the natural language for its element and all descendants.

### Syndication::ElementWrapper &ElementWrapper::operator=(const Syndication::ElementWrapper &*other*) {#operator-eq}

Assigns another element wrapper to this one. Both instances share the same wrapped element instance.

`other` the element wrapper to assign

Returns reference to this instance

### bool ElementWrapper::operator==(const Syndication::ElementWrapper &*other*) const {#operator-eq-eq}

Compares two wrappers.

Two wrappers are equal if and only if the wrapped elements are equal.

`other` another element wrapper to compare to
