---
title: "KServiceGroup Class"
description: "KServiceGroup represents a group of service, for example screensavers."
---

# KServiceGroup Class

[KServiceGroup](kservicegroup.md) represents a group of service, for example screensavers. [More...](#details)

- **Header:** `#include <KServiceGroup>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Service)`  
  `target_link_libraries(mytarget PRIVATE KF6::Service)`
- **Inherits:** [KSycocaEntry](ksycocaentry.md)

[List of all members, including inherited members](kservicegroup-members.md)

## Public Types

- [enum KServiceGroup::EntriesOption](#EntriesOption-enum)
- [KServiceGroup::List](#List-typedef)
- [KServiceGroup::Ptr](#Ptr-typedef)
- [KServiceGroup::SPtr](#SPtr-typedef)

## Public Functions

- [KServiceGroup(const QString &name)](#KServiceGroup)
- [KServiceGroup(const QString &\_fullpath, const QString &\_relpath)](#KServiceGroup-1)
- [bool allowInline() const](#allowInline)
- [QString baseGroupName() const](#baseGroupName)
- [QString caption() const](#caption)
- [int childCount() const](#childCount)
- [QString comment() const](#comment)
- [QString directoryEntryPath() const](#directoryEntryPath)
- [KServiceGroup::List entries(bool sorted = false)](#entries)
- [KServiceGroup::List entries(bool sorted, bool excludeNoDisplay)](#entries-1)
- [KServiceGroup::List entries(bool sorted, bool excludeNoDisplay, bool allowSeparators, bool sortByGenericName = false)](#entries-2)
- [QList\<KServiceGroup::Ptr\> groupEntries(KServiceGroup::EntriesOptions options = ExcludeNoDisplay)](#groupEntries)
- [QString icon() const](#icon)
- [bool inlineAlias() const](#inlineAlias)
- [int inlineValue() const](#inlineValue)
- [bool noDisplay() const](#noDisplay)
- [QString relPath() const](#relPath)
- [KService::List serviceEntries(KServiceGroup::EntriesOptions options = ExcludeNoDisplay)](#serviceEntries)
- [void setAllowInline(bool \_b)](#setAllowInline)
- [void setInlineAlias(bool \_b)](#setInlineAlias)
- [void setInlineValue(int \_val)](#setInlineValue)
- [void setShowEmptyMenu(bool b)](#setShowEmptyMenu)
- [void setShowInlineHeader(bool \_b)](#setShowInlineHeader)
- [bool showEmptyMenu() const](#showEmptyMenu)
- [bool showInlineHeader() const](#showInlineHeader)
- [QStringList suppressGenericNames() const](#suppressGenericNames)

## Static Public Members

- [KServiceGroup::Ptr childGroup(const QString &parent)](#childGroup)
- [KServiceGroup::Ptr group(const QString &relPath)](#group)
- [KServiceGroup::Ptr root()](#root)

## Detailed Description {#details}

This class is typically used like this:

```cpp
// Start from root group
KServiceGroup::Ptr group = KServiceGroup::root();
if (!group || !group->isValid()) return;

KServiceGroup::List list = group->entries();

// Iterate over all entries in the group
for( KServiceGroup::List::ConstIterator it = list.begin();
     it != list.end(); it++)
{
   KSycocaEntry *p = (*it);
   if (p->isType(KST_KService))
   {
      KService *s = static_cast<KService *>(p);
      printf("Name = %s\n", s->name().toLatin1());
   }
   else if (p->isType(KST_KServiceGroup))
   {
      KServiceGroup *g = static_cast<KServiceGroup *>(p);
      // Sub group ...
   }
}
```

## Member Type Documentation {#member-type-documentation}

### enum KServiceGroup::EntriesOption {#EntriesOption-enum}

**flags KServiceGroup::EntriesOptions**

Options for [groupEntries](kservicegroup.md#groupEntries) and [serviceEntries](kservicegroup.md#serviceEntries)

| Constant | Value | Description |
| --- | --- | --- |
| `KServiceGroup::NoOptions` | `0x0` | no options set |
| `KServiceGroup::SortEntries` | `0x1` | sort items |
| `KServiceGroup::ExcludeNoDisplay` | `0x2` | exclude items marked "NoDisplay" |
| `KServiceGroup::AllowSeparators` | `0x4` | allow separator items to be included |
| `KServiceGroup::SortByGenericName` | `0x8` | sort by GenericName+Name instead of Name+GenericName |

The `EntriesOptions` type is a typedef for `QFlags<EntriesOption>. `It stores an OR combination of `EntriesOption` values.

### KServiceGroup::List {#List-typedef}

A list of shared data pointers for [KSycocaEntry](ksycocaentry.md).

### KServiceGroup::Ptr {#Ptr-typedef}

A shared data pointer for [KServiceGroup](kservicegroup.md).

### KServiceGroup::SPtr {#SPtr-typedef}

A shared data pointer for [KSycocaEntry](ksycocaentry.md).

## Member Function Documentation {#member-function-documentation}

### KServiceGroup::KServiceGroup(const QString &*name*) {#KServiceGroup}

Construct a dummy servicegroup indexed with `name`.

`name` the name of the service group

### KServiceGroup::KServiceGroup(const QString &*\_fullpath*, const QString &*\_relpath*) {#KServiceGroup-1}

Construct a service and take all information from a config file

`_fullpath` full path to the config file

`_relpath` relative path to the config file

### bool KServiceGroup::allowInline() const {#allowInline}

Return `true` if we allow to inline menu.

*See also* [setAllowInline](kservicegroup.md#setAllowInline)()

### QString KServiceGroup::baseGroupName() const {#baseGroupName}

Returns a non-empty string if the group is a special base group.

By default, "Settings/" is the kcontrol base group ("settings") and "System/Screensavers/" is the screensavers base group ("screensavers"). This allows moving the groups without breaking those apps.

The base group is defined by the X-KDE-BaseGroup key in the .directory file.

### QString KServiceGroup::caption() const {#caption}

Returns the caption of this group.

### int KServiceGroup::childCount() const {#childCount}

Returns the total number of displayable services in this group and any of its subgroups.

### \[static\] KServiceGroup::Ptr KServiceGroup::childGroup(const QString &*parent*) {#childGroup}

Returns the group of services that have X-KDE-ParentApp equal to `parent` (siblings).

`parent` the name of the service's parent

### QString KServiceGroup::comment() const {#comment}

Returns the comment about this service group.

### QString KServiceGroup::directoryEntryPath() const {#directoryEntryPath}

Returns a path to the .directory file describing this service group. The path is either absolute or relative to the "apps" resource.

### KServiceGroup::List KServiceGroup::entries(bool *sorted* = false) {#entries}

List of all Services and ServiceGroups within this ServiceGroup.

`sorted` true to sort items

Returns the list of entried

### KServiceGroup::List KServiceGroup::entries(bool *sorted*, bool *excludeNoDisplay*) {#entries-1}

### KServiceGroup::List KServiceGroup::entries(bool *sorted*, bool *excludeNoDisplay*, bool *allowSeparators*, bool *sortByGenericName* = false) {#entries-2}

List of all Services and ServiceGroups within this ServiceGroup.

`sorted` true to sort items

`excludeNoDisplay` true to exclude items marked "NoDisplay"

`allowSeparators` true to allow separator items to be included

`sortByGenericName` true to sort GenericName+Name instead of Name+GenericName

Returns the list of entries

### \[static\] KServiceGroup::Ptr KServiceGroup::group(const QString &*relPath*) {#group}

Returns the group with the given relative path.

`relPath` the path of the service group

### QList\<KServiceGroup::Ptr\> KServiceGroup::groupEntries(KServiceGroup::EntriesOptions *options* = ExcludeNoDisplay) {#groupEntries}

subgroups for this service group

### QString KServiceGroup::icon() const {#icon}

Returns the name of the icon associated with the group.

### bool KServiceGroup::inlineAlias() const {#inlineAlias}

Returns `true` to show an inline alias item into menu

*See also* [setInlineAlias](kservicegroup.md#setInlineAlias)()

### int KServiceGroup::inlineValue() const {#inlineValue}

Returns inline limit value

*See also* [setInlineValue](kservicegroup.md#setInlineValue)()

### bool KServiceGroup::noDisplay() const {#noDisplay}

Returns `true` if the NoDisplay flag was set, i.e. if this group should be hidden from menus, while still being in ksycoca.

### QString KServiceGroup::relPath() const {#relPath}

Returns the relative path of the service group.

### \[static\] KServiceGroup::Ptr KServiceGroup::root() {#root}

Returns the root service group.

### KService::List KServiceGroup::serviceEntries(KServiceGroup::EntriesOptions *options* = ExcludeNoDisplay) {#serviceEntries}

entries of this service group

### void KServiceGroup::setAllowInline(bool *\_b*) {#setAllowInline}

*See also* [allowInline](kservicegroup.md#allowInline)()

### void KServiceGroup::setInlineAlias(bool *\_b*) {#setInlineAlias}

*See also* [inlineAlias](kservicegroup.md#inlineAlias)()

### void KServiceGroup::setInlineValue(int *\_val*) {#setInlineValue}

*See also* [inlineValue](kservicegroup.md#inlineValue)()

### void KServiceGroup::setShowEmptyMenu(bool *b*) {#setShowEmptyMenu}

*See also* [showEmptyMenu](kservicegroup.md#showEmptyMenu)()

### void KServiceGroup::setShowInlineHeader(bool *\_b*) {#setShowInlineHeader}

*See also* [showInlineHeader](kservicegroup.md#showInlineHeader)()

### bool KServiceGroup::showEmptyMenu() const {#showEmptyMenu}

Return true if we want to display empty menu entry

*See also* [setShowEmptyMenu](kservicegroup.md#setShowEmptyMenu)()

### bool KServiceGroup::showInlineHeader() const {#showInlineHeader}

Returns `true` to show an inline header into menu

*See also* [setShowInlineHeader](kservicegroup.md#setShowInlineHeader)()

### QStringList KServiceGroup::suppressGenericNames() const {#suppressGenericNames}

Returns a list of untranslated generic names that should be be suppressed when showing this group.

E.g. The group "Games/Arcade" might want to suppress the generic name "Arcade Game" since it's redundant in this particular context.
