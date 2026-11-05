---
title: About page branding
description: Add your distribution's details to the About this System page.
source_url: https://develop.kde.org/docs/administration/kinfocenter/
source_authors: [Blagovest Petrov, Carl Schwan, Harald Sitter, Kristen McWilliam, Nicolas Fella, Thiago Sueto, Yvan Masson, shenleban tongying]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "kcms/about-distro in sonic-system-info: main.cpp, ThirdPartyEntry.cpp and the example file. Read from code; not run."
---

# About page branding

The "About this System" page in System Settings shows information about your system. It gives distributions a way to show their branding, through a simple file in the [Desktop Entry format](https://specifications.freedesktop.org/desktop-entry-spec/latest/).

## Software entries

You can add custom entries at the bottom of the page's software section.

Add a file `/etc/xdg/scm-about-distrorc`, which applies to all users the next time the page is opened. A file at `~/.config/scm-about-distrorc` applies to only one user.

In the `[General]` section, add an `ExtraSoftwareData` entry with a semicolon-separated list of scripts to run when the page opens.

Each script should output at least two lines: one for the label, ending in a colon for consistency with the other entries, and another for its value.

For translations, check the `LANGUAGE` environment variable when the script runs, and keep the English text as the default output. The page's process stops with a fatal error if an entry points to a script that doesn't output two lines, so test your scripts.

For example:

```ini
[General]
ExtraSoftwareData=/usr/bin/whichpartition;/usr/bin/whatsmyname
```

With `/usr/bin/whichpartition` giving this output:

```text
Partition:
A
```

And `/usr/bin/whatsmyname` giving this:

```text
Username:
acoolusername
```

## Showing the build

Another option in this file is `ShowBuild`:

```ini
[General]
ShowBuild=true
```

The page then shows the `BUILD_ID` from `/etc/os-release` next to the version. For example, instead of `SteamOS 3.5` it would say `SteamOS 3.5 Build: 20230201.1000`.

## Other options

The same section can also set `LogoPath`, `Website`, `Name`, `Version` and `Variant`, and `UseOSReleaseVersion`, which controls whether the `VERSION` from `/etc/os-release` is used. An [example file](https://github.com/Sonic-DE/sonic-system-info/blob/master/kcms/about-distro/example/scm-about-distrorc.ex) shows them.
