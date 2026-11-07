---
title: Vaults
description: Keep sensitive files in encrypted folders that you unlock only when you need them.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-vault a37e636 (README.md, kded/service.cpp, kded/engine/vault.cpp, kded/engine/fusebackend_p.cpp, kded/engine/backends/, kded/ui/, plasma/package/, fileitemplugin/); written from the code, and the creation wizard's first page opened from a staged build on a private X server. Creating, unlocking and locking a vault have not been run"
---

# Vaults

A vault is an encrypted folder. While it's locked, its files can't be read. When you unlock it with its password, the files appear in an ordinary folder, and you can use them with any application. Lock it again and that folder is empty.

Vaults are managed from the **Vaults** widget in the [System Tray](../desktop/system-tray.md). If you don't see it, look in the tray's hidden icons.

## Creating a vault

Click **Create a New Vault…** in the widget, then follow these steps:

1. Give the vault a **Vault name**.
2. Choose a password. There's no way to recover a forgotten password: if you forget it, your files are gone.
3. Check the two folders. **Encrypted data location** is where the encrypted files are kept, by default `~/.local/share/plasma-vault/<name>.enc`. **Mount point** is where your files appear when the vault is unlocked, by default `~/Vaults/<name>`. Both have to be empty.
4. Optionally, limit the vault to some [activities](#limiting-a-vault-to-activities) or make it [work offline only](#going-offline-while-a-vault-is-open).

New vaults use gocryptfs for encryption, which has to be installed on your system. FUSE's `fusermount3` or `fusermount` is also needed.

## Using a vault

Each vault in the widget has a button for **Unlock and Open**, or **Lock Vault** once it's unlocked. Expanding it shows more actions:

- **Unlock Vault:** Unlocks it without opening the file manager.
- **Show in File Manager:** Opens the unlocked vault's folder.
- **Forcefully Lock Vault:** Locks an unlocked vault even if applications are using its files.
- **Configure Vault…:** Changes the vault's settings.

To unlock a vault, enter its password when asked. If it can't be unlocked, the window shows why, and **Details…** gives the full error.

In [Ecco](ecco.md), you can also right-click a vault's mount point and choose **Unlock this Plasma Vault** or **Lock this Plasma Vault**.

A vault can't be locked normally while an application has one of its files open, and the widget shows which one is using it. Close that application and try again.

> **Warning:** **Forcefully Lock Vault** immediately kills every process using the vault, without letting it save anything. Any unsaved work in those applications is lost.

## Changing a vault's settings

The settings can only be changed while the vault is locked. If it's unlocked, the window offers **Lock the vault**.

- **General:** The **Vault name** and **Mount point**. The new mount point has to be empty.
- **Advanced:** The activity and offline settings below.
- **Delete:** Deletes the vault.

### Limiting a vault to activities

Select **Limit to the selected activities**, and choose them. The vault is then shown in the widget only in those activities, and it's locked automatically when you switch to any other.

### Going offline while a vault is open

**Go offline while this vault is open (switch off networking and bluetooth)** turns networking off through NetworkManager for as long as the vault is unlocked. The previous state is restored when you lock it.

> **Note:** Despite its label, this option doesn't turn off Bluetooth, so turn that off yourself if you need to.

## Deleting a vault

Open **Configure Vault…**, go to **Delete**, type the vault's name to confirm, click **Delete this vault**, and confirm again. The vault has to be locked.

> **Warning:** This permanently deletes the encrypted data and the mount point, along with every file in the vault. It can't be undone.

## Using an existing vault

If you already have encrypted data from EncFS, CryFS or gocryptfs, you can add it as a vault. The widget has no button for this, so start the import wizard with this command:

```bash
qdbus6 org.kde.kded6 /modules/plasmavault org.kde.plasmavault.requestImportVault
```

Then choose the encryption system, the encrypted data location and an empty mount point. You'll need the matching program installed, with version 1.9.1 or later of EncFS or 0.9.9 or later of CryFS.

If a CryFS vault was made with an older version, you're asked whether to upgrade it when you unlock it. After upgrading, older versions of CryFS can no longer open it.

## Locking and unlocking from the command line

Use the absolute path of the vault's encrypted data location:

```bash
qdbus6 org.kde.kded6 /modules/plasmavault org.kde.plasmavault.openVault "$HOME/.local/share/plasma-vault/Example.enc"
qdbus6 org.kde.kded6 /modules/plasmavault org.kde.plasmavault.closeVault "$HOME/.local/share/plasma-vault/Example.enc"
```

## Keeping files out of a locked mount point

While a vault is locked, its mount point is an ordinary empty folder, so a program could save files there by mistake, leaving them unencrypted. Newer gocryptfs vaults prevent this by locking the folder itself. To turn this on for an existing gocryptfs vault, create a `.directory` file in its mount point while the vault is locked:

```ini
[Desktop Entry]
Icon=folder-encrypted
X-KDE-LockVaultMountPoint=true
```

## Where the settings are kept

The list of vaults and their settings are in `~/.config/plasmavaultrc`. Back up your encrypted data location as well as this file, and remember that a backup is no use without the password.
