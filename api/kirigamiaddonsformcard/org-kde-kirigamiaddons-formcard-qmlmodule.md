---
title: "Kirigami Addons FormCard QML Types"
description: "Form controls for settings pages and dialogs."
---

# Kirigami Addons FormCard QML Types

Form controls for settings pages and dialogs.

The [FormCard](qml-org-kde-kirigamiaddons-formcard-templates-formcard.md) module provides controls for settings pages and other forms. Import it with an alias so that its types are easy to distinguish from regular Qt Quick Controls:

```qml
import org.kde.kirigamiaddons.formcard as FormCard
```

## Organizing a form {#organizing-a-form}

A [FormCardPage](qml-org-kde-kirigamiaddons-formcard-formcardpage.md) is a scrollable page that arranges form sections. Each section normally has a [FormHeader](qml-org-kde-kirigamiaddons-formcard-templates-formheader.md) followed by a [FormCard](qml-org-kde-kirigamiaddons-formcard-templates-formcard.md). Put the header beside the card in the page, not inside it. The card holds one or more form delegates, such as [FormSwitchDelegate](qml-org-kde-kirigamiaddons-formcard-formswitchdelegate.md), [FormSliderDelegate](qml-org-kde-kirigamiaddons-formcard-formsliderdelegate.md), [FormTextFieldDelegate](qml-org-kde-kirigamiaddons-formcard-formtextfielddelegate.md), or [FormButtonDelegate](qml-org-kde-kirigamiaddons-formcard-formbuttondelegate.md). The card lays out its delegates vertically and supplies their shared background.

```qml
import org.kde.kirigamiaddons.formcard as FormCard

FormCard.FormCardPage {
    title: i18nc("@title", "Settings")

    FormCard.FormHeader {
        title: i18nc("@title:group", "Account")
    }

    FormCard.FormCard {
        autoSeparators: true

        FormCard.FormTextFieldDelegate {
            label: i18nc("@label:textbox", "Display name")
        }

        FormCard.FormSwitchDelegate {
            text: i18nc("@option:check", "Show online status")
        }
    }
}
```

Add another header and card for another section. The card's [FormCard::autoSeparators](qml-org-kde-kirigamiaddons-formcard-templates-formcard.md#autoSeparators-prop) property inserts separators between visible delegates when enabled. You can also add [FormDelegateSeparator](qml-org-kde-kirigamiaddons-formcard-formdelegateseparator.md) explicitly when you need to control where a separator appears.

## Creating a custom delegate {#creating-a-custom-delegate}

Use [AbstractFormDelegate](qml-org-kde-kirigamiaddons-formcard-abstractformdelegate.md) as the root of a reusable QML component. It supplies the card's padding, hover and click behavior, and default background. Provide a `contentItem` with an implicit size, and expose any additional properties your delegate needs. For example, save the following as `CounterDelegate.qml`:

```qml
import QtQuick.Controls as Controls
import org.kde.kirigamiaddons.formcard as FormCard

FormCard.AbstractFormDelegate {
    id: root

    property int count: 0

    text: i18nc("@action:button", "Count: %1").arg(count)
    onClicked: root.count++

    contentItem: Controls.Label {
        text: root.text
    }
}
```

Use `CounterDelegate` inside a [FormCard](qml-org-kde-kirigamiaddons-formcard-templates-formcard.md), just like the built-in delegates. The inherited `text` property also gives this clickable delegate an accessible name. To remove the default background for a different design, set `background: null`.

## Using delegates in a dialog {#using-delegates-in-a-dialog}

[FormCardDialog](qml-org-kde-kirigamiaddons-formcard-templates-formcarddialog.md) provides a dialog header, a vertical layout for form delegates, and optional standard buttons. Place delegates directly inside it; no [FormCard](qml-org-kde-kirigamiaddons-formcard-templates-formcard.md) or [FormCardPage](qml-org-kde-kirigamiaddons-formcard-formcardpage.md) is needed. Use `standardButtons` to choose the actions and handle `onAccepted` or `onRejected` as with a Qt Quick Controls Dialog:

```qml
import org.kde.kirigamiaddons.formcard as FormCard
import QtQuick.Controls

FormCard.FormCardDialog {
    title: "Add Thingy"
    autoSeparators: true

    standardButtons: Dialog.Ok | Dialog.Cancel
    FormCard.FormTextFieldDelegate {
        label: i18nc("@label:textbox Notebook name", "Name:")
    }

    FormCard.FormButtonDelegate {
        text: i18nc("@action:button", "Color")
        icon.name: "color-picker"
    }

    FormCard.FormButtonDelegate {
        text: i18nc("@action:button", "Icon")
        icon.name: "preferences-desktop-emoticons"
    }
}
```

Call `dialog.open()` from the action that should show the form. Custom delegates based on [AbstractFormDelegate](qml-org-kde-kirigamiaddons-formcard-abstractformdelegate.md) can also be placed directly in a [FormCardDialog](qml-org-kde-kirigamiaddons-formcard-templates-formcarddialog.md).

