---
title: "KUserFeedback::SurveyInfo Class"
description: "Information about a survey request."
---

# KUserFeedback::SurveyInfo Class

Information about a survey request. [More...](#details)

- **Header:** `#include <KUserFeedback/SurveyInfo>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UserFeedbackCore)`  
  `target_link_libraries(mytarget PRIVATE KF6::UserFeedbackCore)`

[List of all members, including inherited members](kuserfeedback-surveyinfo-members.md)

## Properties

- [\[read-only\] isValid : bool](#isValid-prop)
- [\[read-only\] target : QString](#target-prop)
- [\[read-only\] url : QUrl](#url-prop)
- [\[read-only\] uuid : QUuid](#uuid-prop)

## Public Functions

- [SurveyInfo()](#SurveyInfo)
- [bool isValid() const](#isValid)
- [QString target() const](#target)
- [QUrl url() const](#url)
- [QUuid uuid() const](#uuid)

## Detailed Description {#details}

This class is implicitly shared.

## Property Documentation {#property-documentation}

### \[read-only\] isValid : bool {#isValid-prop}

**Access functions:**

- `bool` **[isValid](kuserfeedback-surveyinfo.md#isValid)**() const

### \[read-only\] target : QString {#target-prop}

**Access functions:**

- `QString` **[target](kuserfeedback-surveyinfo.md#target)**() const

### \[read-only\] url : QUrl {#url-prop}

**Access functions:**

- `QUrl` **[url](kuserfeedback-surveyinfo.md#url)**() const

### \[read-only\] uuid : QUuid {#uuid-prop}

**Access functions:**

- `QUuid` **[uuid](kuserfeedback-surveyinfo.md#uuid)**() const

## Member Function Documentation {#member-function-documentation}

### SurveyInfo::SurveyInfo() {#SurveyInfo}

Create an empty, invalid survey request.

### bool SurveyInfo::isValid() const {#isValid}

Returns `true` if this survey has all necessary information to actually execute it.

> **Note:** Getter function for property [isValid](kuserfeedback-surveyinfo.md#isValid-prop).

### QString SurveyInfo::target() const {#target}

The survey targeting expression.

> **Note:** Getter function for property [target](kuserfeedback-surveyinfo.md#target-prop).

### QUrl SurveyInfo::url() const {#url}

The URL to the survey website.

> **Note:** Getter function for property [url](kuserfeedback-surveyinfo.md#url-prop).

### QUuid SurveyInfo::uuid() const {#uuid}

Internal global unique id of the survey.

Used to locally check if a user has completed the survey already.

> **Note:** Getter function for property [uuid](kuserfeedback-surveyinfo.md#uuid-prop).
