---
title: "Obsolete Members for NetworkManager"
description: "Deprecated members of NetworkManager Namespace."
parent: "networkmanager-qt/networkmanager"
---

# Obsolete Members for NetworkManager

**The following members of class [NetworkManager](networkmanager.md) are deprecated.** We strongly advise against using them in new code.

## Obsolete Classes {#obsolete-classes}

### \[deprecated\] class NetworkManager::GreDevice

**This class is deprecated. We strongly advise against using it in new code.**

## Obsolete Function Documentation {#obsolete-function-documentation}

### \[deprecated\] bool NetworkManager::isWimaxEnabled() {#isWimaxEnabled}

This function is deprecated. We strongly advise against using it in new code.

Retrieves the activation status of wimax networking in the system.

Returns true if this wimax networking is enabled, false otherwise

Wimax support was removed from [NetworkManager](networkmanager.md) 1.2 (always returns false in runtime NM \>= 1.2.0).

### \[deprecated\] bool NetworkManager::isWimaxHardwareEnabled() {#isWimaxHardwareEnabled}

This function is deprecated. We strongly advise against using it in new code.

Retrieves the status of wimax hardware in the system. This is typically controlled by a physical switch so there is no way to set this in software.

Returns true if wimax HW networking is enabled, false otherwise

Wimax support was removed from [NetworkManager](networkmanager.md) 1.2 (always returns false in runtime NM \>= 1.2.0).

### \[deprecated\] void NetworkManager::setWimaxEnabled(bool *enabled*) {#setWimaxEnabled}

This function is deprecated. We strongly advise against using it in new code.

Wimax support was removed from [NetworkManager](networkmanager.md) 1.2 (it is a noop in runtime NM \>= 1.2.0).

*See also* [isWimaxEnabled](networkmanager-obsolete.md#isWimaxEnabled)()
