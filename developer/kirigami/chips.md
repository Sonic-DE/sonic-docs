---
title: Chips
description: Chips are small elements typically used to list related properties.
source_url: https://develop.kde.org/docs/getting-started/kirigami/components-chips/
source_authors: [Kuneho Cottonears, Nicolas Fella, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "Kirigami Chip (template and control), OverlaySheet; examples run with the qml tool, plus model/chip update checks and an add/edit/remove run of the example application"
---

# Chips

[Kirigami.Chip](/docs/api/kirigami/qml-org-kde-kirigami-chip) components are small elements, inherited from [AbstractButton](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html), used to display common properties or filters of something. They are typically text elements that can be clicked, and come with an optional delete button ([closable](/docs/api/kirigami/qml-org-kde-kirigami-chip#closable-prop), on by default), which emits the [removed](/docs/api/kirigami/qml-org-kde-kirigami-chip#removed-signal) signal.

## Quick start

Add chips with the [Kirigami.Chip](/docs/api/kirigami/qml-org-kde-kirigami-chip) component. Assigning a string to its inherited [AbstractButton.text](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html#text-prop) property gives a chip its name.

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Chips"

    pageStack.initialPage: Kirigami.Page {
        title: "Chips"

        Kirigami.FormLayout {
            anchors.fill: parent
            Kirigami.Chip {
                text: "Chip 1"
            }
            Kirigami.Chip {
                text: "Chip 2"
            }
            Kirigami.Chip {
                text: "Chip 3"
            }
        }
    }
}
```

### With repeaters (recommended)

Since chips are meant to be used more than once, you'll likely want to keep them in a list data structure and iterate over it to display them. For this we need a [ListModel](https://doc.qt.io/qt-6/qml-qtqml-models-listmodel.html) and a [Repeater](https://doc.qt.io/qt-6/qml-qtquick-repeater.html).

The ListModel stores the chips. To populate it (and so the chips), we declare a few ListElement components, each with a `text` field. We assign this string to the `text` of each repeated chip.

The Repeater displays the chips. First, set the Repeater's `model` to our ListModel, or create the ListModel inside the Repeater. Then declare the `Kirigami.Chip` component inside the Repeater and assign the element's data to its `text` with the `modelData` property (the model has a single role, so `modelData` holds it).

```qml
Kirigami.ApplicationWindow {
    id: root
    title: "Chips"

    ListModel {
        id: chips

        ListElement { text: "Chip 1" }
        ListElement { text: "Chip 2" }
        ListElement { text: "Chip 3" }
    }

    pageStack.initialPage: Kirigami.Page {
        title: "Chips"

        Kirigami.FormLayout {
            anchors.fill: parent
            Repeater {
                Layout.fillWidth: true
                model: chips

                Kirigami.Chip {
                    id: chip
                    text: modelData
                }
            }
        }
    }
}
```

You can append data to and remove data from the ListModel dynamically, and the Repeater applies those changes automatically. Changing an item of the ListModel (for example with `setProperty()`) also updates its chip, because the chip's `text` is bound to `modelData`. The other way round doesn't work: changing a chip's `text` doesn't change the model, and it replaces the binding, so later model changes no longer reach that chip. So always change the model. See the [example application](#example-application) below.

## Example application

The example application below shows how chips can be used in programs such as to-do lists: type an item and press Enter to add a chip, click a chip to edit it, and click its delete button to remove it.

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    id: root
    title: "Chips"

    ListModel {
        id: chips

        ListElement { text: "Chip 1" }
        ListElement { text: "Chip 2" }
        ListElement { text: "Chip 3" }
    }

    pageStack.initialPage: Kirigami.Page {
        title: "Chips"

        Kirigami.OverlaySheet {
            id: editChipPrompt

            property var chip;
            property var index;

            header: Kirigami.Heading {
                text: "Edit Chip"
            }

            footer: DialogButtonBox {
                standardButtons: DialogButtonBox.Ok | DialogButtonBox.Cancel
                onAccepted: {
                    // Updating the model also updates the chip's text,
                    // as the chip's text is bound to modelData.
                    chips.setProperty(editChipPrompt.index, "text", editTextField.text);
                    editChipPrompt.close();
                }
                onRejected: {
                    editChipPrompt.close();
                }
            }

            TextField {
                id: editTextField
            }
        }

        Kirigami.FormLayout {
            anchors.fill: parent
            TextField {
                id: insertTextField
                Kirigami.FormData.label: "Item:"
                onAccepted: chips.append({ text: insertTextField.text })
            }
            // Wrapped in ColumnLayout to prevent binding loops.
            ColumnLayout {
                Layout.alignment: Qt.AlignHCenter
                Repeater {
                    model: chips

                    Kirigami.Chip {
                        id: chip
                        text: modelData
                        onClicked: {
                            editTextField.text = modelData;
                            editChipPrompt.chip = chip;
                            editChipPrompt.index = index;
                            editChipPrompt.open();
                        }
                        onRemoved: chips.remove(index)
                    }
                }
            }
        }
    }
}
```
