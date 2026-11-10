---
title: KDE Wallet
description: How SonicDE keeps your saved passwords, and how to set up, unlock and manage your wallet.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-keyring d0ad3f16 (README.md, src/kwalletsettings.kcfg, src/api/KWallet/org.kde.KWallet.xml, src/runtime/ksecretd/, src/runtime/kwalletd/, src/runtime/kwallet-query/, docs/kwallet-query/), sonic-frameworks-keyring-pam af1cb47 (pam_kwallet.c, CMakeLists.txt, README.txt), sonic-login-manager (data/pam/); written from the code, and the first-use dialog opened from a staged build on a private X server. Unlocking at login and the password steps have not been run"
---

# KDE Wallet

KDE Wallet keeps passwords and other secrets for your applications in an encrypted file, so you don't have to type them each time. For example, network folders and the SSH passphrase prompt can both save passwords in it.

It runs in the background and has no window of its own. You'll see it when an application needs a wallet that isn't open yet.

## Creating your wallet

The first time an application asks for a wallet, a **KDE Wallet Service** window asks you to create one. It's normally called `kdewallet`. Choose how to encrypt it:

- **Classic, blowfish encrypted file:** Protects the wallet with a password that you choose.
- **Use GPG encryption, for better protection:** Protects the wallet with one of your GPG keys. The list only shows keys you've given ultimate trust. If you have no suitable key, create one first. You can also use the classic type.

Click **Cancel** to refuse the application's request. No wallet is created, and the application has to manage without it.

If you chose the classic type, a second **KDE Wallet Service** window asks you to choose a password for the new wallet. Type it in **Password:** and again in **Verify:**. The **Password strength meter:** shows how hard the password would be to guess, and a weak one gets a **Low Password Strength** warning that lets you use it anyway or pick another. See [Password dialogs](../dialogs/password-dialogs.md) for more about these fields.

> **Warning:** Keep your wallet password safe. The contents are encrypted with it, so a forgotten password means losing what's in the wallet.

## Opening a locked wallet

When an application needs a classic wallet that isn't open yet, a **KDE Wallet Service** window says which wallet was requested and asks for its password. If the password is wrong, the window stays open, says the wallet couldn't be opened, and lets you try again. **Cancel** refuses the request, and the application carries on without the wallet.

If the application asking isn't the active window, the password window can end up hidden behind other windows. A notification then says that an application has requested to open the wallet, naming the wallet, with a **Switch there** button that brings the password window to the front. The notification closes by itself once that window is active.

If applications try more than five times in a row to use a wallet that isn't open to them, a message warns that there have been repeated failed attempts to gain access to a wallet and that an application may be misbehaving.

## Unlocking the wallet when you log in

If your wallet's password is the same as your account password, the wallet can open by itself when you log in, so you aren't asked again. The Sonic Login Manager is set up to do this through the `pam_kwallet5.so` module, as long as:

- The wallet is your default wallet, normally `kdewallet`.
- It's a classic wallet, because a GPG wallet doesn't use a password.
- You typed your password to log in. With automatic login there's no password to use, so the wallet asks you when it's first needed.

Changing your account password doesn't change the wallet's password. Change both, so they still match.

The module needs the `socat` program. It only acts in graphical sessions, and never for the root user.

## Changing a password or deleting a wallet

SonicDE doesn't include a wallet manager application, so these steps use the command line. KWalletManager from your distribution also works with your wallets, and adds a KDE Wallet page to System Settings.

To change a classic wallet's password, run the following command and follow the prompts:

```bash
qdbus6 org.kde.kwalletd6 /modules/kwalletd6 changePassword kdewallet 0 terminal
```

This only works with KDE Wallet's own service, not [another password store](#using-another-password-store). A GPG wallet's password belongs to its key, so use your GPG tools for that.

Your wallets are stored in `~/.local/share/kwalletd/`, as a `.kwl` file and a `.salt` file for each wallet. Copy both to back up a wallet. To delete one, close the applications using it and run:

```bash
qdbus6 org.kde.kwalletd6 /modules/kwalletd6 deleteWallet kdewallet
```

> **Warning:** Deleting a wallet deletes every password saved in it, and it can't be undone.

## Reading and writing secrets from scripts

`kwallet-query` lets shell scripts use a wallet. It can't create one: if the wallet doesn't exist, it says so and stops.

```bash
kwallet-query -l kdewallet                   # list the entries in the Passwords folder
kwallet-query -f "Network" -l kdewallet      # list the entries in another folder
kwallet-query -r "my entry" kdewallet        # print a secret
echo "secret" | kwallet-query -w "my entry" kdewallet   # save a secret read from standard input
```

| Option | What it does |
| --- | --- |
| `-l`, `--list-entries` | List the entries in the folder. |
| `-r`, `--read-password <entry>` | Print the secret stored under an entry. |
| `-w`, `--write-password <entry>` | Store a secret under an entry, read from standard input. This overwrites any secret already there. |
| `-f`, `--folder <folder>` | Use this folder instead of `Passwords`. |
| `-v`, `--verbose` | Print more information, to help with debugging. |

It exits with 0 on success, and with another code if something failed: 1 for a wallet that wasn't found, 2 for a wallet that couldn't be opened, 3 for a folder that wasn't found, and 4 for a failed read or write.

## Settings

With no settings page, the options are in `~/.config/kwalletrc`. The defaults suit most people. Log out and back in after you change this file.

| Group | Key | Default | What it does |
| --- | --- | --- | --- |
| `[Wallet]` | `Enabled` | `true` | Turns the whole wallet system on or off. |
| `[Wallet]` | `Default Wallet` | `kdewallet` | The wallet applications use. |
| `[Wallet]` | `Close When Idle` | `false` | Closes a wallet after it has gone unused for a while. |
| `[Wallet]` | `Idle Timeout` | `10` | How many minutes count as unused. |
| `[Wallet]` | `Use One Wallet` | `true` | Keeps local and network passwords in one wallet. |
| `[Wallet]` | `Local Wallet` | `localwallet` | The wallet for local passwords, when `Use One Wallet` is off. |
| `[org.freedesktop.secrets]` | `apiEnabled` | `true` | Lets applications use the wallet through the Secret Service interface. |

## Using another password store

Besides KDE Wallet's own interface, the wallet service provides the standard Secret Service interface, which many other applications use.

To keep your passwords in a different Secret Service provider, add this to `~/.config/kwalletrc`:

```ini
[KSecretD]
Enabled=false
```

To copy your existing wallets into that provider, also add the following. They're copied the next time the wallet service starts:

```ini
[Migration]
MigrateTo3rdParty=true
```

To use a GPG wallet with KDE Wallet's own service, add `no-allow-external-cache` to `~/.gnupg/gpg-agent.conf`.
