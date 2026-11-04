---
title: "SignOn::AbstractSecretsStorage Class"
description: "Interface for secrets storage implementations."
---

# SignOn::AbstractSecretsStorage Class

Interface for secrets storage implementations. [More...](#details)

- **Header:** `#include <SignOn/AbstractSecretsStorage>`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](signon-abstractsecretsstorage-members.md)

## Public Functions

- [AbstractSecretsStorage(QObject \*parent = 0)](#AbstractSecretsStorage)
- [bool checkPassword(const quint32 id, const QString &username, const QString &password)](#checkPassword)
- [bool clear()](#clear)
- [void clearError()](#clearError)
- [bool close()](#close)
- [bool initialize(const QVariantMap &configuration)](#initialize)
- [bool isOpen() const](#isOpen)
- [SignOn::CredentialsDBError lastError() const](#lastError)
- [bool loadCredentials(const quint32 id, QString &username, QString &password)](#loadCredentials)
- [QVariantMap loadData(quint32 id, quint32 method)](#loadData)
- [bool removeCredentials(const quint32 id)](#removeCredentials)
- [bool removeData(quint32 id, quint32 method)](#removeData)
- [bool storeData(quint32 id, quint32 method, const QVariantMap &data)](#storeData)
- [bool updateCredentials(const quint32 id, const QString &username, const QString &password)](#updateCredentials)

## Protected Functions

- [void setIsOpen(bool isOpen)](#setIsOpen)
- [void setLastError(const SignOn::CredentialsDBError &error)](#setLastError)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] AbstractSecretsStorage::AbstractSecretsStorage(QObject \**parent* = 0) {#AbstractSecretsStorage}

Constructor, with the given `parent`.

### \[virtual\] bool AbstractSecretsStorage::checkPassword(const quint32 *id*, const QString &*username*, const QString &*password*) {#checkPassword}

Checks whether `username` and `password` are correct for the identity `id`. Returns true if username and password match.

### \[pure virtual\] bool AbstractSecretsStorage::clear() {#clear}

Removes all stored secrets. Returns true if successful, false otherwise.

### void AbstractSecretsStorage::clearError() {#clearError}

Clear the last error.

### \[virtual\] bool AbstractSecretsStorage::close() {#close}

Closes the secrets DB. To reopen it, call [initialize](signon-abstractsecretsstorage.md#initialize)(). Returns true if successful, false otherwise.

### \[pure virtual\] bool AbstractSecretsStorage::initialize(const QVariantMap &*configuration*) {#initialize}

Initializes and opens the secrets DB. The implementation should take care of creating the DB, if it doesn't exist. `configuration` is a dictionary of configuration options, dependent on the specific SecretsStorage implementation.

Returns true if successful, false otherwise.

### bool AbstractSecretsStorage::isOpen() const {#isOpen}

Whether the secrets DB is open.

*See also* [setIsOpen](signon-abstractsecretsstorage.md#setIsOpen)()

### SignOn::CredentialsDBError AbstractSecretsStorage::lastError() const {#lastError}

Get the last error.

*See also* [setLastError](signon-abstractsecretsstorage.md#setLastError)()

### \[pure virtual\] bool AbstractSecretsStorage::loadCredentials(const quint32 *id*, QString &*username*, QString &*password*) {#loadCredentials}

Loads the credentials of the identity `id` into `username` and `password`. Returns true if successful, false otherwise.

### \[pure virtual\] QVariantMap AbstractSecretsStorage::loadData(quint32 *id*, quint32 *method*) {#loadData}

Loads extra secret data of the identity `id` for the authentication `method`. Returns a dictionary with the data.

### \[pure virtual\] bool AbstractSecretsStorage::removeCredentials(const quint32 *id*) {#removeCredentials}

Remove the credentials for the identity `id`. Returns true if successful, false otherwise.

### \[pure virtual\] bool AbstractSecretsStorage::removeData(quint32 *id*, quint32 *method*) {#removeData}

Removes extra secret data of the identity `id` for the authentication `method`. Returns true if successful, false otherwise.

### \[protected\] void AbstractSecretsStorage::setIsOpen(bool *isOpen*) {#setIsOpen}

Implementations record whether the DB `isOpen`.

*See also* [isOpen](signon-abstractsecretsstorage.md#isOpen)()

### \[protected\] void AbstractSecretsStorage::setLastError(const SignOn::CredentialsDBError &*error*) {#setLastError}

Implementations record the last `error`.

*See also* [lastError](signon-abstractsecretsstorage.md#lastError)()

### \[pure virtual\] bool AbstractSecretsStorage::storeData(quint32 *id*, quint32 *method*, const QVariantMap &*data*) {#storeData}

Stores extra secret `data` of the identity `id` for the authentication `method`. Calling this method replaces any data which was previously stored for the given id/method. Returns true if successful, false otherwise.

### \[pure virtual\] bool AbstractSecretsStorage::updateCredentials(const quint32 *id*, const QString &*username*, const QString &*password*) {#updateCredentials}

Stores/updates the credentials `username` and `password` for the identity `id`. Returns true if successful, false otherwise.
