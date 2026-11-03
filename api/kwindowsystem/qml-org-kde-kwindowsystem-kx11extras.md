---
title: "KX11Extras QML Type"
description: "A collection of functions to obtain information from and manipulate X11 windows."
---

# KX11Extras QML Type

A collection of functions to obtain information from and manipulate X11 windows. [More...](#details)

- Import Statement: import org.kde.kwindowsystem
- In C++: [KX11Extras](kx11extras.md)

## Detailed Description {#details}

These are generally not applicable to other window systems.

## Property Documentation {#property-documentation}

### \[read-only\] compositingActive : bool {#compositingActive-prop}

Whether desktop compositing is active.

## Method Documentation {#method-documentation}

### \[since 6.0\] void forceActiveWindow(Window \**window*, long *time* = 0) {#forceActiveWindow-method}

timestamp `time` of the user activity that caused this request.

Note that this should be called only in special cases, applications shouldn't force themselves or other windows to be the active window. Generally, this call should used only by pagers and similar tools. See the explanation in the description of KX11Extras::activateWindow().

This method was introduced in Qt 6.0.
