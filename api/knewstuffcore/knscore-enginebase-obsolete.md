---
title: "Obsolete Members for KNSCore::EngineBase"
description: "Deprecated members of KNSCore::EngineBase."
parent: "knewstuffcore/knscore-enginebase"
---

# Obsolete Members for KNSCore::EngineBase

**The following members of class [EngineBase](knscore-enginebase.md) are deprecated.** We strongly advise against using them in new code.

## Public Functions

- [QSharedPointer\<KNSCore::Cache\> cache() const](#cache) (deprecated in 6.9)
- [QList\<KNSCore::Provider::CategoryMetadata\> categoriesMetadata()](#categoriesMetadata) (deprecated in 6.9)
- [QSharedPointer\<KNSCore::Provider\> defaultProvider() const](#defaultProvider) (deprecated in 6.9)
- [QSharedPointer\<KNSCore::Provider\> provider(const QString &providerId) const](#provider) (deprecated in 6.9)
- [QList\<KNSCore::Provider::SearchPreset\> searchPresets()](#searchPresets) (deprecated in 6.9)

## Signals

- [void providersChanged()](#providersChanged) (deprecated in 6.9)
- [void signalCategoriesMetadataLoded(const QList\<KNSCore::Provider::CategoryMetadata\> &categories)](#signalCategoriesMetadataLoded) (deprecated in 6.9)
- [void signalSearchPresetsLoaded(const QList\<KNSCore::Provider::SearchPreset\> &presets)](#signalSearchPresetsLoaded) (deprecated in 6.9)

## Protected Functions

- [void addProvider(QSharedPointer\<KNSCore::Provider\> provider)](#addProvider) (deprecated in 6.9)
- [QList\<QSharedPointer\<KNSCore::Provider\>\> providers() const](#providers) (deprecated in 6.9)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[virtual protected, deprecated in 6.9\] void EngineBase::addProvider(QSharedPointer\<KNSCore::Provider\> *provider*) {#addProvider}

This function is deprecated since 6.9. We strongly advise against using it in new code.

Add a provider and connect it to the right slots Use [providerAdded](knscore-enginebase.md#providerAdded) signal

### \[deprecated in 6.9\] QSharedPointer\<KNSCore::Cache\> EngineBase::cache() const {#cache}

This function is deprecated since 6.9. We strongly advise against using it in new code.

Get the entries cache for this engine (note that it may be null if the engine is not yet initialized).

Returns the cache for this engine (or null if the engine is not initialized)

Do not use the cache directly

### \[deprecated in 6.9\] QList\<KNSCore::Provider::CategoryMetadata\> EngineBase::categoriesMetadata() {#categoriesMetadata}

This function is deprecated since 6.9. We strongly advise against using it in new code.

Use [categoriesMetadata2](knscore-enginebase.md#categoriesMetadata2)

### \[deprecated in 6.9\] QSharedPointer\<KNSCore::Provider\> EngineBase::defaultProvider() const {#defaultProvider}

This function is deprecated since 6.9. We strongly advise against using it in new code.

Return the first provider in the providers list (usually the default provider) Do not write provider-specific code

### \[deprecated in 6.9\] QSharedPointer\<KNSCore::Provider\> EngineBase::provider(const QString &*providerId*) const {#provider}

This function is deprecated since 6.9. We strongly advise against using it in new code.

The Provider instance with the passed ID

`providerId` The ID of the Provider to fetch

Returns the Provider with the passed ID, or null if non such Provider exists Do not write provider-specific code

### \[protected, deprecated in 6.9\] QList\<QSharedPointer\<KNSCore::Provider\>\> EngineBase::providers() const {#providers}

This function is deprecated since 6.9. We strongly advise against using it in new code.

Do not write provider-specific code

### \[signal, deprecated in 6.9\] void EngineBase::providersChanged() {#providersChanged}

This function is deprecated since 6.9. We strongly advise against using it in new code.

Fired whenever the list of providers changes Use [providerAdded](knscore-enginebase.md#providerAdded) signal

### \[deprecated in 6.9\] QList\<KNSCore::Provider::SearchPreset\> EngineBase::searchPresets() {#searchPresets}

This function is deprecated since 6.9. We strongly advise against using it in new code.

Use [searchPresets2](knscore-enginebase.md#searchPresets2)

### \[signal, deprecated in 6.9\] void EngineBase::signalCategoriesMetadataLoded(const QList\<KNSCore::Provider::CategoryMetadata\> &*categories*) {#signalCategoriesMetadataLoded}

This function is deprecated since 6.9. We strongly advise against using it in new code.

Use variant with new argument type

### \[signal, deprecated in 6.9\] void EngineBase::signalSearchPresetsLoaded(const QList\<KNSCore::Provider::SearchPreset\> &*presets*) {#signalSearchPresetsLoaded}

This function is deprecated since 6.9. We strongly advise against using it in new code.

Fires when the engine has loaded search presets. These represent interesting searches for the user, such as recommendations. Use variant with new argument type

> **Note:** This signal is overloaded. To connect to this signal:
>
> ```
> // Connect using qOverload:
> connect(engineBase, qOverload<const QList<KNSCore::Provider::SearchPreset> &>(&EngineBase::signalSearchPresetsLoaded),
>         receiver, &ReceiverClass::slot);
>
> // Or using a lambda:
> connect(engineBase, qOverload<const QList<KNSCore::Provider::SearchPreset> &>(&EngineBase::signalSearchPresetsLoaded),
>         this, [](const QList<KNSCore::Provider::SearchPreset> &presets) { /* handle signalSearchPresetsLoaded */ });
> ```
>
> For more examples and approaches, see [connecting to overloaded signals](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-signals).
