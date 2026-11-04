---
title: "AboutPage QML Type"
description: "An \"About\" page that is ready to integrate in a Kirigami app."
---

# AboutPage QML Type

An "About" page that is ready to integrate in a Kirigami app. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [ScrollablePage](qml-org-kde-kirigami-scrollablepage.md)

## Detailed Description {#details}

Allows to have a page that will show the copyright notice of the application together with the contributors and some information of which platform it's running on.

## Property Documentation {#property-documentation}

### aboutData : KAboutData {#aboutData-prop}

This property holds an object with the same shape as [KAboutData](../kcoreaddons/kaboutdata.md).

For example:

```qml
aboutData: {
    "displayName" : "KirigamiApp",
    "productName" : "kirigami/app",
    "componentName" : "kirigamiapp",
    "shortDescription" : "A Kirigami example",
    "homepage" : "",
    "bugAddress" : "submit@bugs.kde.org",
    "version" : "5.14.80",
    "otherText" : "",
    "authors" : [
        {
            "name" : "...",
            "task" : "",
            "emailAddress" : "somebody@kde.org",
            "webAddress" : "",
            "ocsUsername" : ""
        }
    ],
    "credits" : [],
    "translators" : [],
    "licenses" : [
        {
            "name" : "GPL v2",
            "text" : "long, boring, license text",
            "spdx" : "GPL-2.0"
        }
    ],
    "copyrightStatement" : "© 2010-2018 Plasma Development Team",
    "desktopFileName" : "org.kde.kirigamiapp"
 }
```

*See also* [KAboutData](../kcoreaddons/kaboutdata.md)

### donateUrl : url {#donateUrl-prop}

This property holds a link to a "Donate" page.

default: empty, as SonicDE has no donation page yet.

### getInvolvedUrl : url {#getInvolvedUrl-prop}

This property holds a link to a "Get Involved" page.

default: "https://github.com/Sonic-DE" when your application id starts with "org.sonicde." or "org.kde.", otherwise is empty

### loadAvatars : bool {#loadAvatars-prop}

This property controls whether to load avatars by URL.

If set to false, a fallback "user" icon will be displayed.

default: `false`
