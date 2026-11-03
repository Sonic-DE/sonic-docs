---
title: "KIO Core C++ Classes"
description: "Resource and network access abstraction."
---

# KIO Core C++ Classes

Resource and network access abstraction. [More...](#details)

## Namespaces {#namespaces}

- [KIO](kio.md): A namespace for KIO globals.
- [KRecentDirs](krecentdirs.md)
- [KUrlAuthorized](kurlauthorized.md): The functions in this namespace allow actions to be restricted based on the URL they operate on (see the KAuthorized namespace in KConfig).

## Classes {#classes}

- [KACL](kacl.md): a POSIX ACL encapsulation.
- [KCoreDirLister](kcoredirlister.md): Helper class for the kiojob used to list and update a directory.
- [KFileFilter](kfilefilter.md)
- [KFileItem](kfileitem.md): A KFileItem is a generic class to handle a file, local or remote.
- [KFileItemList](kfileitemlist.md)
- [KFileItemListProperties](kfileitemlistproperties.md): Provides information about the common properties of a group of KFileItem objects.
- [KIO::AskUserActionInterface](kio-askuseractioninterface.md): The AskUserActionInterface class allows a KIO::Job to prompt the user for a decision when e.g. copying directories/files and there is a conflict (e.g. a file with the same name already exists at the destination).
- [KIO::AuthInfo](kio-authinfo.md): A two way messaging class for passing authentication information.
- [KIO::BatchRenameJob](kio-batchrenamejob.md): A KIO job that renames multiple files in one go.
- [KIO::ChmodJob](kio-chmodjob.md): This job changes permissions on a list of files or directories, optionally in a recursive manner.
- [KIO::CopyJob](kio-copyjob.md): CopyJob is used to move, copy or symlink files and directories.
- [KIO::DavJob](kio-davjob.md)
- [KIO::DeleteJob](kio-deletejob.md): A more complex Job to delete files and directories.
- [KIO::DesktopExecParser](kio-desktopexecparser.md): Parses the Exec= line from a .desktop file, and process all the '%' placeholders, e.g. handling URLs vs local files.
- [KIO::DirectorySizeJob](kio-directorysizejob.md): Computes a directory size.
- [KIO::EmptyTrashJob](kio-emptytrashjob.md)
- [KIO::FileCopyJob](kio-filecopyjob.md)
- [KIO::FileJob](kio-filejob.md)
- [KIO::FileSystemFreeSpaceJob](kio-filesystemfreespacejob.md): A KIO job that retrieves the total and available size of a filesystem.
- [KIO::ForwardingWorkerBase](kio-forwardingworkerbase.md): Worker that forwards to other workers.
- [KIO::Job](kio-job.md)
- [KIO::JobUiDelegateExtension](kio-jobuidelegateextension.md)
- [KIO::JobUiDelegateFactory](kio-jobuidelegatefactory.md): A factory for creating job ui delegates.
- [KIO::ListJob](kio-listjob.md): A ListJob is allows you to get the get the content of a directory.
- [KIO::MimeTypeFinderJob](kio-mimetypefinderjob.md): MimeTypeFinderJob finds out the MIME type of a URL.
- [KIO::MimetypeJob](kio-mimetypejob.md)
- [KIO::MkdirJob](kio-mkdirjob.md)
- [KIO::MkpathJob](kio-mkpathjob.md): A KIO job that creates a directory, after creating all parent directories necessary for this.
- [KIO::NameFinderJob](kio-namefinderjob.md): NameFinderJob finds a valid "New Folder" name.
- [KIO::OpenWith](kio-openwith.md): Core class for open with style dialog handling.
- [KIO::RestoreJob](kio-restorejob.md): RestoreJob is used to restore files from the trash.
- [KIO::SimpleJob](kio-simplejob.md): A simple job (one url and one command).
- [KIO::SpecialJob](kio-specialjob.md): A class that sends a special command to a KIO worker.
- [KIO::StatJob](kio-statjob.md): A KIO job that retrieves information about a file or directory.
- [KIO::StoredTransferJob](kio-storedtransferjob.md): StoredTransferJob is a TransferJob (for downloading or uploading data) that also stores a QByteArray with the data, making it simpler to use than the standard TransferJob.
- [KIO::TransferJob](kio-transferjob.md): The transfer job pumps data into and/or out of a KIO worker.
- [KIO::UDSEntry](kio-udsentry.md): Universal Directory Service.
- [KIO::UntrustedProgramHandlerInterface](kio-untrustedprogramhandlerinterface.md): The UntrustedProgramHandlerInterface class allows ApplicationLauncherJob to prompt the user about an untrusted executable or desktop file.
- [KIO::WorkerBase](kio-workerbase.md): WorkerBase is the class to use to implement a worker - simply inherit WorkerBase in your worker.
- [KIO::WorkerConfig](kio-workerconfig.md): This class manages the configuration for KIO workers based on protocol and host.
- [KIO::WorkerResult](kio-workerresult.md): The result of a worker call.
- [KMountPoint](kmountpoint.md): The KMountPoint class provides information about mounted and unmounted disks.
- [KMountPoint::List](kmountpoint-list.md)
- [KOverlayIconPlugin](koverlayiconplugin.md): Base class for overlay icon plugins.
- [KPasswdServerClient](kpasswdserverclient.md): Interface class for kpasswdserver.
- [KProtocolInfo](kprotocolinfo.md): Information about I/O (Internet, etc.) protocols supported by KDE.
- [KProtocolInfo::ExtraField](kprotocolinfo-extrafield.md)
- [KProtocolManager](kprotocolmanager.md): Provides information about I/O (Internet, etc.) settings chosen/set by the end user.
- [KRecentDocument](krecentdocument.md): Manage the "Recent Document Menu" entries displayed by applications such as Kicker and Konqueror.
- [KRemoteEncoding](kremoteencoding.md): Allows encoding and decoding properly remote filenames into Unicode.
- [KSambaShare](ksambashare.md): This class lists Samba user shares and monitors them for addition, update and removal.
- [KSambaShareData](ksambasharedata.md): This class represents a Samba user share.
- [KSslCertificateManager](ksslcertificatemanager.md)
- [KSslCertificateRule](ksslcertificaterule.md)
- [KSslErrorUiData](ksslerroruidata.md)

## Detailed Description {#details}
