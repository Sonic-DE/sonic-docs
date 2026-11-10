---
title: Region & Language
description: Set your preferred languages and formats.
source_url: https://invent.kde.org/plasma/plasma-workspace/-/blob/master/doc/kcontrol/region_language/index.docbook
source_authors: [Mike McBride, Krishna Tateneni, Han Young]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-workspace e4f0096493 (kcms/region_language); read from code, not clicked through"
---

# Region & Language

This module sets your preferred languages and formats for the desktop and applications.

In most cases, you can simply select the language and all the options are set accordingly. The desktop and its applications are written in American English and translated into many languages by teams of volunteers. These translations need to be installed before you can use them.

> [!NOTE]
> Make sure you've installed the language packages or translations for the languages you want. Since the desktop is built on the Qt libraries, you also need Qt's translations for a fully translated interface.

Each entry shows an example of what its setting looks like. As well as numbers, you can see how currency values, dates and times are displayed. When you change a setting, you see the effect before you apply it.

## Languages

**Modify…** on the language entry shows your languages. **Add More…** lists the available languages and shows your selected one first. If it shows “No Language Configured”, you're using the language set by the system. If the language you want isn't listed, install it using the usual method for your system. Add languages in the order you want to see them in your applications.

With only one language set, **Change Language** next to it picks a different one. With several, you can remove a language with the remove button next to it, and change the order of preference by dragging a language by its handle or with **Move to top**.

If English is at the top with other languages below it, the module warns that some applications won't behave as expected. To use your system in English, remove all other languages.

## Formats

If you need different individual settings, select a locale for **Numbers**, **Time**, **Currency**, **Measurements**, **Paper Size**, **Address**, **Name** or **Phone number**.

**Data and Storage Sizes** chooses how sizes are shown: **Binary** in kibibytes (KiB), mebibytes (MiB) and gibibytes (GiB), the older **Binary** in kilobytes (KB), megabytes (MB) and gigabytes (GB), or **Decimal** in kilobytes (kB), megabytes (MB) and gigabytes (GB).

Changing a language automatically changes the settings for numbers, currency and so on to the matching country or region. The configuration file is `~/.config/plasma-localerc`.

Changes take effect the next time you log in, and the module offers **Restart now**, which asks whether to restart the computer. On some systems the module first generates the locale files it needs, and tells you when that's finished.
