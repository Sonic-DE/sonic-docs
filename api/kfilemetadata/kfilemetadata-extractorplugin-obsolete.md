---
title: "Obsolete Members for KFileMetaData::ExtractorPlugin"
description: "Deprecated members of KFileMetaData::ExtractorPlugin."
parent: "kfilemetadata/kfilemetadata-extractorplugin"
---

# Obsolete Members for KFileMetaData::ExtractorPlugin

**The following members of class [ExtractorPlugin](kfilemetadata-extractorplugin.md) are deprecated.** We strongly advise against using them in new code.

## Static Public Members

- [QStringList contactsFromString(const QString &string)](#contactsFromString) (deprecated in 6.12)
- [QDateTime dateTimeFromString(const QString &dateString)](#dateTimeFromString) (deprecated in 6.12)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[static, deprecated in 6.12\] QStringList ExtractorPlugin::contactsFromString(const QString &*string*) {#contactsFromString}

This function is deprecated since 6.12. We strongly advise against using it in new code.

Tries to split the string into names. It cleans up any superfluous words and removes extra junk such as curly braces

### \[static, deprecated in 6.12\] QDateTime ExtractorPlugin::dateTimeFromString(const QString &*dateString*) {#dateTimeFromString}

This function is deprecated since 6.12. We strongly advise against using it in new code.

Tries to extract a valid date time from the string provided.
