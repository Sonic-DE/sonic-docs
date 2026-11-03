---
title: "KIO::JobUiDelegateFactory Class"
description: "A factory for creating job ui delegates."
---

# KIO::JobUiDelegateFactory Class

A factory for creating job ui delegates. [More...](#details)

- **Header:** `#include <KIO/JobUiDelegateFactory>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`

[List of all members, including inherited members](kio-jobuidelegatefactory-members.md)

## Public Functions

- [KJobUiDelegate \*createDelegate() const](#createDelegate)
- [KJobUiDelegate \*createDelegate(KJobUiDelegate::Flags flags, QWidget \*window) const](#createDelegate-1) (since 6.0)

## Protected Functions

- [JobUiDelegateFactory()](#JobUiDelegateFactory)

## Detailed Description {#details}

Every KIO job will get a delegate from this factory.

## Member Function Documentation {#member-function-documentation}

### \[protected\] JobUiDelegateFactory::JobUiDelegateFactory() {#JobUiDelegateFactory}

Constructor

### \[pure virtual\] KJobUiDelegate \*JobUiDelegateFactory::createDelegate() const {#createDelegate}

### \[pure virtual, since 6.0\] KJobUiDelegate \*JobUiDelegateFactory::createDelegate(KJobUiDelegate::Flags *flags*, QWidget \**window*) const {#createDelegate-1}

This function was introduced in Qt 6.0.

## Related Non-Members {#related-non-members}

### KJobUiDelegate \*createDefaultJobUiDelegate() {#createDefaultJobUiDelegate}

Convenience method: use default factory, if there's one, to create a delegate and return it.

### KJobUiDelegate \*createDefaultJobUiDelegate(KJobUiDelegate::Flags *flags*, QWidget \**window*) {#createDefaultJobUiDelegate-1}

Convenience method: use default factory, if there's one, to create a delegate and return it.

### \[since 6.0\] KIO::JobUiDelegateFactory \*defaultJobUiDelegateFactory() {#defaultJobUiDelegateFactory}

Returns the default job UI delegate factory to be used by all KIO jobs (in which [HideProgressInfo](kio.md#JobFlag-enum) is not set) Can return nullptr, if no kio GUI library is loaded.

This function was introduced in Qt 6.0.

*See also* [setDefaultJobUiDelegateFactory](kio-jobuidelegatefactory.md#setDefaultJobUiDelegateFactory)()

### template \<typename T\> T delegateExtension(KJob \**job*) {#delegateExtension}

Returns the child of the job's uiDelegate() that implements the given extension, or nullptr if none was found (or if the job had no uiDelegate).

### \[since 6.0\] void setDefaultJobUiDelegateFactory(KIO::JobUiDelegateFactory \**factory*) {#setDefaultJobUiDelegateFactory}

Internal. Allows the KIO widgets library to register its widget-based job UI delegate factory automatically.

This function was introduced in Qt 6.0.

*See also* [defaultJobUiDelegateFactory](kio-jobuidelegatefactory.md#defaultJobUiDelegateFactory)()
