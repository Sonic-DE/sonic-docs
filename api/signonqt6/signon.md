---
title: "SignOn Namespace"
description: "The Single Sign On client library and plugin API."
---

# SignOn Namespace

The Single Sign On client library and plugin API. [More...](#details)

- **Header:** `#include <SignOn>`
- **CMake:** `find_package(SignOnQt6 REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE SignOnQt6::SignOnQt6)`

## Detailed Description {#details}

## Classes {#classes}

### class [AuthService](signon-authservice.md)

Represents signon for client application.

### class [AuthSession](signon-authsession.md)

Represents a session to authentication plugin/server.

### class [Error](signon-error.md)

Base object definition for Signon error handling.

### class [Identity](signon-identity.md)

Represents a database entry for a single identity.

### class [IdentityInfo](signon-identityinfo.md)

Contains identity information.

### class [SecurityContext](signon-securitycontext.md)

Contains access security context information.

### class [SessionData](signon-sessiondata.md)

Data container to hold values for authentication session.

## Type Documentation {#type-documentation}

### AuthSessionP {#AuthSessionP-typedef}

A guarded pointer to an [AuthSession](signon-authsession.md).

### MechanismsList {#MechanismsList-typedef}

Defines a string list as a list of mechanisms.

### MethodName {#MethodName-typedef}

Defines a string as an authentication method.

### SecurityContextList {#SecurityContextList-typedef}

Defines a list of security contexts.

### enum SignonUiPolicy {#SignonUiPolicy-enum}

Policy to define how the plugin interacts with the user. This is a hint for plugin how to handle user interaction. NoUserInteractionPolicy does not allow any ui interaction to happen and plugin will get error reply QUERY\_ERROR\_FORBIDDEN.

| Constant | Value | Description |
| --- | --- | --- |
| `SignOn::SessionData::DefaultPolicy` | `0` | Plugin can decide when to show ui. |
| `SignOn::SessionData::RequestPasswordPolicy` | `1` | Force user to enter password. |
| `SignOn::SessionData::NoUserInteractionPolicy` | `2` | No ui elements are shown to user. |
| `SignOn::SessionData::ValidationPolicy` | `3` | UI elements can be shown to the user only when captcha-like security measures are required |

*See also* [SessionData::UiPolicy](signon-sessiondata.md#UiPolicy)()
