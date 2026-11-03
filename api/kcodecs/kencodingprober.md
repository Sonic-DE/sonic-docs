---
title: "KEncodingProber Class"
description: "Provides encoding detection(probe) capabilities."
---

# KEncodingProber Class

Provides encoding detection(probe) capabilities. [More...](#details)

- **Header:** `#include <KEncodingProber>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Codecs)`  
  `target_link_libraries(mytarget PRIVATE KF6::Codecs)`

[List of all members, including inherited members](kencodingprober-members.md)

## Public Types

- [enum KEncodingProber::ProberState](#ProberState-enum)
- [enum KEncodingProber::ProberType](#ProberType-enum)

## Public Functions

- [KEncodingProber(KEncodingProber::ProberType proberType = Universal)](#KEncodingProber)
- [float confidence() const](#confidence)
- [QByteArray encoding() const](#encoding)
- [KEncodingProber::ProberState feed(QByteArrayView data)](#feed)
- [void reset()](#reset)
- [void setProberType(KEncodingProber::ProberType proberType)](#setProberType)
- [KEncodingProber::ProberState state() const](#state)

## Static Public Members

- [QString nameForProberType(KEncodingProber::ProberType proberType)](#nameForProberType)
- [KEncodingProber::ProberType proberTypeForName(const QString &lang)](#proberTypeForName)

## Detailed Description {#details}

Probe the encoding of raw data only. In the case it can't find it, return the most possible encoding it guessed.

Always do Unicode probe regardless the [ProberType](kencodingprober.md#ProberType-enum)

Feed data to it several times with [feed](kencodingprober.md#feed)() until [ProberState](kencodingprober.md#ProberState-enum) changes to [FoundIt](kencodingprober.md#ProberState-enum)/[NotMe](kencodingprober.md#ProberState-enum), or [confidence](kencodingprober.md#confidence)() returns a value you find acceptable.

Intended lifetime of the object: one instance per [ProberType](kencodingprober.md#ProberType-enum).

Typical use:

```cpp
QByteArray data, moredata;
...
KEncodingProber prober(KEncodingProber::Chinese);
prober.feed(data);
prober.feed(moredata);
if (prober.confidence() > 0.6)
   encoding  = prober.encoding();
```

At least 256 characters are needed to change the [ProberState](kencodingprober.md#ProberState-enum) from Probing to [FoundIt](kencodingprober.md#ProberState-enum). If you don't have so many characters to probe, decide whether to accept the encoding it guessed so far according to the Confidence by yourself.

## Member Type Documentation {#member-type-documentation}

### enum KEncodingProber::ProberState {#ProberState-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KEncodingProber::FoundIt` | `0` | Sure find the encoding |
| `KEncodingProber::NotMe` | `1` | Sure not included in current [ProberType](kencodingprober.md#ProberType-enum)'s all supported encodings |
| `KEncodingProber::Probing` | `2` | Need more data to make a decision |

### enum KEncodingProber::ProberType {#ProberType-enum}

| Constant |   |
| --- | --- |
| `KEncodingProber::None` | `0` |
| `KEncodingProber::Universal` | `1` |
| `KEncodingProber::Arabic` | `2` |
| `KEncodingProber::Baltic` | `3` |
| `KEncodingProber::CentralEuropean` | `4` |
| `KEncodingProber::ChineseSimplified` | `5` |
| `KEncodingProber::ChineseTraditional` | `6` |
| `KEncodingProber::Cyrillic` | `7` |
| `KEncodingProber::Greek` | `8` |
| `KEncodingProber::Hebrew` | `9` |
| `KEncodingProber::Japanese` | `10` |
| `KEncodingProber::Korean` | `11` |
| `KEncodingProber::NorthernSaami` | `12` |
| `KEncodingProber::Other` | `13` |
| `KEncodingProber::SouthEasternEurope` | `14` |
| `KEncodingProber::Thai` | `15` |
| `KEncodingProber::Turkish` | `16` |
| `KEncodingProber::Unicode` | `17` |
| `KEncodingProber::WesternEuropean` | `18` |

## Member Function Documentation {#member-function-documentation}

### KEncodingProber::KEncodingProber(KEncodingProber::ProberType *proberType* = Universal) {#KEncodingProber}

Default [ProberType](kencodingprober.md#ProberType-enum) is Universal(detect all possible encodings)

### float KEncodingProber::confidence() const {#confidence}

Returns the confidence(sureness) of encoding it guessed so far (0.0 ~ 0.99), not very reliable for single byte encodings

### QByteArray KEncodingProber::encoding() const {#encoding}

Returns a [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) with the name of the best encoding it has guessed so far

### KEncodingProber::ProberState KEncodingProber::feed(QByteArrayView *data*) {#feed}

The main class method

Feed `data` to the prober

Returns the [ProberState](kencodingprober.md#ProberState-enum) after probing the fed data.

### \[static\] QString KEncodingProber::nameForProberType(KEncodingProber::ProberType *proberType*) {#nameForProberType}

map [ProberType](kencodingprober.md#ProberType-enum) to language string

`proberType` the proper type

Returns the language string

### \[static\] KEncodingProber::ProberType KEncodingProber::proberTypeForName(const QString &*lang*) {#proberTypeForName}

Returns the [ProberType](kencodingprober.md#ProberType-enum) for `lang` (e.g. proberTypeForName("Chinese Simplified") will return [KEncodingProber::ChineseSimplified](kencodingprober.md#ProberType-enum)

### void KEncodingProber::reset() {#reset}

reset the prober's internal state and data.

### void KEncodingProber::setProberType(KEncodingProber::ProberType *proberType*) {#setProberType}

change current prober's [ProberType](kencodingprober.md#ProberType-enum) and reset the prober

`proberType` the new type

### KEncodingProber::ProberState KEncodingProber::state() const {#state}

Returns the prober's current [ProberState](kencodingprober.md#ProberState-enum)
