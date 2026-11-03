---
title: "KWallet::Wallet Class"
description: "KDE Wallet Class."
---

# KWallet::Wallet Class

KDE Wallet Class. [More...](#details)

- **Header:** `#include <KWallet>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Wallet)`  
  `target_link_libraries(mytarget PRIVATE KF6::Wallet)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kwallet-wallet-members.md)  
[Deprecated members](kwallet-wallet-obsolete.md)

## Public Types

- [enum Wallet::EntryType](#EntryType-enum)
- [enum Wallet::OpenType](#OpenType-enum)

## Public Functions

- [~Wallet()](#dtor.Wallet)
- [bool createFolder(const QString &f)](#createFolder)
- [const QString &currentFolder() const](#currentFolder)
- [QMap\<QString, QByteArray\> entriesList(bool \*ok) const](#entriesList)
- [QStringList entryList()](#entryList)
- [KWallet::Wallet::EntryType entryType(const QString &key)](#entryType)
- [QStringList folderList()](#folderList)
- [bool hasEntry(const QString &key)](#hasEntry)
- [bool hasFolder(const QString &f)](#hasFolder)
- [bool isOpen() const](#isOpen)
- [QMap\<QString, QMap\<QString, QString\>\> mapList(bool \*ok) const](#mapList)
- [QMap\<QString, QString\> passwordList(bool \*ok) const](#passwordList)
- [int readEntry(const QString &key, QByteArray &value)](#readEntry)
- [int readMap(const QString &key, QMap\<QString, QString\> &value)](#readMap)
- [int readPassword(const QString &key, QString &value)](#readPassword)
- [int removeEntry(const QString &key)](#removeEntry)
- [bool removeFolder(const QString &f)](#removeFolder)
- [int renameEntry(const QString &oldName, const QString &newName)](#renameEntry)
- [bool setFolder(const QString &f)](#setFolder)
- [const QString &walletName() const](#walletName)
- [int writeEntry(const QString &key, const QByteArray &value)](#writeEntry)
- [int writeEntry(const QString &key, const QByteArray &value, KWallet::Wallet::EntryType entryType)](#writeEntry-1)
- [int writeMap(const QString &key, const QMap\<QString, QString\> &value)](#writeMap)
- [int writePassword(const QString &key, const QString &value)](#writePassword)

## Signals

- [void folderListUpdated()](#folderListUpdated)
- [void folderRemoved(const QString &folder)](#folderRemoved)
- [void folderUpdated(const QString &folder)](#folderUpdated)
- [void walletClosed()](#walletClosed)
- [void walletOpened(bool success)](#walletOpened)

## Static Public Members

- [const QString FormDataFolder()](#FormDataFolder)
- [const QString LocalWallet()](#LocalWallet)
- [const QString NetworkWallet()](#NetworkWallet)
- [const QString PasswordFolder()](#PasswordFolder)
- [void changePassword(const QString &name, WId w)](#changePassword)
- [int closeWallet(const QString &name, bool force)](#closeWallet)
- [int deleteWallet(const QString &name)](#deleteWallet)
- [bool disconnectApplication(const QString &wallet, const QString &app)](#disconnectApplication)
- [bool folderDoesNotExist(const QString &wallet, const QString &folder)](#folderDoesNotExist)
- [bool isEnabled()](#isEnabled)
- [bool isOpen(const QString &name)](#isOpen-1)
- [bool keyDoesNotExist(const QString &wallet, const QString &folder, const QString &key)](#keyDoesNotExist)
- [KWallet::Wallet \*openWallet(const QString &name, WId w, KWallet::Wallet::OpenType ot = Synchronous)](#openWallet)
- [QStringList users(const QString &wallet)](#users)
- [QStringList walletList()](#walletList)

## Detailed Description {#details}

This class implements a generic system-wide Wallet for KDE. This is the ONLY public interface.

## Member Type Documentation {#member-type-documentation}

### enum Wallet::EntryType {#EntryType-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KWallet::Wallet::Unknown` | `0` | An invalid entry |
| `KWallet::Wallet::Password` | `1` | The entry is a simple text password |
| `KWallet::Wallet::Stream` | `2` | The entry is binary data which the client will need to know how to decode |
| `KWallet::Wallet::Map` | `3` | The entry is a key/value map and can be decoded as a [QMap](https://doc.qt.io/qt-6/qmap.html)\<[QString](https://doc.qt.io/qt-6/qstring.html), [QString](https://doc.qt.io/qt-6/qstring.html)\> |

### enum Wallet::OpenType {#OpenType-enum}

| Constant |   |
| --- | --- |
| `KWallet::Wallet::Synchronous` | `0` |
| `KWallet::Wallet::Asynchronous` | `1` |
| `KWallet::Wallet::Path` | `2` |

## Member Function Documentation {#member-function-documentation}

### \[override virtual noexcept\] Wallet::~Wallet() {#dtor.Wallet}

Destroy a [KWallet](kwallet-module.md) object.

Closes the wallet.

### \[static\] const QString Wallet::FormDataFolder() {#FormDataFolder}

Returns the standardized name of the form data folder.

It is automatically created when a wallet is created, but the user may still delete it so you should check for its existence and recreate it if necessary and desired.

### \[static\] const QString Wallet::LocalWallet() {#LocalWallet}

Returns the name of the wallet used to store local passwords.

### \[static\] const QString Wallet::NetworkWallet() {#NetworkWallet}

Returns the name of the wallet used to store network passwords.

### \[static\] const QString Wallet::PasswordFolder() {#PasswordFolder}

Returns the standardized name of the password folder.

It is automatically created when a wallet is created, but the user may still delete it so you should check for its existence and recreate it if necessary and desired.

### \[static\] void Wallet::changePassword(const QString &*name*, WId *w*) {#changePassword}

Request to the wallet service to change the password of the wallet `name`.

`name` The wallet to change the password of.

`w` The window id to associate any dialogs with. You can pass 0 if you don't have a window the password dialog should associate with.

### \[static\] int Wallet::closeWallet(const QString &*name*, bool *force*) {#closeWallet}

Close the wallet `name`. The wallet will only be closed if it is open but not in use (rare), or if it is forced closed.

`name` The name of the wallet to close.

`force` Set true to force the wallet closed even if it is in use by others.

Returns 0 on success, non-zero on error.

### \[virtual\] bool Wallet::createFolder(const QString &*f*) {#createFolder}

Created the folder `f`.

`f` the name of the folder to create

Returns true if the folder was successfully created.

### \[virtual\] const QString &Wallet::currentFolder() const {#currentFolder}

Determine the current working folder in the wallet. If the folder name is empty, it is working in the global folder, which is valid but discouraged.

Returns the current working folder.

### \[static\] int Wallet::deleteWallet(const QString &*name*) {#deleteWallet}

Delete the wallet `name`. The wallet will be forced closed first.

`name` The name of the wallet to delete.

Returns 0 on success, non-zero on error.

### \[static\] bool Wallet::disconnectApplication(const QString &*wallet*, const QString &*app*) {#disconnectApplication}

Disconnect the application `app` from `wallet`.

`wallet` The name of the wallet to disconnect.

`app` The name of the application to disconnect.

Returns `true` on success, false on error.

### QMap\<QString, QByteArray\> Wallet::entriesList(bool \**ok*) const {#entriesList}

Get a list of all the entries in the current folder. The entry format is unknown except that it is either a [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) or a [QDataStream](https://doc.qt.io/qt-6/qdatastream.html), which effectively means that it could be anything.

`ok` if not nullptr, the object this parameter points to will be set to true to indicate success or false otherwise

Returns a map of key/value pairs where the key in the map is the entry key

### \[virtual\] QStringList Wallet::entryList() {#entryList}

Return the list of keys of all entries in this folder.

Returns an empty list if the wallet is not open, or if the folder is empty.

### \[virtual\] KWallet::Wallet::EntryType Wallet::entryType(const QString &*key*) {#entryType}

Determine the type of the entry `key` in this folder.

`key` The key to look up.

Returns an enumerated type representing the type of the entry.

### \[static\] bool Wallet::folderDoesNotExist(const QString &*wallet*, const QString &*folder*) {#folderDoesNotExist}

Determine if a folder does not exist in a wallet. This does not require decryption of the wallet. This is a handy optimization to avoid prompting the user if your data is certainly not in the wallet.

`wallet` The wallet to look in.

`folder` The folder to look up.

Returns true if the folder does NOT exist in the wallet, or the wallet does not exist.

### \[virtual\] QStringList Wallet::folderList() {#folderList}

Obtain the list of all folders contained in the wallet.

Returns an empty list if the wallet is not open.

### \[signal\] void Wallet::folderListUpdated() {#folderListUpdated}

Emitted when the folder list is changed in this wallet.

### \[signal\] void Wallet::folderRemoved(const QString &*folder*) {#folderRemoved}

Emitted when a folder in this wallet is removed.

`folder` The folder that was removed.

### \[signal\] void Wallet::folderUpdated(const QString &*folder*) {#folderUpdated}

Emitted when a folder in this wallet is updated.

`folder` The folder that was updated.

### \[virtual\] bool Wallet::hasEntry(const QString &*key*) {#hasEntry}

Determine if the current folder has they entry `key`.

`key` The key to search for.

Returns true if the folder contains `key`.

### \[virtual\] bool Wallet::hasFolder(const QString &*f*) {#hasFolder}

Determine if the folder `f` exists in the wallet.

`f` the name of the folder to check for

Returns true if the folder exists in the wallet.

### \[static\] bool Wallet::isEnabled() {#isEnabled}

Determine if the KDE wallet is enabled. Normally you do not need to use this because [openWallet](kwallet-wallet.md#openWallet)() will just fail.

Returns true if the wallet enabled, else false.

### \[virtual\] bool Wallet::isOpen() const {#isOpen}

Determine if the current wallet is open, and is a valid wallet handle.

Returns true if the wallet handle is valid and open.

### \[static\] bool Wallet::isOpen(const QString &*name*) {#isOpen-1}

Determine if the wallet `name` is open by any application.

`name` The name of the wallet to check.

Returns `true` if the wallet is open, else false.

### \[static\] bool Wallet::keyDoesNotExist(const QString &*wallet*, const QString &*folder*, const QString &*key*) {#keyDoesNotExist}

Determine if an entry in a folder does not exist in a wallet. This does not require decryption of the wallet. This is a handy optimization to avoid prompting the user if your data is certainly not in the wallet.

`wallet` The wallet to look in.

`folder` The folder to look in.

`key` The key to look up.

Returns true if the key does NOT exist in the wallet, or the folder or wallet does not exist.

### QMap\<QString, QMap\<QString, QString\>\> Wallet::mapList(bool \**ok*) const {#mapList}

Get a list of all the maps in the current folder.

`ok` if not nullptr, the object this parameter points to will be set to true to indicate success or false otherwise. Note that if any of the keys was not originally written as a map, the object will be set to false

Returns a map of key/value pairs where the key in the map is the entry key

### \[static\] KWallet::Wallet \*Wallet::openWallet(const QString &*name*, WId *w*, KWallet::Wallet::OpenType *ot* = Synchronous) {#openWallet}

Open the wallet `name`. The user will be prompted to allow your application to open the wallet, and may be prompted for a password. You are responsible for deleting this object when you are done with it.

`name` The name of the wallet to open.

`ot` If Asynchronous, the call will return immediately with a non-null pointer to an invalid wallet. You must immediately connect the [walletOpened](kwallet-wallet.md#walletOpened)() signal to a slot so that you will know when it is opened, or when it fails.

`w` The window id to associate any dialogs with. You can pass 0 if you don't have a window the password dialog should associate with.

Returns a pointer to the wallet if successful, or a null pointer on error or if rejected. A null pointer can also be returned if user choose to deactivate the wallet system.

### QMap\<QString, QString\> Wallet::passwordList(bool \**ok*) const {#passwordList}

Get a list of all the passwords in the current folder, which can be used to populate a list view in a password manager.

`ok` if not nullptr, the object this parameter points to will be set to true to indicate success or false otherwise. Note that the object will be set to false if any of the keys was not originally written as a password

Returns a map of key/value pairs, where the key in the map is the entry key

### \[virtual\] int Wallet::readEntry(const QString &*key*, QByteArray &*value*) {#readEntry}

Read the entry `key` from the current folder. The entry format is unknown except that it is either a [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) or a [QDataStream](https://doc.qt.io/qt-6/qdatastream.html), which effectively means that it is anything.

`key` The key of the entry to read.

`value` A buffer to fill with the value.

Returns 0 on success, non-zero on error.

### \[virtual\] int Wallet::readMap(const QString &*key*, QMap\<QString, QString\> &*value*) {#readMap}

Read the map entry `key` from the current folder.

`key` The key of the entry to read.

`value` A map buffer to fill with the value.

Returns 0 on success, non-zero on error. Will return an error if the key was not originally written as a map.

### \[virtual\] int Wallet::readPassword(const QString &*key*, QString &*value*) {#readPassword}

Read the password entry `key` from the current folder.

`key` The key of the entry to read.

`value` A password buffer to fill with the value.

Returns 0 on success, non-zero on error. Will return an error if the key was not originally written as a password.

### \[virtual\] int Wallet::removeEntry(const QString &*key*) {#removeEntry}

Remove the entry `key` from the current folder.

`key` The key to remove.

Returns 0 on success, non-zero on error.

### \[virtual\] bool Wallet::removeFolder(const QString &*f*) {#removeFolder}

Remove the folder `f` and all its entries from the wallet.

`f` the name of the folder to remove

Returns true if the folder was successfully removed.

### \[virtual\] int Wallet::renameEntry(const QString &*oldName*, const QString &*newName*) {#renameEntry}

Rename the entry `oldName` to `newName`.

`oldName` The original key of the entry.

`newName` The new key of the entry.

Returns 0 on success, non-zero on error.

### \[virtual\] bool Wallet::setFolder(const QString &*f*) {#setFolder}

Set the current working folder to `f`. The folder must exist, or this call will fail. Create a folder with [createFolder](kwallet-wallet.md#createFolder)().

`f` the name of the folder to make the working folder

Returns true if the folder was successfully set.

*See also* [hasFolder](kwallet-wallet.md#hasFolder)()

### \[static\] QStringList Wallet::users(const QString &*wallet*) {#users}

List the applications that are using the wallet `wallet`.

`wallet` The wallet to query.

Returns a list of all D-Bus application IDs using the wallet.

### \[signal\] void Wallet::walletClosed() {#walletClosed}

Emitted when this wallet is closed.

### \[static\] QStringList Wallet::walletList() {#walletList}

List all the wallets available.

Returns a list of the names of all wallets that are open.

### \[virtual\] const QString &Wallet::walletName() const {#walletName}

Returns the name of the current wallet.

### \[signal\] void Wallet::walletOpened(bool *success*) {#walletOpened}

Emitted when a wallet is opened in asynchronous mode.

`success` True if the wallet was opened successfully.

### \[virtual\] int Wallet::writeEntry(const QString &*key*, const QByteArray &*value*) {#writeEntry}

Write `key` = `value` as a binary entry to the current folder.

`key` The key of the new entry.

`value` The value of the entry.

Returns 0 on success, non-zero on error.

### \[virtual\] int Wallet::writeEntry(const QString &*key*, const QByteArray &*value*, KWallet::Wallet::EntryType *entryType*) {#writeEntry-1}

Write `key` = `value` as a binary entry to the current folder. Be careful with this, it could cause inconsistency in the future since you can put an arbitrary entry type in place.

`key` The key of the new entry.

`value` The value of the entry.

`entryType` The type of the entry.

Returns 0 on success, non-zero on error.

### \[virtual\] int Wallet::writeMap(const QString &*key*, const QMap\<QString, QString\> &*value*) {#writeMap}

Write `key` = `value` as a map to the current folder.

`key` The key of the new entry.

`value` The value of the map.

Returns 0 on success, non-zero on error.

### \[virtual\] int Wallet::writePassword(const QString &*key*, const QString &*value*) {#writePassword}

Write `key` = `value` as a password to the current folder.

`key` The key of the new entry.

`value` The value of the password.

Returns 0 on success, non-zero on error.
