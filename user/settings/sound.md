---
title: Sound
description: Control the volume and routing of your audio devices and applications.
source_url: https://invent.kde.org/plasma/plasma-pa/-/blob/master/doc/kcontrol/plasma-pa/index.docbook
source_authors: [Sebastian Kügler]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-audio-applet-pulse e4b67cb7 (src/kcm, applet); read from code, not clicked through"
---

# Sound

This module controls the volume of devices and applications using the PulseAudio sound system: output devices, application channels, and input and recording devices. It also lets you route audio to and from specific devices.

## The module

- **Playback Devices:** Output devices, such as your headphone jack, subwoofer or a connected Bluetooth speaker.
- **Recording Devices:** Sound input devices connected to your computer, such as a microphone or headset.
- **Inactive Cards:** Sound cards that aren't currently in use, which **Show Inactive Devices** in the module's menu reveals.
- **Playback Streams:** Applications that play audio, such as your music player or web browser.
- **Recording Streams:** Applications recording from a device.

Each device can have a **Profile**, such as Analog Stereo or Digital Surround 5.1. For Bluetooth devices, you can switch to the high-fidelity A2DP profile here.

Testing a playback device shows its speakers. **Click on any speaker to test sound**. Testing a recording device shows its **Volume level**, with a **Sensitivity** slider, and lets you **Record** and **Play** a sample.

The menu at the top of the module also has:

- **Rename Devices…** to give your devices your own names. **Save** applies them, which restarts audio services and interrupts applications playing audio.
- **Configure Volume Controls…** to set the volume controls and on-screen displays.
- **Configure…**, with **Add virtual output device for simultaneous output on all local sound cards** and **Automatically switch all running streams when a new output becomes available**. These need the matching PulseAudio module.

## The widget

The Audio Volume widget loads automatically in the system tray. Click the speaker icon on your panel for a popup with volume sliders for your playback devices, which you can change individually.
