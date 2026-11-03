---
title: "SystemInhibitor QML Type"
description: "Inhibit system actions such as logout, suspend, etc. This type was introduced in Qt 6.23."
---

# SystemInhibitor QML Type

Inhibit system actions such as logout, suspend, etc. This type was introduced in Qt 6.23. [More...](#details)

- Import Statement: import org.kde.guiaddons
- Since: Qt 6.23

## Detailed Description {#details}

```qml
readonly property SystemInhibitor inhibitor: SystemInhibitor {
    window: ApplicationWindow.window
    types: SystemInhibitor.Suspend | SystemInhibitor.Idle
    enabled: true
    reason: KI18n.i18nc("inhibition reason", "Playing a video")
}
```

## Property Documentation {#property-documentation}

### enabled : bool {#enabled-prop}

Toggle for enabling/disabling the inhibition. Please note that inhibiting is an asynchronous operation and may be delayed or fail, the property always reflects the requested state, not the actual state.

### \[required\] reason : string {#reason-prop}

The user-facing reason why ths inhibition is in place (e.g. "Playing a video").

### \[required\] types : enumeration {#types-prop}

The types of inhibition to apply. May be a combination of multiple types.

| Constant | Description |
| --- | --- |
| SystemInhibitor.Logout | Inhibit logout/shutdown |
| SystemInhibitor.UserSwitch | Inhibit user switching |
| SystemInhibitor.Suspend | Inhibit suspend/hibernate |
| SystemInhibitor.Idle | Inhibit idle actions (e.g. screen locking) |

### window : Window {#window-prop}

The window for which to apply the inhibition. May be null in which case possible user queries will not be associated with any window.
