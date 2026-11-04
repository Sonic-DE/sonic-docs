---
title: "SignOn::ExtensionInterface Class"
description: "Interface definition for signond extensions."
---

# SignOn::ExtensionInterface Class

Interface definition for signond extensions. [More...](#details)

- **Header:** `#include <SignOn/ExtensionInterface>`
- **Inherited By:** [SignOn::ExtensionInterface2](signon-extensioninterface2.md)

[List of all members, including inherited members](signon-extensioninterface-members.md)

## Public Functions

- [SignOn::AbstractKeyManager \*keyManager(QObject \*parent = 0) const](#keyManager)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[virtual\] SignOn::AbstractKeyManager \*ExtensionInterface::keyManager(QObject \**parent* = 0) const {#keyManager}

Gets the KeyManager object, with the given `parent`.

Returns a key manager object, or 0 if none is provided by this plugin
