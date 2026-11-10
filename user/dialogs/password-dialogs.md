---
title: Password dialogs
description: The windows that ask for a user name and password, or for a new password, in SonicDE applications.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-widgets-addons (src/kpassworddialog.ui, kpassworddialog.cpp, kpasswordlineedit.cpp, knewpasswordwidget.ui, knewpasswordwidget.cpp, knewpassworddialog.cpp), sonic-frameworks-io (src/kpasswdserver/kpasswdserver.cpp); written from the code, not clicked through"
---

# Password dialogs

SonicDE uses the same two windows wherever it needs a password: one to ask for a password you already have, and one to choose a new password.

## Asking for a password

This window appears, for example, when you open a network folder that needs you to log in. It says what the password is for, and shows the fields that place needs:

- **Username:** Your user name there. It may already be filled in.
- **Domain:** The domain or workgroup, for places that use one, such as some Windows shares.
- **Password:** Your password.
- **Remember password:** Saves the password in your [KDE Wallet](../applications/kde-wallet.md), so you aren't asked the next time. It's only offered when the wallet is turned on.

Some places let you connect without an account. Then you can choose between **No password, use anonymous (or guest) login** and **Use this password:**.

Click **OK** to log in, or **Cancel** to give up.

## Choosing a new password

This window appears when you set a new password, for example for a new [KDE Wallet](../applications/kde-wallet.md).

- **Password:** Type the new password.
- **Verify:** Type it again. A message below says whether the two match.
- **Password strength meter:** Shows how hard the password would be to guess. Longer passwords that mix upper- and lower-case letters, numbers and symbols are stronger.

**OK** stays unavailable until both fields match. If the password is weak, a **Low Password Strength** warning gives tips to make it stronger and asks whether to use it anyway. Click **Yes** to use it, or **No** to choose another.

## Showing the password

Password fields hide what you type. Once you start typing, an eye button appears at the end of the field: click it to show the password, and again to hide it. You can also right-click the field and choose **Show Password** or **Hide Password**.
