---
title: "KDESu C++ Classes"
description: "User interface for running shell commands with root privileges."
---

# KDESu C++ Classes

User interface for running shell commands with root privileges. [More...](#details)

## Classes {#classes}

- [KDESu::Client](kdesu-client.md): A client class to access kdesud, the KDE su daemon.
- [KDESu::PtyProcess](kdesu-ptyprocess.md): Synchronous communication with tty programs.
- [KDESu::SshProcess](kdesu-sshprocess.md): Executes a remote command, using ssh.
- [KDESu::StubProcess](kdesu-stubprocess.md): Chat with kdesu\_stub.
- [KDESu::SuProcess](kdesu-suprocess.md): Executes a command under elevated privileges, using su.

## Detailed Description {#details}

KDESU provides functionality for building GUI front ends for (password asking) console mode programs. For example, kdesu and kdessh use it to interface with su and ssh respectively.
