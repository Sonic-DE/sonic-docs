---
title: WebDAV
description: Manage documents on a web server.
source_url: https://invent.kde.org/frameworks/kio/-/blob/master/docs/kioworker6/webdav/index.docbook
source_authors: [Hamish Rodda]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-frameworks-io e3f55ceb (src/kioworkers/http); read from code, not clicked through"
---

# WebDAV

WebDAV is a *D*istributed *A*uthoring and *V*ersioning protocol for the World Wide Web. It allows for easy management of documents and scripts on an HTTP server, and has additional features designed to simplify version management among multiple authors.

Using it is simple. Type the location you want to view, similar to an HTTP URL except for the `webdav://` protocol name at the start, for example `webdav://www.hostname.com/path/`. If you specify a folder name, a list of files and folders is displayed, and you can work with them just as you would with any other file system.

WebDAV also has these capabilities:

- **Locking:** Lets users lock a file, informing others that they're currently working on it. This way, editing can be done without fear that the changes may be overwritten by another person editing the same document.
- **Source file access:** Allows access to the script that produces a specific page, so changes can be made to the script itself.
- **Per-document property support:** Arbitrary properties can be set to help identify a document, such as its author.

To take advantage of these capabilities, you need an application that supports them. No application currently supports them through this KIO worker.

WebDAVS is the WebDAV protocol encrypted with SSL.

The [Network Folder Wizard](../applications/network-folder-wizard.md) can add a WebDAV folder for you.
