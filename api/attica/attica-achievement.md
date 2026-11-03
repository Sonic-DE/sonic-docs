---
title: "Attica::Achievement Class"
description: "Represents an achievement."
---

# Attica::Achievement Class

Represents an achievement. [More...](#details)

- **Header:** `#include <Attica/Achievement>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-achievement-members.md)

## Public Types

- [Achievement::List](#List-typedef)
- [enum Achievement::Type](#Type-enum)
- [enum Achievement::Visibility](#Visibility-enum)

## Public Functions

- [Achievement()](#Achievement)
- [void addDependency(const QString &dependency)](#addDependency)
- [void addOption(const QString &option)](#addOption)
- [QString contentId() const](#contentId)
- [QStringList dependencies() const](#dependencies)
- [QString description() const](#description)
- [QString explanation() const](#explanation)
- [QString id() const](#id)
- [QUrl image() const](#image)
- [bool isValid() const](#isValid)
- [QString name() const](#name)
- [QStringList options() const](#options)
- [int points() const](#points)
- [QVariant progress() const](#progress)
- [void removeDependency(const QString &dependency)](#removeDependency)
- [void removeOption(const QString &option)](#removeOption)
- [void setContentId(const QString &contentId)](#setContentId)
- [void setDependencies(const QStringList &dependencies)](#setDependencies)
- [void setDescription(const QString &description)](#setDescription)
- [void setExplanation(const QString &explanation)](#setExplanation)
- [void setId(const QString &id)](#setId)
- [void setImage(const QUrl &image)](#setImage)
- [void setName(const QString &name)](#setName)
- [void setOptions(const QStringList &options)](#setOptions)
- [void setPoints(const int points)](#setPoints)
- [void setProgress(const QVariant &progress)](#setProgress)
- [void setSteps(const int steps)](#setSteps)
- [void setType(Attica::Achievement::Type type)](#setType)
- [void setVisibility(Attica::Achievement::Visibility visibility)](#setVisibility)
- [int steps() const](#steps)
- [Attica::Achievement::Type type() const](#type)
- [Attica::Achievement::Visibility visibility() const](#visibility)

## Static Public Members

- [QString achievementTypeToString(const Attica::Achievement::Type type)](#achievementTypeToString)
- [QString achievementVisibilityToString(const Attica::Achievement::Visibility visibility)](#achievementVisibilityToString)
- [Attica::Achievement::Type stringToAchievementType(const QString &achievementTypeString)](#stringToAchievementType)
- [Attica::Achievement::Visibility stringToAchievementVisibility(const QString &achievementVisibilityString)](#stringToAchievementVisibility)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### Achievement::List {#List-typedef}

### enum Achievement::Type {#Type-enum}

| Constant |   |
| --- | --- |
| `Attica::Achievement::FlowingAchievement` | `0` |
| `Attica::Achievement::SteppedAchievement` | `1` |
| `Attica::Achievement::NamedstepsAchievement` | `2` |
| `Attica::Achievement::SetAchievement` | `3` |

### enum Achievement::Visibility {#Visibility-enum}

| Constant |   |
| --- | --- |
| `Attica::Achievement::VisibleAchievement` | `0` |
| `Attica::Achievement::DependentsAchievement` | `1` |
| `Attica::Achievement::SecretAchievement` | `2` |

## Member Function Documentation {#member-function-documentation}

### Achievement::Achievement() {#Achievement}

### \[static\] QString Achievement::achievementTypeToString(const Attica::Achievement::Type *type*) {#achievementTypeToString}

### \[static\] QString Achievement::achievementVisibilityToString(const Attica::Achievement::Visibility *visibility*) {#achievementVisibilityToString}

### void Achievement::addDependency(const QString &*dependency*) {#addDependency}

### void Achievement::addOption(const QString &*option*) {#addOption}

### QString Achievement::contentId() const {#contentId}

*See also* [setContentId](attica-achievement.md#setContentId)()

### QStringList Achievement::dependencies() const {#dependencies}

*See also* [setDependencies](attica-achievement.md#setDependencies)()

### QString Achievement::description() const {#description}

*See also* [setDescription](attica-achievement.md#setDescription)()

### QString Achievement::explanation() const {#explanation}

*See also* [setExplanation](attica-achievement.md#setExplanation)()

### QString Achievement::id() const {#id}

*See also* [setId](attica-achievement.md#setId)()

### QUrl Achievement::image() const {#image}

*See also* [setImage](attica-achievement.md#setImage)()

### bool Achievement::isValid() const {#isValid}

### QString Achievement::name() const {#name}

*See also* [setName](attica-achievement.md#setName)()

### QStringList Achievement::options() const {#options}

*See also* [setOptions](attica-achievement.md#setOptions)()

### int Achievement::points() const {#points}

*See also* [setPoints](attica-achievement.md#setPoints)()

### QVariant Achievement::progress() const {#progress}

*See also* [setProgress](attica-achievement.md#setProgress)()

### void Achievement::removeDependency(const QString &*dependency*) {#removeDependency}

### void Achievement::removeOption(const QString &*option*) {#removeOption}

### void Achievement::setContentId(const QString &*contentId*) {#setContentId}

*See also* [contentId](attica-achievement.md#contentId)()

### void Achievement::setDependencies(const QStringList &*dependencies*) {#setDependencies}

*See also* [dependencies](attica-achievement.md#dependencies)()

### void Achievement::setDescription(const QString &*description*) {#setDescription}

*See also* [description](attica-achievement.md#description)()

### void Achievement::setExplanation(const QString &*explanation*) {#setExplanation}

*See also* [explanation](attica-achievement.md#explanation)()

### void Achievement::setId(const QString &*id*) {#setId}

*See also* [id](attica-achievement.md#id)()

### void Achievement::setImage(const QUrl &*image*) {#setImage}

*See also* [image](attica-achievement.md#image)()

### void Achievement::setName(const QString &*name*) {#setName}

*See also* [name](attica-achievement.md#name)()

### void Achievement::setOptions(const QStringList &*options*) {#setOptions}

*See also* [options](attica-achievement.md#options)()

### void Achievement::setPoints(const int *points*) {#setPoints}

*See also* [points](attica-achievement.md#points)()

### void Achievement::setProgress(const QVariant &*progress*) {#setProgress}

*See also* [progress](attica-achievement.md#progress)()

### void Achievement::setSteps(const int *steps*) {#setSteps}

*See also* [steps](attica-achievement.md#steps)()

### void Achievement::setType(Attica::Achievement::Type *type*) {#setType}

*See also* [type](attica-achievement.md#type)()

### void Achievement::setVisibility(Attica::Achievement::Visibility *visibility*) {#setVisibility}

*See also* [visibility](attica-achievement.md#visibility)()

### int Achievement::steps() const {#steps}

*See also* [setSteps](attica-achievement.md#setSteps)()

### \[static\] Attica::Achievement::Type Achievement::stringToAchievementType(const QString &*achievementTypeString*) {#stringToAchievementType}

### \[static\] Attica::Achievement::Visibility Achievement::stringToAchievementVisibility(const QString &*achievementVisibilityString*) {#stringToAchievementVisibility}

### Attica::Achievement::Type Achievement::type() const {#type}

*See also* [setType](attica-achievement.md#setType)()

### Attica::Achievement::Visibility Achievement::visibility() const {#visibility}

*See also* [setVisibility](attica-achievement.md#setVisibility)()
