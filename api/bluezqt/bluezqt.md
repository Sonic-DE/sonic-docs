---
title: "BluezQt Namespace"
description: "Qt wrapper for BlueZ 5 DBus API."
---

# BluezQt Namespace

Qt wrapper for BlueZ 5 DBus API. [More...](#details)

- **Header:** `#include <BluezQt>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`

## Detailed Description {#details}

## Namespaces {#namespaces}

### namespace BluezQt::Services

Service UUIDs.

## Classes {#classes}

### class [Adapter](bluezqt-adapter.md)

Bluetooth adapter.

### class [Agent](bluezqt-agent.md)

Bluetooth agent.

### struct [BluezQt::AudioConfiguration](bluezqt-audioconfiguration.md)

### class [Battery](bluezqt-battery.md)

Device battery.

### class [Device](bluezqt-device.md)

Bluetooth device.

### class [DevicesModel](bluezqt-devicesmodel.md)

Model of all devices.

### class [GattApplication](bluezqt-gattapplication.md)

Bluetooth [GattApplication](bluezqt-gattapplication.md).

### class [GattCharacteristic](bluezqt-gattcharacteristic.md)

### class [GattCharacteristicRemote](bluezqt-gattcharacteristicremote.md)

Bluetooth LE GATT characteristic.

### class [GattDescriptor](bluezqt-gattdescriptor.md)

Bluetooth GATT Descriptor.

### class [GattDescriptorRemote](bluezqt-gattdescriptorremote.md)

Bluetooth LE GATT descriptor.

### class [GattManager](bluezqt-gattmanager.md)

Bluetooth [GattManager](bluezqt-gattmanager.md).

### class [GattService](bluezqt-gattservice.md)

Bluetooth [GattService](bluezqt-gattservice.md).

### class [GattServiceRemote](bluezqt-gattserviceremote.md)

Bluetooth LE GATT service.

### class [InitManagerJob](bluezqt-initmanagerjob.md)

Init manager job.

### class [InitObexManagerJob](bluezqt-initobexmanagerjob.md)

Init obex manager job.

### class [Input](bluezqt-input.md)

Device input.

### class [Job](bluezqt-job.md)

Async job.

### class [LEAdvertisement](bluezqt-leadvertisement.md)

Bluetooth LE advertisement.

### class [LEAdvertisingManager](bluezqt-leadvertisingmanager.md)

Bluetooth LE advertising manager.

### class [Manager](bluezqt-manager.md)

Bluetooth manager.

### class [Media](bluezqt-media.md)

Bluetooth Media.

### class [MediaEndpoint](bluezqt-mediaendpoint.md)

Bluetooth [MediaEndpoint](bluezqt-mediaendpoint.md).

### class [MediaPlayer](bluezqt-mediaplayer.md)

Media player.

### class [MediaPlayerTrack](bluezqt-mediaplayertrack.md)

Media player track.

### class [MediaTransport](bluezqt-mediatransport.md)

Media transport.

### class [ObexAgent](bluezqt-obexagent.md)

Bluetooth OBEX agent.

### class [ObexFileTransfer](bluezqt-obexfiletransfer.md)

OBEX file transfer.

### class [ObexFileTransferEntry](bluezqt-obexfiletransferentry.md)

OBEX file transfer entry.

### class [ObexManager](bluezqt-obexmanager.md)

OBEX manager.

### class [ObexObjectPush](bluezqt-obexobjectpush.md)

OBEX object push.

### class [ObexSession](bluezqt-obexsession.md)

OBEX session.

### class [ObexTransfer](bluezqt-obextransfer.md)

OBEX transfer.

### class [PendingCall](bluezqt-pendingcall.md)

Pending method call.

### class [Profile](bluezqt-profile.md)

Bluetooth profile.

### class [Request](bluezqt-request.md)

D-Bus request.

### class [Rfkill](bluezqt-rfkill.md)

### class [TPendingCall](bluezqt-tpendingcall.md)

Pending method call (template version).

## Type Documentation {#type-documentation}

### BluezQt::AdapterPtr {#AdapterPtr-typedef}

Synonym for [QSharedPointer](https://doc.qt.io/qt-6/qsharedpointer.html)\<[BluezQt::Adapter](bluezqt-adapter.md)\>.

### enum BluezQt::AudioCodec {#AudioCodec-enum}

Assigned number of codec that the endpoint/transport supports. Currently limited to most common codecs. Further codecs reserved.

| Constant |   |
| --- | --- |
| `BluezQt::AudioCodec::Invalid` | `0x0000` |
| `BluezQt::AudioCodec::Sbc` | `0x0001` |
| `BluezQt::AudioCodec::Aac` | `0x0004` |

### enum BluezQt::AudioSampleRate {#AudioSampleRate-enum}

Assigned number of sample rate that the endpoint/transport supports.

Currently limited to most common rates. Further rates reserved.

| Constant |   |
| --- | --- |
| `BluezQt::AudioSampleRate::Invalid` | `0x0000` |
| `BluezQt::AudioSampleRate::Rate44100` | `0x0080` |
| `BluezQt::AudioSampleRate::Rate48000` | `0x0100` |

### BluezQt::BatteryPtr {#BatteryPtr-typedef}

Synonym for [QSharedPointer](https://doc.qt.io/qt-6/qsharedpointer.html)\<[BluezQt::Battery](bluezqt-battery.md)\>.

### BluezQt::DevicePtr {#DevicePtr-typedef}

Synonym for [QSharedPointer](https://doc.qt.io/qt-6/qsharedpointer.html)\<[BluezQt::Device](bluezqt-device.md)\>.

### BluezQt::GattCharacteristicRemotePtr {#GattCharacteristicRemotePtr-typedef}

Synonym for [QSharedPointer](https://doc.qt.io/qt-6/qsharedpointer.html)\<[BluezQt::GattCharacteristicRemote](bluezqt-gattcharacteristicremote.md)\>.

### BluezQt::GattDescriptorRemotePtr {#GattDescriptorRemotePtr-typedef}

Synonym for [QSharedPointer](https://doc.qt.io/qt-6/qsharedpointer.html)\<[BluezQt::GattDescriptorRemote](bluezqt-gattdescriptorremote.md)\>.

### BluezQt::GattManagerPtr {#GattManagerPtr-typedef}

Synonym for [QSharedPointer](https://doc.qt.io/qt-6/qsharedpointer.html)\<[BluezQt::GattManager](bluezqt-gattmanager.md)\>.

### BluezQt::GattServiceRemotePtr {#GattServiceRemotePtr-typedef}

Synonym for [QSharedPointer](https://doc.qt.io/qt-6/qsharedpointer.html)\<[BluezQt::GattServiceRemote](bluezqt-gattserviceremote.md)\>.

### BluezQt::InputPtr {#InputPtr-typedef}

Synonym for [QSharedPointer](https://doc.qt.io/qt-6/qsharedpointer.html)\<[BluezQt::Input](bluezqt-input.md)\>.

### BluezQt::LEAdvertisingManagerPtr {#LEAdvertisingManagerPtr-typedef}

Synonym for [QSharedPointer](https://doc.qt.io/qt-6/qsharedpointer.html)\<[BluezQt::LEAdvertisingManager](bluezqt-leadvertisingmanager.md)\>.

### BluezQt::ManData {#ManData-typedef}

Synonym for [QMap](https://doc.qt.io/qt-6/qmap.html)\<uint16\_t, [QByteArray](https://doc.qt.io/qt-6/qbytearray.html)\>.

### BluezQt::ManagerPtr {#ManagerPtr-typedef}

Synonym for [QSharedPointer](https://doc.qt.io/qt-6/qsharedpointer.html)\<[BluezQt::Manager](bluezqt-manager.md)\>.

### BluezQt::MediaPlayerPtr {#MediaPlayerPtr-typedef}

Synonym for [QSharedPointer](https://doc.qt.io/qt-6/qsharedpointer.html)\<[BluezQt::MediaPlayer](bluezqt-mediaplayer.md)\>.

### BluezQt::MediaPtr {#MediaPtr-typedef}

Synonym for [QSharedPointer](https://doc.qt.io/qt-6/qsharedpointer.html)\<[BluezQt::Media](bluezqt-media.md)\>.

### BluezQt::MediaTransportPtr {#MediaTransportPtr-typedef}

Synonym for [QSharedPointer](https://doc.qt.io/qt-6/qsharedpointer.html)\<[BluezQt::MediaTransport](bluezqt-mediatransport.md)\>.

### BluezQt::ObexManagerPtr {#ObexManagerPtr-typedef}

Synonym for [QSharedPointer](https://doc.qt.io/qt-6/qsharedpointer.html)\<[BluezQt::ObexManager](bluezqt-obexmanager.md)\>.

### BluezQt::ObexSessionPtr {#ObexSessionPtr-typedef}

Synonym for [QSharedPointer](https://doc.qt.io/qt-6/qsharedpointer.html)\<[BluezQt::ObexSession](bluezqt-obexsession.md)\>.

### BluezQt::ObexTransferPtr {#ObexTransferPtr-typedef}

Synonym for [QSharedPointer](https://doc.qt.io/qt-6/qsharedpointer.html)\<[BluezQt::ObexTransfer](bluezqt-obextransfer.md)\>.

### enum BluezQt::RequestOriginatingType {#RequestOriginatingType-enum}

| Constant |   |
| --- | --- |
| `BluezQt::OrgBluezAgent` | `0` |
| `BluezQt::OrgBluezProfile` | `1` |
| `BluezQt::OrgBluezObexAgent` | `2` |
| `BluezQt::OrgBluezMediaEndpoint` | `3` |
