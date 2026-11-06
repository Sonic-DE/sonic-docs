---
title: Session environment variables
description: Set environment variables that apply to your whole desktop session.
source_url: https://userbase.kde.org/Session_Environment_Variables
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-workspace (startkde/startplasma.cpp, startkde/plasma-sourceenv.sh); read from code, not clicked through"
---

# Session environment variables

It's simple to set environment variables that affect your whole session. At startup, SonicDE runs any script it finds in `$HOME/.config/plasma-workspace/env` whose file name ends in `.sh`, and keeps all the environment variables set by them. Any variable you want to set must also be *exported*. Your system is already set up with certain values, so in the case of `PATH`, for instance, you need to add to the existing value rather than replace it.

To add folders to your [`PATH`](https://en.wikipedia.org/wiki/PATH_(variable)), create a file named `$HOME/.config/plasma-workspace/env/path.sh` with contents like this:

```sh
export PATH=$HOME/.local/bin:$PATH
```

Let's explore that. The `export` command tells the system that this should be kept and used when looking for files. Next comes the full name of the folder you want to add, here `$HOME/.local/bin`. Finally, there's the `$PATH` variable itself, because you want to add your new folder to the path, not replace it.

> **Warning:** To refer to your home folder here, use `$HOME`, not `~`.

That's often enough. As you get more familiar with the system, you'll probably want the same environment when using a console or reaching your machine through SSH. To do that, add something like this to the end of your `.bashrc`:

```sh
source $HOME/.config/plasma-workspace/env/path.sh
```

You can also see how this actually works. The X11 session starts through `startplasma-x11`. If you're interested in reading the code, it's in `startkde/startplasma.cpp` in the `sonic-workspace` repository. Search for `plasma-workspace/env`.

## See also

The [Autostart](../settings/autostart.md) module shows which scripts and applications run at login, and lets you add new ones.
