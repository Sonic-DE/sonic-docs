---
title: "DocBook2Markdown::Converter Class"
description: "Create documentation from DocBook."
---

# DocBook2Markdown::Converter Class

Create documentation from DocBook. [More...](#details)

- **Header:** `#include <Converter>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS DocTools)`  
  `target_link_libraries(mytarget PRIVATE KF6::DocTools)`

[List of all members, including inherited members](docbook2markdown-converter-members.md)

## Public Functions

- [QString resolveLink(const QString &fromSlug, const DocBook2Markdown::PageAnchors &own, const QString &href) const](#resolveLink)
- [void setIndexAggregates(QHash\<QString, DocBook2Markdown::IndexAggregate\> aggregates)](#setIndexAggregates)
- [void setModuleAnchors(QHash\<QString, DocBook2Markdown::PageAnchors\> anchors)](#setModuleAnchors)

## Detailed Description {#details}

Converts QDoc's DocBook output (one article per page) into Markdown for the Winter docs plugin.

Class pages get the Qt reference layout: title, brief, requirements, summary sections rebuilt from the member documentation (QDoc's DocBook writer omits them), Detailed Description and member documentation, with explicit heading anchors. Deprecated members move to their own page.

## Member Function Documentation {#member-function-documentation}

### QString Converter::resolveLink(const QString &*fromSlug*, const DocBook2Markdown::PageAnchors &*own*, const QString &*href*) const {#resolveLink}

The Markdown target for a link on page `fromSlug` (whose own anchors are `own`), or an empty string when the link should become plain text.

### void Converter::setIndexAggregates(QHash\<QString, DocBook2Markdown::IndexAggregate\> *aggregates*) {#setIndexAggregates}

The module's structs and unions, by page. With them, their pages get Qt's titles ("\<name\> Struct") and the class page layout, and the class lists of their namespaces and classes link to them.

### void Converter::setModuleAnchors(QHash\<QString, DocBook2Markdown::PageAnchors\> *anchors*) {#setModuleAnchors}

Every page of the module (by file name without ".xml") with its anchors. With it, links to pages QDoc wrote no file for become plain text, links to anchors that don't exist go to the page itself, and links to deprecated members go to their page.
