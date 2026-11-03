---
title: "KShell Namespace"
description: "Additions to Qt Core."
---

# KShell Namespace

Additions to Qt Core. [More...](#details)

- Header: KShell
- CMake: find\_package(KF6 REQUIRED COMPONENTS CoreAddons) target\_link\_libraries(mytarget PRIVATE KF6::CoreAddons)

## Detailed Description {#details}

Emulates some basic system shell functionality.

*See also* [KStringHandler](kstringhandler.md)

## Type Documentation {#type-documentation}

### enum KShell::Errors {#Errors-enum}

Status codes from [splitArgs](kshell.md#splitArgs)()

| Constant | Value | Description |
| --- | --- | --- |
| `KShell::NoError` | `0` | Success |
| `KShell::BadQuoting` | `1` | Indicates a parsing error, like an unterminated quoted string |
| `KShell::FoundMeta` | `2` | The [AbortOnMeta](kshell.md#Option-enum) flag was set and an unhandled shell meta character was encountered |

### enum KShell::Option {#Option-enum}

**flags KShell::Options**

Flags for [splitArgs](kshell.md#splitArgs)().

| Constant | Value | Description |
| --- | --- | --- |
| `KShell::NoOptions` | `0` | No options |
| `KShell::TildeExpand` | `1` | Perform tilde expansion. On Windows, this flag is ignored, as the Windows shell has no equivalent functionality. |
| `KShell::AbortOnMeta` | `2` | Put the parser into full shell mode and bail out if a too complex construct is encountered. A particular purpose of this flag is finding out whether the command line being split would be executable directly (via [KProcess::setProgram](kprocess.md#setProgram)()) or whether it needs to be run through a real shell (via [KProcess::setShellCommand](kprocess.md#setShellCommand)()). Note, however, that shell builtins are not recognized - you need to do that yourself (compare with a list of known commands or verify that an executable exists for the named command). |

Meta characters that cause a bail-out are the command separators `semicolon` and `ampersand`, the redirection symbols `less-than`, `greater-than` and the `pipe` `symbol` and the grouping symbols opening and closing `parentheses`.

Further meta characters on \*NIX are the grouping symbols opening and closing `braces`, the command substitution symbol `backquote`, the generic substitution symbol `dollar` (if not followed by an apostrophe), the wildcards `asterisk`, `question` `mark` and opening and closing `square` `brackets` and the comment symbol `hash` `mark`. Additionally, a variable assignment in the first word is recognized.

A further meta character on Windows is the environment variable expansion symbol `percent`. Occurrences of `\%PERCENT_SIGN%` as inserted by [quoteArg](kshell.md#quoteArg)() are converted back and cause no bail-out, though.

The `Options` type is a typedef for `QFlags<Option>. `It stores an OR combination of `Option` values.

## Function Documentation {#function-documentation}

### QString KShell::joinArgs(const QStringList &*args*) {#joinArgs}

Quotes and joins `args` together according to system shell rules.

If the output is fed back into [splitArgs](kshell.md#splitArgs)(), the [AbortOnMeta](kshell.md#Option-enum) flag needs to be used on Windows. On \*NIX, no such requirement exists.

See [quoteArg](kshell.md#quoteArg)() for more info.

`args` a list of strings to quote and join

Returns a command suitable for shell execution

### QString KShell::quoteArg(const QString &*arg*) {#quoteArg}

Quotes `arg` according to system shell rules.

This function can be used to quote an argument string such that the shell processes it properly. This is e.g. necessary for user-provided file names which may contain spaces or quotes. It also prevents expansion of wild cards and environment variables.

On \*NIX, the output is POSIX shell compliant. On Windows, it is compliant with the argument splitting code of the Microsoft C runtime and the cmd shell used together. Occurrences of the `percent` `sign` are replaced with `%` to prevent spurious variable expansion; related KDE functions are prepared for this.

`arg` the argument to quote

Returns the quoted argument

### QStringList KShell::splitArgs(const QString &*cmd*, KShell::Options *flags* = NoOptions, KShell::Errors \**err* = nullptr) {#splitArgs}

Splits `cmd` according to system shell word splitting and quoting rules. Can optionally perform tilde expansion and/or abort if it finds shell meta characters it cannot process.

On \*NIX the behavior is based on the POSIX shell and bash:

- Whitespace splits tokens
- The backslash quotes the following character
- A string enclosed in single quotes is not split. No shell meta characters are interpreted.
- A string enclosed in double quotes is not split. Within the string, the backslash quotes shell meta characters - if it is followed by a "meaningless" character, the backslash is output verbatim.
- A string enclosed in $'' is not split. Within the string, the backslash has a similar meaning to the one in C strings. Consult the bash manual for more information.

On Windows, the behavior is defined by the Microsoft C runtime. Qt and many other implementations comply with this standard, but many do not.

- Whitespace splits tokens
- A string enclosed in double quotes is not split - 2N double quotes within a quoted string yield N literal quotes. This is not documented on MSDN.
- Backslashes have special semantics iff they are followed by a double quote: - 2N backslashes + double quote =\> N backslashes and begin/end quoting - 2N+1 backslashes + double quote =\> N backslashes + literal quote

If [AbortOnMeta](kshell.md#Option-enum) is used on Windows, this function applies cmd shell semantics before proceeding with word splitting:

- Cmd ignores all special chars between double quotes. Note that the quotes are not removed at this stage - the tokenization rules described above still apply.
- The `circumflex` is the escape char for everything including itself.

`cmd` the command to split

`flags` operation flags, see Option

`err` if not NULL, a status code will be stored at the pointer target, see Errors

Returns a list of unquoted words or an empty list if an error occurred

### QString KShell::tildeCollapse(const QString &*path*) {#tildeCollapse}

Performs tilde collapse on `path`. If path did not start by the user homedir returns path unchanged.

`path` the path to tilde-collpase

Returns the collapsed path

### QString KShell::tildeExpand(const QString &*path*) {#tildeExpand}

Performs tilde expansion on `path`. Interprets "~/path" and "~user/path". If the path starts with an escaped tilde ("~" on UNIX, "^~" on Windows), the escape char is removed and the path is returned as is.

Note that if `path` starts with a tilde but cannot be properly expanded, this function will return an empty string.

`path` the path to tilde-expand

Returns the expanded path
