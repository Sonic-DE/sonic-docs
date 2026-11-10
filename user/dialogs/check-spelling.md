---
title: Check Spelling
description: Go through a document's spelling mistakes one by one and fix them.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-spell-check (src/ui/sonnetui.ui, src/ui/dialog.cpp); written from the code, not clicked through"
---

# Check Spelling

Applications that let you write text, such as text editors, can check a whole document's spelling at once. The **Check Spelling** window, usually opened from the **Tools** menu, goes through the words it doesn't recognise one at a time.

The dictionaries and the words you've taught it are set in the [Spell Check](../settings/spell-check.md) module of System Settings.

## For each unknown word

- **Unknown word:** The word that isn't in the dictionary, with a short extract below it showing where it appears in the text.
- **<< Add to Dictionary** adds the word to your personal dictionary, so it's never marked again.
- **Language:** The dictionary used for the check. Choose another to check the text in a different language.
- The list of suggestions shows possible corrections. Click one to copy it into **Replace with:**, or double-click it to use it straight away. You can also type your own replacement.

Then choose what to do:

- **Suggest:** Finds suggestions for the word you've typed in **Replace with:**.
- **Replace:** Replaces this occurrence with the text in **Replace with:**.
- **Replace All:** Replaces every occurrence in the document.
- **Ignore:** Leaves this occurrence as it is. Useful for names, abbreviations and foreign words that you don't want to add to the dictionary.
- **Ignore All:** Leaves every occurrence of this word as it is.
- **Autocorrect:** Only in applications with autocorrection. Adds the word and its replacement to the list of corrections made as you type.

The check moves on to the next unknown word, and tells you when it's complete. Click **OK** to stop checking and keep the changes made so far, or **Cancel** to stop the check. In many text fields, **Cancel** also takes back the replacements made during this check.
