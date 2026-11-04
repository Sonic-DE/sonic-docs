---
title: "SignOn Plugin Development"
description: "The interface of Single Sign On authentication plugins."
---

# SignOn Plugin Development

The interface of Single Sign On authentication plugins.

This library contains the interface definition and a few classes that should be used when implementing an authentication plugin for the Single Sign On framework.

- [AuthPluginInterface](authplugininterface.md): the interface every authentication plugin implements.
- [SignOn::UiSessionData](signon-uisessiondata.md): a dictionary of data exchanged between the plugin and the [SignOn](signon-sub-signonplugins.md) UI.

All classes but [AuthPluginInterface](authplugininterface.md) reside in the [SignOn](signon-sub-signonplugins.md) namespace.

## Using the Module {#using-the-module}

The library ships with a pkg-config file, `signon-plugins.pc`; its `plugindir` variable is where signond loads plugins from.

## API Reference {#api-reference}

- [SignOn Plugin C++ Classes](signonplugins-module.md)
