---
title: "KNSCore::Entry::DownloadLinkInformation Struct"
description: "Describes a download link option for an Entry."
---

# KNSCore::Entry::DownloadLinkInformation Struct

Describes a download link option for an Entry. [More...](#details)

- **Header:** `#include <DownloadLinkInformation>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NewStuff)`  
  `target_link_libraries(mytarget PRIVATE KF6::NewStuff)`

[List of all members, including inherited members](knscore-entry-downloadlinkinformation-members.md)

## Detailed Description {#details}

*See also* [appendDownloadLinkInformation](knscore-entry.md#appendDownloadLinkInformation), [downloadLinkInformationList](knscore-entry.md#downloadLinkInformationList)

## Member Variable Documentation {#member-variable-documentation}

### QString DownloadLinkInformation::descriptionLink {#descriptionLink-var}

Link to intermediary description.

### QString DownloadLinkInformation::distributionType {#distributionType-var}

OCS Distribution Type, this is for which OS the file is useful.

### int DownloadLinkInformation::id {#id-var}

Unique integer representing the download number in the list.

### bool DownloadLinkInformation::isDownloadtypeLink {#isDownloadtypeLink-var}

TODO

### QString DownloadLinkInformation::name {#name-var}

Displayed name.

### QString DownloadLinkInformation::priceAmount {#priceAmount-var}

Price formatted as a string.

### quint64 DownloadLinkInformation::size {#size-var}

Size in kilobytes.

### QStringList DownloadLinkInformation::tags {#tags-var}

Variety of tags that can represent mimetype or url location.
