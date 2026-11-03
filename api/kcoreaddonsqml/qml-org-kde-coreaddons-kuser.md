---
title: "KUser QML Type"
description: "User provides read-only access to the user's personal information."
---

# KUser QML Type

User provides read-only access to the user's personal information. [More...](#details)

- Import Statement: import org.kde.coreaddons

## Detailed Description {#details}

[KUser](qml-org-kde-coreaddons-kuser.md) is an object allowing read-only access to the user's name, os and version and the configured user image. This object can be used to personalize user interfaces.

Example usage:

```cpp
import org.kde.coreaddons as KCoreAddons
[...]

Item {
    [...]
    KCoreAddons.KUser {
        id: kuser
    }

    Image {
        id: faceIcon
        source: kuser.faceIconUrl
        [...]
    }

    Text {
        text: kuser.fullName
        [...]
    }
}
```

## Property Documentation {#property-documentation}

### faceIconUrl : url {#faceIconUrl-prop}

The url of the user's configured image (including file:/)

### fullName : string {#fullName-prop}

The user's full name

### host : string {#host-prop}

The user's the system's hostname

### loginName : string {#loginName-prop}

The user's login name

### os : string {#os-prop}

The pretty name indicating operating system and version
