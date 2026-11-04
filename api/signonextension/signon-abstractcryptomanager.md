---
title: "SignOn::AbstractCryptoManager Class"
description: "Manages the credentials storage file system encryption."
---

# SignOn::AbstractCryptoManager Class

Manages the credentials storage file system encryption. [More...](#details)

- **Header:** `#include <SignOn/AbstractCryptoManager>`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](signon-abstractcryptomanager-members.md)

## Public Functions

- [AbstractCryptoManager(QObject \*parent = 0)](#AbstractCryptoManager)
- [~AbstractCryptoManager()](#dtor.AbstractCryptoManager)
- [bool addEncryptionKey(const SignOn::Key &key, const SignOn::Key &existingKey)](#addEncryptionKey)
- [QStringList backupFiles() const](#backupFiles)
- [bool deleteFileSystem()](#deleteFileSystem)
- [SignOn::Key encryptionKey() const](#encryptionKey)
- [bool encryptionKeyInUse(const SignOn::Key &key)](#encryptionKeyInUse)
- [bool fileSystemIsMounted() const](#fileSystemIsMounted)
- [bool fileSystemIsSetup() const](#fileSystemIsSetup)
- [QString fileSystemMountPath() const](#fileSystemMountPath)
- [bool initialize(const QVariantMap &configuration)](#initialize)
- [bool mountFileSystem()](#mountFileSystem)
- [bool removeEncryptionKey(const SignOn::Key &key, const SignOn::Key &remainingKey)](#removeEncryptionKey)
- [void setEncryptionKey(const SignOn::Key &key)](#setEncryptionKey)
- [bool setupFileSystem()](#setupFileSystem)
- [bool unmountFileSystem()](#unmountFileSystem)

## Signals

- [void fileSystemMounted()](#fileSystemMounted)
- [void fileSystemUnmounting()](#fileSystemUnmounting)

## Protected Functions

- [void setFileSystemMounted(bool isMounted)](#setFileSystemMounted)
- [void setFileSystemSetup(bool isSetup)](#setFileSystemSetup)

## Detailed Description {#details}

The API is modeled after a LUKS-based implementation.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] AbstractCryptoManager::AbstractCryptoManager(QObject \**parent* = 0) {#AbstractCryptoManager}

Constructs a [AbstractCryptoManager](signon-abstractcryptomanager.md) object with the given `parent`.

### \[virtual noexcept\] AbstractCryptoManager::~AbstractCryptoManager() {#dtor.AbstractCryptoManager}

Destructor.

### \[virtual\] bool AbstractCryptoManager::addEncryptionKey(const SignOn::Key &*key*, const SignOn::Key &*existingKey*) {#addEncryptionKey}

Adds the encryption `key` to one of the available keyslots of the LUKS partition's header; `existingKey` is an already existing key.

Returns true if succeeded, false otherwise.

*See also* [encryptionKeyInUse](signon-abstractcryptomanager.md#encryptionKeyInUse)()

### \[virtual\] QStringList AbstractCryptoManager::backupFiles() const {#backupFiles}

Returns the list of files which need to be backed up.

### \[virtual\] bool AbstractCryptoManager::deleteFileSystem() {#deleteFileSystem}

Deletes the encrypted file system. Returns true if successful, false otherwise.

> **Warning:** Use this carefully, this will lead to data loss.

### SignOn::Key AbstractCryptoManager::encryptionKey() const {#encryptionKey}

Returns the encryption key in use.

*See also* [setEncryptionKey](signon-abstractcryptomanager.md#setEncryptionKey)()

### \[virtual\] bool AbstractCryptoManager::encryptionKeyInUse(const SignOn::Key &*key*) {#encryptionKeyInUse}

Returns whether `key` is occupying a keyslot in the encrypted file system.

> **Note:** If the file system is not mounted and the encryption key can access it, this method will cause the file system to be mounted.

### bool AbstractCryptoManager::fileSystemIsMounted() const {#fileSystemIsMounted}

Returns true if the file system is mounted, false otherwise.

### bool AbstractCryptoManager::fileSystemIsSetup() const {#fileSystemIsSetup}

Returns true if the file system is setup, false otherwise.

### \[virtual\] QString AbstractCryptoManager::fileSystemMountPath() const {#fileSystemMountPath}

Returns the path of the mounted file system.

### \[signal\] void AbstractCryptoManager::fileSystemMounted() {#fileSystemMounted}

The encrypted file system was mounted.

*See also* [setFileSystemMounted](signon-abstractcryptomanager.md#setFileSystemMounted)()

### \[signal\] void AbstractCryptoManager::fileSystemUnmounting() {#fileSystemUnmounting}

The encrypted file system is about to be unmounted.

### \[virtual\] bool AbstractCryptoManager::initialize(const QVariantMap &*configuration*) {#initialize}

\* Initializes the object with the given `configuration`, a dictionary of \* configuration options, dependent on the specific crypto-manager \* implementation. \* \* Returns true if the configuration is valid.

### \[virtual\] bool AbstractCryptoManager::mountFileSystem() {#mountFileSystem}

Mounts the encrypted file system. Returns true if successful, false otherwise.

### \[virtual\] bool AbstractCryptoManager::removeEncryptionKey(const SignOn::Key &*key*, const SignOn::Key &*remainingKey*) {#removeEncryptionKey}

\* Releases the keyslot `key` uses in the LUKS partition's header; \* `remainingKey` is another valid key. \* \*

> **Note:** The system cannot remain keyless. \* \* Returns true if succeeded, false otherwise.

### void AbstractCryptoManager::setEncryptionKey(const SignOn::Key &*key*) {#setEncryptionKey}

Sets the encryption key to `key`, the encrypted file system key.

*See also* [encryptionKey](signon-abstractcryptomanager.md#encryptionKey)()

### \[protected\] void AbstractCryptoManager::setFileSystemMounted(bool *isMounted*) {#setFileSystemMounted}

Implementations record whether the file system `isMounted`.

*See also* [fileSystemMounted](signon-abstractcryptomanager.md#fileSystemMounted)()

### \[protected\] void AbstractCryptoManager::setFileSystemSetup(bool *isSetup*) {#setFileSystemSetup}

Implementations record whether the file system `isSetup`.

### \[virtual\] bool AbstractCryptoManager::setupFileSystem() {#setupFileSystem}

Sets up an encrypted file system. This method is to be called only at the file system creation/formatting. Use [mountFileSystem](signon-abstractcryptomanager.md#mountFileSystem)() on subsequent uses. This method handles also the mounting so when using it, a call to [mountFileSystem](signon-abstractcryptomanager.md#mountFileSystem)() is not necessary.

Returns true if successful, false otherwise.

> **Warning:** This method might format the credentials file system, use carefully.

### \[virtual\] bool AbstractCryptoManager::unmountFileSystem() {#unmountFileSystem}

Unmounts the encrypted file system. Returns true if successful, false otherwise.
