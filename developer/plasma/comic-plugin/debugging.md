---
title: Testing and debugging comic plugins
description: How to test a comic plugin and find what's wrong with it.
source_url: https://develop.kde.org/docs/plasma/comic-plugin/debugging/
source_authors: [Alexander Lohnau, Andrea Marano, Carl Schwan, Kunda Ki, Marius P, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "comic_package, cachedprovider and print in applets/comic/engine in sonic-workspace-addons; plasmawindowed's behavior from the widget testing page. No comic plugin was run."
---

# Testing and debugging comic plugins

## Testing the plugin

To test the plugin, first install it:

```bash
kpackagetool6 -t Plasma/Comic -i my_comic.comic
```

That installs it to `~/.local/share/plasma/comics/my_comic`. You can also edit `~/.local/share/plasma/comics/my_comic/contents/code/main.js` directly, but be sure to copy your changes back to your project.

To test your plugin, run the comic widget:

```bash
plasmawindowed org.kde.plasma.comic
```

and enable the plugin in the settings. The plugin is then loaded, and you see its debug output in the terminal.

Comic strips are cached in `~/.local/share/plasma_engine_comic/`, so if you change the plugin it can help to clear the cache before further testing:

```bash
rm -r ~/.local/share/plasma_engine_comic/
```

## Debugging the plugin

Sometimes your plugin won't work on the first attempt, and debugging can be difficult because there isn't much output unless you add it.

To watch variables and find where your plugin breaks, add `print` statements to `main.js`:

```js
function init() {
    // ...
    const url = "XY" + comic.identifier;
    print("***url: " + url);
    // ...
}

function pageRetrieved(id, data) {
    if (id === comic.Page) {
        print("****in comic.Page");
        // ...
        print("****a");
        // ...
        print("****b");
        // ...
        print("****id: " + comic.identifier);
    }
}
```

The `****` makes the output easier to find. If you don't spot the problem immediately, add more `print` statements to locate it.

`print` logs through the `org.kde.plasma.comic` debug category, so turn that on when you start the widget:

```bash
QT_LOGGING_RULES="org.kde.plasma.comic.debug=true" plasmawindowed org.kde.plasma.comic
```

If none of that helps and `pageRetrieved` is still called, try this to check whether the data is correct:

```js
print(data);
```
