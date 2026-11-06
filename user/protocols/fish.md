---
title: fish
description: Access another computer's files over SSH.
source_url: https://invent.kde.org/network/kio-extras/-/blob/master/doc/kioworker/fish/index.docbook
source_authors: [Jörg Walter, Brad Hards]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-frameworks-io-extras 368b2196 (fish); read from code, not clicked through"
---

# fish

The fish KIO worker lets you access another computer's files using the *S*ecure *SH*ell (SSH) protocol. The remote computer needs to be running the SSH daemon, but the rest of the protocol uses standard command line tools, as discussed below.

Use it like this: `fish://hostname` or `fish://username@hostname`.

> [!NOTE]
> You need to use double forward slashes.

You can leave out the username, and the trailing `@` symbol, if you have the same username on both computers.

You can add a password in the format `fish://username:password@hostname`, but it isn't necessary, because you're asked for one if it isn't supplied.

If the SSH daemon runs on a non-standard port, you can specify that port using the normal URL syntax: `fish://hostname:portnumber`.

Fish should work with any roughly POSIX compatible UNIX based remote computer. It uses the shell commands `cat`, `chgrp`, `chmod`, `chown`, `cp`, `dd`, `env`, `expr`, `grep`, `ls`, `mkdir`, `mv`, `rm`, `rmdir`, `sed` and `wc`. It starts `/bin/sh` as its shell, and expects it to be a Bourne shell or compatible, like `bash`. If the `sed` and `file` commands are available, as well as a `/etc/apache/magic` file with MIME type signatures, these are used to guess MIME types.

If Perl is available on the remote machine, it's used instead. Then only `env` and `/bin/sh` are needed. Using Perl also has the benefit of being faster.

Fish may even work on Windows machines, if tools like Cygwin are installed. All the above utilities must be in the system `PATH`, and the initial shell must be able to process the command `echo FISH:;/bin/sh` correctly.
