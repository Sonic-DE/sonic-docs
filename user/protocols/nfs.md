---
title: NFS
description: Access shared file systems across networks.
source_url: https://invent.kde.org/network/kio-extras/-/blob/master/doc/kioworker/nfs/index.docbook
source_authors: [Lauri Watts]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-frameworks-io-extras 368b2196 (nfs); read from code, not clicked through"
---

# NFS

Sun's NFS protocol provides transparent remote access to shared file systems across networks. It's designed to be independent of machine, operating system, network architecture and transport protocol. This independence is achieved through Remote Procedure Call (RPC) primitives built on top of an eXternal Data Representation (XDR).

The supporting MOUNT protocol performs the operating system-specific functions that let clients attach remote folder trees to a point within the local file system. The mount process also lets the server grant remote access privileges to a restricted set of clients through export control.

The Lock Manager provides file locking in the NFS environment. The Network Lock Manager (NLM) protocol isolates the inherently stateful aspects of file locking into a separate protocol.

See the `nfs` man page.
