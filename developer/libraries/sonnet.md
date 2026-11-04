---
title: Sonnet
description: Spell checking made easy.
source_url: https://develop.kde.org/docs/features/spellchecking/
source_authors: [Jacob R Rideout, Carl Schwan, Chris Holland, Mikhail Zolotukhin, Thiago Sueto]
license: LGPL-2.0-or-later
license_url: https://spdx.org/licenses/LGPL-2.0-or-later.html
checked_against: sonic-frameworks-spell-check (src/plugins, src/core/guesslanguage.h, src/ui, data/trigrams, examples/textedit.cpp, examples/dialogexample.cpp; plugins built in the builder)
---

# Sonnet

Sonnet, in `sonic-frameworks-spell-check` (`find_package(KF6Sonnet)`; `KF6::SonnetCore` and `KF6::SonnetUi`), solves spell checking for text editors. Its spell checkers are plugins: Hunspell and Aspell on SonicDE, with plugins for HSpell, Voikko and the Windows and macOS system spell checkers in the source as well. It also detects the language of a text automatically, combining several methods.

## Spell checking in your QTextEdit

Adding Sonnet to a QTextEdit is easy:

```cpp
QTextEdit *textEdit = new QTextEdit;
textEdit->setText(
    QString::fromLatin1("This is a sample buffer. Whih this thingg will "
                        "be checkin for misstakes. Whih, Enviroment, govermant. Whih."));

Sonnet::SpellCheckDecorator *installer = new Sonnet::SpellCheckDecorator(textEdit);
installer->highlighter()->setCurrentLanguage(QStringLiteral("en_US"));
```

[Sonnet::SpellCheckDecorator](/docs/api/sonnetui/sonnet-spellcheckdecorator) can be extended to check differently formatted text, such as emails:

```cpp
class MailSpellCheckDecorator : public Sonnet::SpellCheckDecorator
{
public:
    explicit MailSpellCheckDecorator(QTextEdit *edit)
        : Sonnet::SpellCheckDecorator(edit)
    {
    }

protected:
    bool isSpellCheckingEnabledForBlock(const QString &blockText) const override
    {
        qDebug() << blockText;
        return !blockText.startsWith(QLatin1Char('>'));
    }
};
```

Use `MailSpellCheckDecorator` exactly like `SpellCheckDecorator`; it also skips the quoted parts of an email (lines starting with `>`).

## Language detection

Sonnet can tell about 70 languages apart in a string. Its method is based on Languid, a Perl script by Maciej Ceglowski, and works in two steps: first it checks which writing systems the text uses, then, for the languages using those writing systems, it compares an n-gram frequency model of each language with one of the text. The most similar language model wins. If no language is found, the result is an empty string.

A simple example with [GuessLanguage](/docs/api/sonnetcore/sonnet-guesslanguage):

```cpp
GuessLanguage languageGuesser;
QString lang = languageGuesser.identify("Mon super texte");
```

`identify()` returns the language's ISO 639-1 code (a three-letter code only where no two-letter code exists).

## Widgets

Sonnet also has widgets for configuring it in Qt applications. [DictionaryComboBox](/docs/api/sonnetui/sonnet-dictionarycombobox), for example, is a combo box for choosing the dictionary. Connect it to the highlighter of a decorator to switch the spell check language:

```cpp
Sonnet::DictionaryComboBox *comboBox = new Sonnet::DictionaryComboBox;
QObject::connect(comboBox, &Sonnet::DictionaryComboBox::dictionaryChanged,
                 installer->highlighter(), &Sonnet::Highlighter::setCurrentLanguage);
```

[Sonnet::Dialog](/docs/api/sonnetui/sonnet-dialog) checks a whole text interactively:

```cpp
void TestDialog::check(const QString &buffer)
{
    Sonnet::Dialog *dlg = new Sonnet::Dialog(new BackgroundChecker(this), nullptr);
    connect(dlg, &Dialog::spellCheckDone, this, &TestDialog::doneChecking);
    dlg->setBuffer(buffer);
    dlg->show();
}
```

[ConfigDialog](/docs/api/sonnetui/sonnet-configdialog) is a fuller settings dialog: the words to ignore, skipping run-together words, and turning automatic language detection on or off.

The examples come from `sonic-frameworks-spell-check/examples` (LGPL-2.1-or-later).
