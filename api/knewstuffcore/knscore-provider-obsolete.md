---
title: "Obsolete Members for KNSCore::Provider"
description: "Deprecated members of KNSCore::Provider."
parent: "knewstuffcore/knscore-provider"
---

# Obsolete Members for KNSCore::Provider

**The following members of class [Provider](knscore-provider.md) are deprecated.** We strongly advise against using them in new code.

## Public Types

- [\[deprecated in 6.9\] enum Provider::SearchPresetTypes](#SearchPresetTypes-enum)

## Obsolete Member Type Documentation {#obsolete-member-type-documentation}

### \[deprecated in 6.9\] enum Provider::SearchPresetTypes {#SearchPresetTypes-enum}

This enum is deprecated since 6.9. We strongly advise against using it in new code.

A helper to identify the kind of label and icon the search preset should have if none are found. Use KNSCore::SearchPreset::SearchPresetTypes

| Constant | Value |   |
| --- | --- | --- |
| `KNSCore::Provider::NoPresetType` | `0` |   |
| `KNSCore::Provider::GoBack` | `1` | Preset representing the previous search. |
| `KNSCore::Provider::Root` | `2` | Preset indicating a root directory. |
| `KNSCore::Provider::Start` | `3` | Preset indicating the first entry. |
| `KNSCore::Provider::Popular` | `4` | Preset indicating popular items. |
| `KNSCore::Provider::Featured` | `5` | Preset for featured items. |
| `KNSCore::Provider::Recommended` | `6` | Preset for recommended. This may be customized by the server per user. |
| `KNSCore::Provider::Shelf` | `7` | Preset indicating previously acquired items. |
| `KNSCore::Provider::Subscription` | `8` | Preset indicating items that the user is subscribed to. |
| `KNSCore::Provider::New` | `9` | Preset indicating new items. |
| `KNSCore::Provider::FolderUp` | `10` | Preset indicating going up in the search result hierarchy. |
| `KNSCore::Provider::AllEntries` | `11` | Preset indicating all possible entries, such as a crawlable list. Might be intense to load. |
