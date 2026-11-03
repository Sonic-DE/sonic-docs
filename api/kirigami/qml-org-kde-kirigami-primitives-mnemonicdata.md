---
title: "MnemonicData QML Type"
description: "An attached property used to calculate automated keyboard sequences to trigger actions based upon their text."
---

# MnemonicData QML Type

An attached property used to calculate automated keyboard sequences to trigger actions based upon their text. [More...](#details)

- Import Statement: import org.kde.kirigami.primitives

## Detailed Description {#details}

If an "&" mnemonic is used (such as "&Ok"), the system will attempt to assign the desired letter giving it priority, otherwise a letter among the ones in the label will be used if possible and not conflicting.

Different kinds of controls will have different priorities in assigning the shortcut: for instance the "Ok/Cancel" buttons in a dialog will have priority over fields of a [FormLayout](qml-org-kde-kirigami-layouts-formlayout.md).

Usually the developer shouldn't use this directly as base components already use this, but only when implementing a custom graphical Control.

## Attached Property Documentation {#attached-property-documentation}

### MnemonicData.active : bool {#active-attached-prop}

True when the user is pressing alt and the accelerators should be shown.

### MnemonicData.controlType : enumeration {#controlType-attached-prop}

The type of control this mnemonic is attached: different types of controls have different importance and priority for shortcut assignment.

| Constant | Description |
| --- | --- |
| MnemonicData.ActionElement | pushbuttons, checkboxes etc |
| MnemonicData.DialogButton | buttons for dialogs |
| MnemonicData.MenuItem | Menu items |
| MnemonicData.FormLabel | Buddy label in a [FormLayout](qml-org-kde-kirigami-layouts-formlayout.md) |
| MnemonicData.SecondaryControl | Other controls that are considered not much important and low priority for shortcuts |

### MnemonicData.enabled : bool {#enabled-attached-prop}

Only if true this mnemonic will be considered for the global assignment.

default: true

### MnemonicData.label : string {#label-attached-prop}

The label of the control we want to compute a mnemonic for, instance "Label:" or "&Ok"

### MnemonicData.mnemonicLabel : string {#mnemonicLabel-attached-prop}

The label with an "&" mnemonic in the place which will have the shortcut assigned, regardless of whether the & was assigned by the user or automatically generated.

### MnemonicData.plainTextLabel : string {#plainTextLabel-attached-prop}

The label in plain text with no markup nor & markers.

### MnemonicData.richTextLabel : string {#richTextLabel-attached-prop}

The user-visible final label, which will have the shortcut letter underlined, such as "\<u\>O\</u\>k".

### MnemonicData.sequence : keysequence {#sequence-attached-prop}

The final key sequence assigned, if any: it will be Alt+alphanumeric char.
