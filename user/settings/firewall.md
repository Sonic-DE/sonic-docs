---
title: Firewall
description: Turn your firewall on, set default policies and add rules for your network connections.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-firewall ab5c76d (kcm/ui/, kcm/core/rulelistmodel.cpp, loglistmodel.cpp, kcm/backends/netstat/connectionsmodel.cpp, kcm/backends/ufw/ufwclient.cpp, kcm/backends/ufw/helper/helper.cpp, ufwlogreader.cpp, RELEASE-NOTES.md); written from the code, not clicked through"
---

# Firewall

This module controls your network rules. It works with a firewall already on your system, either `ufw` or `firewalld`. If neither is installed, it asks you to install one. **Firewall type** shows which one it's using.

The module works whichever init system your computer uses: systemd, OpenRC, runit, s6, dinit, sysvinit or BSD rc.

## Turning it on

Use the switch at the top of the module to enable or disable the firewall.

With `ufw`, turning the firewall on also sets it to start when the computer starts, and turning it off removes it from start-up again. If that part doesn't work, the firewall is still switched as you asked, and the module tells you so: **The firewall is on, but it could not be set to start automatically**, or **The firewall is off, but it could not be removed from startup**, followed by the reason.

If enabling it fails with a message that Iptables can't initialize after a kernel update, reboot your computer.

## Default policies

**Default Incoming Policy** and **Default Outgoing Policy** decide what happens to connections that no rule matches:

- **Allow:** Allows all connections.
- **Ignore:** Keeps the program waiting until the connection attempt times out, some short time later.
- **Reject:** Produces an immediate "Connection refused" message.

## Rules

The list shows your rules, with their **Action**, **From**, **To**, **IP** and **Logging** columns. Each rule has buttons to edit and remove it.

To add a rule, click **Add Rule…**. A simple rule has:

- **Application** with `ufw`, or **Allow connections for** with `firewalld`: The application or service the rule is for
- **Policy**
- **Direction:** **Incoming** or **Outgoing**

If the policy matches the default for that direction, the dialog points this out, since such a rule changes nothing.

Tick **Advanced** to set the rest:

- **IP Version:** **IPv4** or **IPv6**
- **Source** and **Destination:** An address and port. Empty fields mean any IP address and any port.
- **Protocol** and **Interface**
- **Logging:** **None**, **New Connections** or **All Packets**

## Connections and logs

**View Connections** lists your computer's connections with their **Protocol**, **Local address**, **Foreign address**, **Status**, **PID** and **Program**. This needs the `iproute2` or `net-tools` package.

**View Logs** lists the firewall's log entries with their **From**, **Source port**, **To**, **Destination port**, **Protocol**, **Interface**, **Action**, **Time** and **Date**. With `ufw`, the entries come from the system journal where there is one. Otherwise they're read from the usual log files in `/var/log`, such as `ufw.log`, `kern.log`, `messages` or `syslog`, and on systems without a log service, from the kernel's own message buffer.

In both, **Blacklist Connection** creates a rule from the selected entry.
