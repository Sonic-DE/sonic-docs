---
title: "KuitSetup Class"
description: "Class for modifying KUIT markup in a given domain."
---

# KuitSetup Class

Class for modifying KUIT markup in a given domain. [More...](#details)

- **Header:** `#include <KuitSetup>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS I18n)`  
  `target_link_libraries(mytarget PRIVATE KF6::I18n)`

[List of all members, including inherited members](kuitsetup-members.md)

## Public Functions

- [void setFormatForMarker(const QString &marker, Kuit::VisualFormat format)](#setFormatForMarker)
- [void setTagClass(const QString &tagName, Kuit::TagClass aClass)](#setTagClass)
- [void setTagPattern(const QString &tagName, const QStringList &attribNames, Kuit::VisualFormat format, const KLocalizedString &pattern, Kuit::TagFormatter formatter = nullptr, int leadingNewlines = 0)](#setTagPattern)

## Detailed Description {#details}

Not directly constructed, but obtained through [Kuit::setupForDomain](kuit.md#setupForDomain).

## Member Function Documentation {#member-function-documentation}

### void KuitSetup::setFormatForMarker(const QString &*marker*, Kuit::VisualFormat *format*) {#setFormatForMarker}

Set the default visual format for a given UI marker.

Giving "@\<major\>" for `marker` means to set the format only for standalone @\<major\> marker, while "@\<major\>:" (with trailing colon) means to set the same format for all @\<major\>:\<minor\> combinations.

Defined UI marker major/minor combinations are listed in the section uimark\_ctxt. If an UI marker combination outside of the defined is given as `marker`, it will be ignored.

Setting [Kuit::UndefinedFormat](kuit.md#VisualFormat-enum) as `format` means to fall back to default format for the given UI marker.

`marker` the UI marker

`format` the visual format

### void KuitSetup::setTagClass(const QString &*tagName*, Kuit::TagClass *aClass*) {#setTagClass}

Set the KUIT class of the tag.

`tagName` the name of the tag

`aClass` the KUIT tag class

### void KuitSetup::setTagPattern(const QString &*tagName*, const QStringList &*attribNames*, Kuit::VisualFormat *format*, const KLocalizedString &*pattern*, Kuit::TagFormatter *formatter* = nullptr, int *leadingNewlines* = 0) {#setTagPattern}

Set the formatting string for a tag with attributes combination.

If a new tag name is given, this effectively defines a new tag. The same holds for attribute names.

The pattern string `pattern` should contain placeholders for inserting the text and the attribute values. %1 will be replaced with the wrapped text, and %2 and upwards with attribute values in the order given by `attribNames`. Non markup-aware translation call with context (ki18nc) should be used to create the pattern string.

In addition to the pattern, a formatting function of the type TagFormatter can be given. This function receives the full markup parsing context, so that it can do whatever is necessary with the wrapped text. The result of this function is then substituted into the pattern. You can also give an empty pattern (as KLocalizedString()) together with the formatting function, in which case the function is assumed to do everything and no substitution is performed.

`tagName` the name of the tag

`attribNames` the names of the attributes (empty names are ignored)

`format` the target visual format

`pattern` the pattern string

`leadingNewlines` the number of new lines (\\n) to be maintained between any preceding text and the text wrapped with this tag (for formats where it matters)
