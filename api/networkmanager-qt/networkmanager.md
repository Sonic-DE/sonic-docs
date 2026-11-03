---
title: "NetworkManager Namespace"
description: "Qt wrapper for NetworkManager API."
---

# NetworkManager Namespace

Qt wrapper for NetworkManager API. [More...](#details)

- Header: NetworkManager
- CMake: find\_package(KF6 REQUIRED COMPONENTS NetworkManagerQt) target\_link\_libraries(mytarget PRIVATE KF6::NetworkManagerQt)

## Detailed Description {#details}

This class allows querying the underlying system to discover the available network interfaces and reachable networks. It has also the responsibility to notify when a network interface appears or disappears.

It is the unique entry point for network management. Applications should use it to find network interfaces, or to be notified about network related changes.

Note that it is implemented as a singleton

## Classes {#classes}

### class [AccessPoint](networkmanager-accesspoint.md)

Represents an access point.

### class [ActiveConnection](networkmanager-activeconnection.md)

An active connection.

### class [AdslDevice](networkmanager-adsldevice.md)

An adsl device interface.

### class [AdslSetting](networkmanager-adslsetting.md)

Represents adsl setting.

### class [BluetoothDevice](networkmanager-bluetoothdevice.md)

A bluetooth device interface.

### class [BluetoothSetting](networkmanager-bluetoothsetting.md)

Represents bluetooth setting.

### class [BondDevice](networkmanager-bonddevice.md)

A bond device interface.

### class [BondSetting](networkmanager-bondsetting.md)

Represents bond setting.

### class [BridgeDevice](networkmanager-bridgedevice.md)

A bridge device interface.

### class [BridgePortSetting](networkmanager-bridgeportsetting.md)

Represents bridge port setting.

### class [BridgeSetting](networkmanager-bridgesetting.md)

Represents bridge setting.

### class [CdmaSetting](networkmanager-cdmasetting.md)

Represents cdma setting.

### class [Connection](networkmanager-connection.md)

This class represents a single network connection configuration.

### class [ConnectionSettings](networkmanager-connectionsettings.md)

Represents collection of all connection settings.

### class [DcbSetting](networkmanager-dcbsetting.md)

Represents Dcb setting.

### class [Device](networkmanager-device.md)

This class represents a common device interface.

### class [DeviceStateReason](networkmanager-devicestatereason.md)

### class [DeviceStatistics](networkmanager-devicestatistics.md)

Represents device statistics interface.

### class [Dhcp4Config](networkmanager-dhcp4config.md)

This class represents dhcp4 configuration.

### class [Dhcp6Config](networkmanager-dhcp6config.md)

This class represents dhcp4 configuration.

### class [DnsConfiguration](networkmanager-dnsconfiguration.md)

This class represents IP configuration.

### class [DnsDomain](networkmanager-dnsdomain.md)

This class represents the configuration for a DNS domain.

### class [GenericDevice](networkmanager-genericdevice.md)

A generic device interface.

### class [GenericSetting](networkmanager-genericsetting.md)

Represents generic setting.

### class [GsmSetting](networkmanager-gsmsetting.md)

Represents gsm setting.

### class [InfinibandDevice](networkmanager-infinibanddevice.md)

An infiniband device interface.

### class [InfinibandSetting](networkmanager-infinibandsetting.md)

Represents infiniband setting.

### class [IpAddress](networkmanager-ipaddress.md)

This class represents IP address.

### class [IpConfig](networkmanager-ipconfig.md)

This class represents IP configuration.

### class [IpRoute](networkmanager-iproute.md)

This class represents IP route.

### class [IpTunnelDevice](networkmanager-iptunneldevice.md)

A Ip Tunnel device interface.

### class [IpTunnelSetting](networkmanager-iptunnelsetting.md)

Represents IpTunnel setting.

### class [Ipv4Setting](networkmanager-ipv4setting.md)

Represents ipv4 setting.

### class [Ipv6Setting](networkmanager-ipv6setting.md)

Represents ipv6 setting.

### class [MacVlanDevice](networkmanager-macvlandevice.md)

A macvlan device interface.

### class [MacsecSetting](networkmanager-macsecsetting.md)

Represents Macsec setting.

### class [MatchSetting](networkmanager-matchsetting.md)

Represents Match setting.

### class [ModemDevice](networkmanager-modemdevice.md)

Represents a generic modem device, generally defined by the [modemCapabilities](networkmanager-modemdevice.md#modemCapabilities)() it exposes and at the current point in time by the [currentCapabilities](networkmanager-modemdevice.md#currentCapabilities)().

### class [Notifier](networkmanager-notifier.md)

### class [OlpcMeshDevice](networkmanager-olpcmeshdevice.md)

A OLPC mesh interface.

### class [OlpcMeshSetting](networkmanager-olpcmeshsetting.md)

Represents olpc mesh setting.

### class [OvsBridgeSetting](networkmanager-ovsbridgesetting.md)

Represents ovs-bridge setting.

### class [OvsInterfaceSetting](networkmanager-ovsinterfacesetting.md)

Represents ovs-interface setting.

### class [OvsPatchSetting](networkmanager-ovspatchsetting.md)

Represents OvsPatch setting.

### class [OvsPortSetting](networkmanager-ovsportsetting.md)

Represents o setting.

### class [PppSetting](networkmanager-pppsetting.md)

Represents ppp setting.

### class [PppoeSetting](networkmanager-pppoesetting.md)

Represents pppoe setting.

### class [ProxySetting](networkmanager-proxysetting.md)

Represents proxy setting.

### class [SecretAgent](networkmanager-secretagent.md)

Implementation of a private D-Bus interface used by secret agents that store and provide secrets to [NetworkManager](networkmanager.md).

### class [Security8021xSetting](networkmanager-security8021xsetting.md)

Represents 802.1x wireless security setting.

### class [SerialSetting](networkmanager-serialsetting.md)

Represents serial setting.

### class [Setting](networkmanager-setting.md)

Base class for all kinds of setting.

### class [SettingsNotifier](networkmanager-settingsnotifier.md)

This class manages provides access to connections and notify about new ones.

### class [TcSetting](networkmanager-tcsetting.md)

Represents Tc setting.

### class [TeamDevice](networkmanager-teamdevice.md)

A team device interface.

### class [TeamPortSetting](networkmanager-teamportsetting.md)

Represents TeamPort setting.

### class [TeamSetting](networkmanager-teamsetting.md)

Represents team setting.

### class [TemplateSetting](networkmanager-templatesetting.md)

Represents generic setting.

### class [TunDevice](networkmanager-tundevice.md)

A tun device interface.

### class [TunSetting](networkmanager-tunsetting.md)

Represents generic setting.

### class [UserSetting](networkmanager-usersetting.md)

Represents user setting.

### class [VethDevice](networkmanager-vethdevice.md)

A veth device interface.

### class [VlanDevice](networkmanager-vlandevice.md)

A vlan device interface.

### class [VlanSetting](networkmanager-vlansetting.md)

Represents vlan setting.

### class [VpnConnection](networkmanager-vpnconnection.md)

An active VPN connection.

### class [VpnPlugin](networkmanager-vpnplugin.md)

### class [VpnSetting](networkmanager-vpnsetting.md)

Represents vpn setting.

### class [VxlanSetting](networkmanager-vxlansetting.md)

Represents vxlan setting.

### class [WifiP2PDevice](networkmanager-wifip2pdevice.md)

[WiFi](networkmanager.md#LogDomain-enum) P2P device.

### class [WifiP2PPeer](networkmanager-wifip2ppeer.md)

Represents a wifip2p peer.

### class [WifiP2PSetting](networkmanager-wifip2psetting.md)

Represents wifip2p setting.

### class [WimaxDevice](networkmanager-wimaxdevice.md)

Wimax network interface.

### class [WimaxNsp](networkmanager-wimaxnsp.md)

Wimax network service provider (access point).

### class [WimaxSetting](networkmanager-wimaxsetting.md)

Represents wimax setting.

### class [WireGuardDevice](networkmanager-wireguarddevice.md)

A WireGuard device interface.

### class [WireGuardSetting](networkmanager-wireguardsetting.md)

Represents generic setting.

### class [WiredDevice](networkmanager-wireddevice.md)

A wired device interface.

### class [WiredSetting](networkmanager-wiredsetting.md)

Represents wired setting.

### class [WirelessDevice](networkmanager-wirelessdevice.md)

A wireless network interface.

### class [WirelessNetwork](networkmanager-wirelessnetwork.md)

This class represents a wireless network, which aggregates all access points with the same SSID.

### class [WirelessSecuritySetting](networkmanager-wirelesssecuritysetting.md)

Represents wireless security setting.

### class [WirelessSetting](networkmanager-wirelesssetting.md)

Represents wireless setting.

## Type Documentation {#type-documentation}

### enum NetworkManager::Connectivity {#Connectivity-enum}

Describes the network connectivity state.

| Constant | Value | Description |
| --- | --- | --- |
| `NetworkManager::UnknownConnectivity` | `0` | Network connectivity is unknown. |
| `NetworkManager::NoConnectivity` | `1` | The host is not connected to any network. |
| `NetworkManager::Portal` | `2` | The host is behind a captive portal and cannot reach the full Internet. |
| `NetworkManager::Limited` | `3` | The host is connected to a network, but does not appear to be able to reach the full Internet. |
| `NetworkManager::Full` | `4` | The host is connected to a network, and appears to be able to reach the full Internet. |

### NetworkManager::IpAddresses {#IpAddresses-typedef}

### NetworkManager::IpRoutes {#IpRoutes-typedef}

### enum NetworkManager::LogDomain {#LogDomain-enum}

**flags NetworkManager::LogDomains**

| Constant | Value |   |
| --- | --- | --- |
| `NetworkManager::NoChange` | `0` |   |
| `NetworkManager::None` | `1` |   |
| `NetworkManager::Hardware` | `2` |   |
| `NetworkManager::RFKill` | `3` |   |
| `NetworkManager::Ethernet` | `4` |   |
| `NetworkManager::WiFi` | `5` |   |
| `NetworkManager::Bluetooth` | `6` |   |
| `NetworkManager::MobileBroadBand` | `7` |   |
| `NetworkManager::DHCP4` | `8` |   |
| `NetworkManager::DHCP6` | `9` |   |
| `NetworkManager::PPP` | `10` |   |
| `NetworkManager::WiFiScan` | `11` |   |
| `NetworkManager::IPv4` | `12` |   |
| `NetworkManager::IPv6` | `13` |   |
| `NetworkManager::AutoIPv4` | `14` |   |
| `NetworkManager::DNS` | `15` |   |
| `NetworkManager::VPN` | `16` |   |
| `NetworkManager::Sharing` | `17` |   |
| `NetworkManager::Supplicant` | `18` |   |
| `NetworkManager::UserSet` | `19` |   |
| `NetworkManager::SysSet` | `20` |   |
| `NetworkManager::Suspend` | `21` |   |
| `NetworkManager::Core` | `22` |   |
| `NetworkManager::Devices` | `23` |   |
| `NetworkManager::OLPC` | `24` |   |
| `NetworkManager::Wimax` | `25` | TODO: mark it deprecated somehow? |
| `NetworkManager::Infiniband` | `26` |   |
| `NetworkManager::Firewall` | `27` |   |
| `NetworkManager::Adsl` | `28` |   |
| `NetworkManager::Bond` | `29` |   |
| `NetworkManager::Vlan` | `30` |   |
| `NetworkManager::Agents` | `31` |   |
| `NetworkManager::Settings` | `32` |   |
| `NetworkManager::Bridge` | `33` |   |
| `NetworkManager::DbusProps` | `34` |   |
| `NetworkManager::Team` | `35` |   |
| `NetworkManager::ConCheck` | `36` |   |
| `NetworkManager::Dcb` | `37` |   |
| `NetworkManager::Dispatch` | `38` |   |

The `LogDomains` type is a typedef for `QFlags<LogDomain>. `It stores an OR combination of `LogDomain` values.

### enum NetworkManager::LogLevel {#LogLevel-enum}

| Constant | Value |   |
| --- | --- | --- |
| `NetworkManager::Error` | `0` |   |
| `NetworkManager::Warning` | `1` |   |
| `NetworkManager::Info` | `2` |   |
| `NetworkManager::Debug` | `3` |   |
| `NetworkManager::Trace` | `4` | = Debug in runtime NM \< 0.9.10 |

### enum NetworkManager::Status {#Status-enum}

Possible device interfaceflags

| Constant | Value | Description |
| --- | --- | --- |
| `NetworkManager::Unknown` | `0` | the networking system is not active or unable to report its status - proceed with caution |
| `NetworkManager::Asleep` | `1` | networking is inactive and all devices are disabled |
| `NetworkManager::Disconnected` | `2` | the system is not connected to any network |
| `NetworkManager::Disconnecting` | `3` | the system is breaking the connection |
| `NetworkManager::Connecting` | `4` | the system is not connected to any network |
| `NetworkManager::ConnectedLinkLocal` | `5` | a network device is connected, but there is only link-local connectivity |
| `NetworkManager::ConnectedSiteOnly` | `6` | a network device is connected, but there is only site-local connectivity |
| `NetworkManager::Connected` | `7` | the system is currently connected to a network |

### enum NetworkManager::WirelessSecurityType {#WirelessSecurityType-enum}

Capabilities to pass to secret agents

| Constant |   |
| --- | --- |
| `NetworkManager::UnknownSecurity` | `-1` |
| `NetworkManager::NoneSecurity` | `0` |
| `NetworkManager::StaticWep` | `1` |
| `NetworkManager::DynamicWep` | `2` |
| `NetworkManager::Leap` | `3` |
| `NetworkManager::WpaPsk` | `4` |
| `NetworkManager::WpaEap` | `5` |
| `NetworkManager::Wpa2Psk` | `6` |
| `NetworkManager::Wpa2Eap` | `7` |
| `NetworkManager::SAE` | `8` |
| `NetworkManager::Wpa3SuiteB192` | `9` |
| `NetworkManager::OWE` | `10` |

## Function Documentation {#function-documentation}

### QDBusPendingReply\<QDBusObjectPath\> NetworkManager::activateConnection(const QString &*connectionUni*, const QString &*interfaceUni*, const QString &*connectionParameter*) {#activateConnection}

Activate a connection using the supplied device.

`connectionUni` unique identifier for the connection to be activated `interfaceUni` unique identifier of the network interface to be activated `connectionParameter` can be used to specify extra parameters not specific to the NetworkInterface or the connection, eg which AP to use when several present with same ESSID in range (because ESSID does not guarantee that the AP is part of the network you want to join!)

### ActiveConnection::Ptr NetworkManager::activatingConnection() {#activatingConnection}

Returns an active connection that is currently being activated and which is expected to become the new [primaryConnection](networkmanager.md#primaryConnection)() when it finishes activating.

### ActiveConnection::List NetworkManager::activeConnections() {#activeConnections}

Access the list of any active connections

Returns a list of valid [ActiveConnection](networkmanager-activeconnection.md) objects

### QStringList NetworkManager::activeConnectionsPaths() {#activeConnectionsPaths}

Access the list of any active connections paths

Returns a list of valid [ActiveConnection](networkmanager-activeconnection.md) paths

### QDBusPendingReply\<QDBusObjectPath, QDBusObjectPath, QVariantMap\> NetworkManager::addAndActivateConnection2(const NMVariantMapMap &*connection*, const QString &*interfaceUni*, const QString &*connectionParameter*, const QVariantMap &*options*) {#addAndActivateConnection2}

\* Adds a new connection using the given details (if any) as a template (automatically filling in missing settings with the capabilities of the given device and \* specific object), then activate the new connection. Cannot be used for VPN connections at this time. \* \* `connection` connection definition to be added and activated \* `interfaceUni` unique identifier of the network interface to be activated \* `connectionParameter` can be used to specify extra parameters not specific to the NetworkInterface or the connection, eg which AP to use when several \* present with same ESSID in range (because ESSID does not guarantee that the AP is part of the network you want to join!) \* `options` further options for the method call. \* \* This method extends AddAndActivateConnection to allow passing further \* parameters. At this time the following options are supported: \* \* \* persist: A string value of either "disk" (default), "memory" or "volatile". If "memory" is passed, the connection will not be saved to disk. If \* "volatile" is passed, the connection will not be saved to disk and will be destroyed when disconnected. \* \* bind-activation: Bind the activation lifetime. Set to "dbus-name" to automatically disconnect when the requesting process disappears from the bus. \* The default of "none" means the connection is kept activated normally. \* \* ote will call AddAndActivateConnection(connection, interfaceUni, connectionParameter) instead when [NetworkManager](networkmanager.md) is older than 1.16, which means that the \* options property is ignored

### QDBusPendingReply\<QDBusObjectPath, QDBusObjectPath\> NetworkManager::addAndActivateConnection(const NMVariantMapMap &*connection*, const QString &*interfaceUni*, const QString &*connectionParameter*) {#addAndActivateConnection}

Adds a new connection using the given details (if any) as a template (automatically filling in missing settings with the capabilities of the given device and specific object), then activate the new connection. Cannot be used for VPN connections at this time.

`connection` connection definition to be added and activated `interfaceUni` unique identifier of the network interface to be activated `connectionParameter` can be used to specify extra parameters not specific to the NetworkInterface or the connection, eg which AP to use when several present with same ESSID in range (because ESSID does not guarantee that the AP is part of the network you want to join!)

### QDBusPendingReply\<QDBusObjectPath\> NetworkManager::addConnection(const NMVariantMapMap &*settings*) {#addConnection}

Add new connection and save it to disk. This operation does not start the network connection unless (1) device is idle and able to connect to the network described by the new connection, and (2) the connection is allowed to be started automatically. Once the connection has been added, you will get a notification through SettingsNotifier::connectionAddComplete()

Returns Uuid of the new connection that was just added.

### QDBusPendingReply\<QDBusObjectPath\> NetworkManager::addConnectionUnsaved(const NMVariantMapMap &*settings*) {#addConnectionUnsaved}

Add new connection but do not save it to disk immediately. This operation does not start the network connection unless (1) device is idle and able to connect to the network described by the new connection, and (2) the connection is allowed to be started automatically.

Use the 'Save' method on the connection to save these changes to disk. Note that unsaved changes will be lost if the connection is reloaded from disk (either automatically on file change or due to an explicit ReloadConnections call).

Once the connection has been added, you will get a notification through SettingsNotifier::connectionAddComplete()

Returns Uuid of the new connection that was just added.

### bool NetworkManager::canModify() {#canModify}

Returns `true` if the user can modify the settings

### QDBusPendingReply\<uint\> NetworkManager::checkConnectivity() {#checkConnectivity}

Re-check the network connectivity state.

*See also* [connectivity](networkmanager.md#connectivity)()

### bool NetworkManager::checkVersion(const int *x*, const int *y*, const int *z*) {#checkVersion}

Checks if [NetworkManager](networkmanager.md) version is at least x.y.z Returns true if [NetworkManager](networkmanager.md)'s version is greater or equal, false otherwise

### QDateTime NetworkManager::clockBootTimeToDateTime(qlonglong *clockBootime*) {#clockBootTimeToDateTime}

### int NetworkManager::compareVersion(const QString &*version*) {#compareVersion}

Compares [NetworkManager](networkmanager.md)'s version to the parameter version. returns 1, -1 or 0 if [NetworkManager](networkmanager.md)'s version is greater, less or equal to parameter.

### int NetworkManager::compareVersion(const int *x*, const int *y*, const int *z*) {#compareVersion-1}

Compares [NetworkManager](networkmanager.md) version to x.y.z. returns 1, -1 or 0 if [NetworkManager](networkmanager.md)'s version is greater, less or equal to x.y.z.

### NetworkManager::Connectivity NetworkManager::connectivity() {#connectivity}

Returns the network connectivity state

### \[since 6.10.0\] QString NetworkManager::connectivityCheckUri() {#connectivityCheckUri}

Returns the URI used for connectivity check

This function was introduced in Qt 6.10.0.

### QDBusPendingReply\<\> NetworkManager::deactivateConnection(const QString &*activeConnection*) {#deactivateConnection}

Deactivate this network interface, if active

`activeConnection` identifier of the connection to deactivate

### bool NetworkManager::deviceSupportsApCiphers(*NetworkManager::WirelessDevice::Capabilities*, NetworkManager::AccessPoint::WpaFlags *ciphers*, NetworkManager::WirelessSecurityType *type*) {#deviceSupportsApCiphers}

### ActiveConnection::Ptr NetworkManager::findActiveConnection(const QString &*uni*) {#findActiveConnection}

Find an [ActiveConnection](networkmanager-activeconnection.md) object for an active connection id

`uni` the id of the [ActiveConnection](networkmanager-activeconnection.md) Returns a valid [ActiveConnection](networkmanager-activeconnection.md) object

### NetworkManager::WirelessSecurityType NetworkManager::findBestWirelessSecurity(*NetworkManager::WirelessDevice::Capabilities*, bool *haveAp*, bool *adHoc*, NetworkManager::AccessPoint::Capabilities *apCaps*, NetworkManager::AccessPoint::WpaFlags *apWpa*, NetworkManager::AccessPoint::WpaFlags *apRsn*) {#findBestWirelessSecurity}

### int NetworkManager::findChannel(int *freq*) {#findChannel}

`freq` frequency of a wireless network

Returns The frequency channel.

### NetworkManager::Connection::Ptr NetworkManager::findConnection(const QString &*path*) {#findConnection}

Retrieves the connection for the given path, returns null if not found

### NetworkManager::Connection::Ptr NetworkManager::findConnectionByUuid(const QString &*uuid*) {#findConnectionByUuid}

Retrieves the connection for the given `uuid`, returns null if not found

### Device::Ptr NetworkManager::findDeviceByIpFace(const QString &*iface*) {#findDeviceByIpFace}

Return the network device referenced by its IP interface name. This is not system independent so programs that will use this method will not be portable.

### NetworkManager::WirelessSetting::FrequencyBand NetworkManager::findFrequencyBand(int *freq*) {#findFrequencyBand}

### Device::Ptr NetworkManager::findNetworkInterface(const QString &*uni*) {#findNetworkInterface}

Find a new NetworkInterface object given its UNI. This pointer is owned by the Solid infrastructure.

`uni` the identifier of the network interface to find Returns a valid NetworkInterface object if there's a device having the given UNI, an invalid one otherwise

### QList\<QPair\<int, int\>\> NetworkManager::getAFreqs() {#getAFreqs}

### QList\<QPair\<int, int\>\> NetworkManager::getBFreqs() {#getBFreqs}

### QDBusPendingReply\<QString, QString\> NetworkManager::getLogging() {#getLogging}

Get current logging verbosity level and operations domains

### NetworkManager::DnsConfiguration NetworkManager::globalDnsConfiguration() {#globalDnsConfiguration}

Returns Gets the global DNS configuration.

*See also* [setGlobalDnsConfiguration](networkmanager.md#setGlobalDnsConfiguration)()

### QString NetworkManager::hostname() {#hostname}

Returns hostname of the machine

### QHostAddress NetworkManager::ipv6AddressAsHostAddress(const QByteArray &*address*) {#ipv6AddressAsHostAddress}

Returns [QHostAddress](https://doc.qt.io/qt-6/qhostaddress.html) representation of an ipv6 address

`address` byte array containing the binary representation of the address

### QByteArray NetworkManager::ipv6AddressFromHostAddress(const QHostAddress &*address*) {#ipv6AddressFromHostAddress}

Returns binary representation of an ipv6 address

`address` qhostaddress containing the address

### \[since 6.10.0\] bool NetworkManager::isConnectivityCheckAvailable() {#isConnectivityCheckAvailable}

Returns whether the connectivity check is available

This function was introduced in Qt 6.10.0.

### \[since 6.10.0\] bool NetworkManager::isConnectivityCheckEnabled() {#isConnectivityCheckEnabled}

Returns whether the connectivity check is enabled

This function was introduced in Qt 6.10.0.

### bool NetworkManager::isNetworkingEnabled() {#isNetworkingEnabled}

Retrieves the status of networking (as a whole) in the system. This is distinct from whether the system's networking is online or offline. To check that, see [status](networkmanager.md#status)().

Returns true if this networking is enabled, false otherwise

### bool NetworkManager::isStartingUp() {#isStartingUp}

Indicates whether NM is still starting up; this becomes `false` when NM has finished attempting to activate every connection that it might be able to activate at startup.

### bool NetworkManager::isWirelessEnabled() {#isWirelessEnabled}

Retrieves the activation status of wireless networking in the system.

Returns true if this wireless networking is enabled, false otherwise

### bool NetworkManager::isWirelessHardwareEnabled() {#isWirelessHardwareEnabled}

Retrieves the status of wireless hardware in the system. This is typically controlled by a physical switch so there is no way to set this in software.

Returns true if this wireless networking is enabled, false otherwise

### bool NetworkManager::isWwanEnabled() {#isWwanEnabled}

Retrieves the status of wireless broadband (Wireless WAN) in the system.

Returns true if this type of wireless networking is enabled, false otherwise

### bool NetworkManager::isWwanHardwareEnabled() {#isWwanHardwareEnabled}

Retrieves the status of wireless broadband (Wireless WAN) hardware in the system. This is typically controlled by a physical switch so there is no way to set this in software.

Returns true if this broddband hardware is enabled, false otherwise

### NetworkManager::Connection::List NetworkManager::listConnections() {#listConnections}

Retrieves the list of connections.

### QDBusPendingReply\<bool, QStringList\> NetworkManager::loadConnections(const QStringList &*filenames*) {#loadConnections}

Loads or reloads the indicated connections from disk. You should call this after making changes directly to an on-disk connection file to make sure that [NetworkManager](networkmanager.md) sees the changes. (If "monitor-connection-files" in [NetworkManager](networkmanager.md).conf is "true", then this will have no real effect, but is harmless.) As with AddConnection(), this operation does not necessarily start the network connection.

Returns Success or failure of the operation as a whole. True if [NetworkManager](networkmanager.md) at least tried to load the indicated connections, even if it did not succeed. False if an error occurred before trying to load the connections (eg, permission denied).

Returns Paths of connection files that could not be loaded.

### QString NetworkManager::macAddressAsString(const QByteArray &*ba*) {#macAddressAsString}

Returns String representation of a mac address.

`ba` byte array containing the binary repesentation of the address

### QByteArray NetworkManager::macAddressFromString(const QString &*s*) {#macAddressFromString}

Returns binary repesentation of a mac address.

`s` string representation of the address

### bool NetworkManager::macAddressIsValid(const QByteArray &*macAddress*) {#macAddressIsValid}

### bool NetworkManager::macAddressIsValid(const QString &*macAddress*) {#macAddressIsValid-1}

### NetworkManager::Device::MeteredStatus NetworkManager::metered() {#metered}

Returns Indicates whether the connectivity is metered.

### Device::List NetworkManager::networkInterfaces() {#networkInterfaces}

Retrieves the list of all the network interfaces in the system. It includes both hardware and virtual devices.

Returns the list of network interfaces available in this system

### NetworkManager::Notifier \*NetworkManager::notifier() {#notifier}

### NMStringMap NetworkManager::permissions() {#permissions}

### ActiveConnection::Ptr NetworkManager::primaryConnection() {#primaryConnection}

Returns the "primary" active connection being used to access the network. In particular, if there is no VPN active, or the VPN does not have the default route, then this indicates the connection that has the default route. If there is a VPN active with the default route, then this indicates the connection that contains the route to the VPN endpoint.

### NetworkManager::ConnectionSettings::ConnectionType NetworkManager::primaryConnectionType() {#primaryConnectionType}

Returns The connection type of the "primary" active connection being used to access the network. This is the same as the Type property on the object indicated by PrimaryConnection.

### QDBusPendingReply\<bool\> NetworkManager::reloadConnections() {#reloadConnections}

Tells [NetworkManager](networkmanager.md) to reload all connection files from disk, including noticing any added or deleted connection files. By default, connections are re-read automatically any time they change, so you only need to use this command if you have set "monitor-connection-files=false" in [NetworkManager](networkmanager.md).conf.

Returns Success or failure.

### void NetworkManager::saveHostname(const QString &*hostname*) {#saveHostname}

Configure the following hostname

### bool NetworkManager::securityIsValid(NetworkManager::WirelessSecurityType *type*, NetworkManager::WirelessDevice::Capabilities *interfaceCaps*, bool *haveAp*, bool *adHoc*, NetworkManager::AccessPoint::Capabilities *apCaps*, NetworkManager::AccessPoint::WpaFlags *apWpa*, NetworkManager::AccessPoint::WpaFlags *apRsn*) {#securityIsValid}

### NetworkManager::WirelessSecurityType NetworkManager::securityTypeFromConnectionSetting(const NetworkManager::ConnectionSettings::Ptr &*settings*) {#securityTypeFromConnectionSetting}

### void NetworkManager::setGlobalDnsConfiguration(const NetworkManager::DnsConfiguration &*configuration*) {#setGlobalDnsConfiguration}

Returns Sets the global DNS configuration.

*See also* [globalDnsConfiguration](networkmanager.md#globalDnsConfiguration)()

### void NetworkManager::setLogging(*NetworkManager::LogLevel*, *NetworkManager::LogDomains*) {#setLogging}

### void NetworkManager::setNetworkingEnabled(bool *enabled*) {#setNetworkingEnabled}

*See also* [isNetworkingEnabled](networkmanager.md#isNetworkingEnabled)()

### void NetworkManager::setWirelessEnabled(bool *enabled*) {#setWirelessEnabled}

*See also* [isWirelessEnabled](networkmanager.md#isWirelessEnabled)()

### void NetworkManager::setWwanEnabled(bool *enabled*) {#setWwanEnabled}

*See also* [isWwanEnabled](networkmanager.md#isWwanEnabled)()

### NetworkManager::SettingsNotifier \*NetworkManager::settingsNotifier() {#settingsNotifier}

Notifier object for connecting signals

### void NetworkManager::sleep(bool *sleep*) {#sleep}

### NetworkManager::Status NetworkManager::status() {#status}

Get the manager connection state

### Device::Types NetworkManager::supportedInterfaceTypes() {#supportedInterfaceTypes}

Retrieves the interface types supported by this network manager.

Returns the interface types supported by the network manager

### QString NetworkManager::version() {#version}

Get the [NetworkManager](networkmanager.md) version

### bool NetworkManager::wepKeyIsValid(const QString &*key*, NetworkManager::WirelessSecuritySetting::WepKeyType *type*) {#wepKeyIsValid}

### bool NetworkManager::wpaPskIsValid(const QString &*psk*) {#wpaPskIsValid}
