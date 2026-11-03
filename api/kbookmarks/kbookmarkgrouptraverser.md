---
title: "KBookmarkGroupTraverser Class"
description: "Bookmarks management library."
---

# KBookmarkGroupTraverser Class

Bookmarks management library. [More...](#details)

- **Header:** `#include <KBookmark>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Bookmarks)`  
  `target_link_libraries(mytarget PRIVATE KF6::Bookmarks)`

[List of all members, including inherited members](kbookmarkgrouptraverser-members.md)

## Protected Functions

- [void traverse(const KBookmarkGroup &)](#traverse)
- [void visit(const KBookmark &)](#visit)
- [void visitEnter(const KBookmarkGroup &)](#visitEnter)
- [void visitLeave(const KBookmarkGroup &)](#visitLeave)

## Detailed Description {#details}

A class to traverse bookmark groups

## Member Function Documentation {#member-function-documentation}

### \[protected\] void KBookmarkGroupTraverser::traverse(*const KBookmarkGroup &*) {#traverse}

### \[virtual protected\] void KBookmarkGroupTraverser::visit(*const KBookmark &*) {#visit}

### \[virtual protected\] void KBookmarkGroupTraverser::visitEnter(*const KBookmarkGroup &*) {#visitEnter}

### \[virtual protected\] void KBookmarkGroupTraverser::visitLeave(*const KBookmarkGroup &*) {#visitLeave}
