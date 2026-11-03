---
title: "ActivityModel QML Type"
description: "Activities model."
---

# ActivityModel QML Type

Activities model. [More...](#details)

- Import Statement: import org.kde.activities

## Detailed Description {#details}

This model provides the following roles:

- name (string)
- icon (QIcon)
- id (string)
- iconSource (string)
- description (string)
- background (string)
- current (bool)

## Signal Documentation {#signal-documentation}

### shownStatesChanged(string *state*) {#shownStatesChanged-signal}

> **Note:** The corresponding handler is `onShownStatesChanged`.

## Method Documentation {#method-documentation}

### void addActivity(string *name*, var *callback*) {#addActivity-method}

### void removeActivity(string *id*, var *callback*) {#removeActivity-method}

### void setActivityDescription(string *id*, string *description*, var *callback*) {#setActivityDescription-method}

### void setActivityIcon(string *id*, string *icon*, var *callback*) {#setActivityIcon-method}

### void setActivityName(string *id*, string *name*, var *callback*) {#setActivityName-method}

### void setCurrentActivity(string *id*, var *callback*) {#setCurrentActivity-method}
