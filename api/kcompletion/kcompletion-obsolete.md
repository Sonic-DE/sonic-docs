---
title: "Obsolete Members for KCompletion"
description: "Deprecated members of KCompletion."
parent: "kcompletion/kcompletion"
---

# Obsolete Members for KCompletion

**The following members of class [KCompletion](kcompletion.md) are deprecated.** We strongly advise against using them in new code.

## Public Functions

- [void setSoundsEnabled(bool enable)](#setSoundsEnabled) (deprecated in 6.11)
- [bool soundsEnabled() const](#soundsEnabled) (deprecated in 6.11)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[virtual, deprecated in 6.11\] void KCompletion::setSoundsEnabled(bool *enable*) {#setSoundsEnabled}

This function is deprecated since 6.11. We strongly advise against using it in new code.

Enables/disables emitting a sound when

- [makeCompletion](kcompletion.md#makeCompletion)() can't find a match
- there is a partial completion (= multiple matches in Shell-completion mode)
- [nextMatch](kcompletion.md#nextMatch)() or [previousMatch](kcompletion.md#previousMatch)() hit the last possible match and the list is rotated

KNotifyClient() is used to emit the sounds.

`enable` true to enable sounds

not implemented

*See also* [soundsEnabled](kcompletion-obsolete.md#soundsEnabled)

### \[deprecated in 6.11\] bool KCompletion::soundsEnabled() const {#soundsEnabled}

This function is deprecated since 6.11. We strongly advise against using it in new code.

Tells you whether [KCompletion](kcompletion.md) will emit sounds on certain occasions.

Default is enabled.

Not implemented

Returns `true` if sounds are enabled

*See also* [setSoundsEnabled](kcompletion-obsolete.md#setSoundsEnabled)
