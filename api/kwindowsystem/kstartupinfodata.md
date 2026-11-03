---
title: "KStartupInfoData Class"
description: "Class representing data about an application startup notification."
---

# KStartupInfoData Class

Class representing data about an application startup notification. [More...](#details)

- **Header:** `#include <KStartupInfo>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KWindowSystem)`  
  `target_link_libraries(mytarget PRIVATE KF6::KWindowSystem)`

[List of all members, including inherited members](kstartupinfodata-members.md)

## Public Types

- [enum KStartupInfoData::TriState](#TriState-enum)

## Public Functions

- [KStartupInfoData()](#KStartupInfoData)
- [KStartupInfoData(const KStartupInfoData &data)](#KStartupInfoData-1)
- [QByteArray WMClass() const](#WMClass)
- [void addPid(pid\_t pid)](#addPid)
- [QString applicationId() const](#applicationId)
- [const QString &bin() const](#bin)
- [const QString &description() const](#description)
- [int desktop() const](#desktop)
- [const QString &findDescription() const](#findDescription)
- [const QString &findIcon() const](#findIcon)
- [const QString &findName() const](#findName)
- [const QByteArray findWMClass() const](#findWMClass)
- [QByteArray hostname() const](#hostname)
- [const QString &icon() const](#icon)
- [bool is\_pid(pid\_t pid) const](#is_pid)
- [const QString &name() const](#name)
- [QList\<pid\_t\> pids() const](#pids)
- [int screen() const](#screen)
- [void setApplicationId(const QString &desktop)](#setApplicationId)
- [void setBin(const QString &bin)](#setBin)
- [void setDescription(const QString &descr)](#setDescription)
- [void setDesktop(int desktop)](#setDesktop)
- [void setHostname(const QByteArray &hostname = QByteArray())](#setHostname)
- [void setIcon(const QString &icon)](#setIcon)
- [void setName(const QString &name)](#setName)
- [void setScreen(int screen)](#setScreen)
- [void setSilent(KStartupInfoData::TriState state)](#setSilent)
- [void setWMClass(const QByteArray &wmclass)](#setWMClass)
- [void setXinerama(int xinerama)](#setXinerama)
- [KStartupInfoData::TriState silent() const](#silent)
- [void update(const KStartupInfoData &data)](#update)
- [int xinerama() const](#xinerama)

## Detailed Description {#details}

Such data include the icon of the starting application, the desktop on which the application should start, the binary name of the application, etc.

*See also* [KStartupInfo](kstartupinfo.md), [KStartupInfoId](kstartupinfoid.md)

## Member Type Documentation {#member-type-documentation}

### enum KStartupInfoData::TriState {#TriState-enum}

| Constant |   |
| --- | --- |
| `KStartupInfoData::Yes` | `0` |
| `KStartupInfoData::No` | `1` |
| `KStartupInfoData::Unknown` | `2` |

## Member Function Documentation {#member-function-documentation}

### KStartupInfoData::KStartupInfoData() {#KStartupInfoData}

Constructor. Initializes all the data to their default empty values.

### KStartupInfoData::KStartupInfoData(const KStartupInfoData &*data*) {#KStartupInfoData-1}

Copy constructor.

### QByteArray KStartupInfoData::WMClass() const {#WMClass}

Returns the WM\_CLASS value for the startup notification, or empty if not available.

*See also* [setWMClass](kstartupinfodata.md#setWMClass)()

### void KStartupInfoData::addPid(pid\_t *pid*) {#addPid}

Adds a PID `pid` to the list of processes that belong to the startup notification.

It may be used to increase the chance that the windows created by the starting application will be detected correctly, and also for detecting if the application has quit without creating any window.

### QString KStartupInfoData::applicationId() const {#applicationId}

The .desktop file used to initiate this startup notification, or empty.

This information should be used only to identify the application, not to read any additional information.

*See also* [setApplicationId](kstartupinfodata.md#setApplicationId)()

### const QString &KStartupInfoData::bin() const {#bin}

Returns the binary name of the starting application.

*See also* [setBin](kstartupinfodata.md#setBin)()

### const QString &KStartupInfoData::description() const {#description}

Returns the name of the startup notification, or an empty string if not set.

*See also* [setDescription](kstartupinfodata.md#setDescription)()

### int KStartupInfoData::desktop() const {#desktop}

Returns the desktop for the startup notification.

*See also* [setDesktop](kstartupinfodata.md#setDesktop)()

### const QString &KStartupInfoData::findDescription() const {#findDescription}

Returns the description of the startup notification.

If it's not available, it returns [name](kstartupinfodata.md#name)().

### const QString &KStartupInfoData::findIcon() const {#findIcon}

Returns the icon of the startup notification, and if it's not available, tries to get it from the binary name.

### const QString &KStartupInfoData::findName() const {#findName}

Returns the name of the startup notification.

If it's not available, it tries to use other information (binary name).

### const QByteArray KStartupInfoData::findWMClass() const {#findWMClass}

Returns the WM\_CLASS value for the startup notification, or binary name if not available.

### QByteArray KStartupInfoData::hostname() const {#hostname}

Returns the hostname for the startup notification.

*See also* [setHostname](kstartupinfodata.md#setHostname)()

### const QString &KStartupInfoData::icon() const {#icon}

Returns the name of the startup notification icon, or an empty string if not set.

*See also* [setIcon](kstartupinfodata.md#setIcon)()

### bool KStartupInfoData::is\_pid(pid\_t *pid*) const {#is_pid}

Returns `true` if the given `pid` is in the list of PIDs for the startup notification

### const QString &KStartupInfoData::name() const {#name}

Returns the name of the startup notification, or an empty string if not set.

*See also* [setName](kstartupinfodata.md#setName)()

### QList\<pid\_t\> KStartupInfoData::pids() const {#pids}

Returns all PIDs for the startup notification.

### int KStartupInfoData::screen() const {#screen}

The X11 screen on which the startup notification is happening, -1 if unknown.

*See also* [setScreen](kstartupinfodata.md#setScreen)()

### void KStartupInfoData::setApplicationId(const QString &*desktop*) {#setApplicationId}

Sets the `desktop` file that was used to initiate the startup notification.

*See also* [applicationId](kstartupinfodata.md#applicationId)()

### void KStartupInfoData::setBin(const QString &*bin*) {#setBin}

Sets the binary name `bin` of the application (e.g. 'kcontrol').

*See also* [bin](kstartupinfodata.md#bin)()

### void KStartupInfoData::setDescription(const QString &*descr*) {#setDescription}

Sets the description `descr` for the notification (e.g. 'Launching Control Center').

That is, [name](kstartupinfodata.md#name)() describes what is being started, while [description](kstartupinfodata.md#description)() is the actual action performed by the starting.

*See also* [description](kstartupinfodata.md#description)()

### void KStartupInfoData::setDesktop(int *desktop*) {#setDesktop}

Sets the `desktop` for the startup notification (i.e. the desktop on which the starting application should appear).

*See also* [desktop](kstartupinfodata.md#desktop)()

### void KStartupInfoData::setHostname(const QByteArray &*hostname* = QByteArray()) {#setHostname}

Sets the `hostname` on which the application is starting.

It's necessary to set it if PIDs are set. If it's a null string, the current hostname is used.

*See also* [hostname](kstartupinfodata.md#hostname)()

### void KStartupInfoData::setIcon(const QString &*icon*) {#setIcon}

Sets the `icon` for the startup notification (e.g. 'kcontrol').

*See also* [icon](kstartupinfodata.md#icon)()

### void KStartupInfoData::setName(const QString &*name*) {#setName}

Sets the `name` for the notification (e.g. 'Control Center').

*See also* [name](kstartupinfodata.md#name)()

### void KStartupInfoData::setScreen(int *screen*) {#setScreen}

Sets the X11 `screen` on which the startup notification should happen.

This is usually not necessary to set, as it's set by default to QX11Info::screen().

*See also* [screen](kstartupinfodata.md#screen)()

### void KStartupInfoData::setSilent(KStartupInfoData::TriState *state*) {#setSilent}

Sets whether the visual feedback for this startup notification with the given `state` should be silenced (temporarily suspended).

*See also* [silent](kstartupinfodata.md#silent)()

### void KStartupInfoData::setWMClass(const QByteArray &*wmclass*) {#setWMClass}

Sets a WM\_CLASS value `wmclass` for the startup notification.

It may be used for increasing the chance that the windows created by the starting application will be detected correctly.

### void KStartupInfoData::setXinerama(int *xinerama*) {#setXinerama}

Sets the `xinerama` screen for the startup notification (i.e. the screeen on which the starting application should appear).

*See also* [xinerama](kstartupinfodata.md#xinerama)()

### KStartupInfoData::TriState KStartupInfoData::silent() const {#silent}

Returns [KStartupInfoData::Yes](kstartupinfodata.md#TriState-enum) if visual feedback for the startup notification is silenced.

*See also* [setSilent](kstartupinfodata.md#setSilent)()

### void KStartupInfoData::update(const KStartupInfoData &*data*) {#update}

Updates the notification data from the given `data`.

Some data, such as the desktop or the name, won't be rewritten if already set.

### int KStartupInfoData::xinerama() const {#xinerama}

The Xinerama screen for the startup notification, -1 if unknown.

*See also* [setXinerama](kstartupinfodata.md#setXinerama)()
