---
title: "Sonnet::ConfigView Class"
description: "The sonnet ConfigView."
---

# Sonnet::ConfigView Class

The sonnet [ConfigView](sonnet-configview.md). [More...](#details)

- **Header:** `#include <Sonnet/ConfigView>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Sonnet)`  
  `target_link_libraries(mytarget PRIVATE KF6::SonnetUi)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](sonnet-configview-members.md)

## Properties

- [backgroundCheckingButtonShown : bool](#backgroundCheckingButtonShown-prop)
- [ignoreList : QStringList](#ignoreList-prop)
- [language : QString](#language-prop)
- [preferredLanguages : QStringList](#preferredLanguages-prop)
- [showNoBackendFound : bool](#showNoBackendFound-prop)

## Public Functions

- [ConfigView(QWidget \*parent = nullptr)](#ConfigView)
- [bool backgroundCheckingButtonShown() const](#backgroundCheckingButtonShown)
- [QStringList ignoreList() const](#ignoreList)
- [QString language() const](#language)
- [bool noBackendFoundVisible() const](#noBackendFoundVisible)
- [QStringList preferredLanguages() const](#preferredLanguages)

## Public Slots

- [void setBackgroundCheckingButtonShown(bool)](#setBackgroundCheckingButtonShown)
- [void setIgnoreList(const QStringList &ignoreList)](#setIgnoreList)
- [void setLanguage(const QString &language)](#setLanguage)
- [void setNoBackendFoundVisible(bool show)](#setNoBackendFoundVisible)
- [void setPreferredLanguages(const QStringList &ignoreList)](#setPreferredLanguages)

## Signals

- [void configChanged()](#configChanged)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### backgroundCheckingButtonShown : bool {#backgroundCheckingButtonShown-prop}

**Access functions:**

- `bool` **[backgroundCheckingButtonShown](sonnet-configview.md#backgroundCheckingButtonShown)**() const
- `void` **[setBackgroundCheckingButtonShown](sonnet-configview.md#setBackgroundCheckingButtonShown)**(*bool*)

### ignoreList : QStringList {#ignoreList-prop}

**Access functions:**

- `QStringList` **[ignoreList](sonnet-configview.md#ignoreList)**() const
- `void` **[setIgnoreList](sonnet-configview.md#setIgnoreList)**(const `QStringList` &*ignoreList*)

### language : QString {#language-prop}

**Access functions:**

- `QString` **[language](sonnet-configview.md#language)**() const
- `void` **[setLanguage](sonnet-configview.md#setLanguage)**(const `QString` &*language*)

### preferredLanguages : QStringList {#preferredLanguages-prop}

**Access functions:**

- `QStringList` **[preferredLanguages](sonnet-configview.md#preferredLanguages)**() const
- `void` **[setPreferredLanguages](sonnet-configview.md#setPreferredLanguages)**(const `QStringList` &*ignoreList*)

### showNoBackendFound : bool {#showNoBackendFound-prop}

**Access functions:**

- `bool` **[noBackendFoundVisible](sonnet-configview.md#noBackendFoundVisible)**() const
- `void` **[setNoBackendFoundVisible](sonnet-configview.md#setNoBackendFoundVisible)**(`bool` *show*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ConfigView::ConfigView(QWidget \**parent* = nullptr) {#ConfigView}

### bool ConfigView::backgroundCheckingButtonShown() const {#backgroundCheckingButtonShown}

> **Note:** Getter function for property [backgroundCheckingButtonShown](sonnet-configview.md#backgroundCheckingButtonShown-prop).

*See also* [setBackgroundCheckingButtonShown](sonnet-configview.md#setBackgroundCheckingButtonShown)()

### \[signal\] void ConfigView::configChanged() {#configChanged}

### QStringList ConfigView::ignoreList() const {#ignoreList}

> **Note:** Getter function for property [ignoreList](sonnet-configview.md#ignoreList-prop).

*See also* [setIgnoreList](sonnet-configview.md#setIgnoreList)()

### QString ConfigView::language() const {#language}

> **Note:** Getter function for property [language](sonnet-configview.md#language-prop).

*See also* [setLanguage](sonnet-configview.md#setLanguage)()

### bool ConfigView::noBackendFoundVisible() const {#noBackendFoundVisible}

> **Note:** Getter function for property [showNoBackendFound](sonnet-configview.md#showNoBackendFound-prop).

*See also* [setNoBackendFoundVisible](sonnet-configview.md#setNoBackendFoundVisible)()

### QStringList ConfigView::preferredLanguages() const {#preferredLanguages}

> **Note:** Getter function for property [preferredLanguages](sonnet-configview.md#preferredLanguages-prop).

*See also* [setPreferredLanguages](sonnet-configview.md#setPreferredLanguages)()

### \[slot\] void ConfigView::setBackgroundCheckingButtonShown(*bool*) {#setBackgroundCheckingButtonShown}

> **Note:** Setter function for property [backgroundCheckingButtonShown](sonnet-configview.md#backgroundCheckingButtonShown-prop).

*See also* [backgroundCheckingButtonShown](sonnet-configview.md#backgroundCheckingButtonShown)()

### \[slot\] void ConfigView::setIgnoreList(const QStringList &*ignoreList*) {#setIgnoreList}

> **Note:** Setter function for property [ignoreList](sonnet-configview.md#ignoreList-prop).

*See also* [ignoreList](sonnet-configview.md#ignoreList)()

### \[slot\] void ConfigView::setLanguage(const QString &*language*) {#setLanguage}

> **Note:** Setter function for property [language](sonnet-configview.md#language-prop).

*See also* [language](sonnet-configview.md#language)()

### \[slot\] void ConfigView::setNoBackendFoundVisible(bool *show*) {#setNoBackendFoundVisible}

> **Note:** Setter function for property [showNoBackendFound](sonnet-configview.md#showNoBackendFound-prop).

*See also* [noBackendFoundVisible](sonnet-configview.md#noBackendFoundVisible)()

### \[slot\] void ConfigView::setPreferredLanguages(const QStringList &*ignoreList*) {#setPreferredLanguages}

> **Note:** Setter function for property [preferredLanguages](sonnet-configview.md#preferredLanguages-prop).

*See also* [preferredLanguages](sonnet-configview.md#preferredLanguages)()
