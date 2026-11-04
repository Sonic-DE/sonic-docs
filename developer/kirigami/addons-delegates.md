---
title: Form delegates in your settings pages
description: Create elegant custom settings pages.
source_url: https://develop.kde.org/docs/getting-started/kirigami/addons-delegates/
source_authors: [Florian Ruechel, Melissa Autumn, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-quick-ui-addons FormCard delegates (source and examples/FormCardTutorial/SettingsPage.qml); the project built and the settings page driven in a test build, plus checks of combobox modes, trailing items, autoSeparators and separator neighbours"
---

# Form delegates in your settings pages

You have learned how to add [About pages](addons-about.md) to your application. Now you can use the same inner components to create your settings pages.

The project structure should look like this:

```bash
addonsexample/
├── CMakeLists.txt
├── main.cpp
├── Main.qml
├── MyAboutPage.qml
└── SettingsPage.qml
```

## Needed changes

Add `SettingsPage.qml` to `ecm_target_qml_sources()` in `CMakeLists.txt`, and change `Main.qml` to include our new settings page:

```qml
import QtQuick
import QtQuick.Layouts

import org.kde.kirigami as Kirigami
import org.kde.kirigamiaddons.formcard as FormCard

Kirigami.ApplicationWindow {
    id: root
    width: 600
    height: 700

    Component {
        id: aboutsonicde
        FormCard.AboutKDEPage {}
    }

    Component {
        id: aboutpage
        MyAboutPage {}
    }

    Component {
        id: settingspage
        SettingsPage {}
    }

    pageStack.initialPage: Kirigami.ScrollablePage {
        ColumnLayout {
            FormCard.FormCard {
                FormCard.FormButtonDelegate {
                    id: aboutSonicDEButton
                    icon.name: "start-here-sonicde"
                    text: i18n("About SonicDE Page")
                    onClicked: root.pageStack.layers.push(aboutsonicde)
                }

                FormCard.FormButtonDelegate {
                    id: aboutPageButton
                    icon.name: "applications-utilities"
                    text: i18n("About Addons Example")
                    onClicked: root.pageStack.layers.push(aboutpage)
                }

                FormCard.FormButtonDelegate {
                    id: settingsButton
                    icon.name: "settings-configure"
                    text: i18n("Single Settings Page")
                    onClicked: root.pageStack.layers.push(settingspage)
                }
            }
        }
    }
}
```

Now we can look at the components used to create our settings page: the form card and its delegates.

## Form delegates

### FormCard and FormCardPage

[FormCard.FormCard](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formcard) is the main component we use to group its child components, the delegates.

We used a form card in the [Kirigami Addons introduction](addons-introduction.md) before. Its main purpose is to be a container for other components, in a color different from the background, much like a [Kirigami.Card](/docs/api/kirigami/qml-org-kde-kirigami-card).

Create a new `SettingsPage.qml` file:

```qml
import QtQuick
import org.kde.kirigamiaddons.formcard as FormCard

FormCard.FormCardPage {
    FormCard.FormCard {
        // This is where all our delegates go!
    }

    FormCard.FormCard {
        // This is where all our delegates go!
    }
}
```

Since our settings page is a separate QML file, and we need to be ready for scrolling, we use a [FormCard.FormCardPage](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formcardpage), which inherits [Kirigami.ScrollablePage](/docs/api/kirigami/qml-org-kde-kirigami-scrollablepage).

The nice thing about the form card page is its internal layout: no additional ColumnLayout is needed, and form cards can be added directly to it.

> **Note:** You can use FormCard delegates directly with a Kirigami.ScrollablePage, but then you need to add your own layouts.

### FormHeader

For every [FormCard](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formcard) you create, you can create a [FormHeader](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formheader) just before it. The header uses a heavier font weight and appears right above the form card.

```qml
import org.kde.kirigamiaddons.formcard as FormCard

FormCard.FormCardPage {
    FormCard.FormHeader {
        title: i18n("General")
    }

    FormCard.FormCard {
        // Our delegates go here...
    }

    FormCard.FormHeader {
        title: i18n("Accounts")
    }

    FormCard.FormCard {
        // Our delegates go here...
    }
}
```

### FormTextDelegate and FormSectionText

Let's start simple, with plain text.

[FormSectionText](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formsectiontext) simply adds a thin delegate containing a label. [FormTextDelegate](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formtextdelegate) has text and a grayed-out description.

```qml
import QtQuick
import org.kde.kirigami as Kirigami
import org.kde.kirigamiaddons.formcard as FormCard

FormCard.FormCardPage {
    FormCard.FormHeader {
        title: i18n("General")
    }

    FormCard.FormCard {
        FormCard.FormTextDelegate {
            text: i18n("Current Color Scheme")
            description: "Silver Light"
        }
    }

    FormCard.FormHeader {
        title: i18n("Accounts")
    }

    FormCard.FormCard {
        FormCard.FormSectionText {
            text: i18n("Online Account Settings")
        }
        FormCard.FormTextDelegate {
            leading: Kirigami.Icon {source: "user"}
            text: "John Doe"
            description: i18n("The Maintainer ™️")
        }
    }
}
```

We add some dummy text for the hypothetical color scheme detection. Actual detection could be built on a C++ model with [KColorSchemeManager](/docs/api/kcolorscheme/kcolorschememanager).

In the Online Accounts section there is an additional property, [leading](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formtextdelegate#leading-prop). We can give it an [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html) that appears before the text. Its opposite, [trailing](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formtextdelegate#trailing-prop), shows an Item after the text, but we don't use it in our program.

We use a [Kirigami.Icon](/docs/api/kirigami/qml-org-kde-kirigami-primitives-icon) here for simplicity, but this could also be a Kirigami Addons [Avatar](/docs/api/kirigamiaddonscomponents/qml-org-kde-kirigamiaddons-components-avatar) that gets its information from a model.

### FormButtonDelegate

The [FormButtonDelegate](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formbuttondelegate) looks similar to a FormTextDelegate, but it is clickable and shows an arrow pointing to the right. We used it in the [Kirigami Addons introduction](addons-introduction.md) before.

Like the FormTextDelegate, it has [leading](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formbuttondelegate#leading-prop) and [trailing](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formbuttondelegate#trailing-prop) properties to show an item before and after the main content; the arrow stays at the right-most side.

```qml
import QtQuick
import org.kde.kirigami as Kirigami
import org.kde.kirigamiaddons.formcard as FormCard

FormCard.FormCardPage {
    FormCard.FormHeader {
        title: i18n("General")
    }

    FormCard.FormCard {
        FormCard.FormTextDelegate {
            text: i18n("Current Color Scheme")
            description: "Silver Light"
        }
    }

    FormCard.FormHeader {
        title: i18n("Accounts")
    }

    FormCard.FormCard {
        FormCard.FormSectionText {
            text: i18n("Online Account Settings")
        }
        FormCard.FormTextDelegate {
            leading: Kirigami.Icon {source: "user"}
            text: "John Doe"
            description: i18n("The Maintainer ™️")
        }
        FormCard.FormButtonDelegate {
            icon.name: "list-add"
            text: i18n("Add a new account")
            onClicked: console.info("Clicked!")
        }
    }
}
```

We use its [icon.name](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html#icon.name-prop) property to show a plus (+) icon after the space for the [leading](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formbuttondelegate#leading-prop) item and before the main content. This is a common pattern to show that your button adds something to a list.

As this example is purely illustrative, we don't go into what happens when the button is clicked: it just prints "Clicked!" to the terminal. We *could* make a new page for account creation that adds another user to a model, and push that page into view, as we did in `Main.qml`.

### FormRadioDelegate, FormCheckDelegate and FormSwitchDelegate

RadioButton, CheckBox and Switch are very common in any user interface. Kirigami Addons provides them as [FormRadioDelegate](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formradiodelegate), [FormCheckDelegate](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formcheckdelegate) and [FormSwitchDelegate](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formswitchdelegate).

Their main properties are just `text` and `description`. In use they all inherit [AbstractButton](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html), so you use its properties and signal handlers: `checked` and `onCheckedChanged`, `onToggled`, and `onClicked`.

We want some autosave functionality in our application, and to show its settings only if the user has turned it on. Create a new section with a [FormCard](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formcard) and a [FormHeader](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formheader), then add a [FormSwitchDelegate](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formswitchdelegate) and some [FormRadioDelegate](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formradiodelegate) components.

```qml
FormCard.FormHeader {
    title: i18n("Autosave")
}

FormCard.FormCard {
    FormCard.FormSwitchDelegate {
        id: autosave
        text: i18n("Enabled")
    }
    FormCard.FormRadioDelegate {
        text: i18n("After every change")
        visible: autosave.checked
    }
    FormCard.FormRadioDelegate {
        text: i18n("Every 10 minutes")
        visible: autosave.checked
    }
    FormCard.FormRadioDelegate {
        text: i18n("Every 30 minutes")
        visible: autosave.checked
    }
}
```

We bind the visibility of each radio button to the switch, so they only appear when the switch is on.

> **Best practices:** If you have a background in imperative languages such as C++, you might be tempted to change the visibility of the radio buttons from JavaScript when the switch's [checked](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html#checked-prop) property changes:
>
> ```js
> onCheckedChanged: {
>     radio1.visible = checked;
>     radio2.visible = checked;
>     radio3.visible = checked;
> }
> ```
>
> This doesn't suit QML's declarative language. Use QML bindings, like `visible: autosave.checked`, as much as possible instead of JavaScript assignments. See [Qt's best practices](https://doc.qt.io/qt-6/qtquick-bestpractices.html#prefer-declarative-bindings-over-imperative-assignments) for details.

To try our checkbox, add a new [FormCheckDelegate](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formcheckdelegate) to our General section.

```qml
FormCard.FormHeader {
    title: i18n("General")
}

FormCard.FormCard {
    FormCard.FormTextDelegate {
        text: i18n("Current Color Scheme")
        description: "Silver Light"
    }
    FormCard.FormCheckDelegate {
        text: i18n("Show Tray Icon")
        onToggled: {
            if (checkState) {
                console.info("A tray icon appears on your system!")
            } else {
                console.info("The tray icon disappears!")
            }
        }
    }
}
```

Here we use the [signal handler](https://doc.qt.io/qt-6/qtqml-syntax-signals.html) [onToggled](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html#toggled-signal) to print some dummy text that simulates a tray icon appearing on the system. A real tray icon could be built with [KStatusNotifierItem](/docs/api/kstatusnotifieritem/kstatusnotifieritem-index) or Qt's [SystemTrayIcon](https://doc.qt.io/qt-6/qml-qt-labs-platform-systemtrayicon.html).

### FormComboBoxDelegate

The common ComboBox component is available as a [FormComboBoxDelegate](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formcomboboxdelegate).

It has several useful properties: [editable](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formcomboboxdelegate#editable-prop), [displayText](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formcomboboxdelegate#displayText-prop) and [displayMode](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formcomboboxdelegate#displayMode-prop).

Setting `editable: true` lets the user edit the text of the combobox, which is useful if new options may need adding.

To show additional text before each option, use something like `displayText: "Profile: " + currentText`.

The most interesting one, which we use in our example, is [displayMode](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formcomboboxdelegate#displayMode-prop). It has three options:

* **FormComboBoxDelegate.ComboBox**: the standard small box showing a list of options. This is the default on the desktop.
* **FormComboBoxDelegate.Dialog**: a dialog showing a list of options in the middle of the window. This is the default on mobile.
* **FormComboBoxDelegate.Page**: a new page with the list of options, shown in a separate window.

Add the following between the "Current Color Scheme" and "Show Tray Icon" delegates in your "General" form card.

```qml
FormCard.FormComboBoxDelegate {
    text: i18n("Default Profile")
    description: i18n("The profile to be loaded by default.")
    displayMode: FormCard.FormComboBoxDelegate.ComboBox
    currentIndex: 0
    editable: false
    model: ["Work", "Personal"]
}
```

### FormDelegateSeparator

Our settings page is taking shape, but each section is getting long. We can add a few [FormDelegateSeparator](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formdelegateseparator) instances to make the page tidier:

```qml
import QtQuick
import org.kde.kirigami as Kirigami
import org.kde.kirigamiaddons.formcard as FormCard

FormCard.FormCardPage {
    id: root

    title: i18nc("@title", "Settings")

    FormCard.FormHeader {
        title: i18nc("@title:group", "General")
    }

    FormCard.FormCard {
        FormCard.FormTextDelegate {
            text: i18nc("@info", "Current Color Scheme")
            description: "Silver Light"
        }

        FormCard.FormComboBoxDelegate {
            id: combobox
            text: i18nc("@label:listbox", "Default Profile")
            description: i18nc("@info:whatsthis", "The profile to be loaded by default.")
            displayMode: FormCard.FormComboBoxDelegate.ComboBox
            currentIndex: 0
            editable: false
            model: ["Work", "Personal"]
        }

        FormCard.FormDelegateSeparator {
            above: combobox
            below: checkbox
        }

        FormCard.FormCheckDelegate {
            id: checkbox
            text: i18nc("@option:check", "Show Tray Icon")
            onToggled: {
                if (checkState) {
                    console.info("A tray icon appears on your system!")
                } else {
                    console.info("The tray icon disappears!")
                }
            }
        }
    }

    FormCard.FormHeader {
        title: i18nc("@title:group", "Autosave")
    }

    FormCard.FormCard {
        FormCard.FormSwitchDelegate {
            id: autosave
            text: i18nc("@option:check", "Enabled")
        }
        FormCard.FormDelegateSeparator {
            above: autosave
            below: firstradio
            visible: autosave.checked
        }
        FormCard.FormRadioDelegate {
            id: firstradio
            text: i18nc("@option:radio", "After every change")
            visible: autosave.checked
        }
        FormCard.FormRadioDelegate {
            text: i18nc("@option:radio", "Every 10 minutes")
            visible: autosave.checked
        }
        FormCard.FormRadioDelegate {
            text: i18nc("@option:radio", "Every 30 minutes")
            visible: autosave.checked
        }
    }

    FormCard.FormHeader {
        title: i18nc("@title:group", "Accounts")
    }

    FormCard.FormCard {
        FormCard.FormSectionText {
            text: i18nc("@info:whatsthis", "Online Account Settings")
        }
        FormCard.FormTextDelegate {
            id: lastaccount
            leading: Kirigami.Icon {source: "user"}
            text: "John Doe"
            description: i18nc("@info:credit", "The Maintainer ™️")
        }
        FormCard.FormDelegateSeparator {
            above: lastaccount
            below: addaccount
        }
        FormCard.FormButtonDelegate {
            id: addaccount
            icon.name: "list-add"
            text: i18nc("@action:button", "Add a new account")
            onClicked: console.info("Clicked!")
        }
    }
}
```

Generally, use separators wherever you see major distinctions between components, although where to place them is ultimately your choice. For example, in the General section the checkbox differs from the components before it, as it doesn't start with text; in the Autosave section the separator groups the radio buttons together; and in the Accounts section a separator between the last account and the button gives the button some additional focus.

The [above](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formdelegateseparator#above-prop) and [below](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formdelegateseparator#below-prop) properties hold the components above and below the separator, and the separator disappears whenever one of them is hovered or highlighted. By default they are its neighbours in the layout, so you only need to set them when you want other components. For example, the separator above the tray icon setting doesn't appear while that setting is hovered.

If you want a separator between every pair of delegates in a form card, set its [autoSeparators](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-formcard#autoSeparators-prop) property to `true` instead of adding them by hand.
