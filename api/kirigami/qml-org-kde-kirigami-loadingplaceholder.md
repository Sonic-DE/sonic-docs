---
title: "LoadingPlaceholder QML Type"
description: "A placeholder for loading pages."
---

# LoadingPlaceholder QML Type

A placeholder for loading pages. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [PlaceholderMessage](qml-org-kde-kirigami-placeholdermessage.md)

## Detailed Description {#details}

Example usage:

```qml
Kirigami.Page {
    Kirigami.LoadingPlaceholder {
        anchors.centerIn: parent
    }
}
```

```qml
Kirigami.Page {
    Kirigami.LoadingPlaceholder {
        anchors.centerIn: parent
        determinate: true
        progressBar.value: loadingValue
    }
}
```

## Property Documentation {#property-documentation}

### \[default: false\] determinate : bool {#determinate-prop}

This property holds whether the loading message shows a determinate progress bar or not.

This should be true if you want to display the actual percentage when it's loading.

### progressBar : ProgressBar {#progressBar-prop}

This property holds a progress bar.

This should be used to access the progress bar to change its value.
