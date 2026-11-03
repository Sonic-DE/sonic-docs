---
title: "ConfigModel QML Type"
description: "This model contains all the possible config categories for a dialog, such as categories of the config dialog for an Applet."
---

# ConfigModel QML Type

This model contains all the possible config categories for a dialog, such as categories of the config dialog for an Applet. [More...](#details)

- Import Statement: import org.kde.plasma.configuration
- In C++: [ConfigModel](plasmaquick-configmodel.md)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### \[default read-only\] categories : list\<ConfigCategory\> {#categories-prop}

### \[read-only\] count : int {#count-prop}

## Method Documentation {#method-documentation}

### void appendCategory(ConfigCategory *category*) {#appendCategory-method}

### void appendCategory(string *iconName*, string *name*, string *path*, string *pluginName*, bool *visible*) {#appendCategory-method-1}

### void get(int *index*) {#get-method}

`row` The row for which the data will be returned

Returns the data of the specified row

### void removeCategory(ConfigCategory *category*) {#removeCategory-method}

### void removeCategoryAt(int *index*) {#removeCategoryAt-method}
