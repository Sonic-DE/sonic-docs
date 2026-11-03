---
title: "KPassword Namespace"
description: "Large set of desktop widgets."
---

# KPassword Namespace

Large set of desktop widgets. [More...](#details)

- Header: KPassword
- CMake: find\_package(KF6 REQUIRED COMPONENTS WidgetsAddons) target\_link\_libraries(mytarget PRIVATE KF6::WidgetsAddons)

## Detailed Description {#details}

## Type Documentation {#type-documentation}

### \[since 6.0\] enum KPassword::RevealMode {#RevealMode-enum}

This enum describe when the reveal password button is visible.

| Constant | Value | Description |
| --- | --- | --- |
| `KPassword::RevealMode::OnlyNew` | `0` | Display the button when entering a new password, but doesn't let you see a previously entered password. This is the default. |
| `KPassword::RevealMode::Never` | `1` | Never display the reveal button. |
| `KPassword::RevealMode::Always` | `2` | Always display the reveal button. Usefull in a password manager for example. |

This enum was introduced in Qt 6.0.
