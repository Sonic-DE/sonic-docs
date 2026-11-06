---
title: Browser integration
description: Make Firefox and Chromium-based browsers work with your desktop.
source_url: https://userbase.kde.org/Plasma-browser-integration
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-browser-integration (CMakeLists.txt, extension/manifest.json, host/), sonic-workspace (krunner desktop file); read from code, not clicked through"
---

# Browser integration

Browser integration is a suite of features that make Firefox, Chrome and Chromium-based browsers work with your desktop:

- Downloads appear in the notification popup, just like file transfers in [Ecco](ecco.md).
- The Media Controls widget can mute and skip videos and music playing in the browser.
- Browser tabs can be opened directly from [KRunner](../desktop/krunner.md), with the Alt+Space shortcut.
- If you have KDE Connect installed, you can send a link to your phone. It isn't part of SonicDE.

To enable browser integration, add the extension from your browser's add-on store.

## How to install

Before installing the browser extension, you need the part that runs on your computer, the `sonic-browser-integration` package. The package name may differ between distributions.

Then install the extension like any other. It's called Plasma Integration, because it's the same extension KDE publishes for its desktop:

- [Plasma Integration for Firefox](https://addons.mozilla.org/en-US/firefox/addon/plasma-integration/)
- [Plasma Integration for Google Chrome](https://chrome.google.com/webstore/detail/plasma-integration/cimiefiiaegbelhefglklhhakcgmhkai)
