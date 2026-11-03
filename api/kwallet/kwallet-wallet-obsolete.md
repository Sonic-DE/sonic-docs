---
title: "Obsolete Members for KWallet::Wallet"
description: "Deprecated members of KWallet::Wallet."
parent: "kwallet/kwallet-wallet"
---

# Obsolete Members for KWallet::Wallet

**The following members of class [Wallet](kwallet-wallet.md) are deprecated.** We strongly advise against using them in new code.

## Public Functions

- [int lockWallet()](#lockWallet) (deprecated in 6.30)
- [void requestChangePassword(WId w)](#requestChangePassword) (deprecated in 6.30)
- [int sync()](#sync) (deprecated in 6.30)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[virtual, deprecated in 6.30\] int Wallet::lockWallet() {#lockWallet}

This function is deprecated since 6.30. We strongly advise against using it in new code.

This closes and locks the current wallet. It will disconnect all applications using the wallet.

Returns 0 on success, non-zero on error.

Use [closeWallet](kwallet-wallet.md#closeWallet)()

### \[virtual, deprecated in 6.30\] void Wallet::requestChangePassword(WId *w*) {#requestChangePassword}

This function is deprecated since 6.30. We strongly advise against using it in new code.

Request to the wallet service to change the password of the current wallet.

`w` The window id to associate any dialogs with. You can pass 0 if you don't have a window the password dialog should associate with.

Use [changePassword](kwallet-wallet.md#changePassword)

### \[virtual, deprecated in 6.30\] int Wallet::sync() {#sync}

This function is deprecated since 6.30. We strongly advise against using it in new code.

This syncs the wallet file on disk with what is in memory. You don't normally need to use this. It happens automatically on close.

Returns 0 on success, non-zero on error.

Not implemented.
