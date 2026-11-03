---
title: "UrlButton QML Type"
description: "A link to a URL or other remote resource."
---

# UrlButton QML Type

A link to a URL or other remote resource. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [LinkButton](qml-org-kde-kirigami-linkbutton.md)

## Detailed Description {#details}

[UrlButton](qml-org-kde-kirigami-urlbutton.md) will open the URL when left-clicked, tapped, or activated with the keyboard. It will show a context menu with a "Copy" action when right-clicked.

## Property Documentation {#property-documentation}

### \[since 6.11\] externalLink : bool {#externalLink-prop}

This property holds whether the URL is an external link.

External links will have a small icon on their right to show that the link goes to an external website.

default: `true`

This property was introduced in Qt 6.11.

### url : string {#url-prop}

This property holds the URL to open when clicked or tapped.

default: empty string; set a URL to make it work.
