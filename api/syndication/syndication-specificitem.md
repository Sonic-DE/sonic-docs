---
title: "Syndication::SpecificItem Class"
description: "Interface for all format-specific item-like classes, such as RSS2/RDF items, and Atom entries."
---

# Syndication::SpecificItem Class

Interface for all format-specific item-like classes, such as RSS2/RDF items, and Atom entries. [More...](#details)

- **Header:** `#include <Syndication/SpecificItem>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`
- **Inherited By:** [Syndication::Atom::Entry](syndication-atom-entry.md)

[List of all members, including inherited members](syndication-specificitem-members.md)

## Public Functions

- [bool accept(Syndication::SpecificItemVisitor \*visitor)](#accept)

## Detailed Description {#details}

To process items based on their format, use a [SpecificItemVisitor](syndication-specificitemvisitor.md).

## Member Function Documentation {#member-function-documentation}

### \[pure virtual\] bool SpecificItem::accept(Syndication::SpecificItemVisitor \**visitor*) {#accept}

This must be implemented for the double dispatch technique (Visitor pattern).

The usual implementation is

```cpp
return visitor->visit(this);
```

See also [SpecificItemVisitor](syndication-specificitemvisitor.md).

`visitor` the visitor "visiting" this object
