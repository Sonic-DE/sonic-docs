---
title: VPN connections
description: Set up, import and export VPN connections in the Wi-Fi & Networking module.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-network-manager b75aeba0e (vpn/*: plugin metadata and .ui forms; CMakeLists.txt BUILD_OPENCONNECT; libs/models/creatableconnectionsmodel.cpp; libs/handler.cpp; kcms/kcm_connections/kcm.cpp; org.kde.vpnimport.desktop); written from the code, not clicked through"
---

# VPN connections

A VPN (virtual private network) connects your computer to another network, such as your workplace's, over the internet. You set VPN connections up in the [Wi-Fi & Networking](wifi-networking.md) module, and connect and disconnect them with the Networks widget in the system tray like any other connection.

## Adding a VPN connection

In the Wi-Fi & Networking module, click **Add new connection**. The **VPN connections** group lists the types SonicDE can set up:

| Type | For |
| --- | --- |
| **WireGuard** | WireGuard tunnels |
| **OpenVPN** | OpenVPN servers |
| **Cisco Compatible VPN (vpnc)** | Cisco, Juniper, Netscreen and Sonicwall IPsec gateways |
| **IPsec based VPN (strongswan)** and **IPsec based VPN (libreswan)** | IPsec, IKEv1 and IKEv2 servers |
| **Layer 2 Tunneling Protocol (L2TP)** | L2TP servers |
| **Point-to-Point Tunneling Protocol (PPTP)** | Microsoft and other PPTP servers |
| **Secure Socket Tunneling Protocol (SSTP)** | Microsoft and other SSTP servers |
| **Fortinet SSLVPN (fortisslvpn)** | Fortinet SSL VPNs |
| **SSH** | Tunnels through an SSH server |
| **Iodine DNS tunnel (iodine)** | Tunnels through DNS |

The OpenConnect types are only there if SonicDE was built with OpenConnect support: **Cisco AnyConnect Compatible VPN (openconnect)**, **Juniper SSL VPN (openconnect)**, **PAN Global Protect (openconnect)**, **Pulse Connect Secure (openconnect)**, **F5 BIG-IP Compatible VPN (openconnect)**, **Fortinet Compatible VPN (openconnect)** and **Array Networks Compatible VPN (openconnect)**.

Choose a type, fill in the settings your VPN provider or network administrator gave you, and click **Apply**. Almost every type starts with **Gateway:**, the address of the VPN server. What follows depends on the type, for example:

- **OpenVPN:** **Connection type:** **Certificates (TLS)**, **Static Key**, **Password** or **Password with Certificates (TLS)**, with fields for the **CA Certificate:**, **User Certificate:**, **Private Key:** and **Password:** to match. **Advanced…** has many more settings.
- **Cisco Compatible VPN (vpnc):** **User name:**, **User password:**, **Group name:** and **Group password:**, with **Use hybrid authentication** for a certificate as well as a password.
- **IPsec based VPN (strongswan):** **Authentication** by certificate and private key, ssh-agent, smartcard or EAP, and **Options** such as **Request an inner IP address**.
- **Layer 2 Tunneling Protocol (L2TP):** **Authentication type:** **Password** or **Certificates (TLS)**, and **IPsec Settings…** and **PPP Settings…** for the rest.
- **SSH:** The network addresses for the tunnel, and **Type:** **SSH Agent**, **Password** or **Key authentication**.
- The OpenConnect types: **VPN Protocol:**, certificates, **Proxy:** and **Token Authentication**.

## Importing and exporting

If you have a VPN configuration file, use **Import VPN connection…** in the **Other** group instead of a VPN type. SonicDE can import OpenVPN files (`.ovpn` or `.conf`), Cisco files (`.pcf`) and WireGuard files (`.conf`).

You can also open an OpenVPN or Cisco file from the file manager. System Settings opens and asks **Import the VPN configuration from "…"?**; click **Import**.

OpenVPN and Cisco Compatible VPN (vpnc) connections can be saved to a file with **Export selected connection**, or **Export** in the connection's menu.

## When a VPN type is missing

SonicDE only provides the settings pages. Connecting also needs NetworkManager's own plugin for that VPN type, which your distribution packages separately. Install the one for each VPN type you use.

If you try to connect and NetworkManager's plugin is missing, a notification says **NetworkManager is missing support for '…' VPN connections.**, with an **Install** button that asks your software centre for it, if you have one.
