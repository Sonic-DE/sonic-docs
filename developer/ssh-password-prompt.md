---
title: SSH password prompt
description: Use ksshaskpass to ask for SSH passphrases in a window, and optionally save them in KDE Wallet.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-ssh-password-prompt 2e53144 (README, src/main.cpp, doc/man-ksshaskpass.1.docbook); written from the code, and the passphrase and confirmation prompts opened from a staged build on a private X server. Saving a passphrase and a real ssh-add run have not been tried"
---

# SSH password prompt

`ksshaskpass` shows a window when an SSH program needs a passphrase, a password or a yes-or-no answer, and no terminal is available. It can also save passphrases, so you only type them once.

You don't start it directly. OpenSSH runs it for you, once it knows about it.

## Setting it up

SonicDE doesn't set this up for you. OpenSSH uses the program named in the `SSH_ASKPASS` environment variable when it has no terminal. To load your key when you log in, make a script containing the following, make it executable, and add it in [Autostart](../user/settings/autostart.md):

```bash
#!/bin/sh
SSH_ASKPASS=ksshaskpass ssh-add < /dev/null
```

This needs an SSH agent to be running in your session.

## The prompts

For a passphrase or password, the **SSH Credentials** window shows what's being asked for, and has a **Password** field.

When the program recognizes which key or account is being asked for, it also offers **Remember password**:

- Tick it to save the passphrase in your password manager, normally [KDE Wallet](../user/applications/kde-wallet.md). Next time, it's used without asking.
- If a saved passphrase turns out to be wrong, you're asked again. Untick the box then to delete the saved one.

For a yes-or-no question, the window has **Accept** and **Cancel** buttons. When OpenSSH asks whether to trust an unknown server, the **Unknown SSH Host Key** window has **Yes** and **No** instead. Check the key's fingerprint before you answer **Yes**.

## Using it from a script

`ksshaskpass` prints your answer to standard output. You can pass the text to show as its argument:

```bash
ksshaskpass "Enter the passphrase for the backup key:"
```

Set `SSH_ASKPASS_PROMPT=confirm` for a yes-or-no question, or `SSH_ASKPASS_PROMPT=none` to only show a message.
