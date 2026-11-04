---
title: "SignOn::ExtensionInterface2 Class"
description: "Interface definition for signond extensions, version 2."
---

# SignOn::ExtensionInterface2 Class

Interface definition for signond extensions, version 2. [More...](#details)

- **Header:** `#include <SignOn/ExtensionInterface>`
- **Inherits:** [SignOn::ExtensionInterface](signon-extensioninterface.md)
- **Inherited By:** [SignOn::ExtensionInterface3](signon-extensioninterface3.md)

[List of all members, including inherited members](signon-extensioninterface2-members.md)

## Public Functions

- [SignOn::AbstractKeyAuthorizer \*keyAuthorizer(SignOn::KeyHandler \*keyHandler, QObject \*parent = 0) const](#keyAuthorizer)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[virtual\] SignOn::AbstractKeyAuthorizer \*ExtensionInterface2::keyAuthorizer(SignOn::KeyHandler \**keyHandler*, QObject \**parent* = 0) const {#keyAuthorizer}

Gets the KeyAuthorizer object for `keyHandler`, with the given `parent`.

Returns a key authorizer object, or 0 if none is provided by this plugin
