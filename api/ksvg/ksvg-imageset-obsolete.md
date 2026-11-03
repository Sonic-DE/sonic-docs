---
title: "Obsolete Members for KSvg::ImageSet"
description: "Deprecated members of KSvg::ImageSet."
parent: "ksvg/ksvg-imageset"
---

# Obsolete Members for KSvg::ImageSet

**The following members of class [ImageSet](ksvg-imageset.md) are deprecated.** We strongly advise against using them in new code.

## Properties

- [\[read-only, deprecated in 6.21\] useGlobalSettings : bool](#useGlobalSettings-prop)

## Public Functions

- [KPluginMetaData metadata() const](#metadata) (deprecated in 6.21)
- [void setCacheLimit(int kbytes)](#setCacheLimit) (deprecated in 6.21)
- [void setUseGlobalSettings(bool useGlobal)](#setUseGlobalSettings) (deprecated in 6.20)
- [bool useGlobalSettings() const](#useGlobalSettings) (deprecated in 6.21)

## Obsolete Property Documentation {#obsolete-property-documentation}

### \[read-only, deprecated in 6.21\] useGlobalSettings : bool {#useGlobalSettings-prop}

This property is deprecated since 6.21. We strongly advise against using it in new code.

Not used.

**Access functions:**

- `bool` **[useGlobalSettings](ksvg-imageset-obsolete.md#useGlobalSettings)**() const

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[deprecated in 6.21\] KPluginMetaData ImageSet::metadata() const {#metadata}

This function is deprecated since 6.21. We strongly advise against using it in new code.

This method returns the plugin metadata for this theme.

Metadata contains information such as name, description, author, website, and url.

Not used

### \[deprecated in 6.21\] void ImageSet::setCacheLimit(int *kbytes*) {#setCacheLimit}

This function is deprecated since 6.21. We strongly advise against using it in new code.

This method sets the maximum size of the cache (in kilobytes).

If cache gets bigger than the limit, then some entries are removed. Setting cache limit to 0 disables automatic cache size limiting.

Note that the cleanup might not be done immediately, so the cache might temporarily (for a few seconds) grow bigger than the limit.

Not used

### \[deprecated in 6.20\] void ImageSet::setUseGlobalSettings(bool *useGlobal*) {#setUseGlobalSettings}

This function is deprecated since 6.20. We strongly advise against using it in new code.

This method sets whether the theme should follow the global settings or use application-specific settings.

`useGlobal` pass in true to follow the global settings

Not used

*See also* [useGlobalSettings](ksvg-imageset-obsolete.md#useGlobalSettings)()

### \[deprecated in 6.21\] bool ImageSet::useGlobalSettings() const {#useGlobalSettings}

This function is deprecated since 6.21. We strongly advise against using it in new code.

This method returns whether the global settings are followed.

If application-specific settings are being used, it returns `false`.

Not used

> **Note:** Getter function for property [useGlobalSettings](ksvg-imageset-obsolete.md#useGlobalSettings-prop).

*See also* [setUseGlobalSettings](ksvg-imageset-obsolete.md#setUseGlobalSettings)()
