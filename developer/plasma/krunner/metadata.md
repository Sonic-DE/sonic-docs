---
title: KRunner metadata format
description: The metadata keys of C++ and D-Bus runners.
source_url: https://develop.kde.org/docs/plasma/krunner/metadata/
source_authors: [Alexander Lohnau, Carl Schwan, Joshua Wug, Marius P, Nate Graham, Nicolas Fella, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "dbusrunner, runnermanager and kpluginmetadata_utils_p.h in sonic-frameworks-runner; the org.kde.krunner1 interface; read from code, no D-Bus runner was run"
---

# KRunner metadata format

## Universal properties

These include user-visible keys such as `Name`, `Icon` and `Description`, shown in places like the list of search plugins in System Settings.

`EnabledByDefault` should be `true`; otherwise the user has to enable the plugin by ticking its checkbox.

`Authors`, `License` and `Website` appear in the runner's About dialog. [KPluginMetaData](/docs/api/kcoreaddons/kpluginmetadata) describes more keys.

### Deduplication

KRunner can deduplicate matches based on their ID. This isn't on by default, to avoid side effects for plugins that don't define their IDs. An ID set with `setId()` should look like a URL, such as `file:///home/user/foo` or `exec:///bin/konsole`.

To have your plugin's results deduplicated, set `X-Plasma-Runner-Unique-Results` to `true`.

KRunner then has to decide which match to show. To say your matches are less relevant than those from other runners, set `X-Plasma-Runner-Weak-Results` to `true`. A plugin that searches for files and uses the file URL as its ID might use this. If the user enters a full path such as `/home/user/foo`, the plugin and the Locations runner could produce a match for the same URL, and this property makes the Locations runner win. That's desirable, because that runner provides only exact matches.

```json
{
    "KPlugin": {
        "Description": "Example Description",
        "EnabledByDefault": true,
        "Icon": "user-home",
        "Name": "My Runner"
    },
    "X-Plasma-Runner-Unique-Results": true,
    "X-Plasma-Runner-Weak-Results": true
}
```

## D-Bus runner properties

A runner can also be a separate program that provides the `org.kde.krunner1` D-Bus interface, described in [`org.kde.krunner1.xml`](https://github.com/Sonic-DE/sonic-frameworks-runner/blob/master/src/data/org.kde.krunner1.xml). Its metadata is in a `.desktop` file in the `krunner/dbusplugins` data directory, such as `~/.local/share/krunner/dbusplugins/`. KRunner parses this at runtime and converts it to JSON.

The most important key is `X-Plasma-API`, which marks the plugin as a D-Bus runner and sets its supported API. It is `DBus` or `DBus2`. With `DBus2`, KRunner calls the interface's `Config` method, which allows configuration at runtime. With `DBus`, everything else works.

`X-Plasma-DBusRunner-Service` tells KRunner which service name to query. For several service names, it can end in `*`, such as `org.example.testrunner.*`. `X-Plasma-DBusRunner-Path` says at which object path the runner is registered.

### Providing usage help

D-Bus runners can't use [RunnerSyntax](/docs/api/krunner/krunner-runnersyntax) directly, so they can list their syntaxes in the metadata. The [help runner](https://github.com/Sonic-DE/sonic-workspace/tree/master/runners/helprunner) shows them.

Define `X-Plasma-Runner-Syntaxes` and `X-Plasma-Runner-Syntax-Descriptions`, both comma-separated lists of the same size. Each description belongs to the syntax at the same position.

`:q:` is a placeholder that expands to "search term", or its translation, in angle brackets, so you don't have to duplicate or translate that text. For a more precise description than "search term", put your own text in angle brackets too, such as `myrunner <files to search for>`.

### Reducing queries and D-Bus activation

Some runners have a prefix or pattern that must match. Others run expensive queries that should be avoided for short strings.

For these, set an integer in `X-Plasma-Runner-Min-Letter-Count` to return results only after that many letters have been typed. It's equivalent to `setMinLetterCount()` in the C++ API. Only do this with good reason, and don't go above 2 without *very* good reason. High counts can frustrate people who expect results after the first letter, especially in languages like Chinese, which is so dense in information that 2 characters or fewer can give good results.

Another strategy is to filter text with `X-Plasma-Runner-Match-Regex`, equivalent to `setMatchRegex()`.

Finally, `X-Plasma-Request-Actions-Once` makes KRunner ask for the actions only once, before the runner is first queried. This avoids many unneeded D-Bus calls and object creations if the actions stay the same during your runner's lifetime.

```ini
[Desktop Entry]
Name=My Runner
Description=Example Description
Type=Service
Icon=user-home
X-KDE-PluginInfo-Author=YourName
X-KDE-PluginInfo-Email=your.name@example.org
X-KDE-PluginInfo-Name=myrunner
X-KDE-PluginInfo-Version=1.0
X-KDE-PluginInfo-License=LGPL
X-KDE-PluginInfo-EnabledByDefault=true

X-Plasma-API=DBus
X-Plasma-DBusRunner-Service=org.example.myrunner
X-Plasma-DBusRunner-Path=/runner

# Only set this for a good reason
X-Plasma-Runner-Min-Letter-Count=2

# Only set this for a good reason
X-Plasma-Request-Actions-Once=true

# Only set this for a good reason
# This means that the query must start with one or more lowercase letters
X-Plasma-Runner-Match-Regex=^[a-z]+

X-Plasma-Runner-Syntaxes=:q:,myrunner :q:,otherprefix <more specific query>
X-Plasma-Runner-Syntax-Descriptions=Description for example query,Description for example query with prefix,Description for other prefix
```
