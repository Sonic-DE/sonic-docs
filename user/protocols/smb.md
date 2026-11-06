---
title: SMB
description: Browse the shares of a Windows or Samba network.
source_url: https://invent.kde.org/network/kio-extras/-/blob/master/doc/kioworker/smb/index.docbook
source_authors: [Alexander Neundorf]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-frameworks-io-extras 368b2196 (smb); read from code, not clicked through"
---

# SMB

The smb worker lets you browse the shares of a Windows or Samba network.

- To see the workgroups, enter `smb:/`.
- `smb://a_workgroup` lists the hosts in this workgroup.
- To see the shares of a host, enter `smb://the_host` or `smb:/a_workgroup/the_host`.
- To access a share directly, enter `smb://the_host/the_share` or `smb:/a_workgroup/the_host/the_share`.

The smb worker requires `libsmbclient`.

The worker asks for your user name and password if it needs them.

The [Network Folder Wizard](../applications/network-folder-wizard.md) can add a network drive for you.
