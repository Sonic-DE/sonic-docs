---
title: "KCountryFlagEmojiIconEngine Class"
description: "Provides emoji flags as icons This is a special icon engine that internally paints flags using emoji fonts. It provides access to country and region flags from the system emoji font. This class was introduced in Qt 6.0."
---

# KCountryFlagEmojiIconEngine Class

Provides emoji flags as icons This is a special icon engine that internally paints flags using emoji fonts. It provides access to country and region flags from the system emoji font. This class was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <KCountryFlagEmojiIconEngine>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS GuiAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::GuiAddons)`
- **Inherits:** [QIconEngine](https://doc.qt.io/qt-6/qiconengine.html)

[List of all members, including inherited members](kcountryflagemojiiconengine-members.md)

## Public Functions

- [KCountryFlagEmojiIconEngine(const QString &regionOrCountry)](#KCountryFlagEmojiIconEngine)
- [bool isNull()](#isNull)

## Static Public Members

- [void setGlobalDefaultFont(const QFont &font)](#setGlobalDefaultFont)

## Detailed Description {#details}

```cpp
auto l = new QLabel;
l->setMinimumSize(512, 512);
l->setPixmap(QIcon(new KCountryFlagEmojiIconEngine("AT")).pixmap(512, 512));
```

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KCountryFlagEmojiIconEngine::KCountryFlagEmojiIconEngine(const QString &*regionOrCountry*) {#KCountryFlagEmojiIconEngine}

Construct a new [KCountryFlagEmojiIconEngine](kcountryflagemojiiconengine.md) object Please note that regional flag support can be spotty in emoji fonts.

`regionOrCountry` either a ISO 3166-1 alpha-2 country code or a ISO 3166-2 region code (e.g. AT for Austria or GB-SCT for Scotland)

### \[override virtual\] bool KCountryFlagEmojiIconEngine::isNull() {#isNull}

Reimplements: [QIconEngine::isNull()](https://doc.qt.io/qt-6/qiconengine.html#isNull).

Check whether the internal emoji unicode sequence is null This does not necessarily mean that the pixmap output will be a valid flag - that entirely depends on the system's precise font configuration. Returns `true` when the construction of the emoji string failed Returns `false` when the construction of the emoji string succeeded

### \[static\] void KCountryFlagEmojiIconEngine::setGlobalDefaultFont(const QFont &*font*) {#setGlobalDefaultFont}

Set the Global Default Font object This is primarily useful for platform themes that wish to force a specific font being used. By default the "emoji" font family will be used. Forcing a specific font and making sure it is available as runtime requirement is the most reliable way to ensure that flag support is working regardless of system configuration.

`font` the default font to use
