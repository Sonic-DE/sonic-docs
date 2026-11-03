---
title: "KIO Gui C++ Classes"
description: "GUI-related functionality for KIO."
---

# KIO Gui C++ Classes

GUI-related functionality for KIO. [More...](#details)

## Classes {#classes}

- [KCoreUrlNavigator](kcoreurlnavigator.md): Object that helps with keeping track of URLs in file-manager like interfaces.
- [KEMailClientLauncherJob](kemailclientlauncherjob.md): KEMailClientLauncherJob starts a mail client in order to compose a new mail.
- [KIO::ApplicationLauncherJob](kio-applicationlauncherjob.md): ApplicationLauncherJob runs an application and watches it while running.
- [KIO::CommandLauncherJob](kio-commandlauncherjob.md): CommandLauncherJob runs a command and watches it while running.
- [KIO::DndPopupMenuPlugin](kio-dndpopupmenuplugin.md): Base class for drag and drop popup menus.
- [KIO::FavIconRequestJob](kio-faviconrequestjob.md): FavIconRequestJob handles the retrieval of a favicon (either from the local cache or from the internet).
- [KIO::OpenFileManagerWindowJob](kio-openfilemanagerwindowjob.md): Open a File Manager Window.
- [KIO::OpenOrExecuteFileInterface](kio-openorexecutefileinterface.md): The OpenOrExecuteFileInterface class allows OpenUrlJob to ask the user about how to handle various types of executable files, basically whether to run/execute the file, or in the case of text-based ones (shell scripts and .desktop files) open them as text.
- [KIO::OpenUrlJob](kio-openurljob.md): OpenUrlJob finds out the right way to "open" a URL.
- [KIO::OpenWithHandlerInterface](kio-openwithhandlerinterface.md): The OpenWithHandlerInterface class allows OpenUrlJob to prompt the user about which application to use to open URLs that do not have an associated application (via the "Open With" dialog).
- [KIO::PreviewJob](kio-previewjob.md): KIO Job to get a thumbnail picture.
- [KIO::ThumbnailCreator](kio-thumbnailcreator.md): Base class for thumbnail generator plugins.
- [KIO::ThumbnailRequest](kio-thumbnailrequest.md): Encapsulates the input data for a thumbnail request.
- [KIO::ThumbnailResult](kio-thumbnailresult.md): Encapsulates the output of a thumbnail request.
- [KTerminalLauncherJob](kterminallauncherjob.md): KTerminalLauncherJob starts a terminal application, either for the user to use interactively, or to execute a command.
- [KUriFilter](kurifilter.md): Filters the given input into a valid url whenever possible.
- [KUriFilterData](kurifilterdata.md): A class for exchanging filtering information.
- [KUriFilterSearchProvider](kurifiltersearchprovider.md): Class that holds information about a search provider.

## Detailed Description {#details}
