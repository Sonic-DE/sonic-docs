---
title: Sound
description: Control the volume and routing of your audio devices and applications.
source_url: https://invent.kde.org/plasma/plasma-pa/-/blob/master/doc/kcontrol/plasma-pa/index.docbook
source_authors: [Sebastian Kügler]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-audio-applet-pulse dfed5f3a (src/kcm, src/globalconfig.kcfg, applet); read from code, not clicked through"
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

Devices with more than one connector have a **Port:** list, for example to choose between headphones and speakers. Ports with nothing plugged in are marked as unplugged.

**Show Channels** shows a slider for each channel of a device, for example to balance the left and right speakers.

Testing a playback device shows its speakers. **Click on any speaker to test sound**. Testing a recording device shows its **Volume level**, with a **Sensitivity** slider, and lets you **Record** and **Play** a sample.

The menu at the top of the module also has:

- **Rename Devices…** to give your devices your own names. **Save** applies them, which restarts audio services and interrupts applications playing audio.
- **Configure Volume Controls…** to set the volume controls and on-screen displays. See [Volume controls](#volume-controls).
- **Configure…**, with **Add virtual output device for simultaneous output on all local sound cards** and **Automatically switch all running streams when a new output becomes available**. These need the matching PulseAudio module.

## Volume controls

**Configure Volume Controls…** has these settings:

- **Raise maximum volume:** Lets the volume go up to 150% instead of 100%. It's off by default.
- **Volume change step:** How much the volume changes each time you press a volume key or scroll over the widget. The default is 5%.
- **Play audio feedback for changes to:** **Audio volume** plays a short sound when you change the volume.
- **Show OSD popups for changes to:** Which changes show a message on the screen: **Audio volume**, **Microphone sensitivity**, **Mute state**, **Push to talk**, **Application starts using muted microphone** and **Default output device**.

All of these are on by default, apart from **Raise maximum volume**.

## The widget

The Audio Volume widget loads automatically in the system tray. Click the speaker icon on your panel for a popup with volume sliders for your playback devices, which you can change individually.

- The **Devices** and **Applications** tabs switch between your sound devices and the applications playing or recording sound.
- **Test…** next to a microphone opens a test where you can **Record** a sample and **Play** it back, and set its **Sensitivity**.
- **Raise maximum volume** at the bottom lets the volume go above 100%. A warning reminds you that using this for long can damage your speakers.
- **Keep open** keeps the popup open until you close it yourself.

Scroll over the icon to change the volume, and middle-click it to mute all sound, or unmute it.

Right-click the icon, or use **More actions** in the popup, for:

- **Force mute all playback devices** and **Force mute all input devices**
- **Show virtual devices**, which also lists virtual sound devices
- **Configure Audio Devices…**, which opens this module
