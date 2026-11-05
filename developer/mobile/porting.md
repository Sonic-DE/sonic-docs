---
title: Porting a new device
description: What a device needs to run the mobile interface, and how to add its settings.
source_url: https://develop.kde.org/docs/packaging/plasma-mobile/porting/
source_authors: [Alexey Andreyev, Ben Mordecai, Carl Schwan, Mikhail Zolotukhin, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-mobile-interface/devices (README, spec.conf, CMake install path) and envmanager/devicepresets.cpp, which reads the settings; the device preset section is added from those. plasma-mobile-envmanager exists on the stage but wasn't run against a device. The background on Android is from the source page."
---

# Porting a new device

The mobile interface supports devices running a mainline Linux kernel.

Many consumer mobile devices only support Android and don't work with the Linux kernel directly. [Android provides a hardware abstraction layer](https://source.android.com/docs/core/architecture) on top of the kernel. Even if a device's kernel sources are open, the Android environment uses [Bionic](https://android.googlesource.com/platform/bionic.git/+/HEAD/docs) rather than glibc or musl and is specific to that layer, so its drivers can't be used directly in a general Linux environment.

Some projects support devices without mainline Linux, such as [libhybris](https://github.com/libhybris/libhybris) and [Halium](https://halium.org/), which uses libhybris to provide a distribution-independent hardware abstraction. The upstream project dropped support for Halium in favor of mainline devices, and SonicDE doesn't support it either.

To port a device to mainline Linux, see [Porting to a new device](https://wiki.postmarketos.org/wiki/Porting_to_a_new_device) in the postmarketOS wiki.

## Adding the device's settings

Once the device runs, it can have a preset with settings specific to its hardware, such as the sizes and padding of the panels. Presets are files in `/usr/share/plasma-mobile-device-presets`, installed from the `devices/configs` folder of `sonic-mobile-interface`. `spec.conf` in the `devices` folder describes the settings, and any setting left out keeps its default value.

The file is named after the device's ID. The environment manager, `plasma-mobile-envmanager`, works this out from the device tree, and you can see the values it looks at with:

```bash
tr '\0' '\n' < /sys/firmware/devicetree/base/compatible
```

For example, that prints `oneplus,enchilada` and `qcom,sdm845` on a OnePlus 6.

If the ID isn't detected automatically, a distribution can set it in `/etc/xdg/plasmamobilerc`:

```ini
[Device]
device=oneplus,enchilada
```

To try a preset, install it and apply it to the running system:

```bash
plasma-mobile-envmanager --apply-settings
sonicshell -p org.kde.plasma.mobileshell --replace
```

## See also

- [Bionic (software)](https://en.wikipedia.org/wiki/Bionic_(software)) on Wikipedia
- [Hybris (software)](https://en.wikipedia.org/wiki/Hybris_(software)) on Wikipedia
- [Hybris](https://wiki.postmarketos.org/wiki/Hybris) in the postmarketOS wiki
