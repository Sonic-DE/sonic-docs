---
title: Form layouts
description: Easily create attractive interaction areas with Kirigami FormLayouts.
source_url: https://develop.kde.org/docs/getting-started/kirigami/components-formlayouts/
source_authors: [Carl Schwan, Claudio Cambra, Jeongu Kim, Mikhail Zolotukhin, Nicolas Fella, Phu Nguyen, Thiago Sueto, Yuri Chornoivan]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "Kirigami FormLayout.qml and FormData (formlayoutattached.h); examples run with the qml tool, plus label-position measurements with and without labelAlignment"
---

# Form layouts

[Kirigami.FormLayout](/docs/api/kirigami/qml-org-kde-kirigami-layouts-formlayout) components make it easy to create forms that follow the [Human Interface Guidelines](../hig/index.md). They are ideal for settings dialogs and for large groups of related controls and input fields.

With enough space, form layouts take up two columns. The left column holds the labels of the form's child components, and the right column holds the components themselves. In narrower windows (or on mobile), forms become a single vertical column, with each label placed above its component.

## Simple form

[Kirigami.FormLayout](/docs/api/kirigami/qml-org-kde-kirigami-layouts-formlayout) components are used much like [Qt Quick Layouts](https://doc.qt.io/qt-6/qtquicklayouts-index.html) such as [ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html) or [RowLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-rowlayout.html). The child components are arranged automatically according to the space available to the form layout.

Children of a [Kirigami.FormLayout](/docs/api/kirigami/qml-org-kde-kirigami-layouts-formlayout) have an attached property named [Kirigami.FormData.label](/docs/api/kirigami/qml-org-kde-kirigami-layouts-formdata#label-attached-prop), which sets the label shown for that child.

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    pageStack.initialPage: Kirigami.Page {

        Kirigami.FormLayout {
            anchors.fill: parent

            Controls.TextField {
                Kirigami.FormData.label: "TextField 1:"
            }
            Controls.TextField {
                Kirigami.FormData.label: "TextField 2:"
            }
            Controls.TextField {
                Kirigami.FormData.label: "TextField 3:"
            }
        }
    }
}
```

## Sections and separators

Form layouts can also be divided into sections. To start a section, set a child component's [Kirigami.FormData.isSection](/docs/api/kirigami/qml-org-kde-kirigami-layouts-formdata#isSection-attached-prop) to `true`. This gives the component some extra margin at the top to mark the start of the new section.

[Kirigami.Separator](/docs/api/kirigami/qml-org-kde-kirigami-primitives-separator) components are best suited for starting new sections. A separator draws a thin horizontal line marking the end of a section. If you'd rather not have a line between sections, use a plain QML [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html) instead. You could also set [Kirigami.FormData.isSection](/docs/api/kirigami/qml-org-kde-kirigami-layouts-formdata#isSection-attached-prop) on any other component, but this isn't recommended.

On a component whose [Kirigami.FormData.isSection](/docs/api/kirigami/qml-org-kde-kirigami-layouts-formdata#isSection-attached-prop) is `true`, the text of its [Kirigami.FormData.label](/docs/api/kirigami/qml-org-kde-kirigami-layouts-formdata#label-attached-prop) is shown as the section's header text. This doesn't work well with every component, hence the recommendation to use [Kirigami.Separator](/docs/api/kirigami/qml-org-kde-kirigami-primitives-separator) or [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html) components where you want header text.

The header text is larger than the normal label text and gives users a clear visual cue of what the section is about.

```qml
Kirigami.FormLayout {
    anchors.fill: parent

    Controls.TextField {
        Kirigami.FormData.label: "TextField 1:"
    }
    Controls.TextField {
        Kirigami.FormData.label: "TextField 2:"
    }
    Controls.TextField {
        Kirigami.FormData.label: "TextField 3:"
    }
    Kirigami.Separator {
        Kirigami.FormData.isSection: true
        Kirigami.FormData.label: "New Section!"
    }
    ColumnLayout {
        Kirigami.FormData.label: "Radio buttons"
        Controls.RadioButton {
            text: "Radio 1"
            checked: true
        }
        Controls.RadioButton {
            text: "Radio 2"
        }
        Controls.RadioButton {
            text: "Radio 3"
        }
    }
    Item {
        Kirigami.FormData.isSection: true
        Kirigami.FormData.label: "Another Section! (lineless though)"
    }
    Controls.TextField {
        Kirigami.FormData.label: "TextField 4:"
    }
    Controls.TextField {
        Kirigami.FormData.label: "TextField 5:"
    }
    Controls.TextField {
        Kirigami.FormData.label: "TextField 5:"
    }
}
```

## Forcing a desktop or mobile layout

If you want your form layout to look the same whatever the application's environment, use the [wideMode](/docs/api/kirigami/qml-org-kde-kirigami-layouts-formlayout#wideMode-prop) property of [Kirigami.FormLayout](/docs/api/kirigami/qml-org-kde-kirigami-layouts-formlayout):

- When `true`, the form layout uses a desktop-optimized wide (two-column) layout.
- When `false`, the form layout uses a mobile layout (single column).

```qml
Kirigami.FormLayout {
    anchors.fill: parent
    wideMode: false

    Controls.TextField {
        Kirigami.FormData.label: "TextField 1:"
    }
    Controls.TextField {
        Kirigami.FormData.label: "TextField 2:"
    }
    Controls.TextField {
        Kirigami.FormData.label: "TextField 3:"
    }
}
```

## Aligning your labels

Sometimes you want a label for a component with more than one line, or for a list of components. You do this by setting [Kirigami.FormData.label](/docs/api/kirigami/qml-org-kde-kirigami-layouts-formdata#label-attached-prop) on a [ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html), as you may have noticed in [Sections and separators](#sections-and-separators). By default the label is placed in the vertical center of the layout, which isn't always what you want. You can change this with [Kirigami.FormData.labelAlignment](/docs/api/kirigami/qml-org-kde-kirigami-layouts-formdata#labelAlignment-attached-prop).

```qml
Kirigami.FormLayout {
    anchors.fill: parent

    ColumnLayout {
        Kirigami.FormData.label: "This is a label:"
        Kirigami.FormData.labelAlignment: Qt.AlignTop

        Controls.Label {
            text: "This is some rather long text \nthat should elide to multiple lines \nto show how the label gets aligned."
            elide: Text.ElideLeft
        }
    }
}
```

Setting the label alignment is particularly useful for components, or lists of components, whose size you don't know in advance. For example, you can align the label to the top only when the text needs more than one line, with a JavaScript ternary operator:

```qml
Kirigami.FormLayout {
    anchors.fill: parent

    ColumnLayout {
        Kirigami.FormData.label: "This is a label:"
        Kirigami.FormData.labelAlignment: labelText.lineCount > 1 ? Qt.AlignTop : Qt.AlignVCenter

        Controls.Label {
            id: labelText
            text: "This is some rather long text \nthat should elide to a new line \nso it appears below the Form Label."
            elide: Text.ElideLeft
        }
    }
}
```
