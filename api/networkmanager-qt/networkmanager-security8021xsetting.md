---
title: "NetworkManager::Security8021xSetting Class"
description: "Represents 802.1x wireless security setting."
---

# NetworkManager::Security8021xSetting Class

Represents 802.1x wireless security setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/Security8021xSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-security8021xsetting-members.md)

## Public Types

- [enum Security8021xSetting::AuthEapMethod](#AuthEapMethod-enum)
- [enum Security8021xSetting::AuthMethod](#AuthMethod-enum)
- [enum Security8021xSetting::EapMethod](#EapMethod-enum)
- [enum Security8021xSetting::FastProvisioning](#FastProvisioning-enum)
- [Security8021xSetting::List](#List-typedef)
- [enum Security8021xSetting::PeapLabel](#PeapLabel-enum)
- [enum Security8021xSetting::PeapVersion](#PeapVersion-enum)
- [Security8021xSetting::Ptr](#Ptr-typedef)

## Public Functions

- [Security8021xSetting()](#Security8021xSetting)
- [Security8021xSetting(const NetworkManager::Security8021xSetting::Ptr &other)](#Security8021xSetting-1)
- [QStringList altSubjectMatches() const](#altSubjectMatches)
- [QString anonymousIdentity() const](#anonymousIdentity)
- [QByteArray caCertificate() const](#caCertificate)
- [QString caPath() const](#caPath)
- [QByteArray clientCertificate() const](#clientCertificate)
- [QString domainSuffixMatch() const](#domainSuffixMatch)
- [QList\<NetworkManager::Security8021xSetting::EapMethod\> eapMethods() const](#eapMethods)
- [QString identity() const](#identity)
- [QString pacFile() const](#pacFile)
- [QString password() const](#password)
- [Setting::SecretFlags passwordFlags() const](#passwordFlags)
- [QByteArray passwordRaw() const](#passwordRaw)
- [Setting::SecretFlags passwordRawFlags() const](#passwordRawFlags)
- [NetworkManager::Security8021xSetting::FastProvisioning phase1FastProvisioning() const](#phase1FastProvisioning)
- [NetworkManager::Security8021xSetting::PeapLabel phase1PeapLabel() const](#phase1PeapLabel)
- [NetworkManager::Security8021xSetting::PeapVersion phase1PeapVersion() const](#phase1PeapVersion)
- [QStringList phase2AltSubjectMatches() const](#phase2AltSubjectMatches)
- [NetworkManager::Security8021xSetting::AuthEapMethod phase2AuthEapMethod() const](#phase2AuthEapMethod)
- [NetworkManager::Security8021xSetting::AuthMethod phase2AuthMethod() const](#phase2AuthMethod)
- [QByteArray phase2CaCertificate() const](#phase2CaCertificate)
- [QString phase2CaPath() const](#phase2CaPath)
- [QByteArray phase2ClientCertificate() const](#phase2ClientCertificate)
- [QByteArray phase2PrivateKey() const](#phase2PrivateKey)
- [QString phase2PrivateKeyPassword() const](#phase2PrivateKeyPassword)
- [Setting::SecretFlags phase2PrivateKeyPasswordFlags() const](#phase2PrivateKeyPasswordFlags)
- [QString phase2SubjectMatch() const](#phase2SubjectMatch)
- [QString pin() const](#pin)
- [Setting::SecretFlags pinFlags() const](#pinFlags)
- [QByteArray privateKey() const](#privateKey)
- [QString privateKeyPassword() const](#privateKeyPassword)
- [Setting::SecretFlags privateKeyPasswordFlags() const](#privateKeyPasswordFlags)
- [void setAltSubjectMatches(const QStringList &strings)](#setAltSubjectMatches)
- [void setAnonymousIdentity(const QString &identity)](#setAnonymousIdentity)
- [void setCaCertificate(const QByteArray &certificate)](#setCaCertificate)
- [void setCaPath(const QString &path)](#setCaPath)
- [void setClientCertificate(const QByteArray &certificate)](#setClientCertificate)
- [void setDomainSuffixMatch(const QString &domainSuffixMatch)](#setDomainSuffixMatch)
- [void setEapMethods(const QList\<NetworkManager::Security8021xSetting::EapMethod\> &methods)](#setEapMethods)
- [void setIdentity(const QString &identity)](#setIdentity)
- [void setPacFile(const QString &filePath)](#setPacFile)
- [void setPassword(const QString &password)](#setPassword)
- [void setPasswordFlags(Setting::SecretFlags flags)](#setPasswordFlags)
- [void setPasswordRaw(const QByteArray &password)](#setPasswordRaw)
- [void setPasswordRawFlags(Setting::SecretFlags flags)](#setPasswordRawFlags)
- [void setPhase1FastProvisioning(NetworkManager::Security8021xSetting::FastProvisioning provisioning)](#setPhase1FastProvisioning)
- [void setPhase1PeapLabel(NetworkManager::Security8021xSetting::PeapLabel label)](#setPhase1PeapLabel)
- [void setPhase1PeapVersion(NetworkManager::Security8021xSetting::PeapVersion version)](#setPhase1PeapVersion)
- [void setPhase2AltSubjectMatches(const QStringList &strings)](#setPhase2AltSubjectMatches)
- [void setPhase2AuthEapMethod(NetworkManager::Security8021xSetting::AuthEapMethod method)](#setPhase2AuthEapMethod)
- [void setPhase2AuthMethod(NetworkManager::Security8021xSetting::AuthMethod method)](#setPhase2AuthMethod)
- [void setPhase2CaCertificate(const QByteArray &certificate)](#setPhase2CaCertificate)
- [void setPhase2CaPath(const QString &path)](#setPhase2CaPath)
- [void setPhase2ClientCertificate(const QByteArray &certificate)](#setPhase2ClientCertificate)
- [void setPhase2PrivateKey(const QByteArray &key)](#setPhase2PrivateKey)
- [void setPhase2PrivateKeyPassword(const QString &password)](#setPhase2PrivateKeyPassword)
- [void setPhase2PrivateKeyPasswordFlags(Setting::SecretFlags flags)](#setPhase2PrivateKeyPasswordFlags)
- [void setPhase2SubjectMatch(const QString &substring)](#setPhase2SubjectMatch)
- [void setPin(const QString &pin)](#setPin)
- [void setPinFlags(Setting::SecretFlags flags)](#setPinFlags)
- [void setPrivateKey(const QByteArray &key)](#setPrivateKey)
- [void setPrivateKeyPassword(const QString &password)](#setPrivateKeyPassword)
- [void setPrivateKeyPasswordFlags(Setting::SecretFlags flags)](#setPrivateKeyPasswordFlags)
- [void setSubjectMatch(const QString &substring)](#setSubjectMatch)
- [void setSystemCaCertificates(bool use)](#setSystemCaCertificates)
- [QString subjectMatch() const](#subjectMatch)
- [bool systemCaCertificates() const](#systemCaCertificates)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum Security8021xSetting::AuthEapMethod {#AuthEapMethod-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::Security8021xSetting::AuthEapMethodUnknown` | `0` |
| `NetworkManager::Security8021xSetting::AuthEapMethodMd5` | `1` |
| `NetworkManager::Security8021xSetting::AuthEapMethodMschapv2` | `2` |
| `NetworkManager::Security8021xSetting::AuthEapMethodOtp` | `3` |
| `NetworkManager::Security8021xSetting::AuthEapMethodGtc` | `4` |
| `NetworkManager::Security8021xSetting::AuthEapMethodTls` | `5` |

### enum Security8021xSetting::AuthMethod {#AuthMethod-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::Security8021xSetting::AuthMethodUnknown` | `0` |
| `NetworkManager::Security8021xSetting::AuthMethodPap` | `1` |
| `NetworkManager::Security8021xSetting::AuthMethodChap` | `2` |
| `NetworkManager::Security8021xSetting::AuthMethodMschap` | `3` |
| `NetworkManager::Security8021xSetting::AuthMethodMschapv2` | `4` |
| `NetworkManager::Security8021xSetting::AuthMethodGtc` | `5` |
| `NetworkManager::Security8021xSetting::AuthMethodOtp` | `6` |
| `NetworkManager::Security8021xSetting::AuthMethodMd5` | `7` |
| `NetworkManager::Security8021xSetting::AuthMethodTls` | `8` |

### enum Security8021xSetting::EapMethod {#EapMethod-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::Security8021xSetting::EapMethodUnknown` | `0` |
| `NetworkManager::Security8021xSetting::EapMethodLeap` | `1` |
| `NetworkManager::Security8021xSetting::EapMethodMd5` | `2` |
| `NetworkManager::Security8021xSetting::EapMethodTls` | `3` |
| `NetworkManager::Security8021xSetting::EapMethodPeap` | `4` |
| `NetworkManager::Security8021xSetting::EapMethodTtls` | `5` |
| `NetworkManager::Security8021xSetting::EapMethodSim` | `6` |
| `NetworkManager::Security8021xSetting::EapMethodFast` | `7` |
| `NetworkManager::Security8021xSetting::EapMethodPwd` | `8` |

### enum Security8021xSetting::FastProvisioning {#FastProvisioning-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::Security8021xSetting::FastProvisioningUnknown` | `-1` |
| `NetworkManager::Security8021xSetting::FastProvisioningDisabled` | `0` |
| `NetworkManager::Security8021xSetting::FastProvisioningAllowUnauthenticated` | `1` |
| `NetworkManager::Security8021xSetting::FastProvisioningAllowAuthenticated` | `2` |
| `NetworkManager::Security8021xSetting::FastProvisioningAllowBoth` | `3` |

### Security8021xSetting::List {#List-typedef}

### enum Security8021xSetting::PeapLabel {#PeapLabel-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::Security8021xSetting::PeapLabelUnknown` | `0` |
| `NetworkManager::Security8021xSetting::PeapLabelForce` | `1` |

### enum Security8021xSetting::PeapVersion {#PeapVersion-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::Security8021xSetting::PeapVersionUnknown` | `-1` |
| `NetworkManager::Security8021xSetting::PeapVersionZero` | `0` |
| `NetworkManager::Security8021xSetting::PeapVersionOne` | `1` |

### Security8021xSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### Security8021xSetting::Security8021xSetting() {#Security8021xSetting}

### \[explicit\] Security8021xSetting::Security8021xSetting(const NetworkManager::Security8021xSetting::Ptr &*other*) {#Security8021xSetting-1}

### QStringList Security8021xSetting::altSubjectMatches() const {#altSubjectMatches}

*See also* [setAltSubjectMatches](networkmanager-security8021xsetting.md#setAltSubjectMatches)()

### QString Security8021xSetting::anonymousIdentity() const {#anonymousIdentity}

*See also* [setAnonymousIdentity](networkmanager-security8021xsetting.md#setAnonymousIdentity)()

### QByteArray Security8021xSetting::caCertificate() const {#caCertificate}

*See also* [setCaCertificate](networkmanager-security8021xsetting.md#setCaCertificate)()

### QString Security8021xSetting::caPath() const {#caPath}

*See also* [setCaPath](networkmanager-security8021xsetting.md#setCaPath)()

### QByteArray Security8021xSetting::clientCertificate() const {#clientCertificate}

*See also* [setClientCertificate](networkmanager-security8021xsetting.md#setClientCertificate)()

### QString Security8021xSetting::domainSuffixMatch() const {#domainSuffixMatch}

*See also* [setDomainSuffixMatch](networkmanager-security8021xsetting.md#setDomainSuffixMatch)()

### QList\<NetworkManager::Security8021xSetting::EapMethod\> Security8021xSetting::eapMethods() const {#eapMethods}

*See also* [setEapMethods](networkmanager-security8021xsetting.md#setEapMethods)()

### QString Security8021xSetting::identity() const {#identity}

*See also* [setIdentity](networkmanager-security8021xsetting.md#setIdentity)()

### QString Security8021xSetting::pacFile() const {#pacFile}

*See also* [setPacFile](networkmanager-security8021xsetting.md#setPacFile)()

### QString Security8021xSetting::password() const {#password}

*See also* [setPassword](networkmanager-security8021xsetting.md#setPassword)()

### Setting::SecretFlags Security8021xSetting::passwordFlags() const {#passwordFlags}

*See also* [setPasswordFlags](networkmanager-security8021xsetting.md#setPasswordFlags)()

### QByteArray Security8021xSetting::passwordRaw() const {#passwordRaw}

*See also* [setPasswordRaw](networkmanager-security8021xsetting.md#setPasswordRaw)()

### Setting::SecretFlags Security8021xSetting::passwordRawFlags() const {#passwordRawFlags}

*See also* [setPasswordRawFlags](networkmanager-security8021xsetting.md#setPasswordRawFlags)()

### NetworkManager::Security8021xSetting::FastProvisioning Security8021xSetting::phase1FastProvisioning() const {#phase1FastProvisioning}

*See also* [setPhase1FastProvisioning](networkmanager-security8021xsetting.md#setPhase1FastProvisioning)()

### NetworkManager::Security8021xSetting::PeapLabel Security8021xSetting::phase1PeapLabel() const {#phase1PeapLabel}

*See also* [setPhase1PeapLabel](networkmanager-security8021xsetting.md#setPhase1PeapLabel)()

### NetworkManager::Security8021xSetting::PeapVersion Security8021xSetting::phase1PeapVersion() const {#phase1PeapVersion}

*See also* [setPhase1PeapVersion](networkmanager-security8021xsetting.md#setPhase1PeapVersion)()

### QStringList Security8021xSetting::phase2AltSubjectMatches() const {#phase2AltSubjectMatches}

*See also* [setPhase2AltSubjectMatches](networkmanager-security8021xsetting.md#setPhase2AltSubjectMatches)()

### NetworkManager::Security8021xSetting::AuthEapMethod Security8021xSetting::phase2AuthEapMethod() const {#phase2AuthEapMethod}

*See also* [setPhase2AuthEapMethod](networkmanager-security8021xsetting.md#setPhase2AuthEapMethod)()

### NetworkManager::Security8021xSetting::AuthMethod Security8021xSetting::phase2AuthMethod() const {#phase2AuthMethod}

*See also* [setPhase2AuthMethod](networkmanager-security8021xsetting.md#setPhase2AuthMethod)()

### QByteArray Security8021xSetting::phase2CaCertificate() const {#phase2CaCertificate}

*See also* [setPhase2CaCertificate](networkmanager-security8021xsetting.md#setPhase2CaCertificate)()

### QString Security8021xSetting::phase2CaPath() const {#phase2CaPath}

*See also* [setPhase2CaPath](networkmanager-security8021xsetting.md#setPhase2CaPath)()

### QByteArray Security8021xSetting::phase2ClientCertificate() const {#phase2ClientCertificate}

*See also* [setPhase2ClientCertificate](networkmanager-security8021xsetting.md#setPhase2ClientCertificate)()

### QByteArray Security8021xSetting::phase2PrivateKey() const {#phase2PrivateKey}

*See also* [setPhase2PrivateKey](networkmanager-security8021xsetting.md#setPhase2PrivateKey)()

### QString Security8021xSetting::phase2PrivateKeyPassword() const {#phase2PrivateKeyPassword}

*See also* [setPhase2PrivateKeyPassword](networkmanager-security8021xsetting.md#setPhase2PrivateKeyPassword)()

### Setting::SecretFlags Security8021xSetting::phase2PrivateKeyPasswordFlags() const {#phase2PrivateKeyPasswordFlags}

*See also* [setPhase2PrivateKeyPasswordFlags](networkmanager-security8021xsetting.md#setPhase2PrivateKeyPasswordFlags)()

### QString Security8021xSetting::phase2SubjectMatch() const {#phase2SubjectMatch}

*See also* [setPhase2SubjectMatch](networkmanager-security8021xsetting.md#setPhase2SubjectMatch)()

### QString Security8021xSetting::pin() const {#pin}

*See also* [setPin](networkmanager-security8021xsetting.md#setPin)()

### Setting::SecretFlags Security8021xSetting::pinFlags() const {#pinFlags}

*See also* [setPinFlags](networkmanager-security8021xsetting.md#setPinFlags)()

### QByteArray Security8021xSetting::privateKey() const {#privateKey}

*See also* [setPrivateKey](networkmanager-security8021xsetting.md#setPrivateKey)()

### QString Security8021xSetting::privateKeyPassword() const {#privateKeyPassword}

*See also* [setPrivateKeyPassword](networkmanager-security8021xsetting.md#setPrivateKeyPassword)()

### Setting::SecretFlags Security8021xSetting::privateKeyPasswordFlags() const {#privateKeyPasswordFlags}

*See also* [setPrivateKeyPasswordFlags](networkmanager-security8021xsetting.md#setPrivateKeyPasswordFlags)()

### void Security8021xSetting::setAltSubjectMatches(const QStringList &*strings*) {#setAltSubjectMatches}

*See also* [altSubjectMatches](networkmanager-security8021xsetting.md#altSubjectMatches)()

### void Security8021xSetting::setAnonymousIdentity(const QString &*identity*) {#setAnonymousIdentity}

*See also* [anonymousIdentity](networkmanager-security8021xsetting.md#anonymousIdentity)()

### void Security8021xSetting::setCaCertificate(const QByteArray &*certificate*) {#setCaCertificate}

Set certificate authority (ca)'s certificate for this setting.

*certificate* certificate's file path encoded into a byte array.

> **Warning:** certificate have to be null terminated or [NetworkManager](networkmanager.md) will refuse it.

*See also* [caCertificate](networkmanager-security8021xsetting.md#caCertificate)()

### void Security8021xSetting::setCaPath(const QString &*path*) {#setCaPath}

*See also* [caPath](networkmanager-security8021xsetting.md#caPath)()

### void Security8021xSetting::setClientCertificate(const QByteArray &*certificate*) {#setClientCertificate}

Set client certificate for this setting.

*certificate* certificate's file path encoded into a byte array.

> **Warning:** certificate have to be null terminated or [NetworkManager](networkmanager.md) will refuse it.

*See also* [clientCertificate](networkmanager-security8021xsetting.md#clientCertificate)()

### void Security8021xSetting::setDomainSuffixMatch(const QString &*domainSuffixMatch*) {#setDomainSuffixMatch}

*See also* [domainSuffixMatch](networkmanager-security8021xsetting.md#domainSuffixMatch)()

### void Security8021xSetting::setEapMethods(const QList\<NetworkManager::Security8021xSetting::EapMethod\> &*methods*) {#setEapMethods}

*See also* [eapMethods](networkmanager-security8021xsetting.md#eapMethods)()

### void Security8021xSetting::setIdentity(const QString &*identity*) {#setIdentity}

*See also* [identity](networkmanager-security8021xsetting.md#identity)()

### void Security8021xSetting::setPacFile(const QString &*filePath*) {#setPacFile}

Set UTF-8 encoded file path containing PAC for EAP-FAST.

*filePath* file path to be set.

*See also* [pacFile](networkmanager-security8021xsetting.md#pacFile)()

### void Security8021xSetting::setPassword(const QString &*password*) {#setPassword}

*See also* [password](networkmanager-security8021xsetting.md#password)()

### void Security8021xSetting::setPasswordFlags(Setting::SecretFlags *flags*) {#setPasswordFlags}

*See also* [passwordFlags](networkmanager-security8021xsetting.md#passwordFlags)()

### void Security8021xSetting::setPasswordRaw(const QByteArray &*password*) {#setPasswordRaw}

*See also* [passwordRaw](networkmanager-security8021xsetting.md#passwordRaw)()

### void Security8021xSetting::setPasswordRawFlags(Setting::SecretFlags *flags*) {#setPasswordRawFlags}

*See also* [passwordRawFlags](networkmanager-security8021xsetting.md#passwordRawFlags)()

### void Security8021xSetting::setPhase1FastProvisioning(NetworkManager::Security8021xSetting::FastProvisioning *provisioning*) {#setPhase1FastProvisioning}

*See also* [phase1FastProvisioning](networkmanager-security8021xsetting.md#phase1FastProvisioning)()

### void Security8021xSetting::setPhase1PeapLabel(NetworkManager::Security8021xSetting::PeapLabel *label*) {#setPhase1PeapLabel}

*See also* [phase1PeapLabel](networkmanager-security8021xsetting.md#phase1PeapLabel)()

### void Security8021xSetting::setPhase1PeapVersion(NetworkManager::Security8021xSetting::PeapVersion *version*) {#setPhase1PeapVersion}

*See also* [phase1PeapVersion](networkmanager-security8021xsetting.md#phase1PeapVersion)()

### void Security8021xSetting::setPhase2AltSubjectMatches(const QStringList &*strings*) {#setPhase2AltSubjectMatches}

*See also* [phase2AltSubjectMatches](networkmanager-security8021xsetting.md#phase2AltSubjectMatches)()

### void Security8021xSetting::setPhase2AuthEapMethod(NetworkManager::Security8021xSetting::AuthEapMethod *method*) {#setPhase2AuthEapMethod}

*See also* [phase2AuthEapMethod](networkmanager-security8021xsetting.md#phase2AuthEapMethod)()

### void Security8021xSetting::setPhase2AuthMethod(NetworkManager::Security8021xSetting::AuthMethod *method*) {#setPhase2AuthMethod}

*See also* [phase2AuthMethod](networkmanager-security8021xsetting.md#phase2AuthMethod)()

### void Security8021xSetting::setPhase2CaCertificate(const QByteArray &*certificate*) {#setPhase2CaCertificate}

Contains the CA certificate if used by the EAP method specified in the [phase2AuthMethod](networkmanager-security8021xsetting.md#phase2AuthMethod)() or [phase2AuthEapMethod](networkmanager-security8021xsetting.md#phase2AuthEapMethod)() properties.

*certificate* certificate's file path encoded into a byte array.

> **Warning:** certificate have to be null terminated or [NetworkManager](networkmanager.md) will refuse it.

*See also* [phase2CaCertificate](networkmanager-security8021xsetting.md#phase2CaCertificate)()

### void Security8021xSetting::setPhase2CaPath(const QString &*path*) {#setPhase2CaPath}

*See also* [phase2CaPath](networkmanager-security8021xsetting.md#phase2CaPath)()

### void Security8021xSetting::setPhase2ClientCertificate(const QByteArray &*certificate*) {#setPhase2ClientCertificate}

*See also* [phase2ClientCertificate](networkmanager-security8021xsetting.md#phase2ClientCertificate)()

### void Security8021xSetting::setPhase2PrivateKey(const QByteArray &*key*) {#setPhase2PrivateKey}

*See also* [phase2PrivateKey](networkmanager-security8021xsetting.md#phase2PrivateKey)()

### void Security8021xSetting::setPhase2PrivateKeyPassword(const QString &*password*) {#setPhase2PrivateKeyPassword}

*See also* [phase2PrivateKeyPassword](networkmanager-security8021xsetting.md#phase2PrivateKeyPassword)()

### void Security8021xSetting::setPhase2PrivateKeyPasswordFlags(Setting::SecretFlags *flags*) {#setPhase2PrivateKeyPasswordFlags}

*See also* [phase2PrivateKeyPasswordFlags](networkmanager-security8021xsetting.md#phase2PrivateKeyPasswordFlags)()

### void Security8021xSetting::setPhase2SubjectMatch(const QString &*substring*) {#setPhase2SubjectMatch}

*See also* [phase2SubjectMatch](networkmanager-security8021xsetting.md#phase2SubjectMatch)()

### void Security8021xSetting::setPin(const QString &*pin*) {#setPin}

*See also* [pin](networkmanager-security8021xsetting.md#pin)()

### void Security8021xSetting::setPinFlags(Setting::SecretFlags *flags*) {#setPinFlags}

*See also* [pinFlags](networkmanager-security8021xsetting.md#pinFlags)()

### void Security8021xSetting::setPrivateKey(const QByteArray &*key*) {#setPrivateKey}

Set private key for this setting.

*key* the key to be set.

> **Warning:** key have to be null terminated or [NetworkManager](networkmanager.md) will refuse it.

*See also* [privateKey](networkmanager-security8021xsetting.md#privateKey)()

### void Security8021xSetting::setPrivateKeyPassword(const QString &*password*) {#setPrivateKeyPassword}

*See also* [privateKeyPassword](networkmanager-security8021xsetting.md#privateKeyPassword)()

### void Security8021xSetting::setPrivateKeyPasswordFlags(Setting::SecretFlags *flags*) {#setPrivateKeyPasswordFlags}

*See also* [privateKeyPasswordFlags](networkmanager-security8021xsetting.md#privateKeyPasswordFlags)()

### void Security8021xSetting::setSubjectMatch(const QString &*substring*) {#setSubjectMatch}

*See also* [subjectMatch](networkmanager-security8021xsetting.md#subjectMatch)()

### void Security8021xSetting::setSystemCaCertificates(bool *use*) {#setSystemCaCertificates}

*See also* [systemCaCertificates](networkmanager-security8021xsetting.md#systemCaCertificates)()

### QString Security8021xSetting::subjectMatch() const {#subjectMatch}

*See also* [setSubjectMatch](networkmanager-security8021xsetting.md#setSubjectMatch)()

### bool Security8021xSetting::systemCaCertificates() const {#systemCaCertificates}

*See also* [setSystemCaCertificates](networkmanager-security8021xsetting.md#setSystemCaCertificates)()
