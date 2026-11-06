---
title: Spell Check
description: Set the default spell checking options for your applications.
source_url: https://invent.kde.org/plasma/plasma-desktop/-/blob/master/doc/kcontrol/spellchecking/index.docbook
source_authors: [Lauri Watts]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-desktop-interface fad996458a (kcms/spellchecking), sonic-frameworks-spell-check src/ui; read from code, not clicked through"
---

# Spell Check

These options are the defaults for all applications that use Sonnet, a frontend to various free spell checkers. Each application can override them.

To use Sonnet you need to install a spell checker such as [GNU Aspell](http://aspell.net/), [Hspell](http://hspell.ivrix.org.il/) or [Hunspell](https://hunspell.github.io/), and the dictionaries for your language. The module tells you if no spell checker is installed.

**Default language** chooses which of the available dictionaries to use. **Preferred Languages** lets you choose the languages you want to work with.

## Options

- **Enable autodetection of language:** Based on several heuristics (the script used, trigram matching and language ranking), this switches language automatically in a multi-language document.
- **Enable background spellchecking:** Checks spelling in the background.
- **Automatic spell checking enabled by default:** Checks words as you type them. Misspelled ones get a red line under them.
- **Skip all uppercase words:** Doesn't check words consisting of all capital letters. This is useful for documents with many acronyms.
- **Skip run-together words:** If this isn't checked, words that appear in the dictionary separately but have been run together count as spelling errors, such as shutout, cannot and blackout. Checking it also helps stop website and email addresses being flagged.

## Ignored Words

This list holds specific words, such as specialized terminology or proper names, that the spell checker should ignore.

To add a word, type it in the text box and click **Add**. To remove one, select it in the list and click **Remove**.
