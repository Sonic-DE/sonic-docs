---
title: "ActionContext QML Type"
description: "An activation scope for declarative actions."
---

# ActionContext QML Type

An activation scope for declarative actions. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.actions

## Detailed Description {#details}

Action contexts allow actions declared in a global [ActionCollection](qml-org-kde-kirigamiaddons-actions-actioncollection.md) to be active only while a page, document, or tool is active.

## Property Documentation {#property-documentation}

### active : bool {#active-prop}

Whether this context is active.

### contextActive : bool {#contextActive-prop}

Whether this context and all of its parent contexts are active.

### parentContext : ActionContext {#parentContext-prop}

The parent context whose state also controls this context.

### priority : int {#priority-prop}

The priority used to select the active context for an action.
