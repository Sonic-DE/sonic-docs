---
title: "UploadPage QML Type"
description: "A Kirigami.Page component used for showing how to upload KNS entries to a service."
---

# UploadPage QML Type

A Kirigami.Page component used for showing how to upload KNS entries to a service. [More...](#details)

- Import Statement: import org.kde.newstuff

## Detailed Description {#details}

This page shows a short guide for uploading new content to the service provided by a KNewStuff provider. This attempts to use the information available through the provider itself, and shows a link to the service's web page, and email in case it is not the KDE Store.

While there are not currently any services which support direct OCS API based uploading of new content, we still need a way to guide people to how to do this, hence this component's simplistic nature.

This component is functionally equivalent to the old UploadDialog

*See also* KNewStuff::UploadDialog

## Property Documentation {#property-documentation}

### \[required\] engine : NewStuff.Engine {#engine-prop}

The NewStuffQuick Engine instance used to display content for this item. You can either pass in one that has already been set up (such as from a NewStuff.Page or NewStuff.Dialog), or you can construct a new one yourself, simply by doing something like this (which will use the wallpapers configuration):

```qml
NewStuff.UploadPage {
   engine: NewStuff.Engine {
       configFile: "wallpapers.knsrc"
   }
}
```
