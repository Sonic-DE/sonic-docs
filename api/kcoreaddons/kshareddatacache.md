---
title: "KSharedDataCache Class"
description: "A simple data cache which uses shared memory to quickly access data stored on disk."
---

# KSharedDataCache Class

A simple data cache which uses shared memory to quickly access data stored on disk. [More...](#details)

- **Header:** `#include <KSharedDataCache>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`

[List of all members, including inherited members](kshareddatacache-members.md)

## Public Types

- [enum KSharedDataCache::EvictionPolicy](#EvictionPolicy-enum)

## Public Functions

- [KSharedDataCache(const QString &cacheName, unsigned int defaultCacheSize, unsigned int expectedItemSize = 0)](#KSharedDataCache)
- [void clear()](#clear)
- [bool contains(const QString &key) const](#contains)
- [KSharedDataCache::EvictionPolicy evictionPolicy() const](#evictionPolicy)
- [bool find(const QString &key, QByteArray \*destination) const](#find)
- [unsigned int freeSize() const](#freeSize)
- [bool insert(const QString &key, const QByteArray &data)](#insert)
- [bool remove(const QString &key)](#remove) (since 6.18)
- [void setEvictionPolicy(KSharedDataCache::EvictionPolicy newPolicy)](#setEvictionPolicy)
- [void setTimestamp(unsigned int newTimestamp)](#setTimestamp)
- [unsigned int timestamp() const](#timestamp)
- [unsigned int totalSize() const](#totalSize)

## Static Public Members

- [void deleteCache(const QString &cacheName)](#deleteCache)

## Detailed Description {#details}

This class is meant to be used with KImageCache and similar classes but can be used directly if used with care.

Example usage:

```cpp
QString loadTranslatedDocument(KSharedDataCache *cache) {

  // Find the data
  QByteArray document;

  if (!cache->find("translated-doc-template", &document)) {
    // Entry is not cached, manually generate and then add to cache.
    document = translateDocument(globalTemplate());
    cache->insert(document);
  }

  // Don't forget to encode/decode properly
  return QString::fromUtf8(document);
}
```

*See also* KImageCache

## Member Type Documentation {#member-type-documentation}

### enum KSharedDataCache::EvictionPolicy {#EvictionPolicy-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KSharedDataCache::NoEvictionPreference` | `0` | No preference |
| `KSharedDataCache::EvictLeastRecentlyUsed` | `1` | Evict the least recently used entry |
| `KSharedDataCache::EvictLeastOftenUsed` | `2` | Evict the lest often used item |
| `KSharedDataCache::EvictOldest` | `3` | Evict the oldest item |

## Member Function Documentation {#member-function-documentation}

### KSharedDataCache::KSharedDataCache(const QString &*cacheName*, unsigned int *defaultCacheSize*, unsigned int *expectedItemSize* = 0) {#KSharedDataCache}

Attaches to a shared cache, creating it if necessary. If supported, this data cache will be shared across all processes using this cache (with subsequent memory savings). If shared memory is unsupported or a failure occurs, caching will still be supported, but only in the same process, and only using the same [KSharedDataCache](kshareddatacache.md) object.

`cacheName` Name of the cache to use/share.

`defaultCacheSize` Amount of data to be able to store, in bytes. The actual size will be slightly larger on disk due to accounting overhead. If the cache already existed then it will not be resized. For this reason you should specify some reasonable size.

`expectedItemSize` The average size of an item that would be stored in the cache, in bytes. Choosing an average size of zero bytes causes [KSharedDataCache](kshareddatacache.md) to use whatever it feels is the best default for the system.

### void KSharedDataCache::clear() {#clear}

Removes all entries from the cache.

### bool KSharedDataCache::contains(const QString &*key*) const {#contains}

Returns true if the cache currently contains the image for the given filename.

> **Note:** Calling this function is threadsafe, but it is in general not possible to guarantee the image stays cached immediately afterwards, so if you need the result use [find](kshareddatacache.md#find)().

### \[static\] void KSharedDataCache::deleteCache(const QString &*cacheName*) {#deleteCache}

Removes the underlying file from the cache. Note that this is \*all\* that this function does. The shared memory segment is still attached and will still contain all the data until all processes currently attached remove the mapping.

In order to remove the data see [clear](kshareddatacache.md#clear)().

### KSharedDataCache::EvictionPolicy KSharedDataCache::evictionPolicy() const {#evictionPolicy}

Returns the removal policy in use by the shared cache.

*See also* [setEvictionPolicy](kshareddatacache.md#setEvictionPolicy)()

### bool KSharedDataCache::find(const QString &*key*, QByteArray \**destination*) const {#find}

Returns the data in the cache named by `key` (even if it's some other process's data named with the same key!), stored in `destination`. If there is no entry named by `key` then `destination` is left unchanged. The return value is used to tell what happened.

If you simply want to verify whether an entry is present in the cache then see [contains](kshareddatacache.md#contains)().

`key` The key to find in the cache.

`destination` Is set to the value of `key` in the cache if `key` is present, left unchanged otherwise.

Returns true if `key` was present in the cache (`destination` will also be updated), false if `key` was not present (`destination` will be unchanged).

### unsigned int KSharedDataCache::freeSize() const {#freeSize}

Returns the amount of free space in the cache, in bytes. Due to implementation details it is possible to still not be able to fit an entry in the cache at any given time even if it is smaller than the amount of space remaining.

### bool KSharedDataCache::insert(const QString &*key*, const QByteArray &*data*) {#insert}

Attempts to insert the entry `data` into the shared cache, named by `key`, and returns true only if successful.

Note that even if the insert was successful, that the newly added entry may be evicted by other processes contending for the cache.

### \[since 6.18\] bool KSharedDataCache::remove(const QString &*key*) {#remove}

Attempts to remove an entry with the specified `key`. Returns `true` if an entry has been removed; otherwise returns `false`.

This function was introduced in Qt 6.18.

### void KSharedDataCache::setEvictionPolicy(KSharedDataCache::EvictionPolicy *newPolicy*) {#setEvictionPolicy}

Sets the entry removal policy for the shared cache to

`newPolicy`. The default is [EvictionPolicy::NoEvictionPreference](kshareddatacache.md#EvictionPolicy-enum).

*See also* [evictionPolicy](kshareddatacache.md#evictionPolicy)()

### void KSharedDataCache::setTimestamp(unsigned int *newTimestamp*) {#setTimestamp}

Sets the shared timestamp of the cache. Timestamping is supported to allow applications to more effectively "version" the data stored in the cache. However, the timestamp is shared with all applications using the cache so you should always be prepared for invalid timestamps.

When the cache is first created (note that this is different from attaching to an existing shared cache on disk), the cache timestamp is initialized to the time returned by `time(2)`. [KSharedDataCache](kshareddatacache.md) will not update the timestamp again, it is only updated through this method.

Example:

```cpp
QImage loadCachedImage(const QString &key)
{
    // Check timestamp
    if (m_sharedCache->timestamp() < m_currentThemeTimestamp) {
        // Cache is stale, clean it out.
        m_sharedCache->clear();
        m_sharedCache->setTimestamp(m_currentThemeTimestamp);
    }

    // Check cache and load image as usual...
}
```

`newTimestamp` The new timestamp to mark the shared cache with.

*See also* [timestamp](kshareddatacache.md#timestamp)()

### unsigned int KSharedDataCache::timestamp() const {#timestamp}

Returns the shared timestamp of the cache. The interpretation of the timestamp returned is up to the application. [KSharedDataCache](kshareddatacache.md) will initialize the timestamp to the time returned by `time(2)` on cache creation, but [KSharedDataCache](kshareddatacache.md) will not touch the timestamp again.

*See also* [setTimestamp](kshareddatacache.md#setTimestamp)()

### unsigned int KSharedDataCache::totalSize() const {#totalSize}

Returns the usable cache size in bytes. The actual amount of memory used will be slightly larger than this to account for required accounting overhead.
