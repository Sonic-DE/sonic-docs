---
title: "SignOn::CredentialsDBError Class"
description: "An error of the secrets storage."
---

# SignOn::CredentialsDBError Class

An error of the secrets storage. [More...](#details)

- **Header:** `#include <SignOn/AbstractSecretsStorage>`

[List of all members, including inherited members](signon-credentialsdberror-members.md)

## Public Types

- [enum CredentialsDBError::ErrorType](#ErrorType-enum)

## Public Functions

- [CredentialsDBError(const QString &text = QString(), SignOn::CredentialsDBError::ErrorType type = NoError)](#CredentialsDBError)
- [void clear()](#clear)
- [bool isValid() const](#isValid)
- [void setText(const QString &text)](#setText)
- [void setType(SignOn::CredentialsDBError::ErrorType type)](#setType)
- [QString text() const](#text)
- [SignOn::CredentialsDBError::ErrorType type() const](#type)

## Detailed Description {#details}

*See also* [AbstractSecretsStorage::lastError](signon-abstractsecretsstorage.md#lastError)()

## Member Type Documentation {#member-type-documentation}

### enum CredentialsDBError::ErrorType {#ErrorType-enum}

The kind of error.

| Constant | Value | Description |
| --- | --- | --- |
| `SignOn::CredentialsDBError::NoError` | `0` | No error. |
| `SignOn::CredentialsDBError::NotOpen` | `1` | The DB is not open |
| `SignOn::CredentialsDBError::ConnectionError` | `2` | The DB is disconnected |
| `SignOn::CredentialsDBError::StatementError` | `3` | The last command failed |
| `SignOn::CredentialsDBError::UnknownError` | `4` | Any other error. |

## Member Function Documentation {#member-function-documentation}

### CredentialsDBError::CredentialsDBError(const QString &*text* = QString(), SignOn::CredentialsDBError::ErrorType *type* = NoError) {#CredentialsDBError}

Creates an error of `type` with the description `text`.

### void CredentialsDBError::clear() {#clear}

Resets to [NoError](signon-credentialsdberror.md#ErrorType-enum) with no description.

### bool CredentialsDBError::isValid() const {#isValid}

Whether this is an error: true unless the type is [NoError](signon-credentialsdberror.md#ErrorType-enum).

### void CredentialsDBError::setText(const QString &*text*) {#setText}

Sets the description to `text`.

*See also* [text](signon-credentialsdberror.md#text)()

### void CredentialsDBError::setType(SignOn::CredentialsDBError::ErrorType *type*) {#setType}

Sets the kind of error to `type`.

*See also* [type](signon-credentialsdberror.md#type)()

### QString CredentialsDBError::text() const {#text}

The error's description.

*See also* [setText](signon-credentialsdberror.md#setText)()

### SignOn::CredentialsDBError::ErrorType CredentialsDBError::type() const {#type}

The kind of error.

*See also* [setType](signon-credentialsdberror.md#setType)()
