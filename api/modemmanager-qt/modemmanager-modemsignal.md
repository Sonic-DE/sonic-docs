---
title: "ModemManager::ModemSignal Class"
description: "The ModemSignal class."
---

# ModemManager::ModemSignal Class

The [ModemSignal](modemmanager-modemsignal.md) class. [More...](#details)

- **Header:** `#include <ModemManagerQt/ModemSignal>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`
- **Inherits:** [ModemManager::Interface](modemmanager-interface.md)

[List of all members, including inherited members](modemmanager-modemsignal-members.md)

## Public Types

- [ModemSignal::List](#List-typedef)
- [ModemSignal::Ptr](#Ptr-typedef)

## Public Functions

- [ModemSignal(const QString &path, QObject \*parent = nullptr)](#ModemSignal)
- [QVariantMap cdma() const](#cdma)
- [bool errorRateThreshold() const](#errorRateThreshold) (since 6.24.0)
- [QVariantMap evdo() const](#evdo)
- [QVariantMap gsm() const](#gsm)
- [QVariantMap lte() const](#lte)
- [QVariantMap nr5g() const](#nr5g) (since 6.24.0)
- [uint rate() const](#rate)
- [uint rssiThreshold() const](#rssiThreshold) (since 6.24.0)
- [void setTimeout(int timeout)](#setTimeout)
- [QDBusPendingReply\<void\> setup(uint rate)](#setup)
- [QDBusPendingReply\<void\> setupThresholds(const QVariantMap &settings)](#setupThresholds) (since 6.24.0)
- [int timeout() const](#timeout)
- [QVariantMap umts() const](#umts)

## Signals

- [void cdmaChanged(const QVariantMap &cdma)](#cdmaChanged)
- [void errorRateThresholdChanged(bool enabled)](#errorRateThresholdChanged) (since 6.24.0)
- [void evdoChanged(const QVariantMap &evdo)](#evdoChanged)
- [void gsmChanged(const QVariantMap &gsm)](#gsmChanged)
- [void lteChanged(const QVariantMap &lte)](#lteChanged)
- [void nr5gChanged(const QVariantMap &nr5g)](#nr5gChanged) (since 6.24.0)
- [void rateChanged(uint rate)](#rateChanged)
- [void rssiThresholdChanged(uint threshold)](#rssiThresholdChanged) (since 6.24.0)
- [void umtsChanged(const QVariantMap &umts)](#umtsChanged)

## Detailed Description {#details}

This class provides access to extended signal quality information.

## Member Type Documentation {#member-type-documentation}

### ModemSignal::List {#List-typedef}

### ModemSignal::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ModemSignal::ModemSignal(const QString &*path*, QObject \**parent* = nullptr) {#ModemSignal}

### QVariantMap ModemSignal::cdma() const {#cdma}

Returns Dictionary of available signal information for the CDMA1x access technology.

This dictionary is composed of a string key, with an associated data which contains type-specific information.

`rssi` The CDMA1x RSSI (Received Signal Strength Indication), in dBm, given as a floating point value (signature "d").

`ecio` The CDMA1x Ec/Io, in dBm, given as a floating point value (signature "d").

### \[signal\] void ModemSignal::cdmaChanged(const QVariantMap &*cdma*) {#cdmaChanged}

### \[since 6.24.0\] bool ModemSignal::errorRateThreshold() const {#errorRateThreshold}

Returns whether error rate threshold reporting is enabled.

This function was introduced in Qt 6.24.0.

### \[signal, since 6.24.0\] void ModemSignal::errorRateThresholdChanged(bool *enabled*) {#errorRateThresholdChanged}

This function was introduced in Qt 6.24.0.

### QVariantMap ModemSignal::evdo() const {#evdo}

Returns Dictionary of available signal information for the CDMA EV-DO access technology.

This dictionary is composed of a string key, with an associated data which contains type-specific information.

`rssi` The CDMA EV-DO RSSI (Received Signal Strength Indication), in dBm, given as a floating point value (signature "d").

`ecio` The CDMA EV-DO Ec/Io, in dBm, given as a floating point value (signature "d").

`sinr` CDMA EV-DO SINR level, in dB, given as a floating point value (signature "d").

`io` The CDMA EV-DO Io, in dBm, given as a floating point value (signature "d").

### \[signal\] void ModemSignal::evdoChanged(const QVariantMap &*evdo*) {#evdoChanged}

### QVariantMap ModemSignal::gsm() const {#gsm}

Returns Dictionary of available signal information for the GSM/GPRS access technology.

This dictionary is composed of a string key, with an associated data which contains type-specific information.

`rssi` The GSM RSSI (Received Signal Strength Indication), in dBm, given as a floating point value (signature "d").

### \[signal\] void ModemSignal::gsmChanged(const QVariantMap &*gsm*) {#gsmChanged}

### QVariantMap ModemSignal::lte() const {#lte}

Returns Dictionary of available signal information for the UMTS (WCDMA) access technology.

This dictionary is composed of a string key, with an associated data which contains type-specific information.

`rssi` The LTE RSSI (Received Signal Strength Indication), in dBm, given as a floating point value (signature "d").

`rsrq` The LTE RSRQ (Reference Signal Received Quality), in dB, given as a floating point value (signature "d").

`rsrp` The LTE RSRP (Reference Signal Received Power), in dBm, given as a floating point value (signature "d").

`snr` The LTE S/R ratio, in dB, given as a floating point value (signature "d").

### \[signal\] void ModemSignal::lteChanged(const QVariantMap &*lte*) {#lteChanged}

### \[since 6.24.0\] QVariantMap ModemSignal::nr5g() const {#nr5g}

Returns Dictionary of available signal information for the NR5G access technology.

This function was introduced in Qt 6.24.0.

### \[signal, since 6.24.0\] void ModemSignal::nr5gChanged(const QVariantMap &*nr5g*) {#nr5gChanged}

This function was introduced in Qt 6.24.0.

### uint ModemSignal::rate() const {#rate}

Returns refresh rate for the extended signal quality information updates, in seconds. A value of 0 disables the retrieval of the values.

### \[signal\] void ModemSignal::rateChanged(uint *rate*) {#rateChanged}

### \[since 6.24.0\] uint ModemSignal::rssiThreshold() const {#rssiThreshold}

Returns RSSI threshold used for reporting.

This function was introduced in Qt 6.24.0.

### \[signal, since 6.24.0\] void ModemSignal::rssiThresholdChanged(uint *threshold*) {#rssiThresholdChanged}

This function was introduced in Qt 6.24.0.

### void ModemSignal::setTimeout(int *timeout*) {#setTimeout}

Sets the timeout in milliseconds for all async method DBus calls. -1 means the default DBus timeout (usually 25 seconds).

*See also* [timeout](modemmanager-modemsignal.md#timeout)()

### QDBusPendingReply\<void\> ModemSignal::setup(uint *rate*) {#setup}

Setup extended signal quality information retrieval.

`rate` refresh rate to set, in seconds. 0 to disable retrieval.

### \[since 6.24.0\] QDBusPendingReply\<void\> ModemSignal::setupThresholds(const QVariantMap &*settings*) {#setupThresholds}

Setup thresholds for extended signal quality information retrieval.

This function was introduced in Qt 6.24.0.

### int ModemSignal::timeout() const {#timeout}

Returns the current value of the DBus timeout in milliseconds. -1 means the default DBus timeout (usually 25 seconds).

*See also* [setTimeout](modemmanager-modemsignal.md#setTimeout)()

### QVariantMap ModemSignal::umts() const {#umts}

Returns Dictionary of available signal information for the UMTS (WCDMA) access technology.

This dictionary is composed of a string key, with an associated data which contains type-specific information.

`rssi` The UMTS RSSI (Received Signal Strength Indication), in dBm, given as a floating point value (signature "d").

`ecio` The UMTS Ec/Io, in dBm, given as a floating point value (signature "d").

### \[signal\] void ModemSignal::umtsChanged(const QVariantMap &*umts*) {#umtsChanged}
