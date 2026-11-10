---
title: Splash Screen
description: View and choose the splash screen shown when you log in.
source_url: https://invent.kde.org/plasma/plasma-desktop/-/blob/master/doc/kcontrol/splashscreen/index.docbook
source_authors: [Anne-Marie Mahfouf]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-desktop-interface (kcms/ksplash), sonic-silver (look-and-feel/org.kde.silver.desktop/contents/splash); read from code, not clicked through"
---

# Splash Screen

This module lets you view and select splash screen themes.

You can see previews of the installed splash screens, with the current one highlighted. Choose **None** if you don't want a splash screen.

SonicDE's own splash screen is **Silver**, which is used unless you choose another. It shows the Sonic logo and a spinning busy indicator, with "Welcome to SonicDE" and the SonicDE logo in the bottom-right corner. All the [Silver global themes](global-theme.md#the-silver-themes) use it.

![The splash screen module](images/splash-screen/splash-main.png)

Hover over a preview to reveal its buttons:

- **Preview splash screen** shows it in action.
- **Remove splash screen** deletes one you've installed. You can't delete system-installed splash screens or the active one.

**Get New…** shows a list of themes to download, which needs an Internet connection. Clicking **Install** on one installs it locally, and it's available as soon as you close the dialog. Click **Apply** to make it your current splash screen.

![Installing a new splash screen](images/splash-screen/get-new-theme.png)
