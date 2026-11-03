---
title: "Attica::ProviderManager Class"
description: "Attica ProviderManager."
---

# Attica::ProviderManager Class

Attica [ProviderManager](attica-providermanager.md). [More...](#details)

- **Header:** `#include <Attica/ProviderManager>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](attica-providermanager-members.md)

## Public Types

- [enum ProviderManager::ProviderFlag](#ProviderFlag-enum)

## Public Functions

- [ProviderManager(const Attica::ProviderManager::ProviderFlags &flags = NoFlags)](#ProviderManager)
- [void addProviderFile(const QUrl &file)](#addProviderFile)
- [void addProviderFileToDefaultProviders(const QUrl &url)](#addProviderFileToDefaultProviders)
- [void addProviderFromXml(const QString &providerXml)](#addProviderFromXml)
- [void clear()](#clear)
- [bool contains(const QUrl &provider) const](#contains)
- [QList\<QUrl\> defaultProviderFiles()](#defaultProviderFiles)
- [void loadDefaultProviders()](#loadDefaultProviders)
- [Attica::Provider providerByUrl(const QUrl &url) const](#providerByUrl)
- [QList\<QUrl\> providerFiles() const](#providerFiles)
- [Attica::Provider providerFor(const QUrl &url) const](#providerFor)
- [QList\<Attica::Provider\> providers() const](#providers)
- [void removeProviderFileFromDefaultProviders(const QUrl &url)](#removeProviderFileFromDefaultProviders)
- [void setAuthenticationSuppressed(bool suppressed)](#setAuthenticationSuppressed)

## Signals

- [void authenticationCredentialsMissing(const Attica::Provider &provider)](#authenticationCredentialsMissing)
- [void defaultProvidersLoaded()](#defaultProvidersLoaded)
- [void failedToLoad(const QUrl &provider, QNetworkReply::NetworkError error)](#failedToLoad)
- [void providerAdded(const Attica::Provider &provider)](#providerAdded)

## Detailed Description {#details}

This class is the primary access to Attica's functions. Use the [ProviderManager](attica-providermanager.md) to load Open Collaboration Service providers, either the default system ones, or from XML or custom locations.

### Provider Files {#provider-files}

Provider files are defined here: http://www.freedesktop.org/wiki/Specifications/open-collaboration-services

### Basic Use {#basic-use}

See [addProviderFileToDefaultProviders](attica-providermanager.md#addProviderFileToDefaultProviders)(const [QUrl](https://doc.qt.io/qt-6/qurl.html) &url) for an example of what the provider file sohuld look like. You can add providers to the [ProviderManager](attica-providermanager.md) as either raw XML data using [addProviderFromXml](attica-providermanager.md#addProviderFromXml)(const [QString](https://doc.qt.io/qt-6/qstring.html) &providerXml), or from a file somewhere on the system through [addProviderFile](attica-providermanager.md#addProviderFile)(const [QUrl](https://doc.qt.io/qt-6/qurl.html) &file), or you can simply load the default providers provided by your system (which generally means KDE's provider opendesktop.org).

Importantly, to be able to detect when the [ProviderManager](attica-providermanager.md) is ready to manage things, before initialising it you will want to connect to the [providerAdded](attica-providermanager.md#providerAdded)(const [Attica::Provider](attica-provider.md) &provider) signal, which is fired every time a new provider is added to the manager.

If you manually add all providers from XML, you can expect this to happen immediately. This means that once you have added your providers that way, you can access them through the [providers](attica-providermanager.md#providers)() function, which returns a list of all loaded Providers.

Once you have loaded a Provider, you can use its functions to access the services offered by that provider.

## Member Type Documentation {#member-type-documentation}

### enum ProviderManager::ProviderFlag {#ProviderFlag-enum}

**flags ProviderManager::ProviderFlags**

| Constant |   |
| --- | --- |
| `Attica::ProviderManager::NoFlags` | `0x0` |
| `Attica::ProviderManager::DisablePlugins` | `0x1` |

The `ProviderFlags` type is a typedef for `QFlags<ProviderFlag>. `It stores an OR combination of `ProviderFlag` values.

## Member Function Documentation {#member-function-documentation}

### ProviderManager::ProviderManager(const Attica::ProviderManager::ProviderFlags &*flags* = NoFlags) {#ProviderManager}

### void ProviderManager::addProviderFile(const QUrl &*file*) {#addProviderFile}

### void ProviderManager::addProviderFileToDefaultProviders(const QUrl &*url*) {#addProviderFileToDefaultProviders}

Add a provider file to the default providers (xml that contains provider descriptions). Provider files contain information about each provider:

```cpp
<providers>
<provider>
   <id>opendesktop</id>
   <location>https://api.opendesktop.org/v1/</location>
   <name>openDesktop.org</name>
   <icon></icon>
   <termsofuse>https://opendesktop.org/terms/</termsofuse>
   <register>https://opendesktop.org/usermanager/new.php</register>
   <services>
       <person ocsversion="1.3" />
       <friend ocsversion="1.3" />
       <message ocsversion="1.3" />
       <activity ocsversion="1.3" />
       <content ocsversion="1.3" />
       <fan ocsversion="1.3" />
       <knowledgebase ocsversion="1.3" />
       <event ocsversion="1.3" />
   </services>
</provider>
</providers>
```

`url` the url of the provider file

### void ProviderManager::addProviderFromXml(const QString &*providerXml*) {#addProviderFromXml}

Parse a xml file containing a provider description

### \[signal\] void ProviderManager::authenticationCredentialsMissing(const Attica::Provider &*provider*) {#authenticationCredentialsMissing}

### void ProviderManager::clear() {#clear}

Remove all providers and provider files that have been loaded

### bool ProviderManager::contains(const QUrl &*provider*) const {#contains}

Returns whether there's a provider with base url `provider`

### QList\<QUrl\> ProviderManager::defaultProviderFiles() {#defaultProviderFiles}

The list of provider files that get loaded by [loadDefaultProviders](attica-providermanager.md#loadDefaultProviders). Each of these files can contain multiple providers.

### \[signal\] void ProviderManager::defaultProvidersLoaded() {#defaultProvidersLoaded}

### \[signal\] void ProviderManager::failedToLoad(const QUrl &*provider*, QNetworkReply::NetworkError *error*) {#failedToLoad}

### void ProviderManager::loadDefaultProviders() {#loadDefaultProviders}

Load available providers from configuration

### \[signal\] void ProviderManager::providerAdded(const Attica::Provider &*provider*) {#providerAdded}

### Attica::Provider ProviderManager::providerByUrl(const QUrl &*url*) const {#providerByUrl}

Returns the provider with `url` base url.

### QList\<QUrl\> ProviderManager::providerFiles() const {#providerFiles}

### Attica::Provider ProviderManager::providerFor(const QUrl &*url*) const {#providerFor}

Returns the provider for a given provider `url`.

### QList\<Attica::Provider\> ProviderManager::providers() const {#providers}

Returns all loaded providers

### void ProviderManager::removeProviderFileFromDefaultProviders(const QUrl &*url*) {#removeProviderFileFromDefaultProviders}

### void ProviderManager::setAuthenticationSuppressed(bool *suppressed*) {#setAuthenticationSuppressed}

Suppresses the authentication, so that the application can take care of authenticating itself
