---
title: "DownloadAction QML Type"
description: "An action for with bindings for managing the download of a piece of media."
---

# DownloadAction QML Type

An action for with bindings for managing the download of a piece of media. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.labs.components
- Inherits: [Action](../kirigami/qml-org-kde-kirigami-action.md)

## Detailed Description {#details}

The action provides properties to help track progress but is up to the action representation to respond to them. The onTriggered() signal should be used to perform the download action itself.

The most common use case for this is where a custom URI scheme is used that a QML media component can't handle on it's own.

## Property Documentation {#property-documentation}

### \[read-only\] completed : bool {#completed-prop}

Whether the download has completed.

### \[default: -1\] progress : real {#progress-prop}

The download progress between 0% and 100%.

### \[read-only\] started : bool {#started-prop}

Whether the download has started.
