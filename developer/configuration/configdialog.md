---
title: KConfigDialog
description: The standard configuration dialog for QtWidgets applications.
source_url: https://develop.kde.org/docs/features/configuration/configdialog/
source_authors: [Zack Rusin, Carl Schwan, Nicolas Fella]
license: LGPL-2.0-or-later
license_url: https://spdx.org/licenses/LGPL-2.0-or-later.html
checked_against: sonic-frameworks-settings-ui (src/kconfigdialog.h, KConfigWidgets)
---

# KConfigDialog

For a configuration dialog in a QtWidgets application, use [KConfigDialog](/docs/api/kconfigwidgets/kconfigdialog), from `sonic-frameworks-settings-ui` (`find_package(KF6 REQUIRED COMPONENTS ConfigWidgets)`, `KF6::ConfigWidgets`).

KConfigDialog enables and disables its buttons, creates the dialog and deletes its widgets. Through KConfigDialogManager it also restores the settings, resets them to their defaults and saves them.

For that, each widget that edits a setting must be named after the setting's entry with the prefix `kcfg_`: the widget `kcfg_MyOption` edits the entry `MyOption`. The settings come from a [KConfig XT](kconfig-xt.md) class (a `KCoreConfigSkeleton`).

An example:

```cpp
void KCoolApp::showSettings(){
    if (KConfigDialog::showDialog(QStringLiteral("settings"))) {
      return;
    }
    KConfigDialog *dialog = new KConfigDialog(this, QStringLiteral("settings"), MySettings::self());
    dialog->setFaceType(KPageDialog::List);
    dialog->addPage(new General(nullptr, "General"), i18n("General"));
    dialog->addPage(new Appearance(nullptr, "Style"), i18n("Appearance"));
    connect(dialog, &KConfigDialog::settingsChanged, mainWidget, &Bar::loadSettings);
    connect(dialog, &KConfigDialog::settingsChanged, this, &Foo::loadSettings);
    dialog->show();
}
```

`showDialog()` shows the dialog called `settings` if it already exists, so it is only created once. `General` and `Appearance` stand for your own page widgets.

Besides this code, each class whose settings are in the dialog should have a slot like `loadSettings()` that reads the settings and applies them; the dialog's `settingsChanged()` signal calls it.

For the dialog's appearance (buttons, default button, …) see [KPageDialog](/docs/api/kwidgetsaddons/kpagedialog).

For more, see the [KConfigDialog API reference](/docs/api/kconfigwidgets/kconfigdialog).
