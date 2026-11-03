---
title: "NetworkManager::Device Class"
description: "This class represents a common device interface."
---

# NetworkManager::Device Class

This class represents a common device interface. [More...](#details)

- **Header:** `#include <NetworkManagerQt/Device>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)
- **Inherited By:** [NetworkManager::AdslDevice](networkmanager-adsldevice.md), [NetworkManager::BondDevice](networkmanager-bonddevice.md), [NetworkManager::BridgeDevice](networkmanager-bridgedevice.md), [NetworkManager::GenericDevice](networkmanager-genericdevice.md), [NetworkManager::GreDevice](networkmanager-gredevice.md), [NetworkManager::InfinibandDevice](networkmanager-infinibanddevice.md), [NetworkManager::IpTunnelDevice](networkmanager-iptunneldevice.md), [NetworkManager::MacVlanDevice](networkmanager-macvlandevice.md), [NetworkManager::ModemDevice](networkmanager-modemdevice.md), [NetworkManager::OlpcMeshDevice](networkmanager-olpcmeshdevice.md), [NetworkManager::TeamDevice](networkmanager-teamdevice.md), [NetworkManager::TunDevice](networkmanager-tundevice.md), [NetworkManager::VethDevice](networkmanager-vethdevice.md), [NetworkManager::VlanDevice](networkmanager-vlandevice.md), [NetworkManager::WifiP2PDevice](networkmanager-wifip2pdevice.md), [NetworkManager::WimaxDevice](networkmanager-wimaxdevice.md), [NetworkManager::WiredDevice](networkmanager-wireddevice.md), [NetworkManager::WireGuardDevice](networkmanager-wireguarddevice.md), and [NetworkManager::WirelessDevice](networkmanager-wirelessdevice.md)

[List of all members, including inherited members](networkmanager-device-members.md)  
[Deprecated members](networkmanager-device-obsolete.md)

## Public Types

- [enum Device::Capability](#Capability-enum)
- [enum Device::Interfaceflag](#Interfaceflag-enum)
- [Device::List](#List-typedef)
- [enum Device::MeteredStatus](#MeteredStatus-enum)
- [Device::Ptr](#Ptr-typedef)
- [enum Device::State](#State-enum)
- [enum Device::StateChangeReason](#StateChangeReason-enum)
- [enum Device::Type](#Type-enum)

## Properties

- [\[read-only\] InterfaceFlags : Interfaceflags](#InterfaceFlags-prop)
- [autoconnect : bool](#autoconnect-prop)
- [\[read-only\] deviceStatistics : NetworkManager::DeviceStatistics::Ptr](#deviceStatistics-prop)
- [\[read-only\] driver : QString](#driver-prop)
- [\[read-only\] driverVersion : QString](#driverVersion-prop)
- [\[read-only\] firmwareMissing : bool](#firmwareMissing-prop)
- [\[read-only\] firmwareVersion : QString](#firmwareVersion-prop)
- [\[read-only\] genericCapabilities : QVariant](#genericCapabilities-prop)
- [\[read-only\] interfaceName : QString](#interfaceName-prop)
- [\[read-only\] ipInterfaceName : QString](#ipInterfaceName-prop)
- [\[read-only\] ipV4Address : QHostAddress](#ipV4Address-prop)
- [managed : bool](#managed-prop)
- [\[read-only\] metered : MeteredStatus](#metered-prop)
- [\[read-only\] mtu : uint](#mtu-prop)
- [\[read-only\] nmPluginMissing : bool](#nmPluginMissing-prop)
- [\[read-only\] state : State](#state-prop)
- [\[read-only\] stateReason : DeviceStateReason](#stateReason-prop)
- [\[read-only\] udi : QString](#udi-prop)
- [\[read-only\] uni : QString](#uni-prop)

## Public Functions

- [Device(const QString &path, QObject \*parent = nullptr)](#Device)
- [~Device()](#dtor.Device)
- [NetworkManager::ActiveConnection::Ptr activeConnection() const](#activeConnection)
- [template \<typename DevIface\> DevIface \*as()](#as)
- [template \<typename DevIface\> const DevIface \*as() const](#as-1)
- [bool autoconnect() const](#autoconnect)
- [Connection::List availableConnections()](#availableConnections)
- [NetworkManager::Device::Capabilities capabilities() const](#capabilities)
- [QVariant capabilitiesV() const](#capabilitiesV)
- [QDBusPendingReply\<\> deleteInterface()](#deleteInterface)
- [int designSpeed() const](#designSpeed)
- [DeviceStatistics::Ptr deviceStatistics() const](#deviceStatistics)
- [Dhcp4Config::Ptr dhcp4Config() const](#dhcp4Config)
- [Dhcp6Config::Ptr dhcp6Config() const](#dhcp6Config)
- [QDBusPendingReply\<\> disconnectInterface()](#disconnectInterface)
- [QString driver() const](#driver)
- [QString driverVersion() const](#driverVersion)
- [bool firmwareMissing() const](#firmwareMissing)
- [QString firmwareVersion() const](#firmwareVersion)
- [NetworkManager::Device::Interfaceflags interfaceFlags() const](#interfaceFlags)
- [QString interfaceName() const](#interfaceName)
- [QString ipInterfaceName() const](#ipInterfaceName)
- [NetworkManager::IpConfig ipV4Config() const](#ipV4Config)
- [NetworkManager::IpConfig ipV6Config() const](#ipV6Config)
- [bool isActive() const](#isActive)
- [bool isValid() const](#isValid)
- [bool managed() const](#managed)
- [NetworkManager::Device::MeteredStatus metered() const](#metered)
- [uint mtu() const](#mtu)
- [bool nmPluginMissing() const](#nmPluginMissing)
- [QString physicalPortId() const](#physicalPortId)
- [QDBusPendingReply\<\> reapplyConnection(const NMVariantMapMap &connection, qulonglong version\_id, uint flags)](#reapplyConnection)
- [void setAutoconnect(bool autoconnect)](#setAutoconnect)
- [void setManaged(bool managed)](#setManaged) (since 6.18.0)
- [NetworkManager::Device::State state() const](#state)
- [NetworkManager::DeviceStateReason stateReason() const](#stateReason)
- [NetworkManager::Device::Type type() const](#type)
- [QString udi() const](#udi)
- [QString uni() const](#uni)

## Signals

- [void activeConnectionChanged()](#activeConnectionChanged)
- [void autoconnectChanged()](#autoconnectChanged)
- [void availableConnectionAppeared(const QString &connection)](#availableConnectionAppeared)
- [void availableConnectionChanged()](#availableConnectionChanged)
- [void availableConnectionDisappeared(const QString &connection)](#availableConnectionDisappeared)
- [void capabilitiesChanged()](#capabilitiesChanged)
- [void connectionStateChanged()](#connectionStateChanged)
- [void dhcp4ConfigChanged()](#dhcp4ConfigChanged)
- [void dhcp6ConfigChanged()](#dhcp6ConfigChanged)
- [void driverChanged()](#driverChanged)
- [void driverVersionChanged()](#driverVersionChanged)
- [void firmwareMissingChanged()](#firmwareMissingChanged)
- [void firmwareVersionChanged()](#firmwareVersionChanged)
- [void interfaceFlagsChanged()](#interfaceFlagsChanged)
- [void interfaceNameChanged()](#interfaceNameChanged)
- [void ipInterfaceChanged()](#ipInterfaceChanged)
- [void ipV4AddressChanged()](#ipV4AddressChanged)
- [void ipV4ConfigChanged()](#ipV4ConfigChanged)
- [void ipV6ConfigChanged()](#ipV6ConfigChanged)
- [void managedChanged()](#managedChanged)
- [void meteredChanged(NetworkManager::Device::MeteredStatus metered)](#meteredChanged)
- [void mtuChanged()](#mtuChanged)
- [void nmPluginMissingChanged(bool nmPluginMissing)](#nmPluginMissingChanged)
- [void physicalPortIdChanged()](#physicalPortIdChanged)
- [void stateChanged(NetworkManager::Device::State newstate, NetworkManager::Device::State oldstate, NetworkManager::Device::StateChangeReason reason)](#stateChanged)
- [void stateReasonChanged()](#stateReasonChanged)
- [void udiChanged()](#udiChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum Device::Capability {#Capability-enum}

**flags Device::Capabilities**

Possible device capabilities

| Constant | Value | Description |
| --- | --- | --- |
| `NetworkManager::Device::IsManageable` | `0x1` | denotes that the device can be controlled by this API |
| `NetworkManager::Device::SupportsCarrierDetect` | `0x2` | the device informs us when it is plugged in to the medium |

The `Capabilities` type is a typedef for `QFlags<Capability>. `It stores an OR combination of `Capability` values.

### enum Device::Interfaceflag {#Interfaceflag-enum}

**flags Device::Interfaceflags**

Possible device interfaceflags

| Constant | Value | Description |
| --- | --- | --- |
| `NetworkManager::Device::None` | `NM_DEVICE_INTERFACE_FLAG_NONE` | no flags set |
| `NetworkManager::Device::Up` | `NM_DEVICE_INTERFACE_FLAG_UP` | Corresponds to kernel IFF\_UP |
| `NetworkManager::Device::LowerUp` | `NM_DEVICE_INTERFACE_FLAG_LOWER_UP` | Corresponds to kernel IFF\_LOWER\_UP |
| `NetworkManager::Device::Carrier` | `NM_DEVICE_INTERFACE_FLAG_CARRIER` | the interface has carrier |

The `Interfaceflags` type is a typedef for `QFlags<Interfaceflag>. `It stores an OR combination of `Interfaceflag` values.

### Device::List {#List-typedef}

### enum Device::MeteredStatus {#MeteredStatus-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `NetworkManager::Device::UnknownStatus` | `0` | The device metered status is unknown. |
| `NetworkManager::Device::Yes` | `1` | The device is metered and the value was statically set. |
| `NetworkManager::Device::No` | `2` | The device is not metered and the value was statically set. |
| `NetworkManager::Device::GuessYes` | `3` | The device is metered and the value was guessed. |
| `NetworkManager::Device::GuessNo` | `4` | The device is not metered and the value was guessed. |

### Device::Ptr {#Ptr-typedef}

### enum Device::State {#State-enum}

Device connection states describe the possible states of a network connection from the user's point of view. For simplicity, states from several different layers are present - this is a high level view

| Constant | Value | Description |
| --- | --- | --- |
| `NetworkManager::Device::UnknownState` | `0` | The device is in an unknown state |
| `NetworkManager::Device::Unmanaged` | `10` | The device is recognized but not managed by [NetworkManager](networkmanager.md) |
| `NetworkManager::Device::Unavailable` | `20` | The device cannot be used (carrier off, rfkill, etc) |
| `NetworkManager::Device::Disconnected` | `30` | The device is not connected |
| `NetworkManager::Device::Preparing` | `40` | The device is preparing to connect |
| `NetworkManager::Device::ConfiguringHardware` | `50` | The device is being configured |
| `NetworkManager::Device::NeedAuth` | `60` | The device is awaiting secrets necessary to continue connection |
| `NetworkManager::Device::ConfiguringIp` | `70` | The IP settings of the device are being requested and configured |
| `NetworkManager::Device::CheckingIp` | `80` | The device's IP connectivity ability is being determined |
| `NetworkManager::Device::WaitingForSecondaries` | `90` | The device is waiting for secondary connections to be activated |
| `NetworkManager::Device::Activated` | `100` | The device is active |
| `NetworkManager::Device::Deactivating` | `110` | The device's network connection is being torn down |
| `NetworkManager::Device::Failed` | `120` | The device is in a failure state following an attempt to activate it |

### enum Device::StateChangeReason {#StateChangeReason-enum}

Enums describing the reason for a connection state change

> **Note:** StateChangeReasons NewActivation, ParentChanged, ParentManagedChanged are available in runtime NM \>= 1.0.4

| Constant |   |
| --- | --- |
| `NetworkManager::Device::UnknownReason` | `0` |
| `NetworkManager::Device::NoReason` | `1` |
| `NetworkManager::Device::NowManagedReason` | `2` |
| `NetworkManager::Device::NowUnmanagedReason` | `3` |
| `NetworkManager::Device::ConfigFailedReason` | `4` |
| `NetworkManager::Device::ConfigUnavailableReason` | `5` |
| `NetworkManager::Device::ConfigExpiredReason` | `6` |
| `NetworkManager::Device::NoSecretsReason` | `7` |
| `NetworkManager::Device::AuthSupplicantDisconnectReason` | `8` |
| `NetworkManager::Device::AuthSupplicantConfigFailedReason` | `9` |
| `NetworkManager::Device::AuthSupplicantFailedReason` | `10` |
| `NetworkManager::Device::AuthSupplicantTimeoutReason` | `11` |
| `NetworkManager::Device::PppStartFailedReason` | `12` |
| `NetworkManager::Device::PppDisconnectReason` | `13` |
| `NetworkManager::Device::PppFailedReason` | `14` |
| `NetworkManager::Device::DhcpStartFailedReason` | `15` |
| `NetworkManager::Device::DhcpErrorReason` | `16` |
| `NetworkManager::Device::DhcpFailedReason` | `17` |
| `NetworkManager::Device::SharedStartFailedReason` | `18` |
| `NetworkManager::Device::SharedFailedReason` | `19` |
| `NetworkManager::Device::AutoIpStartFailedReason` | `20` |
| `NetworkManager::Device::AutoIpErrorReason` | `21` |
| `NetworkManager::Device::AutoIpFailedReason` | `22` |
| `NetworkManager::Device::ModemBusyReason` | `23` |
| `NetworkManager::Device::ModemNoDialToneReason` | `24` |
| `NetworkManager::Device::ModemNoCarrierReason` | `25` |
| `NetworkManager::Device::ModemDialTimeoutReason` | `26` |
| `NetworkManager::Device::ModemDialFailedReason` | `27` |
| `NetworkManager::Device::ModemInitFailedReason` | `28` |
| `NetworkManager::Device::GsmApnSelectFailedReason` | `29` |
| `NetworkManager::Device::GsmNotSearchingReason` | `30` |
| `NetworkManager::Device::GsmRegistrationDeniedReason` | `31` |
| `NetworkManager::Device::GsmRegistrationTimeoutReason` | `32` |
| `NetworkManager::Device::GsmRegistrationFailedReason` | `33` |
| `NetworkManager::Device::GsmPinCheckFailedReason` | `34` |
| `NetworkManager::Device::FirmwareMissingReason` | `35` |
| `NetworkManager::Device::DeviceRemovedReason` | `36` |
| `NetworkManager::Device::SleepingReason` | `37` |
| `NetworkManager::Device::ConnectionRemovedReason` | `38` |
| `NetworkManager::Device::UserRequestedReason` | `39` |
| `NetworkManager::Device::CarrierReason` | `40` |
| `NetworkManager::Device::ConnectionAssumedReason` | `41` |
| `NetworkManager::Device::SupplicantAvailableReason` | `42` |
| `NetworkManager::Device::ModemNotFoundReason` | `43` |
| `NetworkManager::Device::BluetoothFailedReason` | `44` |
| `NetworkManager::Device::GsmSimNotInserted` | `45` |
| `NetworkManager::Device::GsmSimPinRequired` | `46` |
| `NetworkManager::Device::GsmSimPukRequired` | `47` |
| `NetworkManager::Device::GsmSimWrong` | `48` |
| `NetworkManager::Device::InfiniBandMode` | `49` |
| `NetworkManager::Device::DependencyFailed` | `50` |
| `NetworkManager::Device::Br2684Failed` | `51` |
| `NetworkManager::Device::ModemManagerUnavailable` | `52` |
| `NetworkManager::Device::SsidNotFound` | `53` |
| `NetworkManager::Device::SecondaryConnectionFailed` | `54` |
| `NetworkManager::Device::DcbFcoeFailed` | `55` |
| `NetworkManager::Device::TeamdControlFailed` | `56` |
| `NetworkManager::Device::ModemFailed` | `57` |
| `NetworkManager::Device::ModemAvailable` | `58` |
| `NetworkManager::Device::SimPinIncorrect` | `59` |
| `NetworkManager::Device::NewActivation` | `60` |
| `NetworkManager::Device::ParentChanged` | `61` |
| `NetworkManager::Device::ParentManagedChanged` | `62` |
| `NetworkManager::Device::Reserved` | `65536` |

### enum Device::Type {#Type-enum}

**flags Device::Types**

Device type

| Constant | Value | Description |
| --- | --- | --- |
| `NetworkManager::Device::UnknownType` | `NM_DEVICE_TYPE_UNKNOWN` | Unknown device type |
| `NetworkManager::Device::Ethernet` | `NM_DEVICE_TYPE_ETHERNET` | Ieee8023 wired ethernet |
| `NetworkManager::Device::Wifi` | `NM_DEVICE_TYPE_WIFI` | the Ieee80211 family of wireless networks |
| `NetworkManager::Device::Unused1` | `NM_DEVICE_TYPE_UNUSED1` | Currently unused |
| `NetworkManager::Device::Unused2` | `NM_DEVICE_TYPE_UNUSED2` | Currently unused |
| `NetworkManager::Device::Bluetooth` | `NM_DEVICE_TYPE_BT` | network bluetooth device (usually a cell phone) |
| `NetworkManager::Device::OlpcMesh` | `NM_DEVICE_TYPE_OLPC_MESH` | OLPC Mesh networking device |
| `NetworkManager::Device::Wimax` | `NM_DEVICE_TYPE_WIMAX` | WiMax WWAN technology |
| `NetworkManager::Device::Modem` | `NM_DEVICE_TYPE_MODEM` | POTS, GSM, CDMA or LTE modems |
| `NetworkManager::Device::InfiniBand` | `NM_DEVICE_TYPE_INFINIBAND` | Infiniband network device |
| `NetworkManager::Device::Bond` | `NM_DEVICE_TYPE_BOND` | Bond virtual device |
| `NetworkManager::Device::Vlan` | `NM_DEVICE_TYPE_VLAN` | Vlan virtual device |
| `NetworkManager::Device::Adsl` | `NM_DEVICE_TYPE_ADSL` | ADSL modem device |
| `NetworkManager::Device::Bridge` | `NM_DEVICE_TYPE_BRIDGE` | Bridge virtual device |
| `NetworkManager::Device::Generic` | `NM_DEVICE_TYPE_GENERIC` | Generic device |
| `NetworkManager::Device::Team` | `NM_DEVICE_TYPE_TEAM` | Team master device |
| `NetworkManager::Device::Gre` | `16` | Gre virtual device. Deprecated, use IpTunnel instead |
| `NetworkManager::Device::MacVlan` | `17` | MacVlan virtual device |
| `NetworkManager::Device::Tun` | `18` | Tun virtual device |
| `NetworkManager::Device::Veth` | `19` | Veth virtual device |
| `NetworkManager::Device::IpTunnel` | `20` | IP Tunneling Device |
| `NetworkManager::Device::VxLan` | `21` | Vxlan Device |
| `NetworkManager::Device::MacSec` | `22` | MacSec Device |
| `NetworkManager::Device::Dummy` | `23` | Dummy Device |
| `NetworkManager::Device::Ppp` | `24` | Ppp Device |
| `NetworkManager::Device::OvsInterface` | `25` | OvsInterface Device |
| `NetworkManager::Device::OvsPort` | `26` | OvsPort Device |
| `NetworkManager::Device::OvsBridge` | `27` | OvsBridge Device |
| `NetworkManager::Device::Wpan` | `28` | Wpan Device |
| `NetworkManager::Device::Lowpan` | `29` | Lowpan Device |
| `NetworkManager::Device::WireGuard` | `30` | WireGuard Device |
| `NetworkManager::Device::WifiP2P` | `31` | WifiP2P Device |
| `NetworkManager::Device::VRF` | `32` | VRF (Virtual Routing and Forwarding) Device |
| `NetworkManager::Device::Loopback` | `33` | Loopback Device |

The `Types` type is a typedef for `QFlags<Type>. `It stores an OR combination of `Type` values.

## Property Documentation {#property-documentation}

### \[read-only\] InterfaceFlags : Interfaceflags {#InterfaceFlags-prop}

**Access functions:**

- `NetworkManager::Device::Interfaceflags` **[interfaceFlags](networkmanager-device.md#interfaceFlags)**() const

### autoconnect : bool {#autoconnect-prop}

**Access functions:**

- `bool` **[autoconnect](networkmanager-device.md#autoconnect)**() const
- `void` **[setAutoconnect](networkmanager-device.md#setAutoconnect)**(`bool` *autoconnect*)

### \[read-only\] deviceStatistics : NetworkManager::DeviceStatistics::Ptr {#deviceStatistics-prop}

**Access functions:**

- `DeviceStatistics::Ptr` **[deviceStatistics](networkmanager-device.md#deviceStatistics)**() const

### \[read-only\] driver : QString {#driver-prop}

**Access functions:**

- `QString` **[driver](networkmanager-device.md#driver)**() const

### \[read-only\] driverVersion : QString {#driverVersion-prop}

**Access functions:**

- `QString` **[driverVersion](networkmanager-device.md#driverVersion)**() const

### \[read-only\] firmwareMissing : bool {#firmwareMissing-prop}

**Access functions:**

- `bool` **[firmwareMissing](networkmanager-device.md#firmwareMissing)**() const

### \[read-only\] firmwareVersion : QString {#firmwareVersion-prop}

**Access functions:**

- `QString` **[firmwareVersion](networkmanager-device.md#firmwareVersion)**() const

### \[read-only\] genericCapabilities : QVariant {#genericCapabilities-prop}

**Access functions:**

- `QVariant` **[capabilitiesV](networkmanager-device.md#capabilitiesV)**() const

### \[read-only\] interfaceName : QString {#interfaceName-prop}

**Access functions:**

- `QString` **[interfaceName](networkmanager-device.md#interfaceName)**() const

### \[read-only\] ipInterfaceName : QString {#ipInterfaceName-prop}

**Access functions:**

- `QString` **[ipInterfaceName](networkmanager-device.md#ipInterfaceName)**() const

### \[read-only\] ipV4Address : QHostAddress {#ipV4Address-prop}

### managed : bool {#managed-prop}

**Access functions:**

- `bool` **[managed](networkmanager-device.md#managed)**() const
- `void` **[setManaged](networkmanager-device.md#setManaged)**(`bool` *managed*)

### \[read-only\] metered : MeteredStatus {#metered-prop}

**Access functions:**

- `NetworkManager::Device::MeteredStatus` **[metered](networkmanager-device.md#metered)**() const

### \[read-only\] mtu : uint {#mtu-prop}

**Access functions:**

- `uint` **[mtu](networkmanager-device.md#mtu)**() const

### \[read-only\] nmPluginMissing : bool {#nmPluginMissing-prop}

**Access functions:**

- `bool` **[nmPluginMissing](networkmanager-device.md#nmPluginMissing)**() const

### \[read-only\] state : State {#state-prop}

**Access functions:**

- `NetworkManager::Device::State` **[state](networkmanager-device.md#state)**() const

### \[read-only\] stateReason : DeviceStateReason {#stateReason-prop}

**Access functions:**

- `NetworkManager::DeviceStateReason` **[stateReason](networkmanager-device.md#stateReason)**() const

### \[read-only\] udi : QString {#udi-prop}

**Access functions:**

- `QString` **[udi](networkmanager-device.md#udi)**() const

### \[read-only\] uni : QString {#uni-prop}

**Access functions:**

- `QString` **[uni](networkmanager-device.md#uni)**() const

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Device::Device(const QString &*path*, QObject \**parent* = nullptr) {#Device}

Creates a new device object.

`path` UNI of the device

### \[override virtual noexcept\] Device::~Device() {#dtor.Device}

Destroys a device object.

### NetworkManager::ActiveConnection::Ptr Device::activeConnection() const {#activeConnection}

The current active connection for this device

Returns A valid [ActiveConnection](networkmanager-activeconnection.md) object or NULL if no active connection was found

### \[signal\] void Device::activeConnectionChanged() {#activeConnectionChanged}

Emitted when the autoconnect of this network has changed.

### template \<typename DevIface\> DevIface \*Device::as() {#as}

Retrieves a specialized interface to interact with the device corresponding to a given device interface.

Returns a pointer to the device interface if it exists, `0` otherwise

### template \<typename DevIface\> const DevIface \*Device::as() const {#as-1}

Retrieves a specialized interface to interact with the device corresponding to a given device interface.

Returns a pointer to the device interface if it exists, 0 otherwise

### bool Device::autoconnect() const {#autoconnect}

If the device is allowed to autoconnect.

> **Note:** Getter function for property [autoconnect](networkmanager-device.md#autoconnect-prop).

*See also* [setAutoconnect](networkmanager-device.md#setAutoconnect)()

### \[signal\] void Device::autoconnectChanged() {#autoconnectChanged}

Emitted when the autoconnect of this network has changed.

### \[signal\] void Device::availableConnectionAppeared(const QString &*connection*) {#availableConnectionAppeared}

Emitted when a new connection is available

### \[signal\] void Device::availableConnectionChanged() {#availableConnectionChanged}

Emitted when the list of avaiable connections of this network has changed.

### \[signal\] void Device::availableConnectionDisappeared(const QString &*connection*) {#availableConnectionDisappeared}

Emitted when the connection is no longer available

### Connection::List Device::availableConnections() {#availableConnections}

Returns available connections for this device

Returns List of availables connection

### NetworkManager::Device::Capabilities Device::capabilities() const {#capabilities}

Retrieves the capabilities supported by this device.

Returns the capabilities of the device

### \[signal\] void Device::capabilitiesChanged() {#capabilitiesChanged}

Emitted when the capabilities of this network has changed.

### QVariant Device::capabilitiesV() const {#capabilitiesV}

> **Note:** Getter function for property [genericCapabilities](networkmanager-device.md#genericCapabilities-prop).

### \[signal\] void Device::connectionStateChanged() {#connectionStateChanged}

Emitted when the connection state of this network has changed.

### QDBusPendingReply\<\> Device::deleteInterface() {#deleteInterface}

Deletes a software device from [NetworkManager](networkmanager.md) and removes the interface from the system. The method returns an error when called for a hardware device.

### int Device::designSpeed() const {#designSpeed}

Retrieves the maximum speed as reported by the device. Note that this is only a design related piece of information, and that the device might not reach this maximum.

Returns the device's maximum speed

### DeviceStatistics::Ptr Device::deviceStatistics() const {#deviceStatistics}

Returns Device Statistics interface

> **Note:** Getter function for property [deviceStatistics](networkmanager-device.md#deviceStatistics-prop).

### Dhcp4Config::Ptr Device::dhcp4Config() const {#dhcp4Config}

Get the DHCP options returned by the DHCP server or a null pointer if the device is not Activated or does not use DHCP configuration.

### \[signal\] void Device::dhcp4ConfigChanged() {#dhcp4ConfigChanged}

Emitted when the DHCP configuration for IPv4 of this network has changed.

### Dhcp6Config::Ptr Device::dhcp6Config() const {#dhcp6Config}

Get the DHCP options returned by the DHCP server or a null pointer if the device is not Activated or does not use DHCP configuration.

### \[signal\] void Device::dhcp6ConfigChanged() {#dhcp6ConfigChanged}

Emitted when the DHCP configuration for IPv6 of this network has changed.

### QDBusPendingReply\<\> Device::disconnectInterface() {#disconnectInterface}

Disconnects a device and prevents the device from automatically activating further connections without user intervention.

### QString Device::driver() const {#driver}

Handle for the system driver controlling this network interface

> **Note:** Getter function for property [driver](networkmanager-device.md#driver-prop).

### \[signal\] void Device::driverChanged() {#driverChanged}

Emitted when the driver of this network has changed.

### QString Device::driverVersion() const {#driverVersion}

The driver version.

> **Note:** Getter function for property [driverVersion](networkmanager-device.md#driverVersion-prop).

### \[signal\] void Device::driverVersionChanged() {#driverVersionChanged}

Emitted when the driver version of this network has changed.

### bool Device::firmwareMissing() const {#firmwareMissing}

Is the firmware needed by the device missing?

> **Note:** Getter function for property [firmwareMissing](networkmanager-device.md#firmwareMissing-prop).

### \[signal\] void Device::firmwareMissingChanged() {#firmwareMissingChanged}

Emitted when the firmware missing state of this network has changed.

### QString Device::firmwareVersion() const {#firmwareVersion}

The firmware version.

> **Note:** Getter function for property [firmwareVersion](networkmanager-device.md#firmwareVersion-prop).

### \[signal\] void Device::firmwareVersionChanged() {#firmwareVersionChanged}

Emitted when the firmware version of this network has changed.

### NetworkManager::Device::Interfaceflags Device::interfaceFlags() const {#interfaceFlags}

The up or down flag for the device

> **Note:** Getter function for property [InterfaceFlags](networkmanager-device.md#InterfaceFlags-prop).

### \[signal\] void Device::interfaceFlagsChanged() {#interfaceFlagsChanged}

Emitted when the up or down state of the device

> **Note:** will always return NM\_DEVICE\_INTERFACE\_FLAG\_NONE when runtime NM \< 1.22

### QString Device::interfaceName() const {#interfaceName}

The system name for the network device

> **Note:** Getter function for property [interfaceName](networkmanager-device.md#interfaceName-prop).

### \[signal\] void Device::interfaceNameChanged() {#interfaceNameChanged}

Emitted when the interface name of this network has changed.

### \[signal\] void Device::ipInterfaceChanged() {#ipInterfaceChanged}

Emitted when the ip interface name of this network has changed.

### QString Device::ipInterfaceName() const {#ipInterfaceName}

The name of the device's data interface when available. This property may not refer to the actual data interface until the device has successfully established a data connection, indicated by the device's [state](networkmanager-device.md#state)() becoming ACTIVATED.

> **Note:** Getter function for property [ipInterfaceName](networkmanager-device.md#ipInterfaceName-prop).

### \[signal\] void Device::ipV4AddressChanged() {#ipV4AddressChanged}

Emitted when the IPv4 address of this network has changed.

### NetworkManager::IpConfig Device::ipV4Config() const {#ipV4Config}

Get the current IPv4 configuration of this device. Only valid when device is Activated.

### \[signal\] void Device::ipV4ConfigChanged() {#ipV4ConfigChanged}

Emitted when the IPv4 configuration of this network has changed.

### NetworkManager::IpConfig Device::ipV6Config() const {#ipV6Config}

Get the current IPv6 configuration of this device. Only valid when device is Activated.

### \[signal\] void Device::ipV6ConfigChanged() {#ipV6ConfigChanged}

Emitted when the IPv6 configuration of this network has changed.

### bool Device::isActive() const {#isActive}

Retrieves the activation status of this network interface.

Returns true if this network interface is active, false otherwise

### bool Device::isValid() const {#isValid}

Retrieves the device is valid.

Returns true if this device interface is valid, false otherwise

### bool Device::managed() const {#managed}

Is the device currently being managed by [NetworkManager](networkmanager.md)?

> **Note:** Getter function for property [managed](networkmanager-device.md#managed-prop).

*See also* [setManaged](networkmanager-device.md#setManaged)()

### \[signal\] void Device::managedChanged() {#managedChanged}

Emitted when the managed state of this network has changed.

### NetworkManager::Device::MeteredStatus Device::metered() const {#metered}

Returns Whether the amount of traffic flowing through the device is subject to limitations, for example set by service providers.

> **Note:** Getter function for property [metered](networkmanager-device.md#metered-prop).

### \[signal\] void Device::meteredChanged(NetworkManager::Device::MeteredStatus *metered*) {#meteredChanged}

Emitted when metered property has changed

*See also* [metered](networkmanager-device.md#metered)

### uint Device::mtu() const {#mtu}

The device MTU (maximum transmission unit)

> **Note:** Getter function for property [mtu](networkmanager-device.md#mtu-prop).

### \[signal\] void Device::mtuChanged() {#mtuChanged}

Emitted when the maximum transmission unit has changed

### bool Device::nmPluginMissing() const {#nmPluginMissing}

Returns If TRUE, indicates the [NetworkManager](networkmanager.md) plugin for the device is likely missing or misconfigured.

> **Note:** Getter function for property [nmPluginMissing](networkmanager-device.md#nmPluginMissing-prop).

### \[signal\] void Device::nmPluginMissingChanged(bool *nmPluginMissing*) {#nmPluginMissingChanged}

Emitted when NmPluginMissing property has changed

*See also* [nmPluginMissing](networkmanager-device.md#nmPluginMissing)

### QString Device::physicalPortId() const {#physicalPortId}

Returns If non-empty, an (opaque) indicator of the physical network port associated with the device. This can be used to recognize when two seemingly-separate hardware devices are actually just different virtual interfaces to the same physical port.

### \[signal\] void Device::physicalPortIdChanged() {#physicalPortIdChanged}

Emitted when the physical port ID changes.

*See also* [physicalPortId](networkmanager-device.md#physicalPortId)()

### QDBusPendingReply\<\> Device::reapplyConnection(const NMVariantMapMap &*connection*, qulonglong *version\_id*, uint *flags*) {#reapplyConnection}

Reapplies connection settings on the interface.

### void Device::setAutoconnect(bool *autoconnect*) {#setAutoconnect}

If true, indicates the device is allowed to autoconnect. If false, manual intervention is required before the device will automatically connect to a known network, such as activating a connection using the device, or setting this property to `true`.

> **Note:** Setter function for property [autoconnect](networkmanager-device.md#autoconnect-prop).

*See also* [autoconnect](networkmanager-device.md#autoconnect)()

### \[since 6.18.0\] void Device::setManaged(bool *managed*) {#setManaged}

Sets the managed flag for the device

> **Note:** Setter function for property [managed](networkmanager-device.md#managed-prop).

This function was introduced in Qt 6.18.0.

*See also* [managed](networkmanager-device.md#managed)()

### NetworkManager::Device::State Device::state() const {#state}

Retrieves the current state of the device. This is a high level view of the device. It is user oriented, so actually it provides state coming from different layers.

Returns the current connection state

> **Note:** Getter function for property [state](networkmanager-device.md#state-prop).

*See also* [Device::State](networkmanager-device.md#State-enum)

### \[signal\] void Device::stateChanged(NetworkManager::Device::State *newstate*, NetworkManager::Device::State *oldstate*, NetworkManager::Device::StateChangeReason *reason*) {#stateChanged}

This signal is emitted when the device's link status changed.

`newstate` the new state of the connection

`oldstate` the previous state of the connection

`reason` the reason for the state change, if any. ReasonNone where the backend provides no reason.

*See also* [Device::State](networkmanager-device.md#State-enum), [Device::StateChangeReason](networkmanager-device.md#StateChangeReason-enum)

### NetworkManager::DeviceStateReason Device::stateReason() const {#stateReason}

The current state and reason for changing to that state.

> **Note:** Getter function for property [stateReason](networkmanager-device.md#stateReason-prop).

### \[signal\] void Device::stateReasonChanged() {#stateReasonChanged}

Emitted when the state reason of this network has changed.

### \[virtual\] NetworkManager::Device::Type Device::type() const {#type}

Retrieves the interface type. This is a virtual function that will return the proper type of all sub-classes.

Returns the [NetworkManager::Device::Type](networkmanager-device.md#Type-enum) that corresponds to this device.

### QString Device::udi() const {#udi}

Retrieves the Unique Device Identifier (UDI) of the device. This identifier is unique for each device in the system.

> **Note:** Getter function for property [udi](networkmanager-device.md#udi-prop).

### \[signal\] void Device::udiChanged() {#udiChanged}

Emitted when the Unique Device Identifier of this device has changed.

### QString Device::uni() const {#uni}

Retrieves the Unique Network Identifier (UNI) of the device. This identifier is unique for each network and network interface in the system.

Returns the Unique Network Identifier of the current device

> **Note:** Getter function for property [uni](networkmanager-device.md#uni-prop).
