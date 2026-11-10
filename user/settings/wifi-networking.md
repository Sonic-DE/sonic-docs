---
title: Wi-Fi & Networking
description: Connect to networks from the system tray, and set up and manage your network connections.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-network-manager b75aeba0e (applet/main.qml, Toolbar.qml, ConnectionItem.qml, ConnectionListPage.qml, ShareNetworkQrCodePage.qml; kcms/kcm_connections/kcm.cpp, qml/main.qml, ConnectionItem.qml, ConfigurationDialog.qml; libs/models/creatableconnectionsmodel.cpp; org.kde.vpnimport.desktop); written from the code, not clicked through"
---

# Wi-Fi & Networking

SonicDE uses the NetworkManager service for your network connections. You connect to networks with the **Networks** widget in the system tray, and set connections up in the **Wi-Fi & Networking** module, under **Wi-Fi & Internet** in System Settings.

If something doesn't work, see [Network troubleshooting](../applications/network-troubleshooting.md).

## The Networks widget

Click the network icon in the [System Tray](../desktop/system-tray.md) to open the widget. It lists the networks you can connect to, with a search field to find one.

Click a network's **Connect** button to join it. If it needs a password, a field appears for you to type it in. Connected networks have **Disconnect** instead.

Click a connection to expand it. The **Speed** tab shows a live graph of how fast data is going up and down, and **Details** lists the connection's addresses and other information. The menu button on each connection has:

- **Share:** For a Wi-Fi network with a saved password, shows the password and a QR code that other devices can scan to join.
- **Configure…:** Opens the connection in the Wi-Fi & Networking module.

The buttons along the top of the widget are:

- **Enable Wi-Fi:** Turns Wi-Fi on or off. It only appears if your computer has Wi-Fi.
- **Enable mobile data:** Turns mobile data on or off, on computers with a mobile broadband modem.
- **Enable airplane mode** or **Disable airplane mode:** Turns Wi-Fi and Bluetooth off together, or back on.
- **Hotspot:** Shares your computer's internet connection over Wi-Fi. Its name and password come from the module's [configuration](#configuration). You can't create a hotspot while Wi-Fi is off, or while your only Wi-Fi card is connected to a network.
- **Scan Wi-Fi QR Code:** Joins a network by scanning its QR code with your camera. This needs the QRCA barcode scanner, which isn't part of SonicDE; the button is greyed out until it's installed.
- **Configure network connections…:** Opens the Wi-Fi & Networking module.

When a network needs you to log in on a web page first, as many public hotspots do, the widget shows **You need to log in to this network** with a **Log in** button.

Middle-click the network icon to turn airplane mode on or off. Right-click it for **Enable Wi-Fi**, **Enable Mobile Data**, **Enable Airplane Mode**, **Open Network Login Page…** (when a network is waiting for you to log in) and **Configure Network Connections…**.

## The Wi-Fi & Networking module

The module lists your connections on the left. Select one to change its settings on the right, then click **Apply** to save them. If you move to another connection with unsaved changes, the module asks whether to save them.

Right-click a connection, or use its menu, for:

- **Connect** or **Disconnect**. You can only connect to networks that are in range.
- **Duplicate:** Makes a copy of the connection, with "(Copy)" added to its name.
- **Delete:** Removes the connection.
- **Export:** Saves a VPN connection to a file, for VPN types that support it.

The buttons under the list do the same for the selected connection: **Add new connection**, **Remove selected connection**, which asks before removing it, and **Export selected connection**.

### Adding a connection

**Add new connection** opens **Choose a Connection Type**:

- **Hardware based connections:** DSL, Infiniband, Mobile Broadband, Wired Ethernet, Wired Ethernet (shared), Wi-Fi and Wi-Fi (shared). The shared types share this computer's internet connection with other devices.
- **Virtual connections:** Bond, Bridge, Team and Vlan.
- **VPN connections:** WireGuard and the other VPN types. See [VPN connections](vpn.md).
- **Other:** **Import VPN connection…** reads a saved VPN configuration file.

### Configuration

The **Configuration** button under the list opens these settings:

- **Ask for PIN on modem detection:** Asks for your SIM card's PIN when a mobile broadband modem is plugged in.
- **Show virtual connections:** Also lists virtual connections such as bridges and bonds.
- **Create new connections as system connections:** Saves new connections for every user of this computer, not just for you.
- **Hotspot:** The **Name:** and **Password:** of the hotspot the Networks widget creates. The password can be left empty for an open hotspot; otherwise the module checks that it's a length Wi-Fi accepts.
