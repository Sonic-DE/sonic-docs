---
title: "DialogHeaderTopContent QML Type"
description: "Standard top content for a Dialog, including header text and an optional close button."
---

# DialogHeaderTopContent QML Type

Standard top content for a Dialog, including header text and an optional close button. [More...](#details)

- Import Statement: import org.kde.kirigami.dialogs
- Inherits: [RowLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-rowlayout.html)

## Detailed Description {#details}

Provides appropriate padding and a bottom separator when the dialog's content is scrollable.

Chiefly useful as the first item in a \`[ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html)\` inside a custom header, for when you want a custom header that only consists of extra content, and does not need to override the standard content. Example usage for a this:

```qml
import QtQuick
import QtQuick.Layouts
import org.kde.kirigami as Kirigami
import org.kde.kirigami.dialogs as KDialogs

Kirigami.Dialog {
    id: myDialog

    title: i18n("My Dialog")

    standardButtons: Kirigami.Dialog.Ok | Kirigami.Dialog.Cancel

    header: KDialogs.DialogHeader {
        dialog: myDialog

        contentItem: ColumnLayout {
            Spacing: Kirigami.Units.smallSpacing

            KDialogs.DialogHeaderTopContent {
                dialog: myDialog
            }

            [...]
        }
    }
    [...]
}
```

## Property Documentation {#property-documentation}

### \[required\] dialog : Dialog {#dialog-prop}

This property points to the parent dialog, some of whose properties need to be available here.

### showCloseButton : bool {#showCloseButton-prop}

Whether the close button should be visible.

Defaults to `true`.
