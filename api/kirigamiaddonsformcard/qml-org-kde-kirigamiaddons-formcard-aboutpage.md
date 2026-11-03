---
title: "AboutPage QML Type"
description: "An AboutPage that displays the about data using Form components."
---

# AboutPage QML Type

An [AboutPage](qml-org-kde-kirigamiaddons-formcard-aboutpage.md) that displays the about data using Form components. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard
- Inherits: [FormCardPage](qml-org-kde-kirigamiaddons-formcard-formcardpage.md)

## Detailed Description {#details}

This component consists of an internationalized "About" page with the metadata of your program.

It allows to show the copyright notice of the application together with the contributors and some information of which platform it's running on.

## Property Documentation {#property-documentation}

### aboutData : var {#aboutData-prop}

This property holds an object with the same shape as [KAboutData](../kcoreaddons/kaboutdata.md).

Set this property to either a [KAboutData](../kcoreaddons/kaboutdata.md) instance exposed from C++, or directly via a JSON object.

Example usage:

```cpp
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
           "task" : "...",
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
   "releases" : [
       {
           "version" : "1.0.0",
           "date" : "2025-01-01",
           "description" : "Initial release.",
           "url" : "https://example.org/releases/1.0.0"
       }
   ],
   "copyrightStatement" : "© 2010-2018 Plasma Development Team",
   "desktopFileName" : "org.kde.kirigamiapp"
}
```

*See also* [KAboutData](../kcoreaddons/kaboutdata.md)

### donateUrl : url {#donateUrl-prop}

This property holds a link to a "Donate" page.

Default: "https://www.kde.org/donate" when the application ID starts with "org.kde.", otherwise empty.

### getInvolvedUrl : url {#getInvolvedUrl-prop}

This property holds a link to a "Get Involved" page.

Default: "https://community.kde.org/Get_Involved" when the application ID starts with "org.kde.", otherwise empty.

### showLibraries : bool {#showLibraries-prop}

This property defines whether to show "Libraries in use".

Default: true
