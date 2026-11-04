---
title: "KAuth Namespace"
description: "Execute actions as privileged user."
---

# KAuth Namespace

Execute actions as privileged user. [More...](#details)

- **Header:** `#include <KAuth>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Auth)`  
  `target_link_libraries(mytarget PRIVATE KF6::AuthCore)`

## Detailed Description {#details}

The main macro for writing a helper tool.

`ID` The helper ID as passed to the macro

`HelperClass` The class name of the responder object for the helper

## Namespaces {#namespaces}

### namespace KAuth::HelperSupport

This class provides the API to write the helper tool that executes your actions. You don't create instances of [HelperSupport](kauth-helpersupport.md). Instead, you use its KAUTHCORE\_EXPORT methods.

This them you can notify the application of progress in your action's execution and you can check if the application asked you to terminate it.

## Classes {#classes}

### class [Action](kauth-action.md)

Class to access, authorize and execute actions.

### class [ActionReply](kauth-actionreply.md)

Class that encapsulates a reply coming from the helper after executing an action.

### class [ExecuteJob](kauth-executejob.md)

Job for executing an Action.
