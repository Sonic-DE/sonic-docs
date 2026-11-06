---
title: Web Search Keywords
description: Create shortcuts that search the web or open addresses from anywhere.
source_url: https://invent.kde.org/network/kio-extras/-/blob/master/doc/kcontrol6/webshortcuts/index.docbook
source_authors: [Krishna Tateneni, Yves Arrouye]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-frameworks-io-extras 368b21968 (kcms/webshortcuts); read from code, not clicked through"
---

# Web Search Keywords

Web search keywords let you make up new pseudo URL schemes, or shortcuts, that *parameterize* commonly used addresses. For example, you can set up a shortcut like `gg` to trigger a search with Google, so typing `gg:my query` searches for “my query”. This module is under **Workspace > Search** in System Settings.

> [!NOTE]
> They're called pseudo URL schemes because they're used like one, but the input isn't URL-encoded. You type `google:sonic apps`, not `google:sonic+apps`.

You can use them wherever you'd normally use an address, such as KRunner, which you open with Alt+F2 or Alt+Space. Shortcuts for several search engines should already be set up, and in this module you can add new ones and change or delete existing ones.

## The list

The list shows the names of the keywords you've defined. You can click a column heading to change the sort order, and resize the columns.

**Enable Web search keywords** has to be checked for this feature to work. **New…**, **Edit…** and **Delete** create, change and remove keywords.

If **Use preferred keywords only** is checked, only the keywords marked in the **Preferred** column are used where only a few can be shown at once.

- **Default Web search keyword:** The search engine used in input boxes that look things up automatically when you type words instead of an address. Select **None** to turn this off.
- **Keyword delimiter:** The character separating the keyword from what's being searched for.

## Editing a keyword

Double-click an entry or click **Edit…** to see its details: its **Name**, its **URL** and its **Keywords**, which you type wherever addresses are expected. A provider can have several keywords, separated by commas. **Character set** chooses the encoding for the query.

Most URLs have `\{@}` in them. These four characters are a placeholder, replaced by whatever you type after the colon between the keyword and your query. The button at the right of the field adds it.

Suppose the URL is `https://www.google.com/search?q=\{@}`, and `gg` is its keyword. Typing `gg:alpha` is the same as `https://www.google.com/search?q=alpha`. Whatever you type replaces `\{@}`, after being converted to the search provider's character set and URL-encoded. Only the `\{@}` part is changed. The rest should already be URL-encoded and is left alone.

You can also have shortcuts without a placeholder. If the URL is `file:/home/me/mydocs/words` and the keyword is `mywords`, typing `mywords:` is the same as typing the whole URL. There's nothing after the colon, but it's still needed for the shortcut to be recognized.

So although these are called web search keywords, they really are shortcuts to parameterized addresses, which can point to anything an address can, not just search engines.
