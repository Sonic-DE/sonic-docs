---
title: Translations
description: Translate your desktop widget.
source_url: https://develop.kde.org/docs/plasma/widget/translations-i18n/
source_authors: [Alexander Hau, Alexander Lohnau, Carl Schwan, Chris Holland, Christoph Dreier, Claudius Ellsel, David Edmundson, Florian Ruechel, Fushan Wen, Johannes Zarl-Zierl, Joshua Goins, Kunda Ki, Marco Martin, Mariusz Libera, Michael Pyne, Mikhail Zolotukhin, Nate Graham, Nicolas Fella, Parth Dhiman, Paul Brown, Plata Hill, Raresh Rus, Rony Bou Moujahed, Thiago Sueto, Tino Lorenz, Tobias Fella, Yaron Shahrabani, Zren (Chris Holland), ivan tkachenko, yaniss khima]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "Applet::translationDomain, PluginLoader and the applet package structure in sonic-interface-libraries; KCatalog in sonic-frameworks-internationalization; both scripts run on a test widget, then the widget loaded with a French catalog in plasmawindowed under Xvfb"
---

# Translations

[KI18n](/docs/api/ki18n/ki18n-index) is the translation library SonicDE uses. It has a [programmer's guide](https://github.com/Sonic-DE/sonic-frameworks-internationalization/blob/master/docs/programmers-guide.md); this page covers the basics for a widget.

## i18n()

Wrap translated strings in the `i18n()` function. Always use double quotes: the tool that extracts strings for translation ignores `i18n('Test')`, so that string stays untranslated.

```qml
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami

Kirigami.FormLayout {
    QQC2.CheckBox {
        Kirigami.FormData.label: i18n("Feature:")
        text: i18n("Enabled")
    }
}
```

### Variables

`i18n()` also takes values to put into the string: `i18n(format, variable1, variable2)`. `%1` marks where the first variable goes, and `%2` the second.

```qml
import QtQuick
import org.kde.plasma.plasmoid

PlasmoidItem {
    property int unreadEmailCount: 3
    toolTipSubText: i18n("%1 unread emails", unreadEmailCount)
}
```

### Plurals

In English, a sentence about one item differs from a sentence about two or more. `i18np()` handles this, and other languages can have more plural forms than two.

```qml
i18np("One image in album %2", "%1 images in album %2", numImages, albumName)
```

```qml
i18np("One image in album %2", "More images in album %2", numImages, albumName)
```

This improves the earlier example, which would have read "1 unread emails":

```qml
import QtQuick
import org.kde.plasma.plasmoid

PlasmoidItem {
    property int unreadEmailCount: 3
    toolTipSubText: i18np("%1 unread email", "%1 unread emails", unreadEmailCount)
}
```

## Folder structure

With the messages wrapped, you extract them into a `template.pot` file. From that, translators create a catalog for each language, such as `fr.po` for French. The catalogs are then compiled into the binary `.mo` files SonicDE reads.

Put the sources in a `translate` folder inside the package, so that users can translate the widget when they look at its code. This page adds two scripts: `merge.sh` extracts the messages and updates the catalogs, and `build.sh` compiles them.

```text
package/
├── contents/
│   └── ...
├── translate/
│   ├── build.sh
│   ├── fr.po
│   ├── merge.sh
│   └── template.pot
└── metadata.json
```

After running `build.sh`, the compiled catalog is in the package's `contents/locale` folder. Its name is `plasma_applet_` followed by the widget's ID: this is the widget's translation domain, and SonicDE loads the catalog from here for package widgets.

```text
package/
└── contents/
    └── locale/
        └── fr/
            └── LC_MESSAGES/
                └── plasma_applet_org.example.helloworld.mo
```

## Installing gettext

The scripts use the tools from gettext, which your distribution packages as `gettext`. On Debian-based systems:

```bash
sudo apt install gettext
```

## Extracting and merging messages

`merge.sh` lists the widget's `.qml` and `.js` files and extracts their messages with `xgettext` into `template.pot`. If only the creation date has changed, it keeps the old file, so the file doesn't change in version control for no reason. Then it uses `msgmerge` to bring each catalog up to date with new messages.

Set `widgetId` to your widget's ID and `bugAddress` to where people report problems.

`translate/merge.sh`:

```bash
#!/bin/sh
cd "$(dirname "$0")" || exit 1

widgetId="org.example.helloworld"
bugAddress="https://example.org/helloworld/issues"

find .. -name '*.qml' -o -name '*.js' | sort > infiles.list

xgettext \
    --files-from=infiles.list \
    --from-code=UTF-8 \
    --width=400 \
    --add-location=file \
    -C -ci18n \
    -ki18n:1 -ki18nc:1c,2 -ki18np:1,2 -ki18ncp:1c,2,3 \
    --package-name="${widgetId##*.}" \
    --msgid-bugs-address="$bugAddress" \
    -o template.pot.new \
    || { echo "xgettext failed"; exit 1; }

rm infiles.list

# Keep the old file if only the creation date changed
if [ -f template.pot ] && diff -q -I 'POT-Creation-Date' template.pot template.pot.new > /dev/null; then
    rm template.pot.new
else
    mv template.pot.new template.pot
fi

for catalog in *.po; do
    [ -f "$catalog" ] || continue
    msgmerge --update --backup=none --width=400 --add-location=file --no-fuzzy-matching "$catalog" template.pot
done
```

## Examining template.pot

In `template.pot`, each message appears as a `msgid`, with its source file in a comment above it. Underneath is an empty `msgstr` for the translation, or one for each plural form.

```text
#: ../contents/ui/main.qml
msgid "%1 unread email"
msgid_plural "%1 unread emails"
msgstr[0] ""
msgstr[1] ""

#: ../contents/ui/main.qml
msgid "Show notification"
msgstr ""
```

## Creating fr.po

A translator creates a catalog from the template with `msginit`, which fills in the language's plural rules, and `msgconv`, which sets the encoding to UTF-8. Name it after the locale code: `fr` is French. Use an underscore (`fr_CA`, not `fr-CA`) for a translation that doesn't suit the language as a whole.

```bash
cd package/translate
msginit --input=template.pot --locale=fr --no-translator --output-file=- | msgconv --to-code=UTF-8 --output-file=fr.po
```

Translators then fill in the empty `msgstr` entries.

```text
#: ../contents/ui/main.qml
msgid "%1 unread email"
msgid_plural "%1 unread emails"
msgstr[0] "%1 courriel non lu"
msgstr[1] "%1 courriels non lus"

#: ../contents/ui/main.qml
msgid "Show notification"
msgstr "Montrer les notifications"
```

## Building the .mo files

`build.sh` compiles each catalog with `msgfmt` into `contents/locale/<locale>/LC_MESSAGES/`. Note the `plasma_applet_` in front of the widget's ID.

`translate/build.sh`:

```bash
#!/bin/sh
cd "$(dirname "$0")" || exit 1

widgetId="org.example.helloworld"

for catalog in *.po; do
    [ -f "$catalog" ] || continue
    locale="${catalog%.po}"
    installDir="../contents/locale/$locale/LC_MESSAGES"
    mkdir -p "$installDir"
    msgfmt -o "$installDir/plasma_applet_$widgetId.mo" "$catalog"
done
```

## Testing your translations

Run `build.sh`, install the widget, and start it with the `LANGUAGE` environment variable set to the languages you want, in order. If your widget is a clock, you might also want to set `LC_TIME`.

```bash
sh package/translate/build.sh
kpackagetool6 -t Plasma/Applet -u package
LANGUAGE="fr_CA:fr" plasmawindowed org.example.helloworld
```

`LANGUAGE` only takes effect while your current locale is one that's installed on the system. It is ignored in the `C` locale, or if `LANG` names a locale that isn't installed; `locale -a` lists the ones that are.

## Compiled widgets

A [compiled widget](c-api.md) has no package to put catalogs in, so they are installed to the system's locale directory. Its C++ code needs the domain defined with `TRANSLATION_DOMAIN`; its QML uses the same `plasma_applet_<id>` domain automatically.

Keep the catalogs in `po/<locale>/plasma_applet_<id>.po`, and add this to `CMakeLists.txt`:

```cmake
ki18n_install(po)
```

## Reusing other translations

If you know another component has already translated a string, `i18nd(domain, string, ...)` uses the translation from that domain. A widget's domain starts with `plasma_applet_` and ends with its ID; a wallpaper's starts with `plasma_wallpaper_`. Be careful, because this links to private strings that can change with any update.

The image wallpaper does this for the slideshow wallpaper, which shares its code:

```qml
import org.kde.plasma.core as PlasmaCore

PlasmaCore.Action {
    text: i18nd("plasma_wallpaper_org.kde.image", "Open Wallpaper Image")
}
```
