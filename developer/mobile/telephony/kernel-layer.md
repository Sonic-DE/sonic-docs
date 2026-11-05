---
title: Kernel layer
description: How a phone's modem is connected and exposed by the Linux kernel.
source_url: https://develop.kde.org/docs/packaging/plasma-mobile/telephony/kernel-layer/
source_authors: [Alexey Andreyev, Carl Schwan, Mikhail Zolotukhin]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "Nothing in SonicDE's code: this is general background on hardware and the Linux kernel, from the source page, and wasn't tested on a device."
---

# Kernel layer

The kernel side isn't part of SonicDE, but an overview helps in understanding the higher levels of the stack.

The mobile interface supports devices running a mainline Linux kernel. See [Porting a new device](../porting.md).

Mobile devices have a component called the WWAN modem. In a modular system, the modem is a distinct submodule, typically soldered to the board or mounted in an mPCIe slot, where it uses only the embedded USB bus and power. In modern proprietary phone SoCs, the modem may be a couple of chips rather than a distinct module and may use other interfaces. In many smartphone SoCs, part of the modem has been a processor core on the same die as the application processor, communicating through proprietary on-chip interfaces and shared memory.

Among other things, such as USB and voice support, the kernel needs to support the protocols of the Radio Interface Layer (RIL). Depending on the modem's manufacturer, this could be a serial (TTY) interface in legacy mode with AT commands, a more modern protocol such as MBIM or QRTR with QMI commands, or something else.

For example, the [PinePhone](https://wiki.pine64.org/wiki/PinePhone) has a Quectel EG25 modem connected to its main ARM SoC by USB. The modem can be accessed [with QMI commands over USB](https://github.com/torvalds/linux/blob/master/drivers/net/usb/qmi_wwan.c), thanks to support in the mainline kernel.

[Mainlined SDM845 smartphones](https://wiki.postmarketos.org/wiki/SDM845_Mainlining) such as the OnePlus 6 have a modem exposed as a remote processor of the SoC. It also works with QMI, through the [QRTR](https://github.com/torvalds/linux/blob/master/net/qrtr/Kconfig) interface, and is supported by the kernel.

Kernel drivers don't handle a protocol such as QMI themselves. They export it as a character device, so that [userland](system-daemon/index.md) can handle it.

## See also

- [Wireless WAN](https://en.wikipedia.org/wiki/Wireless_WAN) on Wikipedia
- [Radio Interface Layer](https://en.wikipedia.org/wiki/Radio_Interface_Layer) on Wikipedia
- [Qualcomm MSM Interface](https://en.wikipedia.org/wiki/Qualcomm_MSM_Interface) on Wikipedia
- [Upstreaming support for Qualcomm PCIe modems](https://www.linaro.org/blog/upstreaming-support-for-qualcomm-pcie-modems/) at Linaro
