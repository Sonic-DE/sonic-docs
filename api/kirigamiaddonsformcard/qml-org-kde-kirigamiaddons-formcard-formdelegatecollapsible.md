---
title: "FormDelegateCollapsible QML Type"
description: "A delegate designed to display or hide formcard contents."
---

# FormDelegateCollapsible QML Type

A delegate designed to display or hide formcard contents. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard
- Inherits: [ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html)

## Detailed Description {#details}

```qml
import org.kde.kirigamiaddons.formcard as FormCard

FormCard.FormCard {
     FormCard.FormTextDelegate {
         text: "Always visible text"
     }
     FormCard.FormDelegateSeparator {
         below: collapsible.itemBelowPrev
     }
     FormDelegateCollapsible {
         id: collapsible
         text: "Collapsible"
         description: expanded ? "Click to close!" : "Click to open!"

         FormCard.FormTextDelegate {
             text: "Initially hidden text"
         }
         FormCard.FormDelegateSeparator {}
         FormCard.FormTextDelegate {
             text: "When you click the Collapsible's button, it opens!"
         }
     }
     FormCard.FormDelegateSeparator {
         above: collapsible.itemAboveNext
     }
     FormCard.FormTextDelegate {
         text: "Always visible text"
     }
 }
```

## Property Documentation {#property-documentation}

### \[read-only\] button : FormButtonDelegate {#button-prop}

The buttonDelegate itself.

### description : alias {#description-prop}

The buttonDelegate's description.

### expanded : bool {#expanded-prop}

Controls if the button should be expanded.

### \[read-only\] itemAboveNext : Item {#itemAboveNext-prop}

The delegate visually above the delegate following the collapsible. When a [FormDelegateSeparator](qml-org-kde-kirigamiaddons-formcard-formdelegateseparator.md) is below this, bind its "above" property to this.

### \[read-only\] itemBelowPrev : Item {#itemBelowPrev-prop}

The delegate visually below the previous delegate. When a [FormDelegateSeparator](qml-org-kde-kirigamiaddons-formcard-formdelegateseparator.md) is above this, bind its "below" property to this.

### text : alias {#text-prop}

The buttonDelegate's text.
