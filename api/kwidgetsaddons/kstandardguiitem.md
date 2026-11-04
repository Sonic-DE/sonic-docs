---
title: "KStandardGuiItem Namespace"
description: "Provides a set of standardized KGuiItems."
---

# KStandardGuiItem Namespace

Provides a set of standardized KGuiItems. [More...](#details)

- **Header:** `#include <KStandardGuiItem>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`

## Detailed Description {#details}

The various methods return standardized [KGuiItem](kguiitem.md)'s conforming to the KDE UI Standards. Use them instead of creating your own.

## Type Documentation {#type-documentation}

### enum KStandardGuiItem::BidiMode {#BidiMode-enum}

The back and forward items by default use the RTL settings for Hebrew and Arab countries. If you want those actions to ignore the RTL value and force 'Western' behavior instead, use the IgnoreRTL value instead.

| Constant |   |
| --- | --- |
| `KStandardGuiItem::UseRTL` | `0` |
| `KStandardGuiItem::IgnoreRTL` | `1` |

### enum KStandardGuiItem::StandardItem {#StandardItem-enum}

| Constant |   |
| --- | --- |
| `KStandardGuiItem::Ok` | `1` |
| `KStandardGuiItem::Cancel` | `2` |
| `KStandardGuiItem::Discard` | `3` |
| `KStandardGuiItem::Save` | `4` |
| `KStandardGuiItem::DontSave` | `5` |
| `KStandardGuiItem::SaveAs` | `6` |
| `KStandardGuiItem::Apply` | `7` |
| `KStandardGuiItem::Clear` | `8` |
| `KStandardGuiItem::Help` | `9` |
| `KStandardGuiItem::Defaults` | `10` |
| `KStandardGuiItem::Close` | `11` |
| `KStandardGuiItem::Back` | `12` |
| `KStandardGuiItem::Forward` | `13` |
| `KStandardGuiItem::Print` | `14` |
| `KStandardGuiItem::Continue` | `15` |
| `KStandardGuiItem::Open` | `16` |
| `KStandardGuiItem::Quit` | `17` |
| `KStandardGuiItem::AdminMode` | `18` |
| `KStandardGuiItem::Reset` | `19` |
| `KStandardGuiItem::Delete` | `20` |
| `KStandardGuiItem::Insert` | `21` |
| `KStandardGuiItem::Configure` | `22` |
| `KStandardGuiItem::Find` | `23` |
| `KStandardGuiItem::Stop` | `24` |
| `KStandardGuiItem::Add` | `25` |
| `KStandardGuiItem::Remove` | `26` |
| `KStandardGuiItem::Test` | `27` |
| `KStandardGuiItem::Properties` | `28` |
| `KStandardGuiItem::Overwrite` | `29` |
| `KStandardGuiItem::CloseWindow` | `30` |
| `KStandardGuiItem::CloseDocument` | `31` |

## Function Documentation {#function-documentation}

### KGuiItem KStandardGuiItem::add() {#add}

Returns the 'Add' gui item.

### KGuiItem KStandardGuiItem::adminMode() {#adminMode}

Returns a [KGuiItem](kguiitem.md) suiting for cases where code or functionality runs under root privileges. Used in conjunction with KConfig Modules.

### KGuiItem KStandardGuiItem::apply() {#apply}

Returns the 'Apply' gui item.

### void KStandardGuiItem::assign(QPushButton \**button*, KStandardGuiItem::StandardItem *item*) {#assign}

### KGuiItem KStandardGuiItem::back(KStandardGuiItem::BidiMode *useBidi* = IgnoreRTL) {#back}

Returns the 'Back' gui item, like Konqueror's back button. This GUI item can optionally honor the user's setting for BiDi, so the icon for right-to-left languages (Hebrew and Arab) has the arrow pointing in the opposite direction. By default the arrow points in the Western 'back' direction (i.e. to the left). This is because usually you only want the Bidi aware GUI item if you also want the 'forward' item. Those two are available in the separate [backAndForward](kstandardguiitem.md#backAndForward)() method.

### QPair\<KGuiItem, KGuiItem\> KStandardGuiItem::backAndForward() {#backAndForward}

Return both a back and a forward gui item. This function always returns items that are aware of the Right-to-Left setting for Arab and Hebrew locales. If you have a reason for wanting the 'Western' back/forward buttons, please use the [back](kstandardguiitem.md#back)() and [forward](kstandardguiitem.md#forward)() items instead.

### KGuiItem KStandardGuiItem::cancel() {#cancel}

Returns the 'Cancel' gui item.

### KGuiItem KStandardGuiItem::clear() {#clear}

Returns the 'Clear' gui item.

### KGuiItem KStandardGuiItem::close() {#close}

Returns the 'Close' gui item.

### KGuiItem KStandardGuiItem::closeDocument() {#closeDocument}

Returns the '[CloseDocument](kstandardguiitem.md#StandardItem-enum)' gui item.

### KGuiItem KStandardGuiItem::closeWindow() {#closeWindow}

Returns the '[CloseWindow](kstandardguiitem.md#StandardItem-enum)' gui item.

### KGuiItem KStandardGuiItem::configure() {#configure}

Returns the 'Configure' gui item.

### KGuiItem KStandardGuiItem::cont() {#cont}

Returns the 'Continue' gui item. The short name is due to 'continue' being a reserved word in the C++ language.

### KGuiItem KStandardGuiItem::defaults() {#defaults}

Returns the 'Defaults' gui item.

### KGuiItem KStandardGuiItem::del() {#del}

Returns the 'Delete' gui item. The short name is due to 'delete' being a reserved word in the C++ language.

### KGuiItem KStandardGuiItem::discard() {#discard}

Returns the 'Discard' gui item.

### KGuiItem KStandardGuiItem::dontSave() {#dontSave}

Returns the '[DontSave](kstandardguiitem.md#StandardItem-enum)' gui item.

### KGuiItem KStandardGuiItem::find() {#find}

Returns the 'Find' gui item.

### KGuiItem KStandardGuiItem::forward(KStandardGuiItem::BidiMode *useBidi* = IgnoreRTL) {#forward}

Returns the 'Forward' gui item, like Konqueror's forward button. This GUI item can optionally honor the user's setting for BiDi, so the icon for right-to-left languages (Hebrew and Arab) has the arrow pointing in the opposite direction. By default the arrow points in the Western 'forward' direction (i.e. to the right). This is because usually you only want the Bidi aware GUI item if you also want the 'back' item. Those two are available in the separate [backAndForward](kstandardguiitem.md#backAndForward)() method.

### KGuiItem KStandardGuiItem::guiItem(KStandardGuiItem::StandardItem *id*) {#guiItem}

Returns the gui item for the given identifier `id`.

`id` the identifier to search for

### KGuiItem KStandardGuiItem::help() {#help}

Returns the 'Help' gui item.

### KGuiItem KStandardGuiItem::insert() {#insert}

Returns the 'Insert' gui item.

### KGuiItem KStandardGuiItem::ok() {#ok}

Returns the 'Ok' gui item.

### KGuiItem KStandardGuiItem::open() {#open}

Returns the 'Open' gui item.

### KGuiItem KStandardGuiItem::overwrite() {#overwrite}

Returns the 'Overwrite' gui item.

### KGuiItem KStandardGuiItem::print() {#print}

Returns the 'Print' gui item.

### KGuiItem KStandardGuiItem::properties() {#properties}

Returns the 'Properties' gui item.

### KGuiItem KStandardGuiItem::quit() {#quit}

Returns the 'Quit' gui item.

### KGuiItem KStandardGuiItem::remove() {#remove}

Returns the 'Remove' gui item.

### KGuiItem KStandardGuiItem::reset() {#reset}

Returns the 'Reset' gui item.

### KGuiItem KStandardGuiItem::save() {#save}

Returns the 'Save' gui item.

### KGuiItem KStandardGuiItem::saveAs() {#saveAs}

Returns the '[SaveAs](kstandardguiitem.md#StandardItem-enum)' gui item.

### QString KStandardGuiItem::standardItem(KStandardGuiItem::StandardItem *id*) {#standardItem}

Returns the name of the gui item for the given identifier `id`.

`id` the identifier to search for

### KGuiItem KStandardGuiItem::stop() {#stop}

Returns the 'Stop' gui item.

### KGuiItem KStandardGuiItem::test() {#test}

Returns the 'Test' gui item.
