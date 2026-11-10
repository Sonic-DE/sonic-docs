---
title: Network troubleshooting
description: How networking fits together, finding where a connection fails, and reporting it.
source_url: https://userbase.kde.org/NetworkManagement
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-network-manager (applet/, kcms/, kded/), the stage's org.kde.plasma.networkmanagement applet and kcm_networkmanagement; the source page is marked outdated, so its KDE 3 and 4 tools were replaced with their current counterparts"
---

# Network troubleshooting

On most Linux distributions, the NetworkManager service provides control of network connections that you can configure yourself. In SonicDE, the Networks widget in the system tray and the Wi-Fi & Networking module in System Settings are the main user interfaces to NetworkManager. [Wi-Fi & Networking](../settings/wifi-networking.md) describes how to use them, and [VPN connections](../settings/vpn.md) covers VPNs.

## The stack

Networking on most Linux desktops sits on top of a large and fragile stack of components, which is needed to deal with the vast number of different configurations. When a connection fails, it can be for any one of many reasons throughout this stack, but the symptoms usually look like "the connection got to 28% and then failed". So the first job is to find out at what layer the failure occurred.

### The hardware

Wireless hardware has a surprising number of bugs. These are dealt with at the next layer, if you are lucky.

### The kernel

This is where the driver that controls the hardware lives. There are many interesting bugs here too, though the standard wireless layer in the Linux kernel has improved the situation. You can see the driver's output in the system log, and talk to it with the `iw` command.

### WPA supplicant

`wpa_supplicant` is a low-level tool that talks to the driver and provides authentication and encryption settings. It's open source and generally of high quality. Before NetworkManager, people had to configure it by hand with control files in `/etc`, and doing so has been known to get people out of a tight spot. These days it's mostly controlled remotely by NetworkManager.

### NetworkManager

NetworkManager is the system service at the center of the networking subsystem on most end-user Linux installations. It has root privileges, needed to control the lower layers, and exposes some controls to clients running in your session through D-Bus. It also controls DHCP clients as needed and may rewrite `/etc/resolv.conf` with the DNS servers it has configured.

### User clients

These include SonicDE's Networks widget, `nm-applet` under GNOME, and `nmcli` on the console. They are responsible for:

- giving feedback on the networking status of the system
- passing your actions on to NetworkManager
- storing your network connection details and passing them to NetworkManager

While they are the most visible part of the system, they are also the least important to making a successful connection. Since they share a standard interface to NetworkManager, they can be exchanged easily.

## When things go wrong

### Where does it hurt?

Start at the top of the stack and work down. When you find something that works, you have found the site of the problem. When you run out of things you can change, hand over to an expert, probably the responsible team at your Linux distribution.

1. Are you actually using NetworkManager on your system? Not every distribution does.
2. Try a different NetworkManager client, such as `nmcli`. If that helps, continue in the next section to narrow the problem down.
3. Try to configure a connection with your distribution's system configuration tools. It's unlikely to help, but worth a go.
4. Try a manually configured connection with `wpa_supplicant`. Documentation is sparse, but example configurations are included in the package. If `wpa_supplicant` on its own works, NetworkManager is at fault, so talk to your distribution or report it to the NetworkManager project.
5. If that didn't work, set a wireless router to use a different, weaker encryption type or none at all. If this works, the problem is either in `wpa_supplicant` or the driver. Either way, take it to your distribution.

### If only SonicDE's widget fails

If you're reading this, you've been able to make a connection with a different NetworkManager client.

First, make sure you aren't running another client alongside the Networks widget, which leads to unpredictable results. You can also run the widget on its own with:

```sh
plasmoidviewer -a org.kde.plasma.networkmanagement
```

Next, find out how the connection made by the widget differs from the one made by the other client. To show a connection's settings, run:

```sh
nmcli connection show "connection name"
```

Repeat this with the working client, and copy both sets of output. Remove any passwords, then attach them to your bug report.

## Reporting a bug

To report a useful bug in the [sonic-network-manager issue tracker](https://github.com/Sonic-DE/sonic-network-manager/issues), include:

- Your distribution and its version
- Whether NetworkManager is in use. On some distributions it's optional, and if it isn't in use, this widget won't help you.
- The version of SonicDE's network management package
- The version of the NetworkManager package
- The version of the ModemManager package
- Your computer's hardware, if it isn't ordinary x86-compatible hardware
- Your network hardware (`lspci` and `lsusb` will show it)
- A system log from NetworkManager during the connection attempt, which is in `/var/log` on many distributions, or from `journalctl -u NetworkManager` on those that use the journal

For wireless networks:

- Whether it uses a hidden SSID
- The wireless security type: WEP, WPA-PSK or WPA-EAP
- The key length
- The key type (passphrase or hex for WEP)
- The ciphers (TKIP or AES)
- The authentication mechanism (TLS, TTLS, PEAP and so on)

For mobile broadband:

- The hardware
- The driver in use (`dmesg` shows this when you connect the hardware)
- The network in use
- The network type (GSM, CDMA, UMTS and so on)
- The APN used, if any
- ModemManager logs may help show whether NetworkManager detects your hardware

And very importantly: are you able to connect with another client? If so, attach the comparison described above.

### Crashes

If something crashes, install debugging symbols and take a backtrace. How to do this varies by distribution.
