---
title: "Obsolete Members for NetworkManager::Notifier"
description: "Deprecated members of NetworkManager::Notifier."
parent: "networkmanager-qt/networkmanager-notifier"
---

# Obsolete Members for NetworkManager::Notifier

**The following members of class [Notifier](networkmanager-notifier.md) are deprecated.** We strongly advise against using them in new code.

## Signals

- [void wimaxEnabledChanged(bool)](#wimaxEnabledChanged)
- [void wimaxHardwareEnabledChanged(bool)](#wimaxHardwareEnabledChanged)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[signal, deprecated\] void Notifier::wimaxEnabledChanged(*bool*) {#wimaxEnabledChanged}

This function is deprecated. We strongly advise against using it in new code.

This signal is emitted when the status of the wimax changed

Wimax support was removed from [NetworkManager](networkmanager.md) 1.2 (never emitted in runtime NM \>= 1.2.0).

### \[signal, deprecated\] void Notifier::wimaxHardwareEnabledChanged(*bool*) {#wimaxHardwareEnabledChanged}

This function is deprecated. We strongly advise against using it in new code.

This signal is emitted when the status of the wimax hardware changed

Wimax support was removed from [NetworkManager](networkmanager.md) 1.2 (never emitted in runtime NM \>= 1.2.0).
