---
title: FTP
description: Transfer files between computers.
source_url: https://invent.kde.org/frameworks/kio/-/blob/master/docs/kioworker6/ftp/index.docbook
source_authors: [Lauri Watts]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-frameworks-io e3f55ceb (src/kioworkers/ftp); read from code, not clicked through"
---

# FTP

FTP is the Internet service used to transfer a data file from the disk of one computer to the disk of another, regardless of the operating system type.

Like other Internet applications, FTP uses the client-server approach. A user runs an FTP program on their computer, tells it to contact a remote computer, and then requests the transfer of one or more files. The local FTP program becomes a client that uses TCP to contact an FTP server program on the remote computer. Each time the user requests a file transfer, the client and server programs cooperate to send a copy of the data across the Internet.

FTP servers that allow “anonymous FTP” let any user, not only users with accounts on the host, browse the FTP archives and download files. Some FTP servers are configured to allow users to upload files.

FTP is commonly used to retrieve information and obtain software stored in files at FTP archive sites throughout the world.

See [RFC 959](https://datatracker.ietf.org/doc/html/rfc959) and the `ftp` man page.
