---
title: Creating a global theme package
description: Save your desktop's look as a global theme with the Global Theme Explorer.
source_url: https://userbase.kde.org/Plasma/Create_a_Global_Theme_Package
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-theme-sdk (lookandfeelexplorer/qml/Main.qml, qml/MetadataEditor.qml); read from code, not clicked through"
---

# Creating a global theme package

First, install the `sonic-theme-sdk` package, which gives you the Global Theme Explorer. The package name may differ between distributions. If your distribution doesn't list the Global Theme Explorer in the application launcher, start `lookandfeelexplorer` from a terminal and its window opens.

Once the Global Theme Explorer is open, the steps are straightforward:

1. Click the menu button.
2. Click **New Theme…**.
3. Fill in all the fields and click **OK**.

This creates a global theme based on your desktop's configuration under `~/.local/share/plasma/look-and-feel/`. It doesn't save the splash screen. It may also not create a `metadata.json` file for you.

Here is a basic template for a global theme's `metadata.json`:

```json
{
    "KPackageStructure": "Plasma/LookAndFeel",
    "KPlugin": {
        "Authors": [
            {
                "Email": "X",
                "Name": "X"
            }
        ],
        "Category": "Plasma Look And Feel",
        "Description": "X",
        "EnabledByDefault": true,
        "Id": "X",
        "License": "X",
        "Name": "X",
        "ServiceTypes": [
            "Plasma/LookAndFeel"
        ],
        "Version": "X.X",
        "Website": "X"
    },
    "X-KPackage-Dependencies": [
        "kns://aurorae.knsrc/api.kde-look.org/INSERTNUMBERIFAPPLICABLE",
        "kns://colorschemes.knsrc/api.kde-look.org/INSERTNUMBERIFAPPLICABLE",
        "kns://plasma-themes.knsrc/api.kde-look.org/INSERTNUMBERIFAPPLICABLE",
        "kns://icons.knsrc/api.kde-look.org/INSERTNUMBERIFAPPLICABLE",
        "kns://wallpaper.knsrc/api.kde-look.org/INSERTNUMBERIFAPPLICABLE"
    ]
}
```

Choose the theme in System Settings' [Global Theme](../settings/global-theme.md) module.
