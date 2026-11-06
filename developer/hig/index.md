---
title: Human Interface Guidelines
description: How to design applications that feel at home on SonicDE.
source_url: https://develop.kde.org/hig/
source_authors: [Andy Betts, Carl Schwan, Joshua Goins, Nate Graham, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-docs page list, adapted from the KDE Human Interface Guidelines"
---

# Human Interface Guidelines

Following these guidelines will help you build a beautiful and powerful application that feels at home on SonicDE and works well outside of it. Users will learn how to use your application quickly, accomplish their goals with ease, and encounter fewer issues requiring support.

This document covers SonicDE's design philosophy, common workflows and patterns, standard user interface conventions, and recommendations for platform integration.

The guidelines are adapted from the KDE Human Interface Guidelines. Silver's controls and icons grew out of KDE's Breeze, so the principles carry over directly, but many of the screenshots and icon examples come from the original document and show Breeze artwork and KDE application names.

## Why is good design so important?

Design determines how well something fulfills its functional purpose and how enjoyable it is to interact with. If either is lacking, the result will be frustrating. People won't want to use a poorly-designed application, and if forced to, they'll be resentful and spread negativity about it. Avoid this through good design!

Design involves targeted decisions and trade-offs that bring a project closer to its intended goals and usage paradigms. The best applications know which users and use cases they're targeting, and which ones they leave for others. It's better to succeed by focusing on what you can do well than to spread yourself thin and fail. Under-promise and over-deliver, never the reverse.

## Topics not covered

This document is a set of design guidelines, not instructions for implementing every specific component. While some technical guidance is provided, much more detail can be found in the components' own [API documentation](/docs/api), the [tutorials](../kirigami/setup-cpp.md), and the source code of existing SonicDE applications. It's more of a *what* and a *why*, not a *how*.

This document is not intended to be an ironclad law code. By learning and following the rules, you'll understand how to safely innovate within the guidelines, and when it can be appropriate to break them if it produces a superior result.

## Contributing

This is a living document, intended to be updated over time. The pages are written in Markdown and kept in the [sonic-docs repository](https://github.com/Sonic-DE/sonic-docs).

## Read the guidelines

- [What makes a SonicDE application?](app-design.md)
- [Simple by default](simple-by-default.md)
- [Powerful when needed](powerful-when-needed.md)
- [Layout and navigation](layout-and-navigation.md)
- [Displaying content](displaying-content.md)
- [Getting input](getting-input.md)
- [Communicating status changes](status-changes.md)
- [Text and labels](text-and-labels.md)
- [Icons](icons/index.md)
- [Accessibility and inclusiveness](accessibility.md)
