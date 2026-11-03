---
title: "DialogHeader QML Type"
description: "Base for a header, to be used as the header: item of a Dialog."
---

# DialogHeader QML Type

Base for a header, to be used as the header: item of a Dialog. [More...](#details)

- Import Statement: import org.kde.kirigami.dialogs
- Inherits: [Control](https://doc.qt.io/qt-6/qml-qtquick-controls-control.html)

## Detailed Description {#details}

Provides appropriate padding and a bottom separator when the dialog's content is scrollable.

Chiefly useful as the base element of a custom header. Example usage for this:

```qml
import QtQuick
import org.kde.kirigami as Kirigami
import org.kde.kirigami.dialogs as KD

Kirigami.Dialog {
    id: myDialog

    title: i18n("My Dialog")

    standardButtons: Kirigami.Dialog.Ok | Kirigami.Dialog.Cancel

    header: KDialogs.DialogHeader {
        dialog: myDialog
        contentItem: [...]
    }
    [...]
}
```

## Property Documentation {#property-documentation}

### \[required\] dialog : Dialog {#dialog-prop}

This property points to the parent dialog, some of whose properties need to be available here.
