---
title: "KI18n C++ Classes"
description: "Advanced internationalization framework."
---

# KI18n C++ Classes

Advanced internationalization framework. [More...](#details)

## Namespaces {#namespaces}

- [KLocalization](klocalization.md): Namespace containing helpers for localization.
- [Kuit](kuit.md): Global constants and functions related to KUIT markup.

## Classes {#classes}

- [KLazyLocalizedString](klazylocalizedstring.md): Lazy-initialized variant of KLocalizedString.
- [KLocalizedString](klocalizedstring.md): Class for producing and handling localized messages.
- [KLocalizedTranslator](klocalizedtranslator.md): A QTranslator using KLocalizedString for translations.
- [KuitSetup](kuitsetup.md): Class for modifying KUIT markup in a given domain.

## Detailed Description {#details}

KI18n provides functionality for internationalizing user interface text in applications, based on the GNU Gettext translation system. It wraps the standard Gettext functionality, so that the programmers and translators can use the familiar Gettext tools and workflows.

KI18n provides additional functionality as well, for both programmers and translators, which can help to achieve a higher overall quality of source and translated text. This includes argument capturing, customizable markup, and translation scripting.
