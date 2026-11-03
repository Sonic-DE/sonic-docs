---
title: "BluezQt::TPendingCall Class"
description: "Pending method call (template version)."
---

# BluezQt::TPendingCall Class

Pending method call (template version). [More...](#details)

- **Header:** `#include <BluezQt/TPendingCall>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [BluezQt::PendingCall](bluezqt-pendingcall.md)

[List of all members, including inherited members](bluezqt-tpendingcall-members.md)

## Public Functions

- [template \<int Index\> const typename Select\<Index, T...\>::Type valueAt() const](#valueAt)

## Detailed Description {#details}

This class represents a pending method call. It is a convenient wrapper around QDBusPendingReply and QDBusPendingCallWatcher. The [TPendingCall](bluezqt-tpendingcall.md) is a template class whose parameters are the types that will be used to extract the contents of the reply's data.

## Member Function Documentation {#member-function-documentation}

### template \<int Index\> const typename Select\<Index, T...\>::Type TPendingCall::valueAt() const {#valueAt}

Returns a return value at given index of the call.

Returns the return value at position Index (which is a template parameter) cast to type Type. This function uses template code to determine the proper Type type, according to the type list used in the construction of this object.
