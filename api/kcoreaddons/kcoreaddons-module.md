---
title: "KCoreAddons C++ Classes"
description: "Provides core non-GUI functionality."
---

# KCoreAddons C++ Classes

Provides core non-GUI functionality. [More...](#details)

## Namespaces {#namespaces}

- [KBackup](kbackup.md): Provides utility functions for backup of files.
- [KCoreAddons](kcoreaddons.md): Provides utility functions for metadata about the KCoreAddons library.
- [KFileSystemType](kfilesystemtype.md)
- [KFileUtils](kfileutils.md): A namespace for KFileUtils globals.
- [KFuzzyMatcher](kfuzzymatcher.md): This namespace contains functions for fuzzy matching a list of strings against a pattern.
- [KJsonUtils](kjsonutils.md)
- [KLibexec](klibexec.md): Utility functions around libexec.
- [KMacroExpander](kmacroexpander.md): A group of functions providing macro expansion (substitution) in strings, optionally with quoting appropriate for shell execution.
- [KProcessList](kprocesslist.md)
- [KRandom](krandom.md): Helper to create random data.
- [KRuntimePlatform](kruntimeplatform.md): Utility functions around the runtime platform.
- [KSafeStringError](ksafestringerror-sub-kcoreaddons.md): Thread-safe variants of strerror that return different string types.
- [KSandbox](ksandbox.md): Utility functions for use inside application sandboxes such as Flatpak or Snap.
- [KShell](kshell.md)
- [KStringHandler](kstringhandler.md): This namespace contains utility functions for handling strings.
- [KTextToHTML](ktexttohtml.md)
- [KUrlMimeData](kurlmimedata.md): Utility functions for using URLs in QMimeData.

## Classes {#classes}

- [KAboutComponent](kaboutcomponent.md): This class is used to store information about a third party component.
- [KAboutData](kaboutdata.md): This class is used to store information about a program or plugin.
- [KAboutDataListener](kaboutdatalistener.md): Notify about changes in the global application data
- [KAboutLicense](kaboutlicense.md): This class is used to store information about a license.
- [KAboutPerson](kaboutperson.md): This class is used to store information about a person or developer.
- [KAboutRelease](kaboutrelease.md): An individual release note of a program or plugin.
- [KAutoSaveFile](kautosavefile.md): Creates and manages a temporary "auto-save" file.
- [KCharMacroExpander](kcharmacroexpander.md): Abstract base class for single char macro substitutors.
- [KCompositeJob](kcompositejob.md): The base class for all jobs able to be composed of one or more subjobs.
- [KDirWatch](kdirwatch.md): Class for watching directory and file changes.
- [KFormat](kformat.md): Class for formatting numbers and datetimes.
- [KFuzzyMatcher::Range](kfuzzymatcher-range.md): A range representing a matched sequence in a string.
- [KFuzzyMatcher::Result](kfuzzymatcher-result.md): The result of a fuzzy match.
- [KJob](kjob.md): The base class for all jobs.
- [KJobTrackerInterface](kjobtrackerinterface.md): The interface to implement to track the progresses of a job.
- [KJobUiDelegate](kjobuidelegate.md): The base class for all KJob UI delegate.
- [KMacroExpanderBase](kmacroexpanderbase.md): Abstract base class for the worker classes behind the KMacroExpander namespace and the KCharMacroExpander and KWordMacroExpander classes.
- [KMemoryInfo](kmemoryinfo.md): The KMemoryInfo class provides an interface to get memory information (RAM/SWAP).
- [KNetworkMounts](knetworkmounts.md)
- [KOSRelease](kosrelease.md): The OSRelease class parses /etc/os-release files.
- [KPluginFactory::Result](kpluginfactory-result.md)
- [KPluginFactory](kpluginfactory.md): KPluginFactory provides a convenient way to provide factory-style plugins.
- [KPluginMetaData](kpluginmetadata.md): This class allows easily accessing some standardized values from the JSON metadata that can be embedded into Qt plugins.
- [KProcess](kprocess.md): Child process invocation, monitoring and control.
- [KProcessList::KProcessInfo](kprocesslist-kprocessinfo.md): Contains information about a process.
- [KSandbox::ProcessContext](ksandbox-processcontext.md): Container for host process startup context.
- [KSharedDataCache](kshareddatacache.md): A simple data cache which uses shared memory to quickly access data stored on disk.
- [KSignalHandler](ksignalhandler.md): Allows getting ANSI C signals and forward them onto the Qt eventloop.
- [KSystemClockSkewNotifier](ksystemclockskewnotifier.md): The KSystemClockSkewNotifier class provides a way for monitoring system clock changes.
- [KUser](kuser.md): Represents a user on your system.
- [KUserGroup](kusergroup.md): Represents a group on your system.
- [KWordMacroExpander](kwordmacroexpander.md): Abstract base class for simple word macro substitutors.

## Detailed Description {#details}

[KCoreAddons](kcoreaddons-module.md) provides classes built on top of [QtCore](https://doc.qt.io/qt-6/qtcore-module.html) to perform various tasks such as manipulating mime types, autosaving files, creating backup files, generating random sequences, performing text manipulations such as macro replacement, accessing user information and many more.
