---
title: "KSelectionOwner Class"
description: "ICCCM manager selection owner."
---

# KSelectionOwner Class

ICCCM manager selection owner. [More...](#details)

- **Header:** `#include <KSelectionOwner>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KWindowSystem)`  
  `target_link_libraries(mytarget PRIVATE KF6::KWindowSystem)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kselectionowner-members.md)

## Public Functions

- [KSelectionOwner(xcb\_atom\_t selection, int screen = -1, QObject \*parent = nullptr)](#KSelectionOwner)
- [KSelectionOwner(const char \*selection, int screen = -1, QObject \*parent = nullptr)](#KSelectionOwner-1)
- [KSelectionOwner(const char \*selection, xcb\_connection\_t \*c, xcb\_window\_t root, QObject \*parent = nullptr)](#KSelectionOwner-2)
- [KSelectionOwner(xcb\_atom\_t selection, xcb\_connection\_t \*c, xcb\_window\_t root, QObject \*parent = nullptr)](#KSelectionOwner-3)
- [~KSelectionOwner()](#dtor.KSelectionOwner)
- [void claim(bool force, bool force\_kill = true)](#claim)
- [xcb\_window\_t ownerWindow() const](#ownerWindow)
- [void release()](#release)

## Signals

- [void claimedOwnership()](#claimedOwnership)
- [void failedToClaimOwnership()](#failedToClaimOwnership)
- [void lostOwnership()](#lostOwnership)

## Protected Functions

- [bool genericReply(xcb\_atom\_t target, xcb\_atom\_t property, xcb\_window\_t requestor)](#genericReply)
- [void getAtoms()](#getAtoms)
- [void replyTargets(xcb\_atom\_t property, xcb\_window\_t requestor)](#replyTargets)
- [void setData(uint32\_t extra1, uint32\_t extra2)](#setData)

## Detailed Description {#details}

This class implements claiming and owning manager selections, as described in the ICCCM, section 2.8. The selection atom is passed to the constructor, [claim](kselectionowner.md#claim)() attempts to claim ownership of the selection, [release](kselectionowner.md#release)() gives up the selection ownership. Signal [lostOwnership](kselectionowner.md#lostOwnership)() is emitted when the selection is claimed by another owner.

This class is only useful on the xcb platform. On other platforms the code is only functional if the constructor overloads taking an xcb\_connection\_t are used. In case you inherit from this class ensure that you don't use xcb and/or XLib without verifying the platform.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KSelectionOwner::KSelectionOwner(xcb\_atom\_t *selection*, int *screen* = -1, QObject \**parent* = nullptr) {#KSelectionOwner}

This constructor initializes the object, but doesn't perform any operation on the selection.

`selection` atom representing the manager selection

`screen` X screen, or -1 for default

`parent` parent object, or nullptr if there is none

### \[explicit\] KSelectionOwner::KSelectionOwner(const char \**selection*, int *screen* = -1, QObject \**parent* = nullptr) {#KSelectionOwner-1}

This constructor accepts the selection name and creates the appropriate atom for it automatically.

`selection` name of the manager selection

`screen` X screen, or -1 for default

`parent` parent object, or nullptr if there is none

This is an overloaded function.

### \[explicit\] KSelectionOwner::KSelectionOwner(const char \**selection*, xcb\_connection\_t \**c*, xcb\_window\_t *root*, QObject \**parent* = nullptr) {#KSelectionOwner-2}

This constructor accepts the xcb\_connection\_t and root window and doesn't depend on running on the xcb platform. Otherwise this constructor behaves like the similar one without the xcb\_connection\_t.

`selection` name of the manager selection

`c` the xcb connection this [KSelectionWatcher](kselectionwatcher.md) should use

`root` the root window this [KSelectionWatcher](kselectionwatcher.md) should use

`parent` parent object, or nullptr if there is none

This is an overloaded function.

### \[explicit\] KSelectionOwner::KSelectionOwner(xcb\_atom\_t *selection*, xcb\_connection\_t \**c*, xcb\_window\_t *root*, QObject \**parent* = nullptr) {#KSelectionOwner-3}

This constructor accepts the xcb\_connection\_t and root window and doesn't depend on running on the xcb platform. Otherwise this constructor behaves like the similar one without the xcb\_connection\_t.

`selection` atom representing the manager selection

`c` the xcb connection this [KSelectionWatcher](kselectionwatcher.md) should use

`root` the root window this [KSelectionWatcher](kselectionwatcher.md) should use

`parent` parent object, or nullptr if there is none

This is an overloaded function.

### \[override virtual noexcept\] KSelectionOwner::~KSelectionOwner() {#dtor.KSelectionOwner}

Destructor. Calls [release](kselectionowner.md#release)().

### void KSelectionOwner::claim(bool *force*, bool *force\_kill* = true) {#claim}

Try to claim ownership of the manager selection using the current X timestamp.

This function returns immediately, but it may take up to one second for the claim to succeed or fail, at which point either the [claimedOwnership](kselectionowner.md#claimedOwnership)() or [failedToClaimOwnership](kselectionowner.md#failedToClaimOwnership)() signal is emitted. The claim will not be completed until the caller has returned to the event loop.

If `force` is false, and the selection is already owned, the selection is not claimed, and [failedToClaimOwnership](kselectionowner.md#failedToClaimOwnership)() is emitted. If `force` is true and the selection is owned by another client, the client will be given one second to relinquish ownership of the selection. If `force_kill` is true, and the previous owner fails to disown the selection in time, it will be forcibly killed.

### \[signal\] void KSelectionOwner::claimedOwnership() {#claimedOwnership}

This signal is emitted when [claim](kselectionowner.md#claim)() was successful in claiming ownership of the selection.

### \[signal\] void KSelectionOwner::failedToClaimOwnership() {#failedToClaimOwnership}

This signal is emitted when [claim](kselectionowner.md#claim)() failed to claim ownership of the selection.

### \[virtual protected\] bool KSelectionOwner::genericReply(xcb\_atom\_t *target*, xcb\_atom\_t *property*, xcb\_window\_t *requestor*) {#genericReply}

Called when a SelectionRequest event is received. A reply should be sent using the selection handling mechanism described in the ICCCM section 2.

`target` requested target type

`property` property to use for the reply data

`requestor` requestor window

### \[virtual protected\] void KSelectionOwner::getAtoms() {#getAtoms}

Called to create atoms needed for claiming the selection and communication using the selection handling mechanism. The default implementation must be called if reimplemented. This method may be called repeatedly.

### \[signal\] void KSelectionOwner::lostOwnership() {#lostOwnership}

This signal is emitted if the selection was owned and the ownership has been lost due to another client claiming it, this signal is emitted. IMPORTANT: It's not safe to delete the instance in a slot connected to this signal.

### xcb\_window\_t KSelectionOwner::ownerWindow() const {#ownerWindow}

If the selection is owned, returns the window used internally for owning the selection.

### void KSelectionOwner::release() {#release}

If the selection is owned, the ownership is given up.

### \[virtual protected\] void KSelectionOwner::replyTargets(xcb\_atom\_t *property*, xcb\_window\_t *requestor*) {#replyTargets}

Called to announce the supported targets, as described in the ICCCM section 2.6. The default implementation announces the required targets MULTIPLE, TIMESTAMP and TARGETS.

### \[protected\] void KSelectionOwner::setData(uint32\_t *extra1*, uint32\_t *extra2*) {#setData}

Sets extra data to be sent in the message sent to root window after successfully claiming a selection. These extra data are in data.l\[3\] and data.l\[4\] fields of the XClientMessage.
