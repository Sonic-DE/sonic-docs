---
title: "KRoleNames QML Type"
description: "Maps role numbers and names of the attached model. This type was introduced in Qt 6.0."
---

# KRoleNames QML Type

Maps role numbers and names of the attached model. This type was introduced in Qt 6.0. [More...](#details)

- Import Statement: import org.kde.kitemmodels
- Since: Qt 6.0

## Detailed Description {#details}

Attach [KRoleNames](qml-org-kde-kitemmodels-krolenames.md) to a model to map from roles to role names and vice-versa. It can be used to retrieve data from a model in an imperative fashion when a role enum is not available in QML (for example, when it is not exported via [Q\_ENUM](https://doc.qt.io/qt-6/qobject.html#Q_ENUM)) but role names are known; or to maintain consistency with view delegates (which use role names as properties).

## Attached Method Documentation {#attached-method-documentation}

### \[since 6.0\] int role(string *roleName*) {#role-method}

Maps role name to role number.

Returns -1 if `roleName` is not found in the attached model's roleNames() hash map.

This method was introduced in Qt 6.0.

### \[since 6.0\] string roleName(int *role*) {#roleName-method}

Maps role number to role name.

Returns an empty string if `role` is not found in the attached model's roleNames() hash map.

This method was introduced in Qt 6.0.
