---
title: "SignOn Client Library"
description: "The Single Sign On client library for Qt applications."
---

# SignOn Client Library

The Single Sign On client library for Qt applications.

Single Sign-On is a framework for centrally storing authentication credentials and handling authentication on behalf of applications as requested by applications. It consists of a secure storage of login credentials (for example usernames and passwords), plugins for different authentication systems and a client library for applications to communicate with this system.

This library is the Single Sign On client library for Qt-based applications. By using this library, an application can authenticate to a (usually remote) service using an existing set of credentials, and operate on the credentials database as well.

## Terminology {#terminology}

A few terms are frequently used in this library's APIs:

- **Identity**: a local object representing a record in the credentials DB. It contains information about the username and password (the latter is write-only), plus some metadata such as a descriptive caption, ACL, reference count, and a little more. Identities are referred to in the SSO DB by numeric IDs.
- **Authentication method**: the SSO daemon supports different authentication methods, each being provided by a plugin. Well known examples of authentication methods include [SASL](https://en.wikipedia.org/wiki/Simple_Authentication_and_Security_Layer) and [OAuth](https://en.wikipedia.org/wiki/OAuth). Authentication methods might support different authentication mechanisms.
- **Authentication session**: the process of performing the authentication.

## Main Classes {#main-classes}

All classes reside in the [SignOn](signon.md) namespace.

- [SignOn::AuthSession](signon-authsession.md): local representation of an authentication session. Use this class to perform the authentication.
- [SignOn::Identity](signon-identity.md): local representation of an identity. Use this class to load an existing set of credentials, or to create, edit and delete credentials.

## Using the Module {#using-the-module}

### Building with CMake {#building-with-cmake}

Use the `find_package()` command to locate the [SignOnQt6](signonqt6-module.md) package and link against its target:

```cpp
find_package(SignOnQt6 REQUIRED)
target_link_libraries(mytarget PRIVATE SignOnQt6::SignOnQt6)
```

The library also ships a pkg-config file, `libsignon-qt6.pc`.

## API Reference {#api-reference}

- [SignOn Client Library C++ Classes](signonqt6-module.md)
