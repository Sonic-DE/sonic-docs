---
title: "InputMethod QML Type (Singleton)"
description: "This exposes information about the current used input method."
---

# InputMethod QML Type (Singleton)

This exposes information about the current used input method. [More...](#details)

- Import Statement: import org.kde.kirigami.platform

> **Note:** **Note:** This type is a QML singleton. There is only one instance of this type in the QML engine.

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### \[read-only\] active : bool {#active-prop}

Is the current input method active?

What active means depends on the type of input method. In case of a virtual keyboard for example, it would mean the virtual keyboard is visible.

### \[read-only\] available : bool {#available-prop}

Is an input method available?

This will be true if there is an input method available. When it is false it means there's no special input method configured and input happens directly through keyboard events.

### \[read-only\] enabled : bool {#enabled-prop}

Is the current input method enabled?

If this is false, that means the input method is available but not in use.

### \[read-only\] visible : bool {#visible-prop}

Is the current input method visible?

For some input methods this will match active however for others this may differ.

### \[read-only\] willShowOnActive : bool {#willShowOnActive-prop}

Will the input method be shown when a text input field gains focus?

This is intended to be used to decide whether to give an input field default focus. For certain input methods, like virtual keyboards, it may not be desirable to show it by default. For example, having a search field focused on application startup may cause the virtual keyboard to show, greatly reducing the available application space.
