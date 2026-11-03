---
title: "KIO Namespace"
description: "The KIO namespace includes the following elements from module KIOGui. The full namespace is documented in module KIOCore here.."
---

# KIO Namespace

The KIO namespace includes the following elements from module KIOGui. The full namespace is documented in module KIOCore here..

## Classes {#classes}

### class [ApplicationLauncherJob](kio-applicationlauncherjob.md)

[ApplicationLauncherJob](kio-applicationlauncherjob.md) runs an application and watches it while running.

### class [CommandLauncherJob](kio-commandlauncherjob.md)

[CommandLauncherJob](kio-commandlauncherjob.md) runs a command and watches it while running.

### class [DndPopupMenuPlugin](kio-dndpopupmenuplugin.md)

Base class for drag and drop popup menus.

### class [FavIconRequestJob](kio-faviconrequestjob.md)

[FavIconRequestJob](kio-faviconrequestjob.md) handles the retrieval of a favicon (either from the local cache or from the internet).

### class [OpenFileManagerWindowJob](kio-openfilemanagerwindowjob.md)

Open a File Manager Window.

### class [OpenOrExecuteFileInterface](kio-openorexecutefileinterface.md)

The [OpenOrExecuteFileInterface](kio-openorexecutefileinterface.md) class allows [OpenUrlJob](kio-openurljob.md) to ask the user about how to handle various types of executable files, basically whether to run/execute the file, or in the case of text-based ones (shell scripts and .desktop files) open them as text.

### class [OpenUrlJob](kio-openurljob.md)

[OpenUrlJob](kio-openurljob.md) finds out the right way to "open" a URL.

### class [OpenWithHandlerInterface](kio-openwithhandlerinterface.md)

The [OpenWithHandlerInterface](kio-openwithhandlerinterface.md) class allows [OpenUrlJob](kio-openurljob.md) to prompt the user about which application to use to open URLs that do not have an associated application (via the "Open With" dialog).

### class [PreviewJob](kio-previewjob.md)

KIO Job to get a thumbnail picture.

### class [ThumbnailCreator](kio-thumbnailcreator.md)

Base class for thumbnail generator plugins.

### class [ThumbnailRequest](kio-thumbnailrequest.md)

Encapsulates the input data for a thumbnail request.

### class [ThumbnailResult](kio-thumbnailresult.md)

Encapsulates the output of a thumbnail request.

## Function Documentation {#function-documentation}

### KIO::PreviewJob \*filePreview(const KFileItemList &*items*, const QSize &*size*, const QStringList \**enabledPlugins* = nullptr) {#filePreview}

Creates a [PreviewJob](kio-previewjob.md) to generate a preview image for the given items.

`items` List of files to create previews for.

`size` Desired size of the preview.

`enabledPlugins` If non-zero it defines the list of plugins that are considered for generating the preview. If enabledPlugins is zero the plugins specified in the [KConfigGroup](../kconfigcore/kconfiggroup.md) "PreviewSettings" are used.

### KIO::OpenFileManagerWindowJob \*highlightInFileManager(const QList\<QUrl\> &*urls*, const QByteArray &*asn* = QByteArray()) {#highlightInFileManager}

Convenience method for creating a job to highlight a certain file or folder.

It will create a job for a given URL(s) and automatically start it.
