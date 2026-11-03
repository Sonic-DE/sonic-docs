---
title: "List of All Members for KWallet::Wallet"
description: "Every member of KWallet::Wallet, including inherited members."
parent: "kwallet/kwallet-wallet"
---

# List of All Members for KWallet::Wallet

This is the complete list of members for [KWallet::Wallet](kwallet-wallet.md), including inherited members.

- [~Wallet()](kwallet-wallet.md#dtor.Wallet)
- [changePassword(const QString &, WId)](kwallet-wallet.md#changePassword)
- [closeWallet(const QString &, bool) : int](kwallet-wallet.md#closeWallet)
- [createFolder(const QString &) : bool](kwallet-wallet.md#createFolder)
- [currentFolder() const : const QString &](kwallet-wallet.md#currentFolder)
- [deleteWallet(const QString &) : int](kwallet-wallet.md#deleteWallet)
- [disconnectApplication(const QString &, const QString &) : bool](kwallet-wallet.md#disconnectApplication)
- [entriesList(bool \*) const : QMap\<QString, QByteArray\>](kwallet-wallet.md#entriesList)
- [entryList() : QStringList](kwallet-wallet.md#entryList)
- [entryType(const QString &) : KWallet::Wallet::EntryType](kwallet-wallet.md#entryType)
- [folderDoesNotExist(const QString &, const QString &) : bool](kwallet-wallet.md#folderDoesNotExist)
- [folderList() : QStringList](kwallet-wallet.md#folderList)
- [folderListUpdated()](kwallet-wallet.md#folderListUpdated)
- [folderRemoved(const QString &)](kwallet-wallet.md#folderRemoved)
- [folderUpdated(const QString &)](kwallet-wallet.md#folderUpdated)
- [FormDataFolder() : const QString](kwallet-wallet.md#FormDataFolder)
- [hasEntry(const QString &) : bool](kwallet-wallet.md#hasEntry)
- [hasFolder(const QString &) : bool](kwallet-wallet.md#hasFolder)
- [isEnabled() : bool](kwallet-wallet.md#isEnabled)
- [isOpen() const : bool](kwallet-wallet.md#isOpen)
- [isOpen(const QString &) : bool](kwallet-wallet.md#isOpen-1)
- [keyDoesNotExist(const QString &, const QString &, const QString &) : bool](kwallet-wallet.md#keyDoesNotExist)
- [LocalWallet() : const QString](kwallet-wallet.md#LocalWallet)
- [mapList(bool \*) const : QMap\<QString, QMap\<QString, QString\>\>](kwallet-wallet.md#mapList)
- [NetworkWallet() : const QString](kwallet-wallet.md#NetworkWallet)
- [openWallet(const QString &, WId, KWallet::Wallet::OpenType) : KWallet::Wallet \*](kwallet-wallet.md#openWallet)
- [PasswordFolder() : const QString](kwallet-wallet.md#PasswordFolder)
- [passwordList(bool \*) const : QMap\<QString, QString\>](kwallet-wallet.md#passwordList)
- [readEntry(const QString &, QByteArray &) : int](kwallet-wallet.md#readEntry)
- [readMap(const QString &, QMap\<QString, QString\> &) : int](kwallet-wallet.md#readMap)
- [readPassword(const QString &, QString &) : int](kwallet-wallet.md#readPassword)
- [removeEntry(const QString &) : int](kwallet-wallet.md#removeEntry)
- [removeFolder(const QString &) : bool](kwallet-wallet.md#removeFolder)
- [renameEntry(const QString &, const QString &) : int](kwallet-wallet.md#renameEntry)
- [setFolder(const QString &) : bool](kwallet-wallet.md#setFolder)
- [users(const QString &) : QStringList](kwallet-wallet.md#users)
- [walletClosed()](kwallet-wallet.md#walletClosed)
- [walletList() : QStringList](kwallet-wallet.md#walletList)
- [walletName() const : const QString &](kwallet-wallet.md#walletName)
- [walletOpened(bool)](kwallet-wallet.md#walletOpened)
- [writeEntry(const QString &, const QByteArray &) : int](kwallet-wallet.md#writeEntry)
- [writeEntry(const QString &, const QByteArray &, KWallet::Wallet::EntryType) : int](kwallet-wallet.md#writeEntry-1)
- [writeMap(const QString &, const QMap\<QString, QString\> &) : int](kwallet-wallet.md#writeMap)
- [writePassword(const QString &, const QString &) : int](kwallet-wallet.md#writePassword)

KWallet::Wallet also inherits the members of [QObject](https://doc.qt.io/qt-6/qobject-members.html).
