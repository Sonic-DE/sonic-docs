---
title: "KPty Class"
description: "Provides primitives for opening & closing a pseudo TTY pair, assigning the controlling TTY, utmp registration and setting various terminal attributes."
---

# KPty Class

Provides primitives for opening & closing a pseudo TTY pair, assigning the controlling TTY, utmp registration and setting various terminal attributes. [More...](#details)

- **Header:** `#include <KPty>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Pty)`  
  `target_link_libraries(mytarget PRIVATE KF6::Pty)`
- **Inherited By:** [KPtyDevice](kptydevice.md)

[List of all members, including inherited members](kpty-members.md)

## Public Functions

- [KPty()](#KPty)
- [~KPty()](#dtor.KPty)
- [void close()](#close)
- [void closeSlave()](#closeSlave)
- [void login(const char \*user = nullptr, const char \*remotehost = nullptr)](#login)
- [void logout()](#logout)
- [int masterFd() const](#masterFd)
- [bool open()](#open)
- [bool open(int fd)](#open-1)
- [bool openSlave()](#openSlave)
- [void setCTty()](#setCTty)
- [void setCTtyEnabled(bool enable)](#setCTtyEnabled)
- [bool setEcho(bool echo)](#setEcho)
- [bool setWinSize(int lines, int columns, int height, int width)](#setWinSize)
- [bool setWinSize(int lines, int columns)](#setWinSize-1)
- [int slaveFd() const](#slaveFd)
- [bool tcGetAttr(struct termios \*ttmode) const](#tcGetAttr)
- [bool tcSetAttr(struct termios \*ttmode)](#tcSetAttr)
- [const char \*ttyName() const](#ttyName)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### KPty::KPty() {#KPty}

Constructor

### \[noexcept\] KPty::~KPty() {#dtor.KPty}

Destructor:

If the pty is still open, it will be closed. Note, however, that an utmp registration is not undone.

### void KPty::close() {#close}

Close the pty master/slave pair.

### void KPty::closeSlave() {#closeSlave}

Close the pty slave descriptor.

When creating the pty, [KPty](kpty.md) also opens the slave and keeps it open. Consequently the master will never receive an EOF notification. Usually this is the desired behavior, as a closed pty slave can be reopened any time - unlike a pipe or socket. However, in some cases pipe-alike behavior might be desired.

After this function was called, [slaveFd](kpty.md#slaveFd)() and [setCTty](kpty.md#setCTty)() cannot be used.

### void KPty::login(const char \**user* = nullptr, const char \**remotehost* = nullptr) {#login}

Creates an utmp entry for the tty. This function must be called after calling [setCTty](kpty.md#setCTty) and making this pty the stdin.

`user` the user to be logged on

`remotehost` the host from which the login is coming. This is not the local host. For remote logins it should be the hostname of the client. For local logins from inside an X session it should be the name of the X display. Otherwise it should be empty.

### void KPty::logout() {#logout}

Removes the utmp entry for this tty.

### int KPty::masterFd() const {#masterFd}

Returns the file descriptor of the master pty

This function should be called only while the pty is open.

### bool KPty::open() {#open}

Create a pty master/slave pair.

Returns true if a pty pair was successfully opened

### bool KPty::open(int *fd*) {#open-1}

Open using an existing pty master.

`fd` an open pty master file descriptor. The ownership of the fd remains with the caller; it will not be automatically closed at any point.

Returns true if a pty pair was successfully opened

### bool KPty::openSlave() {#openSlave}

Open the pty slave descriptor.

This undoes the effect of [closeSlave](kpty.md#closeSlave)().

Returns true if the pty slave was successfully opened

### void KPty::setCTty() {#setCTty}

Creates a new session and process group and makes this pty the controlling tty.

### void KPty::setCTtyEnabled(bool *enable*) {#setCTtyEnabled}

Whether this will be a controlling terminal

This is on by default. Disabling the controllig aspect only makes sense if another process will take over control or there is nothing to control or for technical reasons control cannot be set (this notably is the case with flatpak-spawn when used inside a sandbox).

`enable` whether to enable ctty set up

### bool KPty::setEcho(bool *echo*) {#setEcho}

Set whether the pty should echo input.

Echo is on by default. If the output of automatically fed (non-interactive) PTY clients needs to be parsed, disabling echo often makes it much simpler.

This function can be used only while the PTY is open.

`echo` true if input should be echoed.

Returns true on success, false otherwise

### bool KPty::setWinSize(int *lines*, int *columns*, int *height*, int *width*) {#setWinSize}

Change the logical (screen) size of the pty. The default is 24 lines by 80 columns in characters, and zero pixels.

This function can be used only while the PTY is open.

`lines` the number of character rows

`columns` the number of character columns

`height` the view height in pixels

`width` the view width in pixels

Returns true on success, false otherwise

### bool KPty::setWinSize(int *lines*, int *columns*) {#setWinSize-1}

Change the logical (screen) size of the pty. The pixel size is set to zero.

This is an overloaded function.

### int KPty::slaveFd() const {#slaveFd}

Returns the file descriptor of the slave pty

This function should be called only while the pty slave is open.

### bool KPty::tcGetAttr(struct termios \**ttmode*) const {#tcGetAttr}

Wrapper around tcgetattr(3).

This function can be used only while the PTY is open. You will need an \#include \<termios.h\> to do anything useful with it.

`ttmode` a pointer to a termios structure. Note: when declaring ttmode, struct ::termios must be used - without the '::' some version of HP-UX thinks, this declares the struct in your class, in your method.

Returns `true` on success, false otherwise

### bool KPty::tcSetAttr(struct termios \**ttmode*) {#tcSetAttr}

Wrapper around tcsetattr(3) with mode TCSANOW.

This function can be used only while the PTY is open.

`ttmode` a pointer to a termios structure.

Returns true on success, false otherwise. Note that success means that at least one attribute could be set.

### const char \*KPty::ttyName() const {#ttyName}

Returns the name of the slave pty device.

This function should be called only while the pty is open.
