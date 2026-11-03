---
title: "Page QML Type"
description: "A Kirigami.Page component used for managing KNS entries."
---

# Page QML Type

A Kirigami.Page component used for managing KNS entries. [More...](#details)

- Import Statement: import org.kde.newstuff

## Detailed Description {#details}

This component is functionally equivalent to the old DownloadDialog.

*See also* KNewStuff::DownloadDialog

## Property Documentation {#property-documentation}

### configFile : alias {#configFile-prop}

The configuration file which describes the application (knsrc)

The format and location of this file is found in the documentation for KNS3::DownloadDialog

### showUploadAction : alias {#showUploadAction-prop}

Whether or not to show the Upload... context action Usually this will be bound to the engine's property which usually defines this, but you can override it programmatically by setting it here.

*See also* KNSCore::Engine::uploadEnabled

## Method Documentation {#method-documentation}

### showEntryDetails(*providerId*, *entryId*) {#showEntryDetails-method}

Show the details page for a specific entry. If you call this function before the engine initialisation has been completed, the action itself will be postponed until that has happened.

`providerId` The provider ID for the entry you wish to show details for

`entryId` The unique ID for the entry you wish to show details for
