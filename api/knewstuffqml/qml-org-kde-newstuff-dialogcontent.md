---
title: "DialogContent QML Type"
description: "The contents of the NewStuff.Dialog component."
---

# DialogContent QML Type

The contents of the NewStuff.Dialog component. [More...](#details)

- Import Statement: import org.kde.newstuff

## Detailed Description {#details}

This component is equivalent to the old DownloadWidget, but you should consider using NewStuff.Page instead for a more modern style of integration into your application's flow.

*See also* KNewStuff::DownloadWidget

## Property Documentation {#property-documentation}

### configFile : alias {#configFile-prop}

The configuration file to use for this button

### engine : alias {#engine-prop}

The engine which handles the content in this dialog

### viewMode : alias {#viewMode-prop}

The default view mode of the dialog spawned by this button. This should be set using the NewStuff.Page.ViewMode enum

*See also* NewStuff.Page.ViewMode