*See also* [FormCardPage](qml-org-kde-kirigamiaddons-formcard-formcardpage.md), [FormCard](qml-org-kde-kirigamiaddons-formcard-templates-formcard.md), [FormCardDialog](qml-org-kde-kirigamiaddons-formcard-templates-formcarddialog.md), [AbstractFormDelegate](qml-org-kde-kirigamiaddons-formcard-abstractformdelegate.md)

## Contents

- [AboutKDEPage](qml-org-kde-kirigamiaddons-formcard-aboutkdepage.md): An "About KDE" page using Form components.
- [AboutPage](qml-org-kde-kirigamiaddons-formcard-aboutpage.md): An AboutPage that displays the about data using Form components.
- [AbstractFormDelegate](qml-org-kde-kirigamiaddons-formcard-abstractformdelegate.md): A base item for delegates to be used in a FormCard.
- [FormArrow](qml-org-kde-kirigamiaddons-formcard-formarrow.md): An arrow UI component used in Form delegates.
- [FormButtonDelegate](qml-org-kde-kirigamiaddons-formcard-formbuttondelegate.md): A Form delegate that corresponds to a clickable button.
- [FormCard](qml-org-kde-kirigamiaddons-formcard-formcard.md): A single card that follows a form style.
- [FormCardDialog](qml-org-kde-kirigamiaddons-formcard-formcarddialog.md): A dialog designed to use FormCard delegates as its content.
- [FormCardPage](qml-org-kde-kirigamiaddons-formcard-formcardpage.md): A scrollable page used as a container for one or more FormCards.
- [FormCheckDelegate](qml-org-kde-kirigamiaddons-formcard-formcheckdelegate.md): A Form delegate that corresponds to a checkbox.
- [FormColorDelegate](qml-org-kde-kirigamiaddons-formcard-formcolordelegate.md): A FormCard delegate for colors.
- [FormComboBoxDelegate](qml-org-kde-kirigamiaddons-formcard-formcomboboxdelegate.md): A Form delegate that corresponds to a ComboBox.
- [FormDateTimeDelegate](qml-org-kde-kirigamiaddons-formcard-formdatetimedelegate.md): FormDateTimeDelegate is a delegate for FormCard that lets the user enter either a date, a time or both.
- [FormDelegateBackground](qml-org-kde-kirigamiaddons-formcard-formdelegatebackground.md): A background for Form delegates.
- [FormDelegateCollapsible](qml-org-kde-kirigamiaddons-formcard-formdelegatecollapsible.md): A delegate designed to display or hide formcard contents.
- [FormDelegateSeparator](qml-org-kde-kirigamiaddons-formcard-formdelegateseparator.md): A context-aware separator.
- [FormFileDelegate](qml-org-kde-kirigamiaddons-formcard-formfiledelegate.md): A Form delegate that let the user select a file.
- [FormFolderDelegate](qml-org-kde-kirigamiaddons-formcard-formfolderdelegate.md): A Form delegate that let the user select a folder.
- [FormGridContainer](qml-org-kde-kirigamiaddons-formcard-formgridcontainer.md): This component render a grid of small cards.
- [FormHeader](qml-org-kde-kirigamiaddons-formcard-formheader.md): A header item for a form card.
- [FormIconDelegate](qml-org-kde-kirigamiaddons-formcard-formicondelegate.md): A FormCard delegate for icons.
- [FormLinkDelegate](qml-org-kde-kirigamiaddons-formcard-formlinkdelegate.md): A form delegate that contains a URL.
- [FormPasswordFieldDelegate](qml-org-kde-kirigamiaddons-formcard-formpasswordfielddelegate.md): A Form delegate that corresponds to a password field.
- [FormPlaceholderMessageDelegate](qml-org-kde-kirigamiaddons-formcard-formplaceholdermessagedelegate.md): A placeholder message indicating that a FormCard is empty.
- [FormRadioDelegate](qml-org-kde-kirigamiaddons-formcard-formradiodelegate.md): A Form delegate that corresponds to a radio button.
- [FormRadioSelectorDelegate](qml-org-kde-kirigamiaddons-formcard-formradioselectordelegate.md): A FormCard delegate that allows switching between multiple options.
- [FormSectionText](qml-org-kde-kirigamiaddons-formcard-formsectiontext.md): A standard delegate label.
- [FormSliderDelegate](qml-org-kde-kirigamiaddons-formcard-formsliderdelegate.md): A form delegate for selecting a value with a slider.
- [FormSpinBoxDelegate](qml-org-kde-kirigamiaddons-formcard-formspinboxdelegate.md): A Form delegate that corresponds to a spinbox.
- [FormSwitchDelegate](qml-org-kde-kirigamiaddons-formcard-formswitchdelegate.md): A Form delegate that corresponds to a switch.
- [FormTextAreaDelegate](qml-org-kde-kirigamiaddons-formcard-formtextareadelegate.md): A Form delegate that corresponds to a text area.
- [FormTextDelegate](qml-org-kde-kirigamiaddons-formcard-formtextdelegate.md): A Form delegate that corresponds to a text label and a description.
- [FormTextFieldDelegate](qml-org-kde-kirigamiaddons-formcard-formtextfielddelegate.md): A Form delegate that corresponds to a text field.
